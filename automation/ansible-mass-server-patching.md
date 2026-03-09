# Mass Server Patching Using Ansible

## Problem

A large group of Linux servers required security updates.

Manual patching would be inefficient and time-consuming.

---

## Environment

Enterprise Linux servers

Ansible automation

---

## Investigation

Verify connectivity to servers.

ansible all -m ping

Check system status.

ansible all -m command -a "uptime"

---

## Resolution

Clean yum cache.

ansible all -m command -a "yum clean all" -b

Apply updates.

ansible all -m command -a "yum update -y" -b

Rebuild grub configuration if kernel updates occurred.

ansible all -m command -a "/sbin/grub2-mkconfig -o /boot/grub2/grub.cfg" -b

Reboot servers.

ansible all -m command -a "reboot" -b

---

## Result

Security updates were applied across multiple servers in a controlled and efficient manner.

Automation significantly reduced operational effort.

