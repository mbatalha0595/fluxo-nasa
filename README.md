# NASA APOD - Fluxo de Extração de Dados (API REST)

## Objetivo
Consumir a API da NASA para obter a imagem astronômica do dia, processar a resposta JSON, enviar a imagem por e-mail e armazená-la em uma biblioteca do SharePoint.

## Fluxo

<img src="https://raw.githubusercontent.com/mbatalha0595/fluxo-nasa/main/images/fluxo.png">

## Lógica de Execução

1) Disparo e Inicialização

Este fluxo é acionado manualmente.

Em seguida, duas variáveis são inicializadas:

- Chave (API Key)
- Data (data de disparo da trigger)

<img src="https://raw.githubusercontent.com/mbatalha0595/fluxo-nasa/main/images/1.png">

2) Consumo da API

No escopo Try, é realizada uma requisição HTTP (GET) para a API da NASA passando o valor das variáveis Chave e Data.

Nota: Para tratamento de erros, simulei a estrutura Try-Catch usando escopo com run-after. Se houver algum erro, um e-mail de notificação é enviado automaticamente.

Em seguida, a resposta JSON é processada para extrair a URL da imagem, seguida de uma segunda requisição HTTP para baixar a imagem (binário).

<img src="https://raw.githubusercontent.com/mbatalha0595/fluxo-nasa/main/images/2.png">

3) Envio de E-mail e Gravação no SharePoint

Envio automático de e-mail com a imagem e armazenamento na biblioteca do SharePoint.

<img src="https://raw.githubusercontent.com/mbatalha0595/fluxo-nasa/main/images/3.png">
