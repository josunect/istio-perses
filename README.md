# Dashboards for Istio with Perses

This repository contains ready-to-use dashboards for [Perses](https://perses.dev/), designed to monitor Istio on Kubernetes. It allows you to deploy dashboards as native Kubernetes resources, making Istio observability easy with customizable, code-managed panels.

![image](https://github.com/user-attachments/assets/e5e624a0-0e0f-4f12-82ee-783d6bea99b7)


## Prerequisites

- A running Kubernetes cluster.
- `kubectl` configured to access your cluster.
- [Prometheus](https://prometheus.io/) deployed and scraping Istio metrics.
- Istio is installed in the `istio-system` namespace.
- Tested with Perses 0.50.3

## Installation

### 1. Install the Perses Operator

You can install the Perses Operator following the official documentation, for example:

- Clone the [perses operator repository](https://github.com/perses/perses-operator). Note: Tested with release/v0.1, v2 was not working properly
- `make deploy`
- `make install`

This will install the operator and the required CRDs in your cluster.

For troubleshootint:
- Verify that the pods are ready in the `perses-operator-system` namespace
- View manager pod logs 

#### Note about version 2

Note: V2 can be installed with `make deploy-local`, or installing the certificates first, but still, the resources are not created. Should be done with these steps: 

- `kubectl create ns perses-operator-system`
- `./scripts/gen-certs.sh`
- Create certs: 
```
kubectl -n perses-operator-system create secret tls perses-operator-webhook-server-cert \
     --cert=/tmp/k8s-webhook-server/serving-certs/tls.crt \
     --key=/tmp/k8s-webhook-server/serving-certs/tls.key
```
- `make deploy`

But then, applying the examples, this is not working. 

### 2. Create the `istio` namespace

If it does not exist yet, create the namespace where the dashboards will be deployed:

```sh
kubectl create namespace istio
```

### 3. Apply the Istio dashboards

Inside this repository you will find the dashboards in the `dashboards/` directory. To deploy them, run:

```sh
kubectl apply -n istio -f istio-dashboards.yml
```

This will create the dashboards and datasources needed to visualize Istio metrics in Perses.

## Visualization

Access the Perses UI to view the dashboards. The perses service can be port-forward to access it locally:

```sh
kubectl -n istio-system port-forward svc/perses 8080:8080
```

Then open [http://localhost:8080](http://localhost:8080) in your browser.

## Notes

- Make sure Prometheus is configured to scrape Istio metrics and is accessible from Perses.
- You can customize the dashboards by editing the YAML files in `dashboards/` before applying them.


