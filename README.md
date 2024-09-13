# To Do List Backend

## Descrição

Este é o backend da aplicação To-Do List, desenvolvido em Laravel como parte do projeto de validação de conhecimento para o processo seletivo da empresa Newm Stefanini. Ele fornece uma API REST para gerenciar tarefas (novo registro e visualizar todos os registros e um registro específico.).

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

2. Inicie o Docker Compose:
    
   Não é necessário instalar o Laravel e o MySQL fora do Docker, pois o Docker se encarregará disso.
    
   Mova o projeto para um diretório que não esteja sendo sincronizado pelo OneDrive (se estiver usando o OneDrive), para evitar problemas com permissões e sincronização.

   Execute o comando para iniciar os containers:

    ```bash
    docker-compose up -d
    ```
    Isso irá iniciar os containers do backend e do banco de dados, configurando o ambiente para o Laravel e MySQL.

3. Instale as dependências do Laravel usando o Composer:

    ```bash
    docker-compose exec app composer install
    ```
    
4. Configure o arquivo `.env`:
    
    Copie o arquivo `.env.example` para `.env`:

    ```bash
    docker-compose exec app cp .env.example .env
    ```
    Abra o arquivo .env e ajuste as configurações do banco de dados:
   
   ```bash
    docker-compose exec app bash
    ```

   Ajuste as configurações do banco de dados::

    ```env
    DB_CONNECTION=mysql
    DB_HOST=db
    DB_PORT=3306
    DB_DATABASE=to_do_list
    DB_USERNAME=root
    DB_PASSWORD=root

    ```

5. Gere a Chave da Aplicação:

    ```bash
    docker-compose exec app php artisan key:generate
    ```

5. Execute as migrações do banco de dados:

    ```bash
    docker-compose exec app php artisan migrate
    ```
A API está disponível em `http://localhost:8000`.`

Endpoints da API REST (Utilizei o Postman para realização dos testes).

Método | Endpoint | Descrição | Parâmetros
--- | --- | --- | ---
POST | /api/tasks | Cria uma nova tarefa | title, description, status
GET | /api/tasks | Retorna todas as tarefas | -
GET | /api/tasks/{id} | Retorna uma tarefa específica | {id}

Abaixo estão os detalhes dos endpoints disponíveis:

### 1. Criar uma Nova Tarefa

- **URL:** `/api/tasks`
- **Método:** `POST`
- **Descrição:** Cria uma nova tarefa.
- **Corpo da Requisição JSON:**
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

### 6. Buscar uma Tarefa Específica

- **URL:** `/api/tasks/{id}`
- **Método:** `GET`
- **Descrição:** Retorna uma tarefa específica.
- **Resposta de Sucesso:**
    ```json
    {
      "id": 1,
        "title": "Nova Tarefa",
        "description": "Descrição da nova tarefa",
        "status": "Em Andamento"
    }

## Observações:

O banco de dados está configurado para rodar na porta 3307. Caso enfrente erros de conexão com o banco, verifique se o arquivo .env está corretamente configurado.
