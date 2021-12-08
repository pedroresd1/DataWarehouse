# DataWarehouse

<h1>Data Warehouse além de 'facts sales'!</h1>

O conceito de data warehouse pode ser pesquisado através de sites da internet, conforme este <a href="https://www.computerweekly.com/tip/Inmon-or-Kimball-Which-approach-is-suitable-for-your-data-warehouse">aqui</a>.

Na prática, o 'Data Warehouse' é um banco de dados, onde se armazena 'querys' com resultados de sistemas transacionais. Aplicando conceitos de business intelligence, com objetivo de estruturar e centralizar os dados da empresa e facilitar a tomada de decisão por parte da equipe de negócios.

O motivo de ser 'além de fact sales' é que diversos livros sobre 'Data Warehouse' tem o mesmo exemplo, de tabelas transacional de vendas, portanto o objetivo desse texto é trazer um novo exemplo para a internet e ampliar o debate e o pensamento sobre 'data warehouse'.

Então vamos criar um banco dedados relacional onde possamos fazer a gestão de um sistema de escolas. Para isso vamos utilizar a ferramenta <a href="https://www.tutorialspoint.com/sqlite/index.htm">sqlite</a>.

Ao criar o nosso banco de dados.

```
CREATE DATABASE db
```

Em uma sistema simples de escola, vamos precisa armazenar:

1. Alunos
2. Professores
3. Escola

Nessas tabelas, vamos armazenar o nome de cada entidade e sua respectiva data de criação/alteração no sistema.

![image](https://user-images.githubusercontent.com/60554958/145243564-8bef8c6c-4ba0-42e3-ad7e-a23db0505cc9.png)

```
CREATE TABLE Escolas 
    (
     id_escola INTEGER PRIMARY KEY AUTOINCREMENT , 
     nome_escola VARCHAR (10) NOT NULL , 
     data_alteracao DATETIME 
    );

CREATE TABLE Professores 
    (
     id_professor INTEGER PRIMARY KEY AUTOINCREMENT , 
     nome_professor VARCHAR (10) NOT NULL , 
     data_alteracao DATETIME 
    );
	
CREATE TABLE Alunos 
    (
     id_aluno INTEGER PRIMARY KEY AUTOINCREMENT , 
     nome_aluno VARCHAR (10) NOT NULL , 
     data_alteracao DATETIME 
    );

```