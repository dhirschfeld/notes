---
tags: [Terraform]
title: Wait For External IP
created: '2022-09-12T11:45:36.726Z'
modified: '2022-09-12T11:46:55.952Z'
---

# Wait For External IP

```terraform
resource "null_resource" "wait_for_external_ip" {
  depends_on = [helm_release.traefik]
  triggers = {
    always_run = "${timestamp()}"
  }
  provisioner "local-exec" {
    interpreter = ["/bin/bash", "-lc"]
    command     = <<-EOT
      set -eou pipefail
      tmpfile=$(mktemp)
      trap "rm -fv $tmpfile" EXIT
      az aks get-credentials -f $tmpfile -n ${var.cluster_name} -g ${var.cluster_resource_group} --admin
      export KUBECONFIG=$tmpfile
      deadline=$(( $(date +%s) + 20 ))
      while [[ $(date +%s) -lt $deadline ]]; do
        echo "Waiting for external ip..."
        external_ip=$(kubectl -n ${var.namespace} get svc traefik -o=jsonpath='{.status.loadBalancer.ingress[0].ip}')
        if [[ -n "$external_ip" ]]; then
          echo -e "\033[0;32mFound External IP: $external_ip\033[0m"
          exit 0
        fi
        sleep 2
      done
      echo -e "\033[0;31mERROR:\033[0m Timed out waiting for external ip!"
      exit 1
    EOT
  }
}
```
