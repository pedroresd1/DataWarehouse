# DataWarehouse

<h1>Data Warehouse além de 'facts sales'!</h1>

O conceito de data warehouse pode ser pesquisado através de sites da internet, conforme este <a href="https://www.computerweekly.com/tip/Inmon-or-Kimball-Which-approach-is-suitable-for-your-data-warehouse">aqui</a>.

Na prática, o 'Data Warehouse' é um banco de dados, onde se armazena 'querys' com resultados de sistemas transacionais. Aplicando conceitos de business intelligence, com objetivo de estruturar e centralizar os dados da empresa e facilitar a tomada de decisão por parte da equipe de negócios.

O motivo de ser 'além de fact sales' é que diversos livros sobre 'Data Warehouse' tem o mesmo exemplo, de tabelas transacional de vendas, portanto o objetivo desse texto é trazer um novo exemplo para a internet e ampliar o debate e o pensamento sobre 'data warehouse'.

Então vamos criar um banco dedados relacional onde possamos fazer a gestão de um sistema de escolas. Para isso vamos utilizar a ferramenta <a href="https://www.tutorialspoint.com/sqlite/index.htm">sqlite</a>.

Ao criar o nosso banco de dados.

```
CREATE DATABASE db;
```

Em uma sistema simples de escola, vamos precisa armazenar:

1. Alunos
2. Professores
3. Escola

Nessas tabelas, vamos armazenar o nome de cada entidade e sua respectiva data de criação/alteração no sistema. Então o nosso modelo de dados ficará assim:

![image](https://user-images.githubusercontent.com/60554958/145249311-a7f11af1-6fd2-48c5-bbaa-417a4e562b4d.png)

O código sql para a criação dessas tabelas:

```
CREATE TABLE Escolas 
    (
     id_escola INTEGER PRIMARY KEY AUTOINCREMENT , 
     nome_escola VARCHAR (100) NOT NULL , 
     data_alteracao DATETIME 
    );

CREATE TABLE Professores 
    (
     id_professor INTEGER PRIMARY KEY AUTOINCREMENT , 
     nome_professor VARCHAR (100) NOT NULL , 
     data_alteracao DATETIME 
    );
	
CREATE TABLE Alunos 
    (
     id_aluno INTEGER PRIMARY KEY AUTOINCREMENT , 
     nome_aluno VARCHAR (100) NOT NULL , 
     data_alteracao DATETIME 
    );
```
<h5>Observação: O 'AUTOINCREMENT' realiza a inserção do próximo 'id' na tabela de forma 'automatica', sem a necessídade de inclusão do id no momento do insert.</h5>

Populando e conferindo a tabela escolas:
```
INSERT INTO Escolas (nome_escola, data_alteracao)
VALUES ('Escola Estadual Minas Gerais',DATETIME());

INSERT INTO Escolas (nome_escola, data_alteracao)
VALUES ('Escola Estadual São Paulo',DATETIME());

INSERT INTO Escolas (nome_escola, data_alteracao)
VALUES ('Escola Estadual Rio de Janeiro',DATETIME());

SELECT * FROM Escolas;
```
![image](https://user-images.githubusercontent.com/60554958/145245857-4fbd2001-4f46-418c-b436-99c62037ccf5.png)

Populando e conferindo a tabela professores:
```
INSERT INTO Professores (nome_professor, data_alteracao)
VALUES ('Antonio',DATETIME());

INSERT INTO Professores (nome_professor, data_alteracao)
VALUES ('Maria',DATETIME());

INSERT INTO Professores (nome_professor, data_alteracao)
VALUES ('Carlos',DATETIME());

INSERT INTO Professores (nome_professor, data_alteracao)
VALUES ('Francine',DATETIME());

SELECT * FROM Professores;
```
![image](https://user-images.githubusercontent.com/60554958/145247620-a826f16e-1a05-452d-bb00-c350af0b4602.png)

Populando e conferindo a tabela alunos:
```
INSERT INTO Alunos (nome_aluno, data_alteracao)
VALUES ('Everson',DATETIME());

INSERT INTO Alunos (nome_aluno, data_alteracao)
VALUES ('Mariano',DATETIME());

INSERT INTO Alunos (nome_aluno, data_alteracao)
VALUES ('Junior Alonso',DATETIME());

INSERT INTO Alunos (nome_aluno, data_alteracao)
VALUES ('Nathan Silva',DATETIME());

INSERT INTO Alunos (nome_aluno, data_alteracao)
VALUES ('Arana',DATETIME());

INSERT INTO Alunos (nome_aluno, data_alteracao)
VALUES ('Jair',DATETIME());

INSERT INTO Alunos (nome_aluno, data_alteracao)
VALUES ('Allan',DATETIME());

INSERT INTO Alunos (nome_aluno, data_alteracao)
VALUES ('Matias Zaracho',DATETIME());

INSERT INTO Alunos (nome_aluno, data_alteracao)
VALUES ('Keno',DATETIME());

INSERT INTO Alunos (nome_aluno, data_alteracao)
VALUES ('Diego Costa',DATETIME());

INSERT INTO Alunos (nome_aluno, data_alteracao)
VALUES ('Hulk',DATETIME());

SELECT * FROM Alunos;
```
![image](https://user-images.githubusercontent.com/60554958/145248276-1deeaeff-aa8c-4755-b10c-3b4d396231c9.png)

A Escola então contrata mais de um professor e o professor pode ser contratado por mais de uma escola, gerando contratos diferentes, sendo assim, criaremos uma tabela chamada ContrataProfessores, onde armazenara a escola e o professor e o id de seu contrato e se ele se encontra ativo ou não, junto com as datas de criação do contrato e a data de vencimento do contrato.

```
CREATE TABLE ContrataProfessor 
    (
     id_contrato INTEGER NOT NULL , 
     data_contratacao DATE NOT NULL , 
     data_vencimento DATE NOT NULL , 
     sim_nao_ativo VARCHAR (3) NOT NULL , 
     data_alteracao DATETIME 
    );

ALTER TABLE ContrataProfessor ADD COLUMN id_professor INTEGER REFERENCES Professores(id_professor);

ALTER TABLE ContrataProfessor ADD COLUMN id_escola INTEGER REFERENCES Escolas(id_escola);
```
![image](https://user-images.githubusercontent.com/60554958/145251084-b3e0bd95-704d-4d3b-864f-8372c7b96012.png)
