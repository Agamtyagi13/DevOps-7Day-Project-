1. Objective

The objective of Task 6 is to configure monitoring for the Kubernetes environment using Prometheus and Grafana.

The project requires:

Prometheus
Grafana
Grafana connected to Prometheus
CPU Usage dashboard
Memory Usage dashboard
Pod Status
Container Status
2. What is Monitoring?

Monitoring means continuously observing the condition and performance of an application or infrastructure.

Monitoring helps identify:

High CPU usage
High memory usage
Failed Pods
Container problems
Resource utilization
3. What is Prometheus?

Prometheus is a monitoring and metrics collection system.

It collects metrics from monitored systems and stores them so that they can be queried and analyzed.

In this project:

Kubernetes
↓
Metrics
↓
Prometheus

Prometheus acts as the metrics collection component.

4. What is Grafana?

Grafana is a visualization and dashboard platform.

Grafana can connect to Prometheus and use the collected metrics to create dashboards.

The monitoring architecture is:

Kubernetes Cluster
↓
Metrics
↓
Prometheus
↓
Grafana
↓
Dashboard

5. Deploy Prometheus

Prometheus is deployed into the Kubernetes environment.

Helm can be used to install the Prometheus monitoring stack.

After installation, the Prometheus Pods and Services are checked to verify that the monitoring system is running.

6. Deploy Grafana

Grafana is deployed as part of the monitoring environment.

Grafana provides the user interface for visualizing the metrics collected by Prometheus.

After Grafana is running, it can be accessed through a browser.

7. Connect Grafana to Prometheus

Grafana must be connected to Prometheus as a data source.

The connection allows Grafana to query metrics collected by Prometheus.

The process is:

Prometheus
↓
Collected Metrics
↓
Grafana Data Source
↓
Dashboard
↓
Visualization

8. Monitoring Dashboard

The project requires the dashboard to display four main categories.

CPU Usage

CPU Usage shows the CPU consumption of the monitored Kubernetes workloads.

It can help identify applications or containers that are consuming high CPU resources.

Memory Usage

Memory Usage shows the amount of memory being consumed.

It can help identify workloads with high memory utilization.

Pod Status

Pod Status provides information about the state of Kubernetes Pods.

It can help identify whether Pods are running correctly or experiencing problems.

Container Status

Container Status provides information about the state of containers running inside Kubernetes Pods.

It helps verify whether the application containers are running correctly.

9. Dashboard Architecture

The monitoring dashboard follows:

Grafana
↓
Prometheus Data Source
↓
CPU Usage
Memory Usage
Pod Status
Container Status

10. Monitoring Verification

After installing Prometheus and Grafana, the monitoring Pods and Services are checked.

Grafana is then connected to Prometheus.

The dashboard is opened and the required metrics are verified.

The dashboard should display:

CPU Usage
Memory Usage
Pod Status
Container Status

## COMMAND USED
kubectl create namespace monitoring

helm repo add prometheus-community https://prometheus-community.github.io/helm-charts

helm repo update

helm install monitoring prometheus-community/kube-prometheus-stack \
  -n monitoring

kubectl get pods -n monitoring

kubectl get svc -n monitoring

kubectl port-forward -n monitoring \
  svc/monitoring-grafana 3000:80

kubectl port-forward -n monitoring \
  svc/monitoring-kube-prometheus-prometheus 9090:9090