# kube-ao
Kubernetes assets for running AppOptics

## Docker

Replace `APPOPTICS_TOKEN` in `conf/appoptics-config.yaml` and then build and run the docker container with:
```
docker build -t kube-ao .
docker run kube-ao
```

To run a bash shell in the container instead:
```
docker run -it kube-ao /bin/bash
```

## Kubernetes

To deploy to Kubernetes, first update `APPOPTICS_TOKEN` in `conf/appoptics-config.yaml` and then push it as a secret to your namespace:
```
kubectl create secret -n <your-namespace-here> generic kube-ao-config-secret --from-file=./conf/appoptics-config.yaml
```
 
Then replace `<your-namespace-here>` in `kube-ao-deployment.yaml` and run:
```
kubectl apply -f kube-ao-deployment.yaml
```


