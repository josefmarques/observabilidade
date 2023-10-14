### Informações do Projeto
Esse projeto é uma cópia de https://github.com/mmacanmunhoz/prometheus, portanto os créditos são do seu criador e não meus.
Esse projeto permite tutorial de como executar o prometheus, alertmanager, criar alertrules utilizando dockercompose e k8s

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

### Instalando no Docker

Para instalar no docker, basta executar o dockercompose


### Informação importante sobre Alertas 

Monitore para seus usuários
Eu chamo isso de "monitoramento baseado em sintomas", em contraste com "monitoramento baseado em causas". Seus usuários se importam se seus servidores MySQL estão inativos? Não, eles se importam se suas consultas estão falhando. (Talvez você já esteja se encolhendo, apaixonado por suas regras Nagios para servidores MySQL? Seus usuários nem sabem que seus servidores MySQL existem!) Seus usuários se importam se um binário de suporte (ou seja, caminho não veiculado) está em um reiniciar-loop? Não, eles se importam se seus recursos estão falhando. Eles se importam se o envio de dados está falhando? Não, eles se preocupam se seus resultados são recentes.

Os usuários, em geral, se preocupam com um pequeno número de coisas:

Disponibilidade básica e correção. sem "Oops!", sem 500s, sem solicitações interrompidas ou páginas carregadas pela metade ou Javascript ou CSS ou imagens ou vídeos ausentes. Qualquer coisa que interrompa o serviço principal de alguma forma deve ser considerada indisponibilidade.
Latência. Rápido. Rápido. Rápido. Além disso, rápido.
Integralidade/frescura/durabilidade. Os dados de seus usuários devem estar seguros, devem retornar quando você solicitar e os índices de pesquisa devem estar atualizados. Mesmo que esteja temporariamente indisponível, os usuários devem ter plena fé de que voltará sem controle.
Características. Seus usuários se preocupam com o funcionamento de todos os recursos do serviço - você deve monitorar qualquer coisa que seja um aspecto importante do seu serviço, mesmo que não seja a funcionalidade/disponibilidade principal (por exemplo, a calculadora e o ticker da bolsa aparecendo nos resultados da pesquisa).



### Alertas baseados em Causas X Sintomas

Alertas baseados em causa são ruins (mas às vezes necessários)
"Mas", você pode dizer, "eu sei que os servidores de banco de dados que são inacessíveis resultam na indisponibilidade dos dados do usuário". Isso é bom. Alerta sobre a indisponibilidade de dados. Alerta sobre o sintoma: o 500, o Ops!, a métrica da caixa branca que indica que nem todos os servidores foram alcançados pelo cliente do banco de dados. Por que?

Você vai ter que pegar o sintoma de qualquer maneira. Talvez isso aconteça devido à desconexão da rede, contenção da CPU ou inúmeros outros problemas nos quais você ainda não pensou. Então você tem que pegar o sintoma.
Depois de detectar o sintoma e a causa, você tem alertas redundantes; eles precisam de ajustes separados e resultam em duplicação ou em árvores de dependência complicadas
O resultado supostamente inevitável nem sempre é inevitável: talvez seus servidores de banco de dados estejam indisponíveis porque você está ativando uma nova instância ou recusando uma antiga. Ou talvez um recurso tenha sido adicionado para fazer failover rápido de solicitações e, assim, você não se importa mais com a disponibilidade de um único servidor. Claro, você pode pegar todos esses casos com regras cada vez mais complicadas, mas por que se preocupar? O modo de falha é mais páginas falsas, mais confusão e mais ajuste, sem ganho e menos tempo gasto na correção dos alertas que importam.

Mas às vezes eles são necessários. Não há (frequentemente) nenhum sintoma de "quase" ficar sem cota ou memória ou E/S de disco, etc., então você quer que as regras saibam que você está caminhando em direção a um precipício. Use-os com moderação; não escreva regras de paginação baseadas em causa para sintomas que você pode detectar de outra forma.
Alertando do bico (ou além!)
Os melhores alertas em um sistema cliente/servidor em camadas vêm da perspectiva do cliente:

O cliente vê os resultados de novas tentativas, latência de rede entre cliente e servidor e tem uma perspectiva melhor sobre a latência e os erros voltados para o usuário do que o servidor
Em muitos casos, o cliente (por exemplo, um mixer ou servidor de aplicativos) está agregando respostas de muitos back-ends, como serviços de cache, bancos de dados, serviços de gerenciamento/autorização de contas, fragmentos de consulta, etc. Seu monitoramento é mais robusto para mudanças na infraestrutura subjacente (e em failover e novas tentativas no nível do aplicativo) se você vir o que o cliente realmente faz.


Fonte das informações

```
https://docs.google.com/document/d/199PqyG3UsyXlwieHaqbGiWVa8eMWi8zzAn0YfcApr8Q/edit#
```
# observabilidade
