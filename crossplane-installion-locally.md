### Install Docker Desktop on Windows 
To Install Docker Engine/Desktop on **Windows** system,for detailed instructions, refer to the [Docker official website](https://docs.docker.com/desktop/install/windows-install/ "Docker official website")

### Helm Install
To Install Helm Binary,for detailed instructions, refer to the [Web Url](https://helm.sh/docs/intro/install/ "Helm Install")


### Kind Install on windows

```
curl.exe -Lo kind-windows-amd64.exe https://kind.sigs.k8s.io/dl/v0.17.0/kind-windows-amd64
Move-Item .\kind-windows-amd64.exe c:\some-dir-in-your-PATH\kind.exe

```

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

