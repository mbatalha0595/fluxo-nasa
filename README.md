# Fluxo de Extração de Imagens da NASA via API REST

## Objetivo
Este automação tem como objetivo extrair imagens de satélites da NASA via API REST, onde cada imagem é salva no SharePoint e enviada por e-mail.

## Fluxo
Este fluxo é disparado manualmente pelo usuário. Na variável "Chave", armazeno a chave da API da NASA. Em seguida, a data de execução do fluxo é armazenada na variável "Data".

<img src="https://raw.githubusercontent.com/mbatalha0595/fluxo-nasa/main/images/1.png">

Para capturar qualquer problema na execução do fluxo, simulei a estrutura try catch usando Escopos. No escopo "Try", uso a etapa HTTP para passar a data e chave para a API da NASA. Em seguida, capturo o JSON retornado e uso a etapa de HTTP novamente para acessar a imagem via URL. Depois, disparo um e-mail com a imagem e gravo a imagem em uma biblioteca do SharePoint.

<img src="https://raw.githubusercontent.com/mbatalha0595/fluxo-nasa/main/images/2.png">

Se houver algum erro no escopo "Try", o escopo "Catch" é executado e um e-mail é disparado informando que houve erro na requisição de dados.

<img src="https://raw.githubusercontent.com/mbatalha0595/fluxo-nasa/main/images/3.png">
