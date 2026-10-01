# Todo PostgreSQL

Banco de dados de uma lista de tarefas desenvolvido utilizando PostgreSQL e Docker.

O projeto tem como objetivo praticar SQL, modelagem de banco de dados e utilização do PostgreSQL através de containers Docker.

## Tecnologias

- PostgreSQL 16
- Docker
- Docker Compose
- SQL

## Pré-requisitos

Antes de executar o projeto, você precisa ter instalado:

- [Docker](https://www.docker.com/)
- Docker Compose

Verifique se o Docker está instalado:

```bash
docker --version
```

Verifique o Docker Compose:

```bash
docker compose version
```

## Instalação

Clone o repositório:

```bash
git clone https://github.com/SEU-USUARIO/todo-postgres.git
```

Entre na pasta do projeto:

```bash
cd todo-postgres
```

## Executando o projeto

Inicie o PostgreSQL com:

```bash
docker compose up -d
```

Na primeira execução, o Docker irá:

1. Criar o container do PostgreSQL.
2. Criar o banco de dados `todo`.
3. Criar a tabela `tarefas`.
4. Inserir os dados iniciais definidos no `seed.sql`.

Para verificar se o container está funcionando:

```bash
docker ps
```

## Configuração do banco

| Configuração | Valor |
|---|---|
| Banco de dados | `todo` |
| Usuário | `postgres` |
| Senha | `postgres` |
| Host | `localhost` |
| Porta | `5432` |

## Estrutura do projeto

```text
todo-postgres/
│
├── docker-compose.yml
├── README.md
│
└── init/
    ├── 01-schema.sql
    └── 02-seed.sql
```

### `docker-compose.yml`

Responsável pela configuração e execução do PostgreSQL através do Docker.

### `01-schema.sql`

Contém a estrutura do banco de dados, como tabelas, colunas e restrições.

### `02-seed.sql`

Insere dados iniciais para facilitar os testes do banco.

## Estrutura do banco

Atualmente, o banco possui a tabela:

### `tarefas`

| Campo | Tipo | Descrição |
|---|---|---|
| `id` | SERIAL | Identificador único |
| `titulo` | VARCHAR(200) | Título da tarefa |
| `descricao` | TEXT | Descrição da tarefa |
| `concluida` | BOOLEAN | Status da tarefa |
| `criada_em` | TIMESTAMP | Data de criação |

## Consultando os dados

Depois que o banco estiver funcionando, você pode executar:

```sql
SELECT * FROM tarefas;
```

Para mostrar apenas tarefas pendentes:

```sql
SELECT *
FROM tarefas
WHERE concluida = FALSE;
```

Para mostrar apenas tarefas concluídas:

```sql
SELECT *
FROM tarefas
WHERE concluida = TRUE;
```

## Parando o projeto

Para parar o container:

```bash
docker compose down
```

Os dados continuarão armazenados no volume do PostgreSQL.

## Resetando o banco

Para remover o container e também o volume com os dados:

```bash
docker compose down -v
```

Depois, execute novamente:

```bash
docker compose up -d
```

O PostgreSQL será criado novamente e os arquivos da pasta `init` serão executados.

> **Atenção:** `docker compose down -v` apaga os dados armazenados no volume.

## Objetivo

Este projeto foi criado para praticar:

- PostgreSQL
- SQL
- Modelagem de banco de dados
- Docker
- Docker Compose
- Criação e manipulação de tabelas
- Consultas SQL

## Autor

Gabriel Alves