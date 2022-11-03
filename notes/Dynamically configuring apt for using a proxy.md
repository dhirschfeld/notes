---
tags: [System Administration]
title: Dynamically configuring apt for using a proxy
created: '2022-10-18T03:47:40.014Z'
modified: '2022-10-18T03:48:14.263Z'
---

# Dynamically configuring `apt` for using a proxy

```bash
#!/bin/bash

set +e

print_msg() {
    printf '\x0d%s\n' "$1" >&2
}

hostname="$(basename ${HTTPS_PROXY%:*} 2> /dev/null)"

# check if proxy is resolvable
getent hosts "${hostname}" > /dev/null
if [ "$?" -eq "0" ]; then
    echo -n "${HTTPS_PROXY}"
    print_msg "[DEBUG] Detected proxy ${HTTPS_PROXY}"
else
    echo -n "DIRECT"
    print_msg "[DEBUG] No proxy detected!"
fi
```

