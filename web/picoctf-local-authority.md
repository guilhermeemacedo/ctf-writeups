# PicoCTF – Local Authority

## Contexto
O desafio Local Authority apresenta uma aplicação web de login aparentemente
comum, com campos de usuário e senha. O objetivo é obter acesso administrativo
e recuperar a flag.

O desafio foi projetado para demonstrar os riscos de implementar mecanismos de
autenticação diretamente no client-side, sem validação adequada no backend.

---

## Análise Inicial
Ao tentar realizar login com credenciais aleatórias, a aplicação retorna apenas
a mensagem "failed", sem redirecionamentos ou criação de sessão, indicando a
possível ausência de validação server-side.

Ao inspecionar o código-fonte da página, foi identificado o carregamento de um
arquivo JavaScript externo chamado `secure.js`, que contém a lógica de
autenticação da aplicação.

---

## Exploração
Ao acessar o arquivo `secure.js`, foi possível identificar credenciais
hardcoded diretamente no código JavaScript, definidas nas variáveis globais
`window.username` e `window.password`.

Como toda a lógica de validação ocorria no navegador, bastou utilizar as
credenciais expostas no arquivo JavaScript para autenticar com sucesso na
aplicação.

Após realizar o login com essas credenciais, o acesso administrativo foi
concedido e a flag foi exibida na aplicação.

---

## Resultado
A flag do desafio foi obtida ao autenticar-se utilizando credenciais expostas
diretamente no código JavaScript da aplicação.

---

## Aprendizado
Este desafio demonstra um erro crítico de Application Security, onde a
autenticação é implementada inteiramente no client-side.

Como o JavaScript é público e acessível a qualquer usuário, qualquer segredo,
credencial ou lógica sensível presente no código pode ser facilmente
inspecionado e explorado.

Em aplicações reais, esse tipo de falha pode levar ao comprometimento total do
sistema e é classificada como um problema crítico de segurança.

Autenticação e autorização devem sempre ser implementadas e validadas no
backend.
