### Install Docker Desktop on Windows 
To Install Docker Engine/Desktop on **Windows** system,for detailed instructions, refer to the [Docker official website](https://docs.docker.com/desktop/install/windows-install/ "Docker official website")

### Helm Install
To Install Helm Binary,for detailed instructions, refer to the [Web Url](https://helm.sh/docs/intro/install/ "Helm Install")

Need to add the path in system environment variables PATH


### Kind Install on windows

```
curl.exe -Lo kind-windows-amd64.exe https://kind.sigs.k8s.io/dl/v0.17.0/kind-windows-amd64
Move-Item .\kind-windows-amd64.exe c:\kind\kind.exe

```
Need to add the path in system environment variables PATH

### Setup kind cluster
kind version
# output: kind v0.17.0 go1.19.2 windows/amd64
kind create cluster

### to delete cluster
kind delete cluster

kind create cluster --name ucp-learn --config cluster/clusterconfig.yaml
-- verify output with "kubectl cluster-info --context kind-ucp-learn"
-- output: 
        Kubernetes control plane is running at https://127.0.0.1:61388
        CoreDNS is running at https://127.0.0.1:61388/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy

kubectl get nodes
-- output:
      NAME                      STATUS   ROLES           AGE     VERSION
      ucp-learn-control-plane   Ready    control-plane   3m19s   v1.25.3
      ucp-learn-worker          Ready    <none>          2m45s   v1.25.3
      ucp-learn-worker2         Ready    <none>          2m46s   v1.25.3

kubectl get pods
-- output: No resources found in default namespace.

kubectl get pods -n crossplane-system
-- output: No resources found in crossplane-system namespace.

### Crossplane install

Review crossplane-stable release [Crossplane official website](https://charts.crossplane.io/stable)

```
helm repo add \
crossplane-stable https://charts.crossplane.io/stable
helm repo update

helm install crossplane \
crossplane-stable/crossplane \
--namespace crossplane-system \
--create-namespace
```
### Argo CD Install
```
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

kubectl port-forward svc/argocd-server -n argocd 8080:443

kubectl exec -it {argocd-server-pod-id} argocd admin initial-password -n argocd

use the password to login into local argocd and then change your password.
```
### Azure CrossPlane Provider Install

```
cat <<EOF | kubectl apply -f -
apiVersion: pkg.crossplane.io/v1
kind: Provider
metadata:
  name: provider-azure-network
spec:
  package: xpkg.upbound.io/upbound/provider-azure-network:v0.34.0
EOF

```

