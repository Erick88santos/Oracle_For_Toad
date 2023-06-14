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
