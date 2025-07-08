# Provisioning Perses Dashboards with helm charts

Prerequisites: Istio and Prometheus are installed. 

Following the [instructions](https://github.com/perses/helm-charts), helm is installed and the Perses helm repository is already added. 

Then, deploy the config maps that contain the resources (The project, the datasource and the dashboard):

```
kubectl apply -f https://raw.githubusercontent.com/josunect/istio-perses/refs/heads/main/helm-charts/project.yaml
kubectl apply -f https://raw.githubusercontent.com/josunect/istio-perses/refs/heads/main/helm-charts/datasource.yaml
kubectl apply -f https://raw.githubusercontent.com/josunect/istio-perses/refs/heads/main/helm-charts/dashboard.yaml
```

Then, install the helm chart: 

```
helm install perses perses/perses -n perses -f https://raw.githubusercontent.com/josunect/istio-perses/refs/heads/main/helm-charts/values.yaml
```

And port-forward the service: 

```
kubectl port-forward svc/perses 7080:8080 -n perses
```

How to debug? Using Kiali, we can see the logs: 

![image](https://github.com/user-attachments/assets/c4d3f470-86e9-4123-971c-7989ea9049f3)

And we can find the relevant logs every minute (Because the provisioning period is set to 1m in values.yaml): 

![image](https://github.com/user-attachments/assets/79f0570a-58d6-4729-8cef-a040d935a267)

Accessing to perses, we can see the dashboards are loaded: 

![image](https://github.com/user-attachments/assets/3806687c-f3d5-4eca-a2a4-17b6d6c46400)
