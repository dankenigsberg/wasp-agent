```console
# Build
$ bash to.sh build
$ bash to.sh push  # only to my account right now

# Deploy
$ <log into ocp 4.15 or higher>
$ bash to.sh deploy

# Demo
$ oc apply -f manifests/static.yaml
$ oc apply -f manifests/stress.yaml
# Now increase the stress deployment replicacount in order to push out
# memory of static pods

# Destroy
$ bash to.sh destroy
```

The POC does the following
- Node
  - Enable swap on the node
  - Disable swap in the system.slice
  - Set io latency for system.slice
  - Install an OCI hook to enable swap
- Workloads
  - Enable swap=max for every burstable pod using an OCI hook