# Baozi Store API

API REST desenvolvida como atividade prática da disciplina de Desenvolvimento Web Back-End.

O projeto simula uma pequena loja de pães chineses (Baozi), permitindo o cadastro e gerenciamento de clientes, produtos e pedidos.

## Tecnologias utilizadas

- Java 17
- Spring Boot 4.1.1
- Spring MVC
- Spring Data JPA
- MySQL
- Maven
- Postman
- Git/GitHub

## Funcionalidades

A API permite realizar operações sobre três entidades principais:

- Clientes
- Produtos
- Pedidos

Cada entidade possui endpoints para:

- Cadastrar
- Listar todos
- Consultar por ID
- Excluir por ID

## Estrutura do projeto

```text
src/main/java/br/com/baozistore/
├── controller/
│   ├── ClienteController.java
│   ├── ProdutoController.java
│   └── PedidoController.java
│
├── model/
│   ├── Cliente.java
│   ├── Produto.java
│   └── Pedido.java
│
└── repository/
    ├── ClienteRepository.java
    ├── ProdutoRepository.java
    └── PedidoRepository.java
```

## Entidades

### Cliente

| Campo | Tipo |
|---|---|
| id | Long |
| nome | String |
| clienteDesde | LocalDate |

### Produto

| Campo | Tipo |
|---|---|
| id | Long |
| nome | String |
| preco | BigDecimal |
| estoque | Boolean |

### Pedido

| Campo | Tipo |
|---|---|
| id | Long |
| clienteId | Long |
| produtoId | Long |
| quantidade | Integer |

## Endpoints

### Clientes

| Método | Endpoint | Descrição |
|---|---|---|
| POST | `/clientes` | Cadastrar cliente |
| GET | `/clientes` | Listar clientes |
| GET | `/clientes/{id}` | Consultar cliente por ID |
| DELETE | `/clientes/{id}` | Excluir cliente |

### Produtos

| Método | Endpoint | Descrição |
|---|---|---|
| POST | `/produtos` | Cadastrar produto |
| GET | `/produtos` | Listar produtos |
| GET | `/produtos/{id}` | Consultar produto por ID |
| DELETE | `/produtos/{id}` | Excluir produto |

### Pedidos

| Método | Endpoint | Descrição |
|---|---|---|
| POST | `/pedidos` | Cadastrar pedido |
| GET | `/pedidos` | Listar pedidos |
| GET | `/pedidos/{id}` | Consultar pedido por ID |
| DELETE | `/pedidos/{id}` | Excluir pedido |

## Exemplos de requisições

### Cadastrar cliente

`POST /clientes`

```json
{
    "nome": "Max Mitsuya(RU)",
    "clienteDesde": "2026-09-17"
}
```

### Cadastrar produto

`POST /produtos`

```json
{
    "nome": "Baozi Tradicional",
    "preco": 8.50,
    "estoque": true
}
```

### Cadastrar pedido

`POST /pedidos`

```json
{
    "clienteId": 2,
    "produtoId": 1,
    "quantidade": 3
}
```

## Banco de dados

O projeto utiliza o MySQL como banco de dados relacional.

Banco utilizado:

```text
baozi_store
```

As tabelas são criadas e atualizadas automaticamente pelo Hibernate/JPA a partir das entidades da aplicação.

## Configuração

Para executar o projeto localmente, é necessário possuir:

- JDK 17
- MySQL
- Git

Configure o banco de dados no arquivo:

```text
src/main/resources/application.properties
```

A senha do banco de dados deve ser fornecida por meio da variável de ambiente `DB_PASSWORD`.

Exemplo:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/baozi_store
spring.datasource.username=root
spring.datasource.password=${DB_PASSWORD}
```

> A senha do banco de dados não deve ser armazenada diretamente no código-fonte.

## Execução

Após configurar o banco de dados e a variável `DB_PASSWORD`, a aplicação pode ser executada pelo Eclipse ou utilizando o Maven Wrapper.

No Windows:

```bash
mvnw.cmd spring-boot:run
```

A API será disponibilizada em:

```text
http://localhost:8080
```

## Testes

Os endpoints foram testados utilizando o Postman, incluindo:

- POST de Cliente
- GET geral de Clientes
- GET de Cliente por ID
- DELETE de Cliente
- POST de Produto
- GET geral de Produtos
- GET de Produto por ID
- DELETE de Produto
- POST de Pedido
- GET geral de Pedidos
- GET de Pedido por ID
- DELETE de Pedido

## Autor

**Max Mitsuya**

Projeto desenvolvido para fins acadêmicos na disciplina de Desenvolvimento Web Back-End.
