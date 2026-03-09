# Server Data Migration Using rsync

## Problem

Application data needed to be migrated from an old server to a new server with minimal downtime.

---

## Environment

Linux servers

SSH connectivity

---

## Investigation

Verify network connectivity between servers.

ping destination-server

Check disk space on destination server.

df -h

---

## Resolution

Use rsync to transfer data.

rsync -aHAXxv --progress /source_directory/ user@destination:/destination_directory/

Perform incremental sync before final cutover.

rsync -aHAXxv --delete /source_directory/ user@destination:/destination_directory/

---

## Result

Application data successfully migrated with minimal downtime.

