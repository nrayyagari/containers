# Storage Migration Lab

## Goal
Create persistent storage, write data from a pod, and verify data survives pod recreation.

## Prerequisites
- `kubectl` connected to a test cluster with a default StorageClass

## Steps
1. Create PVC:
   ```bash
   cat <<'YAML' | kubectl apply -f -
   apiVersion: v1
   kind: PersistentVolumeClaim
   metadata:
     name: demo-pvc
   spec:
     accessModes: ["ReadWriteOnce"]
     resources:
       requests:
         storage: 1Gi
   YAML
   ```
2. Create writer pod mounting PVC:
   ```bash
   cat <<'YAML' | kubectl apply -f -
   apiVersion: v1
   kind: Pod
   metadata:
     name: pvc-writer
   spec:
     containers:
     - name: app
       image: alpine:3.20
       command: ["sh","-c","echo migrated-data > /data/value.txt; sleep 3600"]
       volumeMounts:
       - name: data
         mountPath: /data
     volumes:
     - name: data
       persistentVolumeClaim:
         claimName: demo-pvc
   YAML
   ```
3. Verify file exists:
   ```bash
   kubectl exec pvc-writer -- cat /data/value.txt
   ```
4. Delete and recreate pod using same PVC.
5. Verify file still exists after recreation.

## Verify
- PVC reaches `Bound` state.
- Data written before pod deletion is present after pod recreation.
- You can explain why this differs from container writable layer behavior.

## Cleanup
- `kubectl delete pod pvc-writer --ignore-not-found`
- `kubectl delete pvc demo-pvc --ignore-not-found`

## Next
Define backup/restore tests for each stateful service class.

## Concept Check
- What failure mode appears if reclaim policy is misunderstood?
- Why is pod restart success not proof of data durability?
- Which SLO should influence storage class choice during migration?

## Why This Lab Proves Understanding
- Verify checks binding, persistence semantics, and conceptual contrast with ephemeral layers.
- Cleanup confirms storage resources are intentionally released.

## Answer Key
A lab is considered successful only when every Verify condition is true and cleanup is completed.

Pass criteria (all required):
- [ ] PVC reaches `Bound` state.
- [ ] Data written before pod deletion is present after pod recreation.
- [ ] You can explain why this differs from container writable layer behavior.
- [ ] Cleanup commands executed successfully.

Fail criteria (any one means FAIL):
- Any Verify condition not met.
- Persistence semantics not demonstrated.
- Environment not in clean state after cleanup.

If failed, record:
- Exact command that failed.
- Error output.
- Root cause and fix applied before rerun.
