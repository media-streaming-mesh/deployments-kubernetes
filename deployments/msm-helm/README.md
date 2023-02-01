Install Helm 

Follow the official doc instructions from https://helm.sh/docs/intro/install/

or

from script: $ curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
			 $ chmod 700 get_helm.sh
			 $ ./get_helm.sh

or mac users "brew install helm"

Install MSM Helm

helm install APP_NAME FOLDER_NAME_CONTAINING_HELM_TEMPLATES_AND_VALUES_YAMLS --values PATH_TO_VALUES_YAML_FILE

example: 

helm install msm-dev-release msm-helm/ --values msm-helm/values.yaml

NOTE: Need to be outside the FOLDER_NAME_CONTAINING_HELM_TEMPLATES_AND_VALUES_YAML_FILES (e.g. msm-helm) folder to execute this command.

Output of the above command should be similar to this:

NAME: APP_NAME
LAST DEPLOYED: DATE_AND_TIME_STAMP
NAMESPACE: default
STATUS: deployed
REVISION: 1
TEST SUITE: None

Verify the Deployment

"kubectl get all"

Test/Upgrade the Deployment via Helm

Try changing the "tag" value (which represents the docker image tag) in values.yaml file
e.g:

proxyImage:
  name: ciscolabs/msm-proxy
  tag: latest

proxyImage:
  name: ciscolabs/msm-proxy
  tag: "20230123"   ----> this is docker image tag and must be in ""


