# FastAPI + SQLModel + PostgreSQL Backend

Este é um projeto backend usando FastAPI com SQLModel (ORM moderno) e PostgreSQL.

## Estrutura do Projeto

```
fastapi_sqlmodel_backend/
├── app/
│   ├── __init__.py
│   ├── main.py
│   ├── config.py
│   ├── database.py
│   ├── models/
│   │   ├── __init__.py
│   │   └── user.py
│   ├── api/
│   │   ├── __init__.py
│   │   ├── deps.py
│   │   └── routes/
│   │       ├── __init__.py
│   │       └── users.py
│   └── core/
│       ├── __init__.py
│       └── security.py
├── requirements.txt
├── docker-compose.yml
├── Dockerfile
├── .env
├── .gitignore
└── README.md
```

## Como Executar

### Opção 1: Com Docker Compose (Recomendado)

1. Clone o repositório
2. Configure as variáveis no arquivo `.env` se necessário
3. Execute:
```bash
docker-compose up --build
```

### Opção 2: Desenvolvimento Local

1. Crie um ambiente virtual:
```bash
python -m venv venv
source venv/bin/activate  # Linux/Mac
# ou
venv\Scripts\activate  # Windows
```

2. Instale as dependências:
```bash
pip install -r requirements.txt
```

3. Certifique-se de que o PostgreSQL está rodando
4. Execute a aplicação:
```bash
uvicorn app.main:app --reload
```

## Acessar a API

- **API Base**: http://localhost:8000
- **Documentação Interativa (Swagger)**: http://localhost:8000/docs
- **Health Check**: http://localhost:8000/health

## Endpoints Principais

- `POST /api/v1/users/register` - Registrar usuário
- `POST /api/v1/users/login` - Login
- `GET /api/v1/users/me` - Perfil do usuário autenticado
- `GET /api/v1/users/` - Listar usuários (requer autenticação)
- `PUT /api/v1/users/me` - Atualizar perfil

## Tecnologias Utilizadas

- **FastAPI**: Framework web moderno para Python
- **SQLModel**: ORM moderno que unifica SQLAlchemy + Pydantic
- **PostgreSQL**: Banco de dados relacional
- **Docker**: Containerização
- **JWT**: Autenticação baseada em tokens
- **bcrypt**: Hash seguro de senhas

## Exemplo de Uso

### 1. Registrar usuário
```bash
curl -X POST "http://localhost:8000/api/v1/users/register" \
     -H "Content-Type: application/json" \
     -d '{
       "email": "usuario@email.com",
       "nome": "João Silva",
       "password": "minhasenha123"
     }'
```

### 2. Login
```bash
curl -X POST "http://localhost:8000/api/v1/users/login" \
     -H "Content-Type: application/json" \
     -d '{
       "email": "usuario@email.com",
       "password": "minhasenha123"
     }'
```

### 3. Acessar perfil (com token)
```bash
curl -X GET "http://localhost:8000/api/v1/users/me" \
     -H "Authorization: Bearer SEU_TOKEN_AQUI"
```

## Recursos Implementados

✅ Conexão com PostgreSQL via SQLModel  
✅ Autenticação JWT  
✅ Hash de senhas com bcrypt  
✅ Validação de dados com Pydantic/SQLModel  
✅ CORS configurado para frontend  
✅ Documentação automática (Swagger/OpenAPI)  
✅ Estrutura modular e escalável  
✅ Tratamento de erros  
✅ Docker e Docker Compose  
✅ Health checks