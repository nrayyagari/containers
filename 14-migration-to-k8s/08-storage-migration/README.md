# Storage Migration

## What It Is
Storage Migration covers How persistent data semantics change under scheduling.

## Why It Matters
It matters because Kubernetes migration fails when Docker assumptions are copied over unchanged.

## Key Points
- Image layers, writable layers, and persistent volumes have different lifecycles.
- Copy-on-write behavior affects both performance and troubleshooting.
- Durability depends on where data is stored, not on whether the write succeeded once.

## Lab Focus
Use the lab to prove how persistent data semantics change under scheduling.
- Key commands:
  - `kubectl apply -f - <<'YAML'`
  - `kubectl apply -f - <<'YAML'`
  - `kubectl exec pvc-writer -- cat /data/value.txt`
- Finish only when:
  - PVC in Bound state.
  - Data present before and after pod recreation.

## Common Mistakes
- Mixing up image content, writable-layer content, and durable data.
- Testing writes without proving what survives a restart.

## Next
Read the lab after this README and use the output as proof, not as a checklist.
Then continue to [Service Mesh](../09-service-mesh/README.md).
