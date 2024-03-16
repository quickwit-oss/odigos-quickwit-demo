# odigos-test

1. Test odigos following their [CONTRIBUTING.md](https://github.com/keyval-dev/odigos/blob/main/CONTRIBUTING.md)

2. Run [imalive](https://github.com/comworkio/imalive) on the same kind cluster that is used by odigos

```shell
kubectl create ns imalive
cd helm/imalive
helm dependency update
helm template . --values values.yaml|kubectl -n imalive apply -f -
```

3. Run quickwit on the same kind cluster

```shell
kubectl create ns quickwit
cd helm/quickwit
helm dependency update
helm template . --values values.yaml|kubectl -n quickwit apply -f -
```
