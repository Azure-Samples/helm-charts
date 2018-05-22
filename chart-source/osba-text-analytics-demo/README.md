# osba-storage-sample

Open Service Broker for Azure text analytics sample.

## Installing the Chart

Add the Azure Samples chart repository.

```
helm repo add azure-samples https://azure-samples.github.io/helm-charts/
```

Install the chart.

NOTE: Azure text analytics is not currently included in the Open Service Broker for Azure. I have created a fork with this functionality. Use the following command to run my OSBA fork:

```
helm install azure/open-service-broker-azure --name osba --namespace osba \
  --set azure.subscriptionId=$AZURE_SUBSCRIPTION_ID \
  --set azure.tenantId=$AZURE_TENANT_ID \
  --set azure.clientId=$AZURE_CLIENT_ID \
  --set azure.clientSecret=$AZURE_CLIENT_SECRET \
  --set modules.minStability=experimental \
  --set image.repository=neilpeterson/open-service-broker-azure_broker \
  --set image.tag=text-analytics
```

Once set, run the helm chart with this command.

```
helm install azure-samples/osba-text-analytics-demo
```

## Configuration

This chart has no configurations.