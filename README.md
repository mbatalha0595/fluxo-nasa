# NASA - Fluxo de Extração de Dados (API REST)

## Objetivo
Consumir a API da NASA para obter a imagem astronômica do dia, processar a resposta JSON, enviar a imagem por e-mail e armazená-la em uma biblioteca do SharePoint.

## Fluxo

<img src="https://raw.githubusercontent.com/mbatalha0595/fluxo-nasa/main/images/Fluxo.png" width=700>

## Lógica de Execução

### 1) Disparo e Inicialização

Este fluxo é acionado manualmente.

Em seguida, duas variáveis são inicializadas:

- Chave (chave da API)
- Data (data de disparo da trigger)

<img src="https://raw.githubusercontent.com/mbatalha0595/fluxo-nasa/main/images/1.png" width=700>

### 2) Requisição de Dados

No escopo Try, é realizada uma requisição HTTP (GET) para a API da NASA passando o valor das variáveis Chave e Data.

Nota: Para tratamento de erros, simulei a estrutura Try-Catch usando escopos com Run After. Caso ocorra algum erro no escopo Try, o fluxo segue para o escopo Catch, que envia um e-mail de notificação.

Em seguida, a resposta JSON é processada para extrair a URL da imagem, seguida de uma segunda requisição HTTP para baixar a imagem (binário).

<img src="https://raw.githubusercontent.com/mbatalha0595/fluxo-nasa/main/images/2.png" width=700>

### 3) Envio da Imagem por E-mail e Gravação no SharePoint

Envio automático de e-mail com a imagem e armazenamento na biblioteca do SharePoint.

<img src="https://raw.githubusercontent.com/mbatalha0595/fluxo-nasa/main/images/3.png" width=700>

### 4) Notificação de Erro

Em caso de erro no escopo Try, esse escopo é executado, enviando um e-mail de notificação automaticamente.

<img src="https://raw.githubusercontent.com/mbatalha0595/fluxo-nasa/main/images/4.png" width=700>

### 5) E-mail com Imagem

Este é o e-mail enviado com a imagem baixada da NASA via API REST.

<img src="https://raw.githubusercontent.com/mbatalha0595/fluxo-nasa/main/images/5.png" width=700>
