# INCIDENT-006: VMware Datastore Full

## Summary

A VMware datastore reached critical capacity, causing virtual machines to experience performance degradation and snapshot operations to fail.

---

## Impact

Some virtual machines experienced disk latency.

Snapshot creation failed for several VMs.

Backup jobs were unable to complete.

---

## Detection

Monitoring alerts indicated datastore usage above 95%.

VMware vCenter reported datastore capacity warnings.

---

## Investigation

Check datastore usage in VMware.

Get-Datastore

Identify datastores with high utilization.

Get-Datastore | Sort-Object FreeSpaceGB

Check virtual machines with snapshots.

Get-VM | Get-Snapshot

Identify snapshots consuming datastore space.

Get-VM | Get-Snapshot | Sort-Object Created

---

## Root Cause

Snapshots created during maintenance or backup operations were not removed after completion.

Over time these snapshots consumed significant datastore capacity.

---

## Resolution

Remove old snapshots.

Get-Snapshot -VM "vm-name" | Remove-Snapshot -Confirm:$false

Alternatively remove all snapshots across VMs.

Get-VM | Get-Snapshot | Remove-Snapshot -Confirm:$false

Monitor datastore usage after cleanup.

---

## Outcome

Datastore space was reclaimed and VM performance returned to normal.

Backup operations resumed successfully.

---

## Preventive Measures

Monitor snapshot age and datastore usage.

Implement alerts for large or long-running snapshots.

Ensure maintenance procedures include snapshot cleanup.

---

## Lessons Learned

Snapshots should only be temporary and must be removed after maintenance tasks.

Regular monitoring of datastore usage helps prevent capacity-related incidents.

