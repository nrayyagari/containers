# Storage Migration Lab

## Goal
Verify persistent data survives pod recreation using PVC.

## Prerequisites
- kubectl access to a cluster with default StorageClass.

## Steps
1. Create PVC.
   COMMAND: kubectl apply -f - <<'YAML'
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: mig-pvc
spec:
  accessModes: [ReadWriteOnce]
  resources:
    requests:
      storage: 1Gi
YAML
2. Create writer pod.
   COMMAND: kubectl apply -f - <<'YAML'
apiVersion: v1
kind: Pod
metadata:
  name: pvc-writer
spec:
  containers:
  - name: app
    image: alpine:3.20
    command: ["sh","-c","echo migrated-data > /data/value.txt; sleep 300"]
    volumeMounts:
    - name: data
      mountPath: /data
  volumes:
  - name: data
    persistentVolumeClaim:
      claimName: mig-pvc
YAML
3. Verify data then recreate pod.
   COMMAND: kubectl exec pvc-writer -- cat /data/value.txt
   COMMAND: kubectl delete pod pvc-writer
   COMMAND: kubectl apply -f - <<'YAML'
apiVersion: v1
kind: Pod
metadata:
  name: pvc-writer
spec:
  containers:
  - name: app
    image: alpine:3.20
    command: ["sh","-c","sleep 300"]
    volumeMounts:
    - name: data
      mountPath: /data
  volumes:
  - name: data
    persistentVolumeClaim:
      claimName: mig-pvc
YAML
   COMMAND: kubectl exec pvc-writer -- cat /data/value.txt

## Expected Observations
- PVC binds successfully.
- Data persists across pod recreation.
- Behavior differs from ephemeral writable layer.

## Verify
- PVC in Bound state.
- Data present before and after pod recreation.
- You documented one reclaim-policy risk.

## Cleanup
- COMMAND: kubectl delete pod pvc-writer --ignore-not-found
- COMMAND: kubectl delete pvc mig-pvc --ignore-not-found

## Concept Check
- Which evidence proves persistence across pod recreation, not just restart luck?
- What reclaim-policy misunderstanding can cause irreversible data loss?
- Which restore test should be required before stateful migration cutover?

## Why This Lab Proves Understanding
- You validated persistence using stateful lifecycle evidence.

## Answer Key
Pass when all Verify points are satisfied and cleanup is complete.
