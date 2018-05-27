# Tweet Factory SaaS Operator

Operator for creating and managing instances of the Tweet Factory SaaS solution.

https://github.com/neilpeterson/tweet-factory-operator

## Installing the Chart

Add the Azure Samples chart repository.

```
helm repo add azure-samples https://azure-samples.github.io/helm-charts/
```

Install the chart.

```
helm install azure-samples/tweet-factory-operator
```

## Using the operator

Once the operator is running, a Tweet factory instance is created for each instance of the tweet factory resource created in the Kuberntes cluster.

Create a file names `seattle-tweet-factory.yaml` and copy in the following YAML. Update the Twitter keys and tokens with your Twitter Application API information.

```yaml
apiVersion: "tweet-factory.com/v1alpha1"
kind: "TweetFactory"
metadata:
  name: "seattle"
spec:
  consumerKey: ""
  consumerSecret: ""
  accessToken: ""
  accessTokenSecret: ""
  filterText: "Seattle"
```

Create the tweet factory resource:

```
kubectl create -f seattle-tweet-factory.yaml
```

