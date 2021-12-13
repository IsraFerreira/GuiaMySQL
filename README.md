# Repositório para dúvidas e/ou aprendizado acerda de MySQL 
Baseado nos ensinamentos do curso MySQL do Curso em Vídeo


Arquivos guardam Tabelas que guardam Registros

Arquivos de acesso sequencial - registros que tinham que ser lidos em sequência

Arquivos de Acesso direto -  registros são armazenados e acessados de maneira direta

Baco de dados é composto por 4 coisas: 
<br>Base de dados - dados propriamente ditos (estrutura dos dados)
<br>Sistema Gerenciador (DNS / SGBD) - Gerencia esses dados
<br>Linguagem de exploração - Lingugagem de acesso ao dado
<br>Programas adicionais - Gerência de usuários / Otimizadores de dados, enfim, tudo o que tiver de extra que o banco de dados irá conter.

Modelo de estruturação de dados (na sua criação)
<br>Modelo Hierárquico 
<br>Modelo em rede 

(No futuro surgiu o:)
<br>Modelo Relacional (utilizado no curso)

Modelos baseados a documentos 
<br>Modelos orientados a objetos


A partir de dados armazenados podemos prosseguir em suas relações.

SQL é uma linguagem de consulta 
<br>ANSI SQL - Padrão que foi criado para o SQL

Tipos de banco de dados pagos: 
<br>Oracle
<br>IBM (DB2)
<br>dBASE
<br>SQL Server

Tipos de banco de dados gratuitos:
<br>MySQL
<br>MariaDB
<br>Firebird
<br>PostgreSQL


## Iniciando no mundo do MySQL

Surgiu em 1994 na suécia
<br>Michael Widenius e David Axmark criaram um modelo gratuito baseado no modelo relacional
<br>Grátis e Livre (cadastrado na GPL)

O grupo MySQL foi comprado pela empresa Sun Microsystems
<br>E a Sun foi comprada pela Oracle

MySQL é usado por várias empresas famosas (Nasa, Google, Wikipedia, Adobe, Cisco, Ebay, todas as empresas de telecomunicações, Bradesco, Forças Armadas)

Tem DDL - linguagem de definição
<br>DLL - linguagem de manipulação
<br>DQL - faz solicitações
<br>DCL - controla
<br>DTL - trata das transações (qualquer solicitação feita a um banco de dados e ele irá te atender da melhor forma possível)

Seguindo o padrão D I C A  (características e uma boa transação)
<br>Durabilidade (os dados se mantém mesmo depois de muito tempo)
<br>Isolamento (toda a transação é isolada, podendo ocorrer 2 ao mesmo tempo, sem influenciar na outra)
<br>Consistência (se tudo esta OK, o BD se mantém OK)
<br>Atomicidade (Ou tudo dá certo ou retorna ao estado anteriormente consistente)

No curso utilizamos o Wamp e acessamos no MySQL Workbench


## Códigos Iniciais e Tipos primitivos

Bancos de dados são conjuntos de tabelas e tabelas são conjuntos de registros e registros são compostos por campos

<b>CREATE DATABASE</b> Cadastro;  //Cria BD
<br>afetamos 1 linha, pois temos 1 bd novo.

<b>USE</b> ...; (seleciona BD)
<br><b>CREATE TABLE</b> pessoas (); //cria tabela
<br><b>DESCRIBE</b> ... ; (descreve a tabela)

Tipos primitivos do MySQL
<br>Numérico (Inteiro - TinyIny(3)/ SmallInt/ Int/ MediumInt/ BigInt, Real - Decimal/ Float/ Double/ Real, Logico - Bit/ Boolean)
<br>Data/Tempo (Date/ DateTime/ TimeStamp/ Time/ Year)
<br>Literal (Caractere - Char/ VarChar, Texto - TinyText/ MediumText/ MediumText/ LongText, Binário - TinyBlob/ Blob/ MediumBlob/ LongBlob, Coleção - Enum/ Set)
<br>Espacial (Geometry/ Point/ Polygon/ MultiPolygon)


## Estrutura melhorada da tabela inicial


utf-8 - preparado para nossa linguagem acentuada
</br><b>CREATE DATABASE cadastro DEFAULT CHARACTER SET utf8 DEFAULT COLLATE utf8_general_ci;</b>  

<b>DROP DATABASE</b> (apaga banco de dados)

NOT NULL (precisa ser preenchido)
</br>ENUM('M','F') - Só aceita o padrão que coloquei
</br>DECIMAL (5,2) - Será criado um numero decimal onde haverão 5 casas, com 2 antes da vírgula e o resto depois  (total / antes da vírgula)
</br>DEFAULT 'Brasil' (caso não seja preenchido, será Brasil)

create table pessoas (id int NOT NULL AUTO_INCREMENT, nome varchar(30) NOT NULL, nascimento date, sexo enum('M','F'), peso decimal(5,2), altura decimal(3,2), nacionalidade varchar(20) DEFAULT 'Brasil', PRIMARY KEY(id)) DEFAULT CHARSET = utf8;

AUTO_INCREMENT - incrementa automaticamente
</br>PRIMARY KEY (chave primária)


##  Inserção

Insert into Insert into pessoas (id, nome, nascimento, sexo, peso, altura, nacionalidade) values ('1', 'Godofredo', '1984-01-02', 'M', '78.5', '1.83', 'Brasil');
<br>Coloca dados na tabela

DEFAULT - coloca o padrão no determinado campo
<br>Insert into pessoas (id, nome, nascimento, sexo, peso, altura, nacionalidade) values (DEFAULT, 'Creusa', '1920-12-30', 'F', '50.2', '1.65', DEFAULT);

