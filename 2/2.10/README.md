# $ docker build -t <USER_NAME>/todo-backend-db:2.9.13 .
# $ docker push <USER_NAME>/todo-backend-db:2.9.13
# $ docker exec k3d-k3s-default-agent-0 mkdir -p /var/lib/postgresql/data/pgdata
# $ kubectl create namespace <NAME_SPACE>
# $ kubectl delete configmap app-db-env -n todos-db-namespace
# $ kubectl create configmap app-db-env -n todos-db-namespace --from-env-file=.env
# $ kubectl get configmap -n todos-db-namespace
# $ kubectl describe configMap app-db-env -n todos-db-namespace
# $ kubectl delete -f manifests/
# $ kubectl delete -f manifests/deployment-backend.yaml -n todos-db-namespace
# $ kubectl apply -f manifests/ -n todos-db-namespace
# $ kubectl create -f manifests/deployment-backend.yaml -n todos-db-namespace
# $ kubectl get pods -n todos-db-namespace
# $ kubectl get svc -n todos-db-namespace
# $ kubectl get ing -n todos-db-namespace
# $ kubectl describe deployment todos-backend-db-dep -n todos-db-namespace
# $ kubectl describe pod <POD_NAME> -n <NAME_SPACE>
# $ kubectl logs <POD_NAME> -c <CONTAINER_NAME> -n todos-db-namespace
# $ kubectl logs <POD_NAME> -n <NAME_SPACE>
# $ kubectl exec <POD_NAME> -n todos-db-namespace -- printenv
# $ kubectl get jobs --watch -n todos-db-namespace
# $ kubectl create -f manifests/shell-script.yaml
# $ kubectl describe cronjob -n todos-db-namespace
# $ kubectl describe configmap shell-script -n todos-db-namespace 
# $ kubectl delete jobs $(kubectl get jobs -n todos-db-namespace | awk '$2 ~ 1/1' | awk '{print $1}')
# $ kubectl delete job $(kubectl get jobs -n todos-db-namespace | awk '$2 ~ 1' | awk '{print $1}')
# $ kubectl get jobs --all-namespaces | sed '1d' | awk '{ print $2, "--namespace", $1 }' | while read line; do kubectl delete jobs $line; done
# $ kubectl delete job $(kubectl get jobs --all-namespaces -o jsonpath='{.items[?(@.status.completionTime)].metadata.name}')
# $ curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
# $ chmod 700 get_helm.sh
# $ ./get_helm.sh
# $ ls -l /usr/local/bin/helm
# $ curl https://baltocdn.com/helm/signing.asc | sudo apt-key add -
# $ sudo apt-get install apt-transport-https --yes
# $ echo "deb https://baltocdn.com/helm/stable/debian/ all main" | sudo tee /etc/apt/sources.list.d/helm-stable-debian.list
# $ sudo apt-get update
# $ sudo apt-get install helm
# $ helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
# $ helm repo add stable https://charts.helm.sh/stable
# $ kubectl create namespace prometheus
# $ helm install prometheus-community/kube-prometheus-stack --generate-name --namespace prometheus
# kubectl -n prometheus port-forward <POD_NAME> 3000
FROM node:alpine
# GRAFANA: USER: admin PASSWORD: 
# https://linuxblog.xyz/posts/kube-prometheus-stack/
# $ kubectl create namespace loki
# $ helm repo add loki https://grafana.github.io/loki/charts
# $ helm repo update
# $ helm upgrade --install loki loki/loki-stack --namespace=loki --set grafana.enabled=true
# $ kubectl get secret loki-grafana --namespace=loki -o jsonpath="{.data.admin-password}" | base64 --decode ; echo
