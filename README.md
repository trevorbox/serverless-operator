# serverless-operator

Openshift Knative Serverless installation and example with Service Mesh

## Install operators

```sh
helm upgrade -i serverless-operators helm/serverless-operators -n openshift-serverless --create-namespace
```

```sh
helm upgrade -i service-mesh-operators helm/service-mesh-operators -n openshift-operators-redhat --create-namespace
```

## Deploy knative-serving

```sh
helm upgrade -i knative helm/knative -n knative-serving
```

## Create namespaces

```sh
helm upgrade -i serverless-namespace helm/namespaces -n default
```

## Create control plane

```sh
helm upgrade -i control-plane helm/control-plane -n istio-system --create-namespace
```

## Label knative system namespaces

```sh
oc label namespace knative-serving knative.openshift.io/system-namespace=true
```

## Deploy services

```sh
helm upgrade -i services helm/services -n serverless-test
```
