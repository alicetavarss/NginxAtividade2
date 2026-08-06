# Instalação do Apache Bench e Execução de Teste de Carga no ReactJS

## Passo a Passo:

### 1- Instalação do Apache Bench:

Em sistemas baseados em Debian/Ubuntu:

```
   sudo apt update
   sudo apt install apache2-utils -y

```

Em sistemas baseados em CentOS/RHEL/Fedora:

`sudo dnf install httpd-tools -y`

Para verificar se a instalação foi concluída com sucesso:

`ab -V`

### 2- Conceito das Métricas do Teste de Carga:
Ao executar o comando ab, utilizaremos principalmente dois parâmetros:

`-n`(number of requests): Quantidade total de requisições enviadas ao servidor.
`-c`(concurrency): Número de requisições simultâneas (concorrentes).

### 3- Executando o Teste de Carga:

Substitua `http://localhost/` pelo IP ou domínio onde sua aplicação ReactJS está rodando.

Exemplo de Teste Moderado (1.000 requisições totais, com 100 simultâneas):

`ab -n 1000 -c 100 http://localhost/`

>É importante colocar a barra / no final da URL para requisições no endpoint raiz.

### 4- Análise dos Resultados:

   Após a execução, preste atenção nas seguintes métricas do relatório:

   `Complete requests:`Número total de requisições concluídas com sucesso.

   `Failed requests:` Número de requisições que falharam.

   `Requests per second (RPS):` Quantidade de requisições processadas por segundo pelo servidor Nginx (Vazão).
 
   `Time per request (mean):` Tempo médio gasto para responder cada grupo de requisições concorrentes (Latência).

  `Percentage of the requests served within a certain time:` Distribuição percentual do tempo de resposta.
  
  ### 5-Exemplo de Saída Esperada:

  Server Software: nginx/1.18.0
  Server Hostname: localhost
  Server Port: 80

  Document Path: /
  Document Length: 642 bytes

  Concurrency Level: 100
  Time taken for tests: 0.854 seconds
  Complete requests: 1000
  Failed requests: 0
  Total transferred: 875000 bytes
  HTML transferred: 642000 bytes
  Requests per second: 1170.96 [#/sec] (mean)
  Time per request: 85.399 [ms] (mean)

