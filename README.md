# Trabalho-Final-API-Restful-Serratec-2022.1
Repositório criado para subir o trabalho final feito na disciplina de API Restful.

## Descrição

Modelo de uma API e-commerce do grupo 3 proposta pela matéria de Desenvolvimento de API Restful do Serratec.

<hr>

### Professor: Alexandre Paixão

<hr>

## Script do banco de dados

```bash
CREATE TABLE endereco (
id_endereco SERIAL PRIMARY KEY, 
cep varchar(9) NOT NULL, 
rua varchar(100) NOT NULL,
bairro varchar(50) NOT NULL,
cidade varchar(30),
numero INTEGER NOT NULL,
complemento varchar(20),
uf varchar(2))
;

CREATE TABLE cliente (
id_cliente SERIAL PRIMARY KEY,
email varchar(100) NOT NULL,
nome_completo varchar(100) NOT NULL,
cpf varchar(14) NOT NULL,
telefone varchar(11),
data_nascimento DATE, 
id_endereco INTEGER, 
FOREIGN KEY(id_endereco) REFERENCES endereco(id_endereco)
);

CREATE TABLE pedido (
id_pedido SERIAL PRIMARY KEY,
data_pedido DATE NOT NULL,
data_entrega DATE, 
data_envio DATE,
status boolean,
id_cliente INTEGER, 
FOREIGN KEY(id_cliente) REFERENCES cliente(id_cliente)
);

CREATE TABLE categoria (
id_categoria SERIAL PRIMARY KEY, 
nome varchar(30) NOT NULL, 
descricao varchar(150)
);

CREATE TABLE produto (
id_produto SERIAL PRIMARY KEY,
nome varchar(30) NOT NULL,
descricao varchar(100),
qtd_estoque INTEGER NOT NULL,
data_cadastro DATE,
valor_unitario FLOAT NOT NULL, 
imagem varchar(100),
id_categoria INTEGER, 
FOREIGN KEY(id_categoria) REFERENCES categoria(id_categoria)
);


CREATE TABLE item_pedido (
id_item_pedido SERIAL PRIMARY KEY,
quantidade INTEGER NOT NULL,
preco_venda NUMERIC(10,2) NOT NULL,
percentual_desconto NUMERIC(10,2),
valor_bruto NUMERIC(10,2),
valor_liquido NUMERIC(10,2),
id_pedido INTEGER, 
FOREIGN KEY (id_pedido) REFERENCES pedido(id_pedido),
id_produto INTEGER,  
FOREIGN KEY (id_produto) REFERENCES produto(id_produto)
);
```
## Configurando a API para execução

As credenciais para acesso ao banco de dados, nome do contexto da API, o caminho da pasta de imagem e as do gmail deverão ser alterados no arquivo application.properties

## Sobre

- Author - [Aysha Alessandra]
- Author - [Fernanda Machado]
- Author - [Talles Dias]
- Author - [Pedro Louzada]
- Author - [Bernardo Gutman]