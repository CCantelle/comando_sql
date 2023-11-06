## Comandos de banco de dados

### Criar database
* Local para criar as tabelas do sistema
```
create database NOME_DATABASE;
```
### Executar o comando
```
Ctrl + Enter
```
### Selecionar database
```
use NOME_DATABASE;
```
<hr>

## Projeto site Ecommerce
* Tabela de usuarios
* Tabela de produtos
* tabela de carrinho de compras

### Criar tabela de usuários
```
create table usuários(
  id int not null auto_autoincrement
  nome varchar(120) not null,
  email varchar(120) not null,
  senha varchar(120) not null
  primary key(id)
);
```
* id: indetificador de cada registro
* not null: campo obrigatorio, pode ser nulo
* auto_autoincrement: soma +1 no último registro de id
* varchar(120): campo de texto com 120 caracteres

### Cria tabela de produtos
```
create table produtos(
    id int not null auto_increment,
    modelo varchar(120),
    nome varchar(120) not null,
    valor float not null,
    primary key(id)
);
```
### Criar tabela de carrinho
```
create table carrinho(
    id int not null auto_increment,
    id_usuario int not null,
    id_produto int not null,
    primary key(id),
    foreign key(id_usuario) references usuarios(id)
    foreign key(id_produto) references produtos(id)
)
```
* foreign key: chave estrangeiro que recebe a referencia de outra tabela
* references: atributo para a definir a tabela e o campo estrangeiro

### Inserir usuarios
```
insert into usuarios(nome, email, senha) values('Renato Gaucho','teste@teste.com','secret')
```

### Inserir produto
```
insert into produtos(modelo, nome, vaor) values('nike','camiseta', 129.90)
```

### Inserir carrinho
```
insert into carrinho(id_usuario, id_produto) values(43, 234);
insert into carrinho(id_usuario, id_produto) values(43, 120);
insert into carrinho(id_usuario, id_produto) values(43, 6);
insert into carrinho(id_usuario, id_produto) values(43, 234);
insert into carrinho(id_usuario, id_produto) values(43, 234);
insert into carrinho(id_usuario, id_produto) values(43, 234);
```

### Listar todos usuarios
```
select * from usuarios;
```

### Listar os nomes dos usuarios
```
select nome from usuarios;
```

### Listar os nomes e email dos usuarios
```
select nome, email form usuarios;
```

### Listar usuarios pelo id
```
select * from usuarios where id = 23;
```

### Verificar produtos no carrinho pelo id do usuario
```
select p.nome
from produtos p, carrinho c 
where c.id_usuario = 23 AND p.id = c.id_produtos;
```