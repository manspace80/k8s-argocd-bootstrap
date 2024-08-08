# helm repo add metallb https://metallb.github.io/metallb
# helm repo update
# helm install metallb metallb/metallb --create-namespace --namespace metallb-system
# k apply -f addresspool.yaml -f l2advertisement.yaml
kubectl get configmap kube-proxy -n kube-system -o yaml | \
sed -e "s/strictARP: false/strictARP: true/" | \
kubectl apply -f - -n kube-system
