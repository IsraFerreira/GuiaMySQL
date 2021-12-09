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

create table pessoas (nome varchar(30) NOT NULL, nascimento date, sexo enum('M','F'), peso decimal(5,2), altura decimal(3,2), nacionalidade varchar(20) DEFAULT 'Brasil') DEFAULT CHARSET = utf8;

AUTO_INCREMENT - incrementa automaticamente
</br>PRIMARY KEY (chave primária)

