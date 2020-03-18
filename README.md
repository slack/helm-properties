```console

# install chart
helm upgrade --install chart1 ./chart1

# check cm
kubectl -n default get cm/chart1 -o yaml

# add a value (would be caBundle in the real world)
kubectl -n default patch cm/chart1 -p '{"data": { "key3": "foo" }}'
configmap/chart1 patched

# check the cm
kubectl -n default get cm/chart1 -o yaml
apiVersion: v1
data:
  key1: value1
  key2: value2
  key3: foo
kind: ConfigMap
metadata:
  creationTimestamp: "2020-03-18T21:26:59Z"
  labels:
    app.kubernetes.io/instance: chart1
    app.kubernetes.io/managed-by: Helm
    app.kubernetes.io/name: chart1
    app.kubernetes.io/version: 1.16.0
    helm.sh/chart: chart1-0.1.0
  name: chart1
  namespace: default
  resourceVersion: "5715151"
  selfLink: /api/v1/namespaces/default/configmaps/chart1
  uid: 74514d2b-e362-4048-be67-6bf106ec8d8c

# upgrade with helm
$ helm upgrade --install chart1 ./chart1

# check chart, `key3` still there
$ kubectl -n default get cm/chart1 -o yaml
apiVersion: v1
data:
  key1: value1
  key2: value2
  key3: foo
kind: ConfigMap
metadata:
  creationTimestamp: "2020-03-18T21:26:59Z"
  labels:
    app.kubernetes.io/instance: chart1
    app.kubernetes.io/managed-by: Helm
    app.kubernetes.io/name: chart1
    app.kubernetes.io/version: 1.16.0
    helm.sh/chart: chart1-0.1.0
  name: chart1
  namespace: default
  resourceVersion: "5715151"
  selfLink: /api/v1/namespaces/default/configmaps/chart1
  uid: 74514d2b-e362-4048-be67-6bf106ec8d8c

```

