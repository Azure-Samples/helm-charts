# burst-scheduler

Chart for the Kubernetes burst scheduler. For more information on the burst scheduler, see:

https://github.com/neilpeterson/kubernetes-burst-scheduler

## Installing the Chart

Add the Azure Samples chart repository.

```
helm repo add azure-samples https://azure-samples.github.io/helm-charts/
```

Install the chart.

```
helm install azure-samples/burst-scheduler
```

## Configuration

The following tables lists the configurable parameters of the azure-vote chart and the default values.

| Parameter | Description | Default |
|---|---|---|
| name | Scheduler name. | burst-scheduler |
| burstNode | Name of burst node. | irtual-kubelet-aci-connector-linux |
| burstValue | Burst threashold. | 5 |