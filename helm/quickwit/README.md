# Quickwit chart

## Update the chart

```
helm dependency update
```

## Deploy the chart

```
NS=quickwit
helm template . -n $NS --values values.yaml --values postgres-values.yaml | kubectl -n $NS apply -f -
```

## Expose the port

```shell
kubectl -n quickwit port-forward svc/release-name-quickwit-searcher 7280:7280
```

Then you can go on your browser with http://localhost:7280

Also the API is available with the `/api` subpath:

```shell
curl http://localhost:7280/api/v1/indexes|jq .
```
