# Twitter sentiment with OSBA

Multi container / managed service application deployed using Helm chart, Kubernetes service catalog, and Open Service Broker for Azure.

# Prerequisites

Kubernetes cluster with Helm installed.

## Install service catalog:

```
helm repo add svc-cat https://svc-catalog-charts.storage.googleapis.com
helm install svc-cat/catalog --name catalog --namespace catalog --set controllerManager.healthcheck.enabled=false --set apiserver.healthcheck.enabled=false --set controllerManager.healthcheck.enabled=false
```

## Azure Identity

Generate Azure identity, requires the Azure CLI:

```
SERVICE_PRINCIPAL=$(az ad sp create-for-rbac)
AZURE_CLIENT_ID=$(echo $SERVICE_PRINCIPAL | cut -d '"' -f 4)
AZURE_CLIENT_SECRET=$(echo $SERVICE_PRINCIPAL | cut -d '"' -f 16)
AZURE_TENANT_ID=$(echo $SERVICE_PRINCIPAL | cut -d '"' -f 20)
AZURE_SUBSCRIPTION_ID=$(az account show --query id --output tsv)
```

## Install the Open Service Broker for Azure

```
helm repo add azure https://kubernetescharts.blob.core.windows.net/azure

helm install azure/open-service-broker-azure --name osba --namespace osba \
  --set azure.subscriptionId=$AZURE_SUBSCRIPTION_ID \
  --set azure.tenantId=$AZURE_TENANT_ID \
  --set azure.clientId=$AZURE_CLIENT_ID \
  --set azure.clientSecret=$AZURE_CLIENT_SECRET \
  --set modules.minStability=experimental
```

## Installing the Chart

Install the Twitter sentiment chart.

```
helm install azure-samples/twitter-sentiment --set consumerKey=<> --set consumerSecret=<> --set accessToken=<> --set accessTokenSecret=<>
```

## Configuration

The following table lists the configurable parameters of the azure-vote chart and the default values.

| Parameter | Description | Default |
|---|---|---|
| twitterSecretName | Twitter API consumer secret.| twitter-api |
| consumerKey | Twitter API consumer key. | control |
| consumerSecret| Twitter API consumer secret.| null |
| accessToken | Twitter API access token.| null |
| accessTokenSecret | Twitter API access token secret.| null |
| filterText | Text to analyze. | Seattle |
| plan | Azure Text Analytics tier. | standard-b1 |
| resourceGroup | Azure resource group where all services are created. | twitter-sentiment |
