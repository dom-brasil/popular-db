# Origem dos dados de testes para pesquisados

Para gerar os dados de testes utilizamos o script em python que copia os registros da tabela 
pesquisado de origem para a tabela pesquisado de destino.

A base de dados `employees` possui mais de 300.000 registros e é um exemplo criado para testar 
as funcionalidades do MySQL sem a necessidade de se criar os dados.


## Popular employees

Verifique se a base de dados `employees` existe no servidor, caso não existe cria a base de dados da seguinte forma:

    Crie a base de dados no terminal...

        mysql -h localhost - u root -p
        > CREATE DATABASE employees;
        > exit

    Execute o comando abaixo...

        git clone https://github.com/datacharmer/test_db.git

    E execute o comando do MySQL para inserir os dados na database employees...

        mysql -h localhost --database=employees- u root -p < employees.sql


## Instalação do script populat-db

Depois de ter criado a base de dados employees, localize o projeto `popular-db`, caso não tenha execute no terminal...

    git clone https://github.com/kenji-tabata/popular-db.git

Instale o VirtualEnv no projeto.

    $ virtualenv popular-db

Ative o VirtualEnv.

    $ cd popular-db
    $ source bin/activate

Instale os módulos SqlAlchemy e PyMySQL.

    $ pip install sqlalchemy
    $ pip install pymysql


## Copiando registros do employees para base de dados selecionada

Edite o arquivo `pesquisados/adicionar.py` altere os dados da conexão do usuário do Mysql se necessário

    conexao.user = "seu-usuario"
    conexao.psw  = "sua-senha"
    conexao.host = "seu-endereço-de-host"
    conexao.port = "porta-do-mysql"

Altere o nome da base de dados para onde os dados serão adicionados

    adicionar_na_base_dados = "nome-da-base-de-dados"

Altere a quantidade de registros que serão adicionados

    add_quantos_registros = 100

Caso queira ver o log dos registros sendo adicionados altere para True a variável `ver_registros_add`.

    ver_registros_add = True

Caso a tabela já tenha dados populados ative `adicionar_entre_os_ids` e especifique o `id_inicial` e 
`id_final` de acordo com a quantidade de registros copiados.

    adicionar_entre_os_ids = True
    id_inicial  = 11025
    id_final = 11030

E execute o script...

    $ python pesquisados/adicionar.py