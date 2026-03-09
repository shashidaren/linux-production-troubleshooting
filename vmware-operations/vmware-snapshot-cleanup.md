# VMware Snapshot Cleanup

## Problem

Multiple virtual machines had accumulated large snapshots, causing datastore space consumption and performance degradation.

---

## Environment

VMware vSphere environment

Production cluster

---

## Investigation

Identify snapshots for VMs.

Get-VM | Get-Snapshot

List snapshots sorted by creation date.

Get-VM | Get-Snapshot | Sort-Object Created

Identify old snapshots consuming datastore space.

---

## Root Cause

Snapshots created during maintenance or backup operations were not removed.

Over time these snapshots consumed significant datastore capacity.

---

## Resolution

Remove snapshots using PowerCLI.

Get-Snapshot -VM "vm-name" | Remove-Snapshot -Confirm:$false

Alternatively remove all snapshots.

Get-VM | Get-Snapshot | Remove-Snapshot -Confirm:$false

---

## Result

Datastore space was reclaimed and VM performance returned to normal.

---

## Lessons Learned

Snapshots should only be used temporarily and removed after maintenance tasks.

Monitoring alerts should be configured for large or long-running snapshots.

