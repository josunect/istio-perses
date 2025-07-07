# Perses Datasource and Dashboard for the integration with OpenShift monitoring and Cluster Observability

This repository contains ready-to-use dashboards for [Perses](https://perses.dev/), designed to monitor Istio on OpenShift. It allows you to deploy dashboards as native Kubernetes resources, enabling easy observability of Istio with customizable, code-managed panels.

The resources are intended to integrate with OpenShift Monitoring (the datasource is configured for Thanos Query), and the dashboards do not specify a particular namespace or datasource — they will use the default Prometheus configuration.

Make sure to use the correct namespace when creating the resources.

![image](https://github.com/user-attachments/assets/9af991cb-66a3-4565-8e32-b597b002a14a)
