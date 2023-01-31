# MSM K3D Setup

- Install K3D https://k3d.io/v5.4.6/#installation 
     
     curl -s https://raw.githubusercontent.com/k3d-io/k3d/main/install.sh | bash

     or

     (For Mac users "brew install k3d")


     What is k3d?
		
			k3d is a lightweight wrapper to run k3s (Rancher Lab’s minimal Kubernetes distribution) in docker.

			k3d makes it very easy to create single- and multi-node k3s clusters in docker, e.g. for local development on Kubernetes.


- Create a cluster 

    k3d cluster create NAME [flags]

    	example for MSM with 2 Nodes and 1 Server: "k3d cluster create msm --agents 2 --servers 1"

    Test/Use the new Cluster

    	"kubectl cluster-info"
    	"kubectl get nodes"

- Copy Test Video to Docker Container (/tmp/ folder)

	"docker cp {options} CONTAINER_ID:SRC_PATH DEST_PATH "

	example: "docker cp video.mpeg CONTAINER_ID:/tmp/"

	to get container Id "docker ps -a"

- Start MSM

	Use Deployment-Kubernetes Repo for that. Follow the README in msm-demo folder, it has "./start-all" script.

	Note: may need to change the Cluster IPs from "10.96" to "10.43" of "msm-controller-scv.yaml", "msm-gateway.yaml", "rtsp-svc.yaml", "webhook.yaml"

	also change nodeSelector from "" to "true" in "msm-controller.yaml" and "webhook.yaml"

	From: 

		nodeSelector:
        node-role.kubernetes.io/control-plane: ""

    To:

    	nodeSelector:
        node-role.kubernetes.io/control-plane: "true"

- Testing Internal Client(s)

	Bash into Client Pod

	"kubectl exec -it 'CLIENT_POD_NAME' --  bash"

	Start Streamimg

	"ffmpeg -i rtsp://IP_OF_SERVER_POD:554/mystream -c copy output.mp4"

- Testing External Client(s)

	RUN port forwarding to test outside kubernetes/k3d cluster

	"kubectl get service"

	"kubectl port-forward service/SERVICE_NAME 8080:554"

	Open VLC

	Open Network source

	"rtsp://IP_OF_MSM_GATEWAY_POD:8554/mystream"

