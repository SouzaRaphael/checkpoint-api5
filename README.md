# 🚗 API de Gerenciamento de Carros e Marcas

Esta é uma API RESTful desenvolvida com **Spring Boot** para gerenciar o cadastro de veículos e suas respectivas fabricantes. A aplicação utiliza **JPA/Hibernate** para persistência de dados em um banco **SQL server**.

---

## 🛠️ Tecnologias e Dependências

* **Java 17+**
* **Spring Boot 3**
* **Spring Data JPA**: Para abstração da camada de dados.
* **SQL server Driver**: Conector para o banco de dados.
* **Lombok**: Para geração automática de getters, setters e outros métodos boilerplate.
* **SpringDoc OpenApi**: Para documentação via Swagger.

---

## ⚙️ Configuração do Ambiente

A aplicação está configurada para rodar na porta **8080**.

### Banco de Dados
Certifique-se de ter um servidor SQL server rodando com as seguintes credenciais:
* **URL**: `jdbc:sqlserver://localhost:1433;databaseName=api;encrypt=false;trustServerCertificate=true`
* **Usuário**: `sa`
* **Senha**: `1q2w3e4R@`

## Garanta que a base de dados "api" esteja criada

---

## 🛣️ Endpoints da API

### 🏎️ Carros (`/carros`)
Entidade que armazena informações técnicas e comerciais dos veículos.

* **GET `/carros`**: Retorna a lista de todos os carros.
* **GET `/carros/{id}`**: Busca um carro específico pelo ID.
* **POST `/carros`**: Registra um novo veículo.
* **PUT `/carros/{id}`**: Atualiza os dados de um veículo (Nome, Preço, Tipo de Motor, Portas).
* **DELETE `/carros/{id}`**: Remove um veículo do sistema.

### 🏭 Marcas (`/marcas`)
Gerenciamento das fabricantes e controle de estoque de peças.

* **GET `/marcas`**: Retorna todas as marcas cadastradas.
* **GET `/marcas/{id}`**: Busca uma marca específica pelo ID.
* **POST `/marcas`**: Cadastra uma nova marca.
* **PUT `/marcas/{id}`**: Atualiza dados (Nome, Data de Criação, Qtd de Carros, Peças em Estoque).
* **DELETE `/marcas/{id}`**: Remove uma marca do sistema.

---

## 📖 Documentação (Swagger UI)

A documentação interativa da API (Swagger) está configurada para ser acessada diretamente na raiz do servidor:

> **URL:** [http://localhost:8080/](http://localhost:8080/)

---

## ⚙️ Profiles do Spring Boot

O profile ativo da aplicação é definido através da variável de ambiente:

```text
SPRING_PROFILES_ACTIVE
```

### Desenvolvimento

Para executar utilizando o profile `dev`:

```sh
export SPRING_PROFILES_ACTIVE=dev
```

### Produção

Para executar utilizando o profile `prd`:

```sh
export SPRING_PROFILES_ACTIVE=prd
```

Ao executar com Docker:

```sh
docker run \
  -p 8080:8080 \
  -e SPRING_PROFILES_ACTIVE=prd \
  study-api:1.1
```

---

## 🔐 Variáveis de ambiente

As configurações de conexão com o banco de dados devem ser fornecidas através de variáveis de ambiente.

Variáveis utilizadas pela aplicação:

```text
DB_SERVER_URL
DB_SERVER_PORT
DB_SCHEMA
DB_USER
DB_PWD
SPRING_PROFILES_ACTIVE
```


## 🧪 Como Executar
1. Configure seu SQL server de acordo com o arquivo `application.properties`.
2. Inicialize o docker do SQL server com o seguinte comando.

```sql
docker run -d \
    --name sqlserver \
    --rm \
    -e MSSQL_SA_PASSWORD=1q2w3e4R@ \
    -e "ACCEPT_EULA=Y" \
    -p 1433:1433 \
    mcr.microsoft.com/mssql/server:latest 
```