Quando uma nova pasta/arquivo é criado, muitas vezes queremos adicionar uma permissão a mais para um usuário ou grupo, e ficamos na dúvida do que fazer. O que a maioria tenta fazer era utilizar o comando chown, sendo que eles não podem ser dados por usuários sem root e podem apenas dar permissão para um único usuário/grupo.

O comando que deve ser utilizado nessas situações é o setfacl, e só funcionará se você for dono do arquivo ou root. Ele irá adicionar uma permissão a uma pasta/arquivo sem mudar o dono/grupo principal. A estrutura dele é bem simples:

``setfacl -m permissão /local/do/diretório/ou/arquivo``

Onde no lugar de permissão você vai colocar o acesso que desejar com a seguinte estrutura: user/group:Usuario/Grupo:Permissão
Exemplos:
```
setfacl -m user:2rp-guilherme:rwx /home/2rp-guilherme
setfacl -m group:dataadmin_users:rwx /home/dataadmin
```
Lembrando, no Linux as permissões disponíveis são:
```
read:    r (Ler)
write:   w (Editar)
execute: x (Executar)
```
***OBS: Para remover uma permissão, troque o -m por -x, e caso queira dar permissão em tudo o que tiver dentro de uma pasta, coloque um -R antes do -m***
 
Caso queira ver quais permissões já existem em uma pasta/arquivo, basta usar o getfacl com a seguinte estrutura:

``getfacl /local/do/diretório/ou/arquivo``

 
Links para saberem com mais detalhes o funcionamento do comando:
https://www.dicas-l.com.br/arquivo/permissoes_no_linux_alem_do_chmod.php
http://www.bosontreinamentos.com.br/linux/acl-access-control-list-ajustando-permissoes-avancadas-no-linux/