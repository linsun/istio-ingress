# istio-ingress

This repository contains simple ingress example to have Istio configured with a kubernetes cluster deployed in IBM Cloud.

The default secret is created in the default namespace, and you can view it via `kubectl get secret -n default`.   Copy it to the istio-system namespace:

```
kubectl get secret {secret-name} -o yaml | sed 's/default/istio-system/g' | kubectl -n istio-system create -f -
```

Open the `plans/frontdoor-ingress.yaml` file and check if it is using the same region as your kubernetes cluster.  The default being used is us-east.  Change it to your region if needed, and deploy the `plans/frontdoor-ingress.yaml`:

```
cat frontdoor-ingress.yml| sed 's/xxxx/{cluster-name}/g' | sed 's/ssss/{secret-name}/g' | kubectl -n istio-system create -f -
```
