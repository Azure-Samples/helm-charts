# image-pull-secret

Simple aks-helloworld chart demonstrating image pull secrets.

## Installing the Chart

Add the Azure Samples chart repository.

```
helm repo add azure-samples https://azure-samples.github.io/helm-charts/
```

Install the chart.

```
helm install azure-samples/image-pull-secret --set image=myacr0008.azurecr.io/aks-helloworld --set imagePullSecret=acr-auth
```

## Configuration

The following tables lists the configurable parameters of the azure-vote chart and the default values.

| Parameter | Description | Default |
|---|---|---|
| title | Title for hello world app. | Azure Vote App |
| serviceName | Name for Kubernetes service. | aks-helloworld |
| serviceType | Type for Kubernetes service. | ClusterIP |
| image | Full image name inclding registry. | myacrregistry.azurecr.io/aks-helloworld | 
| imagePullSecret | Name of docker-registry secret with auth credentials for ACR. | acr-auth |