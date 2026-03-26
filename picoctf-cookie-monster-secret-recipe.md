# PicoCTF – Cookie Monster Secret Recipe

## Contexto
- Plataforma: PicoCTF
- Categoria: Web Exploitation
- Dificuldade: Easy

O desafio apresenta uma aplicação web que protege uma receita secreta
por meio de um sistema de autenticação, desafiando o usuário a descobrir
como obter acesso ao conteúdo protegido.


## Análise Inicial
Ao acessar a aplicação, foi identificada uma página de login com campos
para nome de usuário e senha, além de um botão de autenticação.

O título da página indicava tratar-se da "Receita Secreta do Monstro dos Biscoitos",
sugerindo que o acesso ao conteúdo era restrito.


## Exploração
A partir da dica fornecida pelo desafio, foi possível identificar que a falha
estava relacionada ao uso de cookies para controle de acesso.

Ao analisar os cookies definidos pela aplicação, foi identificado um cookie
chamado `secret-recipe`. O valor desse cookie não se encontrava em texto claro,
indicando a utilização de algum tipo de codificação.

Após uma análise mais cuidadosa, foi identificado que o valor do cookie estava
codificado em Base64, permitindo a recuperação da flag do desafio.


## Resultado
Após a identificação e decodificação do valor armazenado no cookie,
foi possível recuperar a receita secreta, que correspondia à flag
do desafio.


## Aprendizado
Este desafio demonstra os riscos de utilizar cookies no lado do cliente
para armazenar informações sensíveis ou controlar acesso a conteúdos
protegidos.

Reforça a importância de que dados confidenciais não sejam expostos ou
facilmente recuperáveis no navegador, além de destacar que mecanismos de
autenticação e autorização devem ser tratados exclusivamente no backend.
