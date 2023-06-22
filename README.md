# Oracle_For_Toad
SQL  👋


<div  alt="linguagens"style="display: inline_block"></br>
 
 <img align="center" alt="ORACLE" src="https://img.shields.io/badge/ORACLE-DD0031?style=for-the-badge&logo=oracle&logoColor=white"/>
  <img align="center" alt="virtualbox" src="https://img.shields.io/badge/VIRTUALBOX-02569B?style=for-the-badge&logo=virtualbox&logoColor=white"/>
   <img align="center" alt="sQl" src="https://img.shields.io/badge/SQL-00000F?style=for-the-badge&logo=sql&logoColor=white"/>
  
 <img align="center" alt="" src="https://img.shields.io/badge/PL/SQL-14354C?style=for-the-badge&logo=pl/sql&logoColor=white"/>
  
</div></br>

# **Práticas com o Oracle DB pelo Toad**

---





[Oracle Database by zorddie](https://i.ytimg.com/vi/_NzJpnERaqA/hqdefault.jpg?sqp=-oaymwEbCKgBEF5IVfKriqkDDggBFQAAiEIYAXABwAEG&rs=AOn4CLCQ7zki-8Llu_hdKo29tK8N6I8HVw)


## **Para executar os comandos, selecionar a linha e teclar F9**

## **Para executar várias linhas de uma vez, selecionar a linha e teclar F5**

## Primeiro passo:

1. [criar um mabiente virtual do windows 10](https://www.youtube.com/watch?v=_NzJpnERaqA&list=PLJZRlbWeQvwI8nRzviH5ckXwYudrw2T56&index=1&pp=iAQB)

2. [preparar e configurar o firewal](https://www.youtube.com/watch?v=_NzJpnERaqA&list=PLJZRlbWeQvwI8nRzviH5ckXwYudrw2T56&index=1&pp=iAQB)

3. [instalação do Oracle 11g](https://www.youtube.com/watch?v=_NzJpnERaqA&list=PLJZRlbWeQvwI8nRzviH5ckXwYudrw2T56&index=1&pp=iAQB)

4. [intalação do toad for Oracle](https://www.youtube.com/watch?v=_NzJpnERaqA&list=PLJZRlbWeQvwI8nRzviH5ckXwYudrw2T56&index=1&pp=iAQB)

  ## **Dicionário**

1. grant =  permissão
2. dba = Administrador de Banco de Dados
3. identified = criador de senha

## **COMANDO INTERNO DO ORACLE**

## *HORA E DATA ATUAL*
````
select sysdate
from dual
````

## **Criando usuário admin**
```
create user admin identified by "asdf@789";
```

## Fornecendo credencial de DBA
```
grant dba to admin with admin option;
```

# **Criando usuário**

## **Criação de usuário e senha de acesso**
```
create user zorddie identified by "lkjh@123";
```

# **Autorização e tipos para usuario**

## Autorizando criação de conexão
```
grant connect to zorddie;
```

## Autorizando criar sessão
````
grant create session to zorddie;
````

## Autorizando alterar seção

```
grant alter session to zorddie;
```

## Autorizando o usuário selecionar todas as tabelas
````
grant select any table to zorddie;
````

## Autorizando o usuário a criar todo tipo de tabela
````
grant create any table to zorddie;
````

## Autorizando a criação de vários tipos de procedimentos
````
grant create any procedure to zorddie;
````

## Autorizando o usuário a executar diversos tipos de procedimentos
````
grant execute any procedure to zorddie;
````

## Autorizando o usuário a criar views
````
grant create any view to zorddie;
````

## Autorizando o usuário a criar um procedimento armazenado no banco de dados que é chamado automaticamente sempre que ocorre um evento especial no banco de dados. Por exemplo, um acionador pode ser chamado quando uma linha é inserida em uma tabela especificada ou quando determinadas colunas da tabela estão sendo atualizadas.
````
grant create trigger to zorddie;
````

# **Criação de ROLES**

 Uma Role ou papel é um agrupamento de permissões que pode ser concedida a usuários ou outras roles. Sua utilização ajuda a administrar as permissões de objetos no banco de dados, e poupa o tempo que seria gasto com permissões e revogações individuais.


# **Nível 1**

### **Fazendo a separação de nível que cada "ROLE" deve conter.**

## Criação da Role nivel_1

````
create role nivel_1;
````

## Permissão de seleção de todas as tabelas rode nivel_1

````
grant select any table to nivel_1;
````

## Permissão de conexão com o banco
````
grant connect to nivel_1;
````

## Permissão de alteração de sessão
````
grant alter session to nivel_1
````

## Permissão para criar sessão
````
grant create session to nivel_1;
````

## Permissão para executar procedimentos
````
grant execute any procedure to nivel_1
````

### **Após criar a ROLE nivel_1 já pode escolher um usuário criado, ou cria um usuário para conceder-le permissões de nível 1.**


## criando um usuário
````
create user joao identified by "lkjh@123";
````

## Conceder permissão de nivel_1 para um determidado usuário
````
grant nivel_1 to joao;
````

## definição de padrão nivel_1 para joao  por default
````
alter user joao default role nivel_1;
````

# **Nível 2**

## Criação da Role nivel_2

````
create role nivel_2;
````

## Autorizar todas as permissões que existem na ROLE nivel_1 por default na nivel_2
````
grant nivel_1 to nivel_2;
````

### **EXCLUSIVO DO NÍVEL 2,3**
## Permissão para inserir qualquer tabela
````
grant insert any table to nivel_2;
````

## Permissão para fazer Update em qualquer tabela
````
grant update any table to nivel_2;
````

## Permissão para fazer delete em qualquer tabela
````
grant delete any table to nivel_2;
````

## Permissão de seleção sequencial
````
grant select any sequence to nivel_2;
````

### **Após criar a ROLE nivel_2 já pode escolher um usuário criado, ou cria um usuário para conceder-le permissões de nível 1. Lembrando que a ROLE de nível 2 é composta pela ROLE de nível 1 e mais algumas permissões.**

## criando um usuário para conceder-lhe a permissão de nivel_2
````
create user luiz identified by "lkjh@123";
````

## Permissão de nível 2 para usuário luiz
````
grant nivel_2 to luiz;
````

## definição de padrão nivel_2 para luiz  por default
````
alter user luiz default role nivel_2;
````


# **Nível 3**

## criando ROLE nivel_3
````
create role nivel_3;
````

## Autorizar todas as permissões que existem na ROLE nivel_2 por default na nivel_3
````
grant nivel_2 to nivel_3;
````

### **EXCLUSIVO DO NÍVEL 3**

## criar tabela
````
grant create any table to nivel_3;
````

## Permissão de criar qualquer tabela
````
grant create any table to nivel_3;
````

## Autorizando o usuário de nível 3 a criar um procedimento armazenado no banco de dados que é chamado automaticamente sempre que ocorre um evento especial no banco de dados. Por exemplo, um acionador pode ser chamado quando uma linha é inserida em uma tabela especificada ou quando determinadas colunas da tabela estão sendo atualizadas
````
grant create any trigger to nivel_3;
````

## Permissão de criação de View
````
grant create any view to nivel_3;
````

## Permissão para o usuário do nível 3 a executar diversos tipos de procedimentos
````
grant create any procedure to nivel_3;
````

## Permissão para sequenciar
````
grant create any sequence to nivel_3;
````

## Permissão para dropar
````
grant drop any table to nivel_3;
````

## Permissão para dropar trigger
````
grant drop any trigger to nivel_3;
````

## Permissão para dropar trigger
````
grant drop any procedure to nivel_3;
````

## Permissão para dropar trigger
````
grant drop any view to nivel_3;
````

## Permissão para dropar trigger
````
grant drop any sequence to nivel_3;
````

## criando usuário para o nível 3
````
create user zorddie identified by "alsk@456";
````

## definir o usuário para o nível 3
````
grant nivel_3 to zorddie;
````

## definição de padrão nivel_3 para zorddie  por default
````
alter user zorddie default role nivel_3;
````
## corrige o erro de espaçamento de parentese na criaçãode tables para usuário
````
grant unlimited tablespace to zorddie;
````

# **Aprendendo o DROP**

### **O drop é a deleção**

## Dropando o usuário
````
drop user nameUser;
````

# **Outras formas de inserir/alterar usuários de acordo com a grant desejada pelo nível**.

#### 1 **Bastando segurar a tecla CTRL + click no mouse em cima do nome do usuário.**
#### 2 **Assim que abrir a janela clique denteo da janela com o botão direito do mouse e escolha a opcção "alter".**

#### 3 **Escolher aba "ROLES"**

# **REMOVENDO uma ROLE de um usuário**

## Removendo as permissões do usuário
````
revoke nivel_3 from nameUser;
````
# *Criando Tabelas*

### **Necessário logar um usuário de nível 3 defeinido para começar.**

## Criando a tabela pessoa_fisica
````
create table pessoa_fisica(
 nr_sequencia integer, 
 dt_criacao date, 
 dt_alteracao date, 
 nm_pessoa_fisica varchar2(255), 
 dt_nascimento date, 
 nr_cpf varchar2(11), 
 qt_altura number(3,2)
 )
````

## Criando uf
````
create table uf(
 nr_sequencia integer,
 dt_criacao date,
 dt_alteracao date,
 cd_uf_ibge number(2),
 sg_uf varchar2(2),
 ds_uf varchar2(255) 
 );
````

## Criando tabela municipio
````
create table municipio(
 nr_sequencia integer,
 dt_criacao date,
 dt_alteracao date,
 cd_municipio_ibge number(7),
 ds_municipio varchar2(255)
 );
````

## Criando a tabela pessoa_fisica_endereco
````
create table pessoa_fisica_endereco(
 nr_sequencia integer,
 dt_criacao date,
 dt_alteracao date,
 nr_seq_pessoa_fisica integer,
 nr_seq_uf integer,
 nr_seq_municipio integer,
 ds_logradouro varchar(255),
 nr_endereco integer,
 ds_bairro varchar2(255),
 nr_cpf number(8)
 );
````

# *Inserção de registro*

````
 insert into pessoa_fisica (
 nr_sequencia,
 nm_pessoa_fisica,
 qt_altura
 ) 
 values (
 1, 
 'Erick',
 1.72
 )
````

# *Adicionar coluna*

````
 alter table pessoa_fisica add (teste number(10));
````

# *Modificar coluna*
````
alter table pessoa_fisica modify (teste number(5,3));
````
## Testando se mudou
````
desc pessoa_fisica
````
# *Renomear coluna*
````
alter table pessoa_fisica rename column teste to nome_nova_coluna
````
## Testando se mudou
````
desc pessoa_fisica
````
# *Renomear coluna novamente*
````
alter table pessoa_fisica rename column nome_nova_coluna to teste
````
## Testando se mudou
````
select *
from pessoa_fisica
````

# *UPDATE*
````
update pessoa_fisica set teste_novo = 10.5;
````
## Testando se mudou
````
select *
from pessoa_fisica
````

# *Renomear a tabela*
````
alter table pessoa_fisica rename to pessoa_fisica_novo;
````

# *Dropar Coluna*
````
alter table pessoa_fisica drop column teste
````

# **Constraints**
### *(PK, FK, UNIQUE, CHECK)*
CONSTRAINTS TRAZEM LIMITAÇÕES NO BANCO DE DADOS 

# **PRIMARY KEY**
Impõe exclusividade de linhas e também não permite valores do tipo NULLs nos atributos de constraint. Cada valor nos atributos de uma constraint do tipo Primary Key pode aparecer somente uma vez na tabela, somente em uma linha e cada tabela só pode possuir uma primary key
## **SUPONDO QUE UMA TABELA FOI CRIADA E ESTAMOS A ALTERAR PARA ADD AS CONSTRAINTS**
## *Vamos alterar nr_sequencia da tabela uf, para nr_seq_uf_pk e adicionar como constraint*
````
alter table uf add constraint nr_seq_uf_pk primare key (nr_sequencia);
````

# **UNIQUE**
impede que valores duplicados sejam inseridos na coluna. É implementada criando-se um índice unívoco em uma coluna. Como mostrado na Listagem 3, o UNIQUE impede valores duplicados na coluna.
## *Vamos alterar a tabela cd_uf_ibge para sg_uf_un e Add constraint do tipo unique*
````
 alter table uf add constraint sg_uf_un unique (sg_uf);
````
# **DROPAR UMA CONSTRAINT**
````
alter table nameTabe drop constraint nameConstraint
````
# **MODIFY - CAMPOS NÃO NULOS**

## *DEFININDO OS CAMPOS NÃO NULOS OU NOT NULL da tabela uf as colunas sg_uf, cd_uf_ibge*
````
alter table uf modify(sg_uf not null, cd_uf_ibge not null);
````
## *VAMOS DROPAR A TABELA E CONSTRUÍ-LA DO JEITO CERTO*
````
drop table uf;
````
# **CONSTRUINDO  TABELA UF DO JEITO CORRETO**
````
 create table uf(
 nr_sequencia integer constraint nr_seq_uf_pk primary key,
 dt_criacao date,
 dt_alteracao date,
 cd_uf_ibge number(2)not null constraint cd_uf_ibge_un unique,
 sg_uf varchar2(2)not null constraint sg_uf_un unique,
 ds_uf varchar2(255) 
 );
````

# **CONSTRUINDO  TABELA  DO JEITO CORRETO**
## *DROPAR A TABELA PSSOA_FISICA*
````
drop table pessoa_fisica
````
## *Criando a tabela pessoa_fisica do jeito correto restritivo* 
````
 create table pessoa_fisica(
 nr_sequencia integer constraint nr_seq_pf_pk primary key, 
 dt_criacao date, 
 dt_alteracao date, 
 nm_pessoa_fisica varchar2(255), 
 dt_nascimento date, 
 nr_cpf varchar2(11) constraint pessoa_fisica_cpf_un unique, 
 qt_altura number(3,2)
 );
````
# **ALTERANDO A TABELA pessoa_fisica_endereco DO JEITO CORRETO ADD CONSTRAINTS**
### *EM CASO DE JÁ POSSUIR DADOS A TABELA DEVERÁ SER ALTERADA E NÃO DROPADA PARA EVITAR A PERDA DE DADOS.*
````
alter table pessoa_fisica_endereco add constraint nr_seq_end_pf_pk primary key(nr_sequencial);
````
# **CONSTRAINTS CHAVES ESTRANGEIRAS FK.**
````
alter table pessoa_fisica_endereco add constraint nr_seq_pf_end_fk foreign key (nr_seq_pessoa_fisica) references pessoa_fisica(nr_sequencia);
````
#
````
alter table pessoa_fisica_endereco add constraint nr_seq_uf_end_fk foreign key (nr_seq_uf) references uf(nr_sequencia);
````
#
````
alter table pessoa_fisica_endereco add constraint nr_seq_municipio_end_fk foreign key (nr_seq_municipio) references municipio(nr_sequencia);
````
# *COMO NA TABELA PESSOA_FISICA_ENDERECO SEMPRE IRÁ PRECISAR DE UMA PESSOA ELE DEVE SER NOT NULL*
## **DEVEMOS ALTERAR PARA NOT NULL COM O COMANDO MODIFY**
````
alter table pessoa_fidica_endereco modify (nr_seq_pessoa_fisica not null)
````
# **CONSTRAINT CHECK**
### *A CONSTRAINT CHECK SERVE PARA RESTRINGIR OS TIPOS DE DADOS A SEREM INSERIDOS NA TABELA*

## *CRIANDO TABELA TESTE E ALTERANDO PARA COSNTRAINT CHECK*
````
create table teste (a1 varchar2(2), b1 number, b2 number)
````
## *ALTERANDO A TABELA A1 PARA CONSTRAINT CHECK*
````
alter table add constraint a1_ck check(a1 in('nameEmpresa','silgalEmpresa','cnpjEmpresa'))
````
## *A PARTIR DESSE COMANDO ACIMA VOCÊ SÓ CONSEGUIRÁ INSERIR O DADO EXCLUSIVO ESCOLHIDO, O EXEMPLO ACIMA MOSTRA COMO PARÂMETRO O nome da empresa, ou sigla da empresa, ou cnpj da empresa, ISSO PARA CRIAR UMA IDENTIDADE NA TABELA.*

## *ALTERANDO A TABELA B1 PARA CONSTRAINT APENAS RECEBER NUMEROS MAIORES OU IGUAIS A 1*
````
alter table add constraint b1_ck check(b1 >= 1)
````
#### **TENTE INSERIR APÓS ALTERAR A CONSTRANTE ACIMA**
````
insert into teste (a1) values (0);
````
## *APARECERÁ UM ERRO INFORMANDO QUE EXISTE RESTRIÇÃO DE VERIFICAÇÃO VIOLADA PELO USUÁRIO*

# *CONSTRAINT CHECK criando, alterando e testando a restrição.*
````
create table teste(a1 varchar2(2), b1 number)
alter table teste add constraint a1_ck check(a1 in('ER','er','Er'));
alter table teste add constraint b1_ck check(b1 between 10 and 18)
insert into teste (a1) values('sjah')
insert into teste (b1) values ('20')
````
# *DESAFIO DA CONSTRAINT CHECK*

## **------DESAFIO------**
 **ADICIONAR UMA COLUNA CHAMADA SEXO DO TIPO VARCHAR2(1) NA TABELA PESSOA_FISICA E CRIAR 
 UMA CONSTRAINT SEXO_CK PARA RECEBER APENAS AS LETRAS ('F','f','M','m','I','i')**

#### *DESAFIO RESOLVIDO: [RESPOSTA](https://commie.io/#QC4f0ABO)*

# *CREATE SEQUENCE + INSERT INTO + SQLPLUS*

## **SEQUENCE**
### Sequences são objetos que geram números sequenciais dentro do Oracle. São excelentes em termos de performance já que armazenam um range de números no cache e também porque tiram do desenvolvedor a responsabilidade de gerenciar a geração de Ids em casos de multiplos acessos.

*start with* = INICIANDO A SEQUENCE COM UM DETERMINADO NÚMERO.

 *increment* by = PODE SER NEGATIVO OU POSITIVO A DEPENDER DA ORDEM DE SEQUÊNCIA PARA INCREMENTAR COMO DESEJAR.

 *maxvalue* = MÁXIMO VALOR DA SEQUENCE
 
 *minvalue* = MENOR VALOR DA SEQUENCE
 
 *nocache* = INDICA QUE A SEQUENCE NÃO TERÁ CACHE DE QUANTIDADE DE REGISTROS QUE O ORACLE VAI ARMAZENAR EM MEMÓRIA PARA AUMENTO DE PERFORMANCE. SE NÃO USAR A FLAG "NOCACHE" O PADRÃO VAI SER CACHE 20
 
 *cycle* =  APÓS COMPLETAR A SEQUÊNCIA DEFINIDA PELO MAXVALUE ELE RETORNA PARA O VALOR DE START DA SEQEUNCE.
 
## *CRIANDO SEQUENCE*
````
create sequence pessoa_fisica_seq
 start with 1
 increment by 1
 maxvalue 9999999
 minvalue 1
 nocache
````

````
create sequence uf_seq
 start with 1
 increment by 1
 maxvalue 9999999
 minvalue 1
 nocache;
````

## **INSERT**
INSERÇÃO DE ELEMENTOS NA TABELA

## **INSERÇÃO DE ELEMENTOS EM TODAS AS COLUNAS**
````
insert into uf values();
````

## FORÇANDO O AUTO INCREMENTO DE VALOR DA COLUNA uf_seq.
````
select uf_seq.nextval
from dual
````
## **INSERÇÃO DE ELEMENTOS EM COLUNAS ESPECÍFICAS**
````
insert into uf(
nr_sequencia,
dt_criacao,
cd_uf_ibge,
sg_uf,
ds_uf)
values(
uf_seq.nextval, 
sysdate,
12, 
'SC', 
'Santa Catarina');
````
## **COMMIT**
*DEVEMOS INSERIR O COMMIT OU CASO CONTRÁRIO A INSERÇÃO CRIADA ACIMA ESTARÁ SÓ EM MEMÓRIA NO BANCO E NÃO SERÁ GRVADA*
````
commit
````
OU
## **ROLLBACK**
ESTE COMANDO SERVE PARA DESFAZER AS ALTERAÇÕES.
````
rollback
````

## **OUTRA FORMA DE INSERT: colocar todas as colunas**
````
declare
cd_uf_w number(2);  
begin
insert into uf values(
nr_sequencia,
dt_criacao,
cd_uf_ibge,
sg_uf,
ds_uf
sysdate,
sysdate,
16,
'PR',
'PARANÁ')return nr_sequencia into cd_uf_w;
end;
````

## **INSERIR A PARTIR DE UM SELECT**
````
insert into uf(
nr_sequence,
dt_criacao,
cd_uf_ibge,
sg_uf,
ds_uf) select uf_seq.nextval, sysdate, 15, 'AP', 'AMAPÁ' from dual
````
# ***DELETA A TABELA UF E COMMITA*
````
delete uf
````
````
commit
````

## **inserção de dados**
````
insert into uf(nr_sequencia, dt_criacao, cd_uf_ibge, sg_uf, ds_uf)values(uf_seq.nextval, sysdate, 12,    'AC', 'Acre');
insert into uf(nr_sequencia, dt_criacao, cd_uf_ibge, sg_uf, ds_uf)values(uf_seq.nextval, sysdate, 27,    'AL', 'Alagoas');
insert into uf(nr_sequencia, dt_criacao, cd_uf_ibge, sg_uf, ds_uf)values(uf_seq.nextval, sysdate, 16,    'AP', 'Amapá');
insert into uf(nr_sequencia, dt_criacao, cd_uf_ibge, sg_uf, ds_uf)values(uf_seq.nextval, sysdate, 13,    'AM', 'Amazonas');
insert into uf(nr_sequencia, dt_criacao, cd_uf_ibge, sg_uf, ds_uf)values(uf_seq.nextval, sysdate, 29,    'BA', 'Bahia');
insert into uf(nr_sequencia, dt_criacao, cd_uf_ibge, sg_uf, ds_uf)values(uf_seq.nextval, sysdate, 23,    'CE', 'Ceará');
insert into uf(nr_sequencia, dt_criacao, cd_uf_ibge, sg_uf, ds_uf)values(uf_seq.nextval, sysdate, 53,    'DF', 'Distrito Federal');
insert into uf(nr_sequencia, dt_criacao, cd_uf_ibge, sg_uf, ds_uf)values(uf_seq.nextval, sysdate, 32,    'ES', 'Espírito Santo');
insert into uf(nr_sequencia, dt_criacao, cd_uf_ibge, sg_uf, ds_uf)values(uf_seq.nextval, sysdate, 52,    'GO', 'Goiás');
insert into uf(nr_sequencia, dt_criacao, cd_uf_ibge, sg_uf, ds_uf)values(uf_seq.nextval, sysdate, 21,    'MA', 'Maranhão');
insert into uf(nr_sequencia, dt_criacao, cd_uf_ibge, sg_uf, ds_uf)values(uf_seq.nextval, sysdate, 51,    'MT', 'Mato Grosso');
insert into uf(nr_sequencia, dt_criacao, cd_uf_ibge, sg_uf, ds_uf)values(uf_seq.nextval, sysdate, 50,    'MS', 'Mato Grosso do Sul');
insert into uf(nr_sequencia, dt_criacao, cd_uf_ibge, sg_uf, ds_uf)values(uf_seq.nextval, sysdate, 31,    'MG', 'Minas Gerais');
insert into uf(nr_sequencia, dt_criacao, cd_uf_ibge, sg_uf, ds_uf)values(uf_seq.nextval, sysdate, 15,    'PA', 'Pará');
insert into uf(nr_sequencia, dt_criacao, cd_uf_ibge, sg_uf, ds_uf)values(uf_seq.nextval, sysdate, 25,    'PB', 'Paraíba');
insert into uf(nr_sequencia, dt_criacao, cd_uf_ibge, sg_uf, ds_uf)values(uf_seq.nextval, sysdate, 41,    'PR', 'Paraná');
insert into uf(nr_sequencia, dt_criacao, cd_uf_ibge, sg_uf, ds_uf)values(uf_seq.nextval, sysdate, 26,    'PE', 'Pernambuco');
insert into uf(nr_sequencia, dt_criacao, cd_uf_ibge, sg_uf, ds_uf)values(uf_seq.nextval, sysdate, 22,    'PI', 'Piauí');
insert into uf(nr_sequencia, dt_criacao, cd_uf_ibge, sg_uf, ds_uf)values(uf_seq.nextval, sysdate, 33,    'RJ', 'Rio de Janeiro');
insert into uf(nr_sequencia, dt_criacao, cd_uf_ibge, sg_uf, ds_uf)values(uf_seq.nextval, sysdate, 24,    'RN', 'Rio Grande do Norte');
insert into uf(nr_sequencia, dt_criacao, cd_uf_ibge, sg_uf, ds_uf)values(uf_seq.nextval, sysdate, 43,    'RS', 'Rio Grande do Sul');
insert into uf(nr_sequencia, dt_criacao, cd_uf_ibge, sg_uf, ds_uf)values(uf_seq.nextval, sysdate, 11,    'RO', 'Rondônia');
insert into uf(nr_sequencia, dt_criacao, cd_uf_ibge, sg_uf, ds_uf)values(uf_seq.nextval, sysdate, 14,    'RR', 'Roraima');
insert into uf(nr_sequencia, dt_criacao, cd_uf_ibge, sg_uf, ds_uf)values(uf_seq.nextval, sysdate, 42,    'SC', 'Santa Catarina');
insert into uf(nr_sequencia, dt_criacao, cd_uf_ibge, sg_uf, ds_uf)values(uf_seq.nextval, sysdate, 35,    'SP', 'São Paulo');
insert into uf(nr_sequencia, dt_criacao, cd_uf_ibge, sg_uf, ds_uf)values(uf_seq.nextval, sysdate, 28,    'SE', 'Sergipe');
insert into uf(nr_sequencia, dt_criacao, cd_uf_ibge, sg_uf, ds_uf)values(uf_seq.nextval, sysdate, 17,    'TO',  'Tocantins');
````
# ***DELETA A TABELA UF E COMMITA PARA INSERIR COM SQL PLUS*
````
delete uf
````
````
commit
````
# *SQL PLUS*
1. APERTE AS TECLAS 'WINDOWS + R'.
2. DIGITE ````sqlplus````
