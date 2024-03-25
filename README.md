# odigos-test

1. Install and run odigos (version v1.0.49 at least) on a kind cluster:

```shell
brew install keyval-dev/homebrew-odigos-cli/odigos
odigos version
kind create cluster
odigos install
```

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

4. Test quickwit

```shell
kubectl -n quickwit port-forward svc/release-name-quickwit 7280:7280
```

Then you can go to: http://localhost:7280

5. Launch odigos on the browser: http://localhost:3000

And select "imalive"

![odigos_select_imalive](./img/odigos_select_imalive.png)

Then select the "Quickwit" destination

![odigos_destination_quickwit](./img/odigos_destination_quickwit.png)

Then:

![odigos_configure_connection](./img/odigos_configure_connection.png)

URL of endpoint: `release-name-quickwit.quickwit.svc.cluster.local:7281`

Then you should see this overview:

![odigos_overview](./img/odigos_overview.png)