Não precisa necessariamente colocar as colunas, caso os valores estejam em ordem certa, podemos utilizar apenas:
<br>Insert into pessoas values (DEFAULT, 'Adalgiza', '1930-11-2', 'F', '63.2', '1.75', 'Irlanda');

Podemos também fazer 1 Insert into para vários registros.
<br>Insert into pessoas values (DEFAULT, 'Ana', '1975-12-22', 'F', '52.3', '1.45', 'EUA'), (DEFAULT, 'Pedro', '2000-07-15', 'M', '52.3', '1.45', 'Brasil'), (default, 'Maria', '1999-05-30', 'F', '75.9', '1.70', 'Portugal');

DDL - definição (ex: create database, create table)
<br>DML - Manipulação (insert into)


## Alter Table e drop table

ALTER TABLE pessoas ADD COLUMN profissao varchar (10);
<br>Altera a coluna pessoas adicionando a coluna profissão

DROP COLUMN (elimina coluna da tabela)
<br>AFTER (coloca coluna depois de outra específica)
<br>FIRST (coloca coluna no primeiro campo)
<br>MODIFY (Modifica a coluna)

ALTER TABLE pessoas ADD COLUMN profissao varchar(10) AFTER nome;

CHANGE COLUMN (Muda o nome de uma coluna)

Para mudar o nome de uma tabela é usado o comando:
<br>ALTER TABLE pessoas RENAME TO gafanhotos;

IF NOT EXISTIS / IF EXISTS (Funções boas para verificação)
<br>UNIQUE (Faz com que os dados de uma coluna não possam ser repetidos)
<br>UNSIGNED (sem sinal)

ADD PRIMARY KEY(coluna);

DROP TABLE (exclui estrutura da tabela)


## UPDATE, DELETE e TRUNCATE

Manipulando registros / linhas / tuplas

UPDATE (atualiza registro)
<br>SET (colocar)
<br>WHERE (escolhendo um campo para se basear)
<br>LIMIT (limita quantas linhas são afetadas)

UPDATE cursos SET nome = 'HTML' WHERE idcurso = 1 LIMIT 1;

Para excluir uma linha podemos usar DELETE FROM (delimitando à aquela linha)
<br>DELETE FROM cursos WHERE idcurso = 8;

Também é possível remover todas as linhas da tabela
<br>TRUNCATE cursos;


## Obtendo dados das tabelas

No comando Select:
<br>Podemos selecionar colunas em específico (mais de uma) ou * para todos
<br>ORDER BY (ordena os elementos, podendo usar mais de um atributo de ordenação)
<br>ASC - ascendente 
<br>DESC - descendente (ordem inversa)
<br>select ano, nome, carga from cursos order by ano, nome ASC;



WHERE (linhas específicas)
<br>Select * from cursos WHERE carga = '40' order by nome;

Diferente  <> ou !=

BETWEEN AND (entre uma coisa e outra)
<br>Select nome, ano from cursos where ano between 2014 and 2016 order by ano desc, nome asc;

IN (Valores específicos)
<br>Select nome, ano from cursos where ano in (2014, 2016) order by ano;

Operadores lógicos também podem ser usados
<br>Select nome, carga, totaulas from cursos where carga > 35 and totaulas < 30 order by ano; (E)
<br>Select nome, carga, totaulas from cursos where carga > 35 or totaulas < 30 order by ano;(OU)


Seleção por Like (parecido)
<br>p% - começando por P (nenhum ou vários caracteres)
<br>%a% (a em qualquer lugar)
<br>%p - P no final

not like %a% (irá mostrar tudo o que não tem A no nome)

select * from cursos where nome like 'ph%p_' ; (cursos que tenham seus nomes começados em PH, tenham algo ou nada no meio, terminem com p e tenham um caractere no final)
<br>select * from cursos where nome like 'p_p%' ; (começam com p, tem um caractere depois, em seguida tem p e terminam com qualquer coisa)

Distinção
<br>SELECT DISTINCT (não busca repetidamente - considera apenas uma ocorrência)
<br>select distinct nacionalidade from gafanhotos order by nacionalidade;

Agregação
<br>count (*) - conta todos que fazem parte
<br>select count(*) from cursos;
<br>select count(*) from cursos where carga > 40;

max() - mostra o maior valor
<br>select max(carga) from cursos;
<br>select max(totaulas) from cursos where ano = '2016';

min() - mostra o menor valor
<br>select nome, min(totaulas) from cursos where ano = '2016';

sum() - somatório
<br>select sum(totaulas) from cursos where ano = '2016';

avg (tira a média)
<br>select avg(totaulas) from cursos where ano = '2016';



Group By (cria agrupamentos com o que foi solicitado)
<br>select carga, count(nome) from cursos group by carga;

Having (usado na mesma coluna do group by, para fazer seleções)
<br>select ano, count(*) from cursos group by ano having count(ano) >= 5 order by count(*) desc;

Podemos colocar um select dentro de outro: 
<br>select carga, count(*) from cursos where ano > 2015 group by carga having carga > (select avg(carga) from cursos);

Uma lista que mostra os gafanhotos que nasceram fora do Brasil, mostrando o país de origem e o total de pessoas nascidas lá. Onde aparecem os países que tiverem mais de 3 <br>gafanhotos com essa nacionalidade.
<br>select nacionalidade, count(*) from gafanhotos where nacionalidade != 'Brasil' group by nacionalidade having count(nacionalidade) > 3;





