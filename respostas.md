# Respostas · Avaliação Prática de Docker · Cooperativa AgroVale (Turma A)

Nome: Evelyn Victoria Araújo dos Santos
Matrícula: 26128015
Usuário do GitHub: lyndacrebs
Usuário do Docker Hub: lyndacrebs

Responda com as suas palavras e com o que aconteceu na SUA máquina. Resposta curta e certa vale mais
do que texto longo copiado. Resposta que contradiz o seu próprio Dockerfile ou compose vale zero.

## Parte 1 · Dockerfile do portal

1. Qual imagem base você usou e qual o tamanho final da imagem do portal (saída de `docker images`)?
Usei a imagem base oficial nginx:alpine. O tamanho final da imagem foi 93.6MB

2. Em qual pasta do container o Nginx procura os arquivos do site? Mostre o comando que você usou para
   conferir que o `index.html` está lá dentro.
O Nginx procura os arquivos em /usr/share/nginx/html. Conferi com o comando docker exec teste-portal ls /usr/share/nginx/html.

## Parte 2 · Docker Hub

3. Nome completo da imagem publicada e link público do repositório no Docker Hub.
Nome: lyndacrebs/agrovale-portal:1.0-26128015
Repositório: https://hub.docker.com/repository/docker/lyndacrebs/agrovale-portal/general

4. Por que o `docker login` foi feito com um token de acesso e não com a senha da conta?
Porque o token é mais seguro para autenticação no Docker Hub e pode ter permissões específicas, sem precisar expor a senha da conta.

## Parte 3 · Página de manutenção

5. Preencha uma linha por defeito encontrado. Defeito inexistente listado aqui desconta pontos.

| # | Instrução | O que estava errado | O que você viu acontecer | Como corrigiu |
|---|---|---|---|---|
| 1 | Rodar os comandos antes de alterar o DOckerfile | a página personalizada esperada não apareceu | Alterei o Dockerfile
| 2 |verificar o Dockerfile antigo | não tinha um COPY apontando para o html | Adicionei o COPY site/ /usr/share/nginx/html/
| 3 | Rodar o comando que constroi o container denovo | Deu o mesmo erro que na primeira vez | limpei o cache da imagem para contruir o container denovo usando o comando docker build --no-cache -t manutencao:26128015 ./manutencao

6. Qual a diferença entre `-p 7042:80` e `-p 80:7042` no `docker run`? Qual dos dois números é a porta do container?
A diferença está na ordem das portas. No Docker, a sintaxe é -p porta_do_host:porta_do_container. Portanto, em -p 7042:80, a porta 7042 é do host e a porta 80 é do container. Já em -p 80:7042, a porta 80 é do host e a porta 7042 é do container. Assim, o segundo número é sempre a porta do container.

## Parte 4 · docker-compose.yml

7. No serviço `blog`, por que `WORDPRESS_DB_HOST` recebe `db` e não `localhost`?
Porque db é o nome do serviço do MariaDB na rede do Docker Compose. localhost apontaria para o próprio container do WordPress, e não para o banco.

8. Por que o serviço `db` não publica a porta 3306? Se precisar consultar o banco, como faz sem publicar
   a porta? Mostre o comando.
Porque o WordPress acessa o banco pela rede interna do Docker Compose, sem precisar expor o MariaDB para o computador. Para consultar o banco, posso acessar o container diretamente com docker exec.

## Parte 5 · Persistência

9. Quais comandos você usou para derrubar e subir a stack? Qual comando teria apagado o post que você criou,
   e por quê?

10. Código de conclusão impresso pelo verificador:

```
(cole aqui)
```
