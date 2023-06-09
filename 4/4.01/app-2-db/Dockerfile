# $ sudo apt-get upgrade docker-ce
# $ sudo systemctl restart docker.service
# $ sudo chown -R $USER:$USER /usr/src/app/files
# $ docker build -t <USER_NAME>/app-2-db:v4.01 .
# $ docker run -p 3001:3001 --name app-2-db <USER_NAME>/app-2-db
# $ k3d cluster create --port 8082:30080@agent:0 -p 8081:80@loadbalancer --agents 2
# $ kubectl cluster-info
# $ docker exec k3d-k3s-default-agent-0 mkdir -p /tmp/kube
# $ sudo -i -u postgres 
# $ psql
# $ sudo -u postgres psql
# $ kubectl create namespace <NAME_SPACE>
# $ kubectl apply -f manifests/ -n <NAME_SPACE>
# $ kubectl get all --all-namespaces
# $ kubectl create -f manifests/postgres-secrets.yaml -n app-db-namespace
# $ kubectl get secret postgres-secret-config -n app-db-namespace -o yaml
# $ kubectl create -f manifests/postgresql.yaml -n app-db-namespace
# $ kubectl exec -it postgresql-ss-0 -n app-db-namespace bash
# $ kubectl exec -it <POD_NAME> -n app-db-namespace -- psql -U postgres
# root# ls -la /var/lib/postgresql/data/pgdata/pg_hba.conf
# $ kubectl create -f manifests/deployment-app-2-db.yaml -n app-db-namespace
# $ docker push <USER_NAME>/app-2-db
# $ docker pull docker.io/<USER_NAME>/app-2-http
# $ kubectl create configmap app-db-env -n app-db-namespace --from-env-file=.env
# $ kubectl get configmap -n app-db-namespace
# $ kubectl describe configMap app-db-env -n app-db-namespace
# postgres# CREATE TABLE counters (ID SERIAL PRIMARY KEY, COUNTER INT NOT NULL); 
# $ docker info | grep -i cgroup
# $ docker ps
# $ k3d cluster delete
# $ k3d cluster create --port 8082:30080@agent:0 -p 8081:80@loadbalancer --agents 2
# $ kubectl cluster-info
# $ docker exec k3d-k3s-default-agent-0 mkdir -p /var/lib/postgresql/data
# $ kubectl create namespace <NAME_SPACE>
# $ kubectl delete configmap app-db-env -n app-db-namespace
# $ kubectl create configmap app-db-env -n app-db-namespace 
# $ docker exec k3d-k3s-default-agent-0 mkdir -p /tmp/kube
# $ docker exec k3d-k3s-default-agent-0 mkdir -p /data/pgdata
# $ kubectl delete -f manifests/
# $ kubectl create namespace <NAME_SPACE>
# $ kubectl apply -f manifests/ -n app-db-namespace
# $ kubectl describe pod <POD_NAME> -n app-db-namespace
# $ kubectl get svc -n <NAME_SPACE>
# $ kubectl get ing -n <NAME_SPACE>
# $ kubectl get pods -n <NAME_SPACE>
# $ kubectl get all --all-namespaces
# $ kubectl get pods -n <NAME_SPACE>
# $ kubectl get nodes -n <NAME_SPACE>
# $ kubectl describe deployment app-2-db-dep -n <NAME_SPACE>
# $ kubectl logs <POD_NAME> -c app-2-db
# $ kubectl logs <POD_NAME> -n <NAME_SPACE>
# $ kubectl describe pod <POD_NAME> -n <NAME_SPACE>
# $ kubectl port-forward <POD_NAME> 8081:3001
# $ kubectl expose manifests/service
# http://localhost:8081/pingpong
# $ kubectl get jobs --all-namespaces | sed '1d' | awk '{ print $2, "--namespace", $1 }' | while read line; do kubectl delete jobs $line; done
# $ kubectl rollout undo deployment flaky-update-dep

FROM node:alpine

WORKDIR /usr/src/app

RUN npm install npm@latest -g

RUN npm cache clean --force

RUN npm config rm proxy 

RUN npm config rm https-proxy

COPY package* ./

RUN npm ci

RUN apk --no-cache add curl

COPY . .

EXPOSE 3001

CMD ["npm", "start"]