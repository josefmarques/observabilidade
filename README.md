curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh


helm search repo prometheus (Mostra os values, versões)
helm inspect values prometheus-community/prometheus (mostra na tela o conteudo dos values)
helm upgrade --install prometheus prometheus-community/prometheus --values values.yaml --namespace prometheus



while true; do curl http://localhost:8080/produto; sleep 1; done;


http_request_duration_seconds_bucket{code=200}

mongodb_op_counters_total{type=~"insert|query"} // somente insert e query

mongodb_op_counters_total{type!~"insert|query"} // todas tirando insert e query

mongodb_op_counters_total[1m] // mostra as métricas executadas a 1 minuto atrás

rate(http_request_duration_seconds_bucket[10m]) // média de logs dentro desse intervalo

sum(rate(http_request_duration_seconds_bucket[10m])) // mostra o total das requisições dentro desse intervalo

sum(rate(http_request_duration_seconds_bucket[10m])) by (job) // somo com base na label

---------------------------------------------

Ações que posso efetuar com o alert manager + prometheus

Silenciar por determinado periodo de tempo
Inibir um alerta dependente de outro ex: aplicação e banco
Agrupar por determinados contextos os alertas

----------------------------------------------


https://pruu.herokuapp.com/dump/wpwebhookdefault

