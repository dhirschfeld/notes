---
tags: [System Administration/Bash]
title: Bash Profile Loading
created: '2021-12-15T01:58:21.474Z'
modified: '2023-05-18T03:17:36.658Z'
---

# Bash Profile Loading

* https://www.gnu.org/software/bash/manual/html_node/Bash-Startup-Files.html#Bash-Startup-Files
* https://itectec.com/ubuntu/ubuntu-scripts-in-etc-profile-d-being-ignored/
* https://stackoverflow.com/questions/18186929/what-are-the-differences-between-a-login-shell-and-interactive-shell
* https://linuxhint.com/understanding_bash_shell_configuration_startup/


```bash
echo exit | strace bash -li |& grep '^open'
```
* https://unix.stackexchange.com/a/334389

