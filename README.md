# application-hub-chart

## Get Started

- Clone the application-hub-chart repository:
```
git clone https://github.com/EOEPCA/application-hub-chart.git
cd application-hub-chart
```

- Install the JupyterHub chart 
```
helm repo add jupyterhub https://jupyterhub.github.io/helm-chart/
helm repo update
```
  This should show output like:
```
Hang tight while we grab the latest from your chart repositories...
...Skip local chart repository
...Successfully got an update from the "stable" chart repository
...Successfully got an update from the "jupyterhub" chart repository
Update Complete. ⎈ Happy Helming!⎈
```

- Deploy the application-hub-chart using the following command:
```
helm upgrade --cleanup-on-fail \
  --install application-hub jupyterhub/jupyterhub \
  --namespace application-hub \
  --create-namespace \
  --version=1.0.0 \
  --values config.json
```

- Port forward traffic to the k8s Service proxy-public with kubectl to access it from your computer.
```
kubectl --namespace=eoepcahub port-forward service/proxy-public 8080:http
```
- Try insecure HTTP access: http://localhost:8080


