# Pesquisa de bibliotecas Python para Bancos de Dados

## Contexto
Em projetos reais de software, aplicações precisam se conectar a bancos de dados para consultar, inserir, atualizar e excluir informações. No ecossistema Python, existem diversas bibliotecas que permitem essa comunicação, cada uma com finalidades diferentes.

## Objetivo
Pesquisar, comparar e apresentar bibliotecas Python utilizadas para conectar aplicações a bancos de dados relacionais e não relacionais, entendendo suas características, vantagens, limitações e cenários de uso.

## Biblioteca sqlite3 vs. psycopg2

### 1. Qual é o objetivo principal da biblioteca?

SQLite é uma biblioteca em linguagem C que permite a aplicações Python se conectarem e trabalharem com um banco de dados leve baseado em disco (SQLite), que não requer um processo de servidor separado e permite o acesso ao banco de dados usando uma variante não padronizada da linguagem de consulta SQL. 
Com ela, é possível criar bancos, criar tabelas e realizar operações como inserir, consultar, atualizar e excluir dados.

### 2. Que tipo de banco de dados ela permite acessar?

A sqlite3 permite acessar bancos de dados **SQLite**.
O SQLite é um banco de dados relacional que normalmente armazena todas as informações em um único arquivo '.db'
Diferentemente de bancos como MySQL e PostgreSQL, normalmente não é necessário executar um servidor separado para utilizar o SQLite.

### 3. Ela é mais indicada para bancos relacionais ou não relacionais?

É mais indicada para bancos de dados relacionais, afinal o SQLite utiliza **SQL (Structured Query Language)** e organiza os dados em estruturas como tabelas, linhas e colunas .

### 4. A biblioteca trabalha com SQL puro, ORM ou ambos?

A sqlite3 trabalha diretamente com SQL, não sendo um ORM.

Por exemplo:

### 5. Como é feita a instalação?

Não é necessário instalar a sqlite3 separadamente, pois ela faz parte da **biblioteca padrão do Python**.

Basta importá-la:

```python
import sqlite3
```

Portanto, normalmente não é necessário executar `pip install sqlite3`.

### 6. Como é criado um exemplo simples de conexão?

Podemos utilizar `sqlite3.connect()` para criar uma conexão com um banco de dados.

Exemplo:

```python
import sqlite3

conexao = sqlite3.connect("meu_banco.db")

print("Conexão realizada com sucesso!")

conexao.close()
```

Nesse exemplo, se o arquivo `meu_banco.db` ainda não existir, o SQLite poderá criá-lo automaticamente.

A variável `conexao` representa a conexão entre a aplicação Python e o banco de dados.

### 7. Como executar uma consulta `SELECT` simples?

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


## Pesquisa

1. Qual é o objetivo principal da biblioteca?
2. Que tipo de banco de dados ela permite acessar?
3. Ela é mais indicada para bancos relacionais ou não relacionais?
4. A biblioteca trabalha com SQL puro, ORM ou ambos?
5. Como é feita a instalação?
6. Como é criado um exemplo simples de conexão?
7. Como executar uma consulta *SELECT* simples?




