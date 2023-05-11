### Instalando Prometheus no K8s

```
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
helm install [RELEASE_NAME] prometheus-community/prometheus

```

Para exibir os values do chart

```
helm search repo prometheus 

```

Para exibir na tela o conteudo dos values

```
helm inspect values prometheus-community/prometheus

```

Para atualizar com os values

```
helm upgrade --install prometheus prometheus-community/prometheus --values values.yaml --namespace prometheus
```


### WebHook

Site interessante para teste de webhook

```
https://pruu.herokuapp.com

```




