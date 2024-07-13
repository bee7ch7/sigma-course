
# inside docker container:
apt update
apt install -y vim
vi /etc/nginx/conf.d/status.conf
```
server {
    listen 8080;
    # Optionally: allow access only from localhost
    # listen 127.0.0.1:8080;

    server_name _;

    location /status {
        stub_status;
    }
}

```
# test:
curl localhost:8080/status

# nginx exporter:
`docker run -p 9113:9113 nginx/nginx-prometheus-exporter:1.1.0 --nginx.scrape-uri=http://<nginx>:8080/status
`






















# kubernetes

kubectl run my-nginx --image=nginx

kubectl create deployment my-nginx --image=nginx --replicas=2
kubectl scale deployment my-nginx --replicas=5

kubectl describe deployment my-nginx
kubectl get deployment my-nginx -o yaml

kubectl expose deployment nginx

# publish as LB:
minikube ip -p sigma-lab
k edit svc nginx

# add 
externalIPs:
  - 192.168.76.2


# secrets
kubectl create secret generic my-secret --from-literal=username=admin --from-literal=password=P@rol123
