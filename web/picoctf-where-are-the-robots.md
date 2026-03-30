# PicoCTF – Where are the robots

## Contexto
- Plataforma: PicoCTF
- Categoria: Web Exploitation
- Dificuldade: Easy

O desafio apresenta uma aplicação web simples que levanta a questão sobre a
localização de áreas ocultas do site, sugerindo a análise de arquivos e
comportamentos comuns da web relacionados a robôs e acessos automatizados.

## Análise Inicial
Ao acessar a aplicação, foi exibida apenas uma página simples com uma mensagem
de boas-vindas acompanhada da pergunta "Onde estão os robôs?".

Tanto o nome do desafio quanto a mensagem apresentada indicavam que a solução
estava relacionada a algum mecanismo padrão da web utilizado para orientar
robôs ou crawlers de indexação.

## Exploração
Considerando a referência direta a "robôs", foi realizada a verificação do
arquivo `robots.txt`, um recurso padrão da web utilizado para informar a
robôs de indexação quais caminhos não devem ser acessados ou indexados.

Ao acessar o arquivo `robots.txt`, foi identificado um caminho explicitamente
listado como não permitido. Esse caminho pôde ser acessado manualmente por meio
do navegador, já que o arquivo não implementa nenhum controle real de acesso.

O acesso direto ao caminho listado resultou na exposição da flag do desafio.

## Resultado
Após acessar o caminho exposto no arquivo `robots.txt`, foi possível localizar
e obter a flag do desafio com sucesso.

## Aprendizado
Este desafio demonstra que o arquivo `robots.txt` não deve ser utilizado como
mecanismo de segurança, uma vez que seu conteúdo é público e facilmente
acessível por qualquer usuário.

Reforça a importância de implementar controles reais de autenticação e
autorização no backend da aplicação, evitando confiar na simples ocultação de
caminhos ou em mecanismos baseados em obscuridade.
