# istio-ingress

This repository contains simple ingress example to have Istio configured with a kubernetes cluster deployed in IBM Cloud.

The default secret is created in the default namespace.  Copy it to the istio-system namespace:

```
kubectl get secret {secret-name} -o yaml | sed 's/default/istio-system/g' | kubectl -n istio-system create -f -
```
