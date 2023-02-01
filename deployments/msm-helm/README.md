# MSM Deployment via Helm

### Install Helm 

Follow the official doc instructions from https://helm.sh/docs/intro/install/

or

from script: 

	$ curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3

	$ chmod 700 get_helm.sh
		
	$ ./get_helm.sh

or if on Mac

	$ brew install helm

### Install MSM

> helm install APP_NAME msm-helm/ --values msm-helm/values.yaml

example: 

	$ helm install msm-dev-release msm-helm/ --values msm-helm/values.yaml

**NOTE**: Need to be outside the msm-helm folder to execute this command.

### Verify the Deployment

	$ helm ls

	$ kubectl get all

### Test/Upgrade the Deployment via Helm

Try changing the "tag" value (which represents the docker image tag) in values.yaml file.
e.g:

	proxyImage:

  		name: ciscolabs/msm-proxy
  
  		tag: latest

	proxyImage:

  		name: ciscolabs/msm-proxy
  
  		tag: "20230123"   ----> this is docker image tag and must be in ""
  
execute the helm upgrade command

	$ helm upgrade msm-dev-release msm-helm/ --values msm-helm/values.yaml
	
### Verify the Upgrade

	$ kubectl get all
	
Verify the STATUS (may take few seconds to show/update). The pod(s) whose tag value(s) was/were changed will go through the lifecycle (Terminating -> ContainerCreating -> Running)
