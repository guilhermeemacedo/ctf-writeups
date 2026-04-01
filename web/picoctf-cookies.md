# PicoCTF – Cookies

## Contexto
O desafio Cookies apresenta uma aplicação web simples que permite ao usuário
buscar tipos de biscoitos. A aplicação aparenta ser inofensiva, mas utiliza
cookies HTTP para controlar o estado e o conteúdo das respostas exibidas.

O nome do desafio já indica o vetor principal de exploração: cookies
controlados pelo cliente.

---

## Análise Inicial
Ao interagir com a aplicação e realizar buscas por diferentes tipos de
biscoitos, nota-se que o comportamento do servidor muda a cada requisição.

Ao inspecionar os cookies no navegador, foi identificado um cookie chamado
`name`, cujo valor era alterado após cada interação do usuário. A resposta da
aplicação dependia exclusivamente desse valor.

Isso indica que o backend estava confiando diretamente em dados enviados pelo
cliente para determinar o conteúdo retornado.

---

## Exploração
A partir da observação de que o valor do cookie `name` era numérico, foi feita
a modificação manual desse valor diretamente no navegador.

Ao alterar sequencialmente o valor do cookie e atualizar a página, o servidor
retornava diferentes respostas, cada uma associada a um número específico.

Ao chegar no valor `18`, a aplicação retornou diretamente a flag do desafio,
confirmando que o backend não realizava qualquer validação ou controle de
acesso sobre esse estado.

---

## Resultado
A flag foi obtida simplesmente através da modificação manual de um cookie
controlado pelo cliente, sem necessidade de autenticação ou exploração
avançada.

---

## Aprendizado
Este desafio demonstra uma falha grave de Application Security, onde o backend
confia em dados provenientes do cliente para controlar a lógica da aplicação.

Cookies enviados pelo navegador podem ser facilmente manipulados e nunca
devem ser utilizados como fonte confiável para decisões de segurança.

Em aplicações reais, esse tipo de erro pode levar a acesso indevido,
vazamento de dados e controle total da aplicação por um atacante.

Toda decisão sensível deve ser validada exclusivamente no servidor.
