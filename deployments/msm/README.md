# MSM setup for testing

The scripts/YAMLs here set up a basic MSM deployment on a Kuberneters cluster

Scripts are:

1. start-all (starts the whole setup)
2. start-msm (just starts the core components)
3. start-rtsp (starts RTSP client and server pods)
4. end-all / end-msm / end-rtsp (shutdown scripts)

YAML files are:

1. webhook-prep.yaml
2. cni-prep.yaml
2. cni.yaml (chained micro-CNI)
3. webhook.yaml (admission webhook)
4. msm-controller.yaml (control plane)
5. msm-controller-svc.yaml (control plane service)
6. msm-proxy.yaml (not currently used by scripts) 
7. msm-gateway.yaml (RTP proxy and gateway stub)
8. rtsp-server.yaml
9. rtsp-svc.yaml (service that maps onto the RTSP server)
10. rtsp-client.yaml

Instructions:

1. run start-all
2. go into the RTSP server pod and do "./start"
1. connect to the RTSP server from one or mode RTSP clients (e.g. VLC) with "rtsp://node-ip:8554/mystream"
1. enjoy the video 

If you hit issues you can do stop-rtsp and then start-rtsp to get a new RTSP server (remember to run "./start" in the server pod).

Worst case you can do stop-all and then start-all etc.


