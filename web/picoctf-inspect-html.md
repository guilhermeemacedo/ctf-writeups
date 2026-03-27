# PicoCTF – Inspect HTML


## Contexto
- Plataforma: PicoCTF
- Categoria: Web Exploitation
- Dificuldade: Easy

O desafio apresenta uma página web simples, desafiando o usuário a identificar
informações sensíveis expostas diretamente no código HTML da aplicação.


## Análise Inicial
Ao acessar a aplicação, foi exibida uma página web contendo apenas texto
informativo, sem campos de entrada, formulários ou funcionalidades aparentes.

O enunciado do desafio sugeria que a informação procurada estaria presente
no código da página, indicando que o conteúdo exposto no lado do cliente
deveria ser analisado.


## Exploração
Considerando a dica do desafio, foi realizada a inspeção do código-fonte da
página utilizando as ferramentas do navegador.

Ao analisar o HTML da aplicação, foi possível identificar que a flag do desafio
estava diretamente exposta no código, sem qualquer tipo de codificação,
ofuscação ou proteção adicional.


## Resultado
Após a inspeção do código HTML da página, foi possível localizar e recuperar
a flag do desafio com sucesso.


## Aprendizado
Este desafio demonstra que todo conteúdo presente no HTML de uma aplicação
web é acessível ao usuário, incluindo comentários e informações sensíveis.

Reforça a importância de não expor dados confidenciais ou lógica de segurança
no lado do cliente, destacando que informações sensíveis devem ser tratadas
exclusivamente no backend da aplicação.
