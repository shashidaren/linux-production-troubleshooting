# VMware Snapshot Removal Procedure

## Purpose

Procedure for safely removing VMware snapshots.

---

## Identify Snapshots

Get-VM | Get-Snapshot

---

## Identify Snapshot Age

Get-VM | Get-Snapshot | Sort-Object Created

---

## Remove Snapshot

Get-Snapshot -VM "vm-name" | Remove-Snapshot -Confirm:$false

---

## Verify Snapshot Removal

Get-VM | Get-Snapshot

---

## Best Practices

Avoid keeping snapshots longer than necessary.

Monitor datastore usage regularly.

