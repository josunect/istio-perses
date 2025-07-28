# Dashboards for Istio with Perses

This repository contains ready-to-use dashboards for [Perses](https://perses.dev/), designed to monitor Istio on Kubernetes. It allows you to deploy dashboards as native Kubernetes resources, making Istio observability easy with customizable, code-managed panels.

![image](https://github.com/user-attachments/assets/e5e624a0-0e0f-4f12-82ee-783d6bea99b7)

There are different deployment methods: 
- Using the Operator
- With helm charts
- As an addon with provisioned resources

## Prerequisites

Istio needs to be installed in the cluster, as well as the required dependency Prometheus.

## Installation

The easiest way is using the addon: 

`kubectl apply -f https://raw.githubusercontent.com/josunect/istio-perses/refs/heads/main/addon/perses.yaml`

Port forward the perses service: 

`kubectl port-forward svc/perses 4000:4000`

And access to the server: 

`http://localhost:4000/`
