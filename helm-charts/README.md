# Provisioning Perses Dashboards with helm charts

Prerequisites: Istio and Prometheus are installed. 

Following the [instructions](https://github.com/perses/helm-charts), helm is installed and the Perses helm repository is already added. 

Then, deploy the config maps that contain the resources (The project, the datasource and the dashboard):

```
kubectl apply -f project.yaml
kubectl apply -f datasource.yaml
kubectl apply -f dashboard.yaml
```

Then, install the helm chart: 

```
helm install perses perses/perses -n perses -f values.yaml
```

And port-forward the service: 

```
helm install perses perses/perses -n perses -f values.yaml
```

How to debug? Using Kiali, we can see the logs: 

And we can find the relevant logs: 



