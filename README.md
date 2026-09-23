# Pesquisa de bibliotecas Python para Bancos de Dados

## Integrantes da equipe
- Igor dos Santos Lopes
- André Manoel de Santana
- Denis Sebastian Medina Crusado
  
## Contexto
Em projetos reais de software, aplicações precisam se conectar a bancos de dados para consultar, inserir, atualizar e excluir informações. No ecossistema Python, existem diversas bibliotecas que permitem essa comunicação, cada uma com finalidades diferentes.

## Objetivo
Pesquisar, comparar e apresentar bibliotecas Python utilizadas para conectar aplicações a bancos de dados relacionais e não relacionais, entendendo suas características, vantagens, limitações e cenários de uso.

## Biblioteca sqlite3 vs. psycopg2

### 1. Qual é o objetivo principal da biblioteca?

#### sqlite3
SQLite é uma biblioteca em linguagem C que permite a aplicações Python se conectarem e trabalharem com um banco de dados leve baseado em disco (SQLite), que não requer um processo de servidor separado e permite o acesso ao banco de dados usando uma variante não padronizada da linguagem de consulta SQL. 
Com ela, é possível criar bancos, criar tabelas e realizar operações como inserir, consultar, atualizar e excluir dados.

#### psycopg2
O psycopg2 é um adaptador de banco de dados para Python que permite que aplicações Python se conectem e trabalhem com bancos de dados PostgreSQL.
Com ele, é possível estabelecer conexões com o PostgreSQL, executar comandos SQL, consultar dados, inserir, atualizar e excluir registros, além de controlar transações com operações como commit() e rollback().


### 2. Que tipo de banco de dados ela permite acessar?

#### sqlite3
A sqlite3 permite acessar bancos de dados **SQLite**.
O SQLite é um banco de dados relacional que normalmente armazena todas as informações em um único arquivo '.db'.
Diferentemente de bancos como MySQL e PostgreSQL, não é necessário executar um servidor separado para utilizar o SQLite.

#### psycopg2
O psycopg2 permite acessar bancos de dados PostgreSQL.
O PostgreSQL é um sistema gerenciador de banco de dados relacional e objeto-relacional, que utiliza SQL para realizar operações sobre os dados. O psycopg2 atua como uma ponte entre a aplicação Python e uma instância do PostgreSQL. 

### 3. Ela é mais indicada para bancos relacionais ou não relacionais?

#### sqlite3
É mais indicada para bancos de dados relacionais, afinal o SQLite utiliza **SQL (Structured Query Language)** e organiza os dados em estruturas como tabelas, linhas e colunas.

#### psycopg2
É indicada para bancos de dados relacionais, especificamente para o PostgreSQL. O PostgreSQL utiliza tabelas, linhas, colunas e SQL para organizar e manipular os dados. 


### 4. A biblioteca trabalha com SQL puro, ORM ou ambos?

#### sqlite3
A sqlite3 trabalha diretamente com SQL, não sendo um ORM.

#### psycopg2
O psycopg2 trabalha diretamente com SQL, não sendo um ORM.

### 5. Como é feita a instalação?

#### sqlite3
Não é necessário instalar a sqlite3 separadamente, pois ela faz parte da **biblioteca padrão do Python**.
Basta importá-la:
```python
import sqlite3
```

#### psycopg2
O psycopg2 pode ser instalado utilizando o pip:
```python
# obs: pode exigir um compilador C
pip install psycopg2

#versao pre-compilatoria (sem exigir compilador):
pip install psycopg2-binary
```

Depois da instalação, a biblioteca pode ser importada normalmente:
```python
import psycopg2
```

### 6. Como é criado um exemplo simples de conexão?

#### sqlite3
Podemos utilizar `sqlite3.connect()` para criar uma conexão com um banco de dados.

Exemplo:

```python
import sqlite3

#representa a conexão entre a aplicação Python e o banco de dados
conexao = sqlite3.connect("meu_banco.db")

print("Conexão realizada com sucesso!")

conexao.close()
```
Nesse exemplo, se o arquivo `meu_banco.db` ainda não existir, o SQLite poderá criá-lo automaticamente.

#### psycopg2
Podemos utilizar psycopg2.connect() para criar uma conexão com um banco de dados PostgreSQL. É necessário informar dados da conexão, como o nome do banco e o usuário. 

```python
import psycopg2

# representa a conexão entre a aplicação Python e o PostgreSQL
conexao = psycopg2.connect(
    dbname="meu_banco",
    user="postgres",
    password="minha_senha",
    host="localhost",
    port="5432"
)

print("Conexão realizada com sucesso!")

conexao.close()
```

O PostgreSQL normalmente funciona como um servidor de banco de dados, portanto é necessário que uma instância do PostgreSQL esteja disponível para que a aplicação possa estabelecer a conexão. 

### 7. Como executar uma consulta `SELECT` simples?

#### sqlite3
A consulta é feita a partir de um **"cursor"** que é utilizado para executar o `SELECT`.
Vamor fingir que já temos um banco de dados com uma tabela 'usuarios', a consulta poderia ser feita assim:

```python
import sqlite3

# conecta ao banco
conexao = sqlite3.connect("meu_banco.db")

# cria um cursor
cursor = conexao.cursor()

# executa o SELECT
cursor.execute("SELECT * FROM usuarios")

# recupera os registros retornados pela consulta
usuarios = cursor.fetchall()

# exibe os resultados
for usuario in usuarios:
    print(usuario)

# fecha a conexão
conexao.close()
```

#### psycopg2
É utilizado cursor para executar o SELECT. O método execute() executa a consulta e fetchall() recupera todos os registros retornados. 

```python
import psycopg2

# conecta ao banco
conexao = psycopg2.connect(
    dbname="meu_banco",
    user="postgres",
    password="minha_senha",
    host="localhost",
    port="5432"
)

# cria um cursor
cursor = conexao.cursor()

# executa o SELECT
cursor.execute("SELECT * FROM usuarios")

# recupera os registros retornados pela consulta
usuarios = cursor.fetchall()

# exibe os resultados
for usuario in usuarios:
    print(usuario)

# fecha o cursor e a conexão
cursor.close()
conexao.close()
```
