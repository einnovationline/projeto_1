--------------------LARAVEL
Cinco comandos mais importantes se o seu Laravel não estiver funcionando como esperado após algumas modificações 
no .env ou na pasta do banco de dados ou por causa de qualquer outra modificação. Aqui está a explicação completa: 
https://www.youtube.com/watch?v=Q1ynDMC8UGg

#erro1 file_put_contents No such file or directory --> solução com os comandos abaixo na sequência 1, 3 e 4
#erro2 class-redis-not-found -> solução 6, 1, 3, 4 e finalmente o 2 onde dava o erro que mostro a frente do comando
#erro3 ao executar o comando 2 dava o erro = Predis\Connection\ConnectionException -- php_network_getaddresses: getaddrinfo for redis failed: Este host no  conhecido. [tcp://redis:6379], a solução foi do erro #1

1- php artisan config:clear
2- php artisan cache:clear 
3- php artisan view:clear
4- php artisan route:clear
5- composer dump-autoload
6- docker pull redis:latest
7- php artisan migrate 

--------------------MYSQL
senha do mysql workbench (tanto pro root como pro usuário hnhostins): 123456
comando para entrar no mysql: mysql -u root -p
comando para sair do mysql: \q ou exit ou ctrl + c

#o erro no workbench sumiu ao dar o comando 1 com o usuário 'hnhostins' e senha '123456'
1- ALTER USER 'hnhostins'@'127.0.0.1' IDENTIFIED WITH mysql_native_password BY '123456';
GRANT INSERT ON *.* TO 'hnhostins'@'127.0.0.1';
GRANT ALL PRIVILEGES ON *.* TO 'hnhostins'@'127.0.0.1' IDENTIFIED BY '123456' WITH GRANT OPTION;

--------------------Ubuntu
senha do ubuntu: hnhostins

--------------------WSL
O comando: wsl --shutdown --> desligará todas as distribuições WSL 2 em execução.

-------------------GIT
…or create a new repository on the command line
echo "# app-laravel" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/hnhostins/app-laravel.git
git push -u origin main


…or push an existing repository from the command line
git remote add origin https://github.com/hnhostins/app-laravel.git
git branch -M main
git push -u origin main

…or import code from another repository
You can initialize this repository with code from a Subversion, Mercurial, or TFS project.

1 - Para verificar as modificações realizadas:
Utilize o comando "git status", ele serve para listar todos os arquivos que foram modificados.

2 - Para adicionar as mudanças ao seu repositório local:
Para adicionar todas as modificações realizadas de uma só vez, é necessário usar "git add ." 
(git add e um ponto vai tudo) e, para adicionar as mudanças em algum arquivo específico, usa-se git add nome-do-arquivo-alterado.
2.1 - se quiser modificar somente alguns arquivos:
"git add arquivo1 arquivo2 arquivo3" - separados por espaço

3 - Para salvar as alterações:
Utilize o comando "git commit -m "colocar o comentário", ele é usado quando queremos capturar e salvar o estado atual do repositório.

4 - Para enviar as modificações ao repositório remoto:
Utilize o comando "git push origin main" (main é o branch), ele é utilizado para envio das alterações gravadas no diretório local para o 
repositório remoto.
	4.1 força um commit para o servidor "git push --force origin main"

#criar uma branch paralela a master
1- git checkout -b desenvolvimento --> desenvolvimento é o nome da ramificação --é criada e já estará nela
	1.1 - git checkout desenvolvimento --> vai para a branch especificada, no caso desenvolvimento
2- git switch nomedabranch --> vai para a branch selecionada
3- git branch --> para saber em quais repositórios existem e a com * qual está
4- git remote -v --> saber qual repositório
5- git remote set-url main https://github.com/hnhostins/app-laravel.git  --> abrir conexão com o github

programas visuais para git https://desktop.github.com/ e https://www.gitkraken.com/ --> melhor

-------------------Docker
A classe seria a imagem, e o container o objeto. Volumes são diretórios externos ao container.
Para extrair nomes de contêineres docker e seus IPs, use o comando abaixo em seu terminal:
docker inspect -f '{{.Name}} - {{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' $(docker ps -aq)
