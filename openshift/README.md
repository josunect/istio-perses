# Perses Datasource and Dashboard for the integration with OpenShift monitoring and Cluster Observability

This repository contains ready-to-use dashboards for [Perses](https://perses.dev/), designed to monitor Istio on OpenShift. It allows you to deploy dashboards as native Kubernetes resources, making Istio observability easy with customizable, code-managed panels.

The resources aim to integrate with OpenShift monitoring (Datasource configured for Thanos query) and the Dashboards doesn't contain a specific namespace or datasource (They will use the Prometheus default). 

Make sure the right namespace is used when creating the resources. 
