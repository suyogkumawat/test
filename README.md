# test

Prometheus Setup in K8s Cluster

helm repo add prometheus-community https://prometheus-community.github.io/helm-charts


Full Process

 26  curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
   27  chmod 700 get_helm.sh
   28  ./get_helm.sh
   29  ls -l
   30  helm
   31  helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
   32  helm repo list
   33  helm repo add stable https://charts.helm.sh/stable
   34  helm repo update
   35  kubectl create namespace monitoring
   36  helm install kind-prometheus prometheus-community/kube-prometheus-stack --namespace monitoring --set prometheus.service.nodePort=30000 --set prometheus.service.type=NodePort --set grafana.service.nodePort=31000 --set grafana.service.type=NodePort --set alertmanager.service.nodePort=32000 --set alertmanager.service.type=NodePort --set prometheus-node-exporter.service.nodePort=32001 --set prometheus-node-exporter.service.type=NodePort
   37  kubectl get po -n monitoring
   38  kubectl get svc
   39  kubectl get svc -n monitoring
   40  kubectl port-forward svc/kind-prometheus-kube-prome-prometheus -n monitoring 30000:30000 --address=0.0.0.0 &
   41  kubectl port-forward svc/kind-prometheus-kube-prome-prometheus -n monitoring 9090:9090 --address=0.0.0.0 &
   42  kubectl get svc -n monitoring
   43  kubectl port-forward svc/kind-prometheus-grafana -n monitoring 3000:80 --address=0.0.0.0 &

