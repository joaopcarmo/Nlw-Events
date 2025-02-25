# Sistema de Eventos - NLW Events

Este é um sistema de gerenciamento de eventos desenvolvido com Spring Boot, que permite a criação, consulta e gerenciamento de eventos, além de um sistema de inscrições com indicações e ranking.

## Visão Geral

O sistema consiste em uma aplicação Java Spring Boot que gerencia eventos e inscrições de usuários. Ele oferece uma API REST para interagir com os recursos do sistema.

### Principais funcionalidades:

- Cadastro e consulta de eventos
- Inscrição de usuários em eventos
- Sistema de indicação, onde um usuário pode indicar outro
- Geração de ranking de indicações
- Consulta da posição de um usuário específico no ranking

## Estrutura do Projeto

### Pacotes principais:

- **controller**: Controladores REST que expõem a API
- **model**: Entidades de domínio mapeadas para o banco de dados
- **service**: Camada de serviço que implementa as regras de negócio
- **repository**: Interfaces para acesso ao banco de dados
- **dto**: Objetos de transferência de dados
- **exception**: Exceções personalizadas

### Entidades principais:

- **Event**: Representa um evento com título, local, preço e datas
- **User**: Representa um usuário com nome e email
- **Subscription**: Representa a inscrição de um usuário em um evento, podendo incluir informação de quem o indicou

## Endpoints da API

### Eventos

- `POST /events` - Cadastra um novo evento
- `GET /events` - Lista todos os eventos
- `GET /events/{prettyName}` - Busca um evento específico pelo seu nome formatado

### Inscrições

- `POST /subscription/{prettyName}` - Inscreve um usuário em um evento
- `POST /subscription/{prettyName}/{userId}` - Inscreve um usuário em um evento com indicação
- `GET /subscription/{prettyName}/ranking` - Retorna o top 3 do ranking de indicações para um evento
- `GET /subscription/{prettyName}/ranking/{userId}` - Retorna a posição de um usuário específico no ranking

## Configurações

O sistema inclui configuração de CORS para permitir acesso de aplicações frontend, com suporte para os métodos GET, POST, PUT e DELETE.

## Tratamento de Exceções

O sistema trata as seguintes situações de erro:

- Evento não encontrado
- Conflito de inscrição (usuário já inscrito em um evento)
- Usuário indicador não encontrado

## Modelagem de Dados

O sistema utiliza um banco de dados relacional com as seguintes tabelas:

- `tbl_event`: Armazena informações dos eventos
- `tbl_user`: Armazena informações dos usuários
- `tbl_subscription`: Armazena as inscrições e suas relações

## Como executar

1. Clone o repositório
2. Configure seu banco de dados nas propriedades da aplicação
3. Execute o projeto usando Maven: `mvn spring-boot:run`
4. A API estará disponível em: `http://localhost:8080`

## Tecnologias utilizadas

- Java
- Spring Boot
- Spring Data JPA
- Spring Web
- Banco de dados relacional (configurável)
