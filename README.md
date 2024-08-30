# Como restaurar backup postgresql 

> [!NOTE]
> esse procedimento é realizado para restaurar backup de projetos sql que são feitos em containers docker e sem utilização de volumes no compose.yaml

>[!ATTENTION]
> o procedimento deve ser realizado após a criação dos containers e criação do servidor postgres na interface do pgadmin

## Passo inicial
criar backup do banco na interface do pgadmin _(salvar com .sql)_ e realizar o download do arquivo para a máquina local. _(pensando em container docker)_ 

## Segundo passo 
copiar o arquivo sql _(arquivo no diretório que o terminal estiver aberto)_ e enviar para o postgres via linha de comando. 
``` 
 1: -$ sudo docker cp [arquivo.sql] [id do container postgres]:/
```
Se o processo for bem sucedido, vai mostrar sussesful + tamanho do arquivo copiado para o diretório raiz do container postgres

## Terceiro passo
acessar o terminal interno do container do postgres com o seguinte comando
``` 
2: -$ sudo docker exec -it [id do container postgres] bash
```
se funcionar, vai abrir o terminal no container postgres.
ex:\
`root@e[id do container postgres]:/#`
## Quarto passo
criar um banco para incluir o backup
``` 
3: -$ createdb -U postgres [nome do banco]
```
## Quinto passo
o aquivo.sql é aquele que foi copiado anteriormente, com o comando 'ls' é possivel verificar se está realmente presente!
```
4: -$ psql -U postgres -d [nome do banco] < [arquivo.sql]
```
GG, boa boa.
