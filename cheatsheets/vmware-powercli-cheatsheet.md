# VMware PowerCLI Cheatsheet

## Connect to vCenter

Connect-VIServer -Server vcenter.example.com

---

## List Virtual Machines

Get-VM

---

## Get VM Details

Get-VM -Name vm-name

---

## List Snapshots

Get-VM | Get-Snapshot

---

## Remove Snapshot

Get-Snapshot -VM "vm-name" | Remove-Snapshot -Confirm:$false

---

## Get Datastores

Get-Datastore

---

## Get ESXi Hosts

Get-VMHost

