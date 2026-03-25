# PicoCTF - Crack the Gate 1
## Contexto
- Plataforma: PicoCTF
- Categoria: Web Exploitation
- Dificuldade: Easy

O desafio apresenta uma aplicação web com um portal de login restrito,
onde o objetivo é obter acesso ao sistema.

## Análise Inicial
Ao acessar a aplicação, foi identificada uma página de login contendo
campos de email e senha, além de um botão de autenticação.

O enunciado do desafio indicava que havia alguma informação sensível exposta,
sugerindo que o problema estivesse relacionado à implementação interna da aplicação.

## Exploração
Ao inspecionar o código-fonte da aplicação, foi identificado um comentário
que aparentava estar codificado, sugerindo a existência de um mecanismo
de bypass de autenticação.

A mensagem encontrada foi decodificada utilizando ROT13, revelando a
instrução para o uso de um header HTTP específico como forma de
contornar o mecanismo de autenticação.

Ao enviar a requisição de login contendo o header indicado,
foi possível acessar o sistema sem a validação de credenciais válidas.

## Resultado
Após a exploração da falha, foi possível acessar o conteúdo restrito,
obtendo a flag do desafio com sucesso.

## Aprendizado
Este desafio demonstra que não se deve confiar em dados controlados pelo usuário,
especialmente no que diz respeito a mecanismos de autenticação.

Reforça a importância de que toda a lógica de autenticação e controle de acesso
seja tratada exclusivamente no backend, além da necessidade de revisar o código
antes de colocá-lo em produção para evitar a permanência de mecanismos inseguros.

