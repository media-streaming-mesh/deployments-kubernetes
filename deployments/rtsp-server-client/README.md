# RTSP Sever and Client Deployment via Helm

### Install Helm 

Follow the official doc instructions from https://helm.sh/docs/intro/install/

or

from script: 

	$ curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3

	$ chmod 700 get_helm.sh
		
	$ ./get_helm.sh

or if on Mac

	$ brew install helm

### Install RTSP Server/Client

**NOTE**: Please deploy MSM App first before deploying RTSP Server/Client. Refer to Msm-Helm README.

> helm install APP_NAME rtsp-server-client/ --values rtsp-server-client/values.yaml

example: 

	$ helm install msm-rtsp rtsp-server-client/ --values rtsp-server-client/values.yaml

**NOTE**: Need to be outside the rtsp-server-client folder to execute this command.

### Verify the Deployment

	$ helm ls

	$ kubectl get all
