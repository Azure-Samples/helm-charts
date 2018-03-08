# oms-daemonset

Chart for the Azure OMS daemonset. For more information, see:

https://docs.microsoft.com/en-us/azure/aks/tutorial-kubernetes-monitor

## Installing the Chart

Pre-create a Kubernetes secret that contains the OMS Workspace ID and Key. Update `WORKSPACE_ID` with your OMS workspace ID and `WORKSPACE_KEY` with the workspace key.

```
kubectl create secret generic omsagent-secret --from-literal=WSID=WORKSPACE_ID --from-literal=KEY=WORKSPACE_KEY
```

Add the Azure Samples chart repository.

```
helm repo add azure-samples https://azure-samples.github.io/helm-charts/
```

Install the chart.

```
helm install azure-samples/oms-daemonset --set secretName=omsagent-secret
```

## Configuration

The following tables lists the configurable parameters of the oms-daemonset chart and the default values.

| Parameter | Description | Default |
|---|---|---|
| secretName | Name of Kubernetes secret containign OMS workspace settings. | omsagent-secret |
