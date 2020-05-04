Kubernetes Installation
========================

### Prepare for helm installation Google Cloud GDE 
    kubectl create serviceaccount --namespace kube-system tiller
    kubectl create clusterrolebinding tiller-cluster-rule --clusterrole=cluster-admin --serviceaccount=kube-system:tiller
    kubectl patch deploy --namespace kube-system tiller-deploy -p '{"spec":{"template":{"spec":{"serviceAccount":"tiller"}}}}'


## General helm commands 

### install chart 
    kubectl create namespace jitsi-meet
    helm install -f values.yaml --namespace jitsi-meet --name jitsi-meet .
    helm status jitsi-meet
    kubectl get pods --namespace jitsi-meet

### update your installation after changing values.yaml 
    helm upgrade -f values.yaml jitsi-meet .

### delete you installation
    helm delete --purge jitsi-meet