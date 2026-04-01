# PicoCTF – GET aHEAD

## Contexto
O desafio GET aHEAD apresenta uma aplicação web simples que permite ao usuário
escolher cores por meio de botões na interface. O objetivo real do desafio é
avaliar como o backend trata diferentes métodos HTTP e identificar falhas de
lógica associadas a suposições incorretas sobre o comportamento do cliente.

---

## Análise Inicial
Ao acessar a aplicação, são apresentados dois botões: "choose red" e
"choose blue". Ao interagir com os botões, não há retorno visível na interface.

Interceptando as requisições com o Burp Suite, observou-se que o botão "red"
envia uma requisição utilizando o método HTTP GET, enquanto o botão "blue"
envia uma requisição utilizando o método POST. Isso indica que o backend possui
lógica específica baseada no método HTTP recebido.

---

## Exploração
A partir da análise inicial, identificou-se que o backend não validava outros
métodos HTTP além de GET e POST. O método HTTP HEAD, que é válido e padronizado,
foi testado manualmente.

Uma das requisições interceptadas foi enviada ao Burp Repeater e teve seu método
alterado para HEAD. Ao reenviar a requisição, o servidor respondeu normalmente,
retornando apenas os headers da resposta.

Nos headers retornados pela resposta ao método HEAD, foi possível identificar
a flag do desafio, evidenciando que o backend expunha informações sensíveis ao
utilizar um método HTTP não tratado corretamente.

---

## Resultado
O uso do método HTTP HEAD permitiu a recuperação da flag do desafio diretamente
nos headers da resposta, sem necessidade de interação pela interface gráfica.

---

## Aprendizado
Este desafio demonstra a importância de aplicar validações consistentes para
todos os métodos HTTP suportados pelo servidor. Assumir que apenas GET e POST
serão utilizados é uma falha comum de design que pode levar à exposição de
informações sensíveis.

Em ambientes reais, falhas semelhantes podem causar vazamento de metadados,
bypass de controles de segurança e comportamentos inesperados. A aplicação deve
tratar qualquer requisição de forma segura, independentemente do método HTTP
utilizado.
