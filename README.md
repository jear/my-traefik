# my-traefik
```
# https://traefik.io/blog/install-and-configure-traefik-with-helm/


# helm repo add traefik https://helm.traefik.io/traefik
helm repo add traefik https://traefik.github.io/charts
helm repo update

helm repo list
traefik                 https://traefik.github.io/charts

helm search repo traefik -l
WARNING: Kubernetes configuration file is group-readable. This is insecure. Location: /home/ubuntu/.kube/gpu01.yaml
WARNING: Kubernetes configuration file is world-readable. This is insecure. Location: /home/ubuntu/.kube/gpu01.yaml
NAME                    CHART VERSION   APP VERSION     DESCRIPTION
traefik/traefik         21.1.0          v2.9.7          A Traefik based Kubernetes ingress controller
traefik/traefik-mesh    4.1.1           v1.4.8          Traefik Mesh - Simpler Service Mesh
traefik/traefikee       1.7.0           v2.9.1          Traefik Enterprise is a unified cloud-native ne...
traefik/hub-agent       1.2.2           v1.1.0          Traefik Hub is an all-in-one global networking ...
traefik/maesh           2.1.2           v1.3.2          Maesh - Simpler Service Mesh

helm fetch traefik/traefik --version 21.1.0

tar zxvf traefik-21.1.0.tgz

cp traefik/values.yaml my-values-21.1.0.yaml
rm -fr traefik && rm traefik-21.1.0.tgz

# helm install my-traefik traefik/traefik  -f my-values-21.1.0.yaml --namespace traefik-v2 --create-namespace

helm upgrade --install my-traefik traefik/traefik  --namespace traefik-v2 --create-namespace -f gpu01-values.yaml --version 21.1.0

# ipwhitelist  .....   externalTrafficPolicy 
https://community.traefik.io/t/limiting-clients-to-specific-ips-ipwhitelist/9568/3

k edit svc -n traefik-v2 my-traefik 
  externalTrafficPolicy: Local
```
