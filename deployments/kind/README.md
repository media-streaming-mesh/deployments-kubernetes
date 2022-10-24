# Kind Setup

This is the setup for testing MSM locally using [Kind](https://kind.sigs.k8s.io).

There are kind setups for the old "sidecar" demo and for the newer MSM demo based on separate control plane and data plane proxies.

Both setups use the Calico CNI.

Files shared between both demos are:

1. calico-prep (pulls Calico Docker images)
2. calico (loads Calico Docker images into kind and start Calico)
3. kind-calico.yaml (Calico config file)
4. end (shuts cluster down)

Files for the sidecar demo are:

1. sidecar-prep (pulls demo Docker images)
2. sidecar (loads sidecar demo Docker images into Kind)
3. start-sidecar (runs the sidecar demo)

Files for the MSM demo are:

1. msm-prep (pulls MSM Docker images)
2. msm (loads MSM Docker images into Kind)
3. start-msm (runs the MSM demo)

