# MSM sidecar setup for testing

The scripts/YAMLs here set up the old MSM RTSP sidecar demo on a Kubernetes cluster.

Scripts are:

1. start 
2. end

YAML files are:

1. msm-prep.yaml (sets up config maps etc.)
2. cni-prep.yaml
3. cni.yaml (chained micro-CNI)
4. webhook.yaml (admission webhook)
5. k8s-api.yaml (K8s API helper app)
6. camera.yaml (fake camera feed including RTSP and Envoy sidecars)
7. gateways.yaml (gateway DaemonSet for north/south traffic)
8. gateway2.yaml (packet doubling gateway)
9. envoy.yaml (Envoy gateway)
10. simple-server.yaml (packet loss simulator app)

Instructions:

1. run ./start
2. connect to the RTSP server from one or mode RTSP clients (e.g. VLC) with "rtsp://node-ip:xxxx/camera"
3. enjoy the video

Values for xxxx:

1. 8554 (MSM using gateways.yaml proxy)
2. 8854 (Envoy)
3. 9554 (MSM using gateway2.yaml proxy)
4. 30554 (kube-proxy / NodePort)

Note that 9554 and 30554 will be TCP only so VLC will have to fall back to that.

The packet loss simulator source is at [https://github.com/media-streaming-mesh/simple-api-server]()

There's also a UI [demo](https://github.com/media-streaming-mesh/msm-ui), though it only works fully with Google Chrome on x86.






