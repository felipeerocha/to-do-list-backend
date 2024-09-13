# To Do List Backend

## Descrição

Este é o backend da aplicação To-Do List, desenvolvido em Laravel como parte do projeto de validação de conhecimento para o processo seletivo da empresa Newm Stefanini. Ele fornece uma API REST para gerenciar tarefas (criação, consulta, atualização e remoção).

## Requisitos

- PHP >= 8.0
- Composer
- MySQL
- Docker
- Git

## Instruções para Instalação

1. Clone o repositório

    ```bash
    git clone https://github.com/felipeerocha/to-do-list-backend.git
    cd to-do-list-backend
    ```
2. Instale as dependências do Laravel usando o Composer:

    ```bash
    composer install
    ```
    
3. Configure o arquivo `.env`:
    
    Copie o arquivo `.env.example` para `.env`:

    ```bash
    cp .env.example .env
    ```
    Abra o arquivo `.env` e ajuste as configurações do banco de dados conforme necessário:

    ```env
    DB_CONNECTION=mysql
    DB_HOST=127.0.0.1
    DB_PORT=3307
    DB_DATABASE=nome_do_banco
    DB_USERNAME=usuario
    DB_PASSWORD=senha
    ```

4. Gere a Chave da Aplicação:

    ```bash
    docker-compose run --rm php php artisan key:generate
    ```

5. Execute as migrações do banco de dados:

    ```bash
    docker-compose run --rm php php artisan migrate
    ```

## Como Executar

1. Inicie o Docker Compose:

    ```bash
    docker-compose up -d
    ```

    Isso irá iniciar os containers do backend e do banco de dados.

A API está disponível em `http://localhost:8000/api/tasks`.`

Endpoints da API REST

Método | Endpoint | Descrição | Parâmetros
--- | --- | --- | ---
GET | /api/tasks | Retorna todas as tarefas | -
POST | /api/tasks | Cria uma nova tarefa | title, description, status
GET | /api/tasks/{id} | Retorna uma tarefa específica | {id}
PUT | /api/tasks/{id} | Atualiza uma tarefa específica | {id}, title, description, status
DELETE | /api/tasks/{id} | Remove uma tarefa específica | {id}

Abaixo estão os detalhes dos endpoints disponíveis:

### 1. Criar uma Nova Tarefa

- **URL:** `/api/tasks`
- **Método:** `POST`
- **Descrição:** Cria uma nova tarefa.
- **Corpo da Requisição:**
    ```json
    {
      "title": "Nova Tarefa",
      "description": "Descrição da nova tarefa",
      "status": "Em Andamento"
    }
    ```
- **Resposta de Sucesso:**
    ```json
    {
      "id": 1,
      "title": "Nova Tarefa",
      "description": "Descrição da nova tarefa",
      "status": "Em Andamento"
    }
    ```

### 2. Listar Todas as Tarefas

- **URL:** `/api/tasks`
- **Método:** `GET`
- **Descrição:** Retorna uma lista de todas as tarefas.
- **Resposta de Sucesso:**
    ```json
    [
      {
        "id": 1,
        "title": "Nova Tarefa",
        "description": "Descrição da nova tarefa",
        "status": "Em Andamento"
      },
    ]
    ```

### 3. Atualizar uma Tarefa

- **URL:** `/api/tasks/{id}`
- **Método:** `PUT`
- **Descrição:** Atualiza uma tarefa existente.
- **Corpo da Requisição:**
    ```json
    {
      "title": "Tarefa Atualizada",
      "description": "Descrição atualizada",
      "status": "Concluída"
    }
    ```
- **Resposta de Sucesso:**
    ```json
    {
      "id": 1,
      "title": "Tarefa Atualizada",
      "description": "Descrição atualizada",
      "status": "Concluída"
    }

    ```
### 6. Buscar uma Tarefa Específica

- **URL:** `/api/tasks/{id}`
- **Método:** `GET`
- **Descrição:** Retorna uma tarefa específica.
- **Resposta de Sucesso:**
    ```json
    {
      "id": 1,
      "title": "Tarefa Atualizada",
      "description": "Descrição atualizada",
      "status": "Concluída"
    }

### 5. Excluir uma Tarefa

- **URL:** `/api/tasks/{id}`
- **Método:** `DELETE`
- **Descrição:** Remove uma tarefa existente.
- **Resposta de Sucesso:**
    ```json
    {
      "message": "Tarefa excluída com sucesso."
    }
    ```

## Observações:

O banco de dados está configurado para rodar na porta 3307. Caso enfrente erros de conexão com o banco, verifique se o arquivo .env está corretamente configurado.
