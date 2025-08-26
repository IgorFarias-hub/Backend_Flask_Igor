# 🎉 Lista de Convidados — Flask + PostgreSQL

Aplicação web para cadastro e gerenciamento de lista de convidados, feita em **Flask** com banco de dados **PostgreSQL**.  

Permite:
- Cadastrar convidados (nome e e-mail com validação).
- Listar todos os convidados.
- Ver a quantidade total de convidados.
- Ver quem já confirmou presença.
- Editar ou remover convidados via API (PUT/DELETE).
- Confirmar presença via API.

---

## 🚀 Tecnologias usadas
- Python 3.10+
- Flask 2.2
- Flask-WTF (formulários e validação)
- Flask-SQLAlchemy (ORM)
- Flask-Migrate (migrations)
- PostgreSQL (banco de dados)
- Gunicorn / Waitress (servidor de produção)

---

## 📦 Instalação

### 1. Clonar o repositório
```bash
git clone https://github.com/IgorFarias-hub/Backend_Flask_Igor.git
cd Backend_Flask_Igor
```
---

### 2. Criar e ativar ambiente virtual
```bash
python -m venv venv
source venv/bin/activate   # Linux/Mac
venv\Scripts\activate      # Windows
```
---

### 3. Instalar dependências
```bash
pip install -r requirements.txt
```

---

## 🗄️ Configuração do Banco de Dados

### 1. Criar banco e usuário no PostgreSQL:
```sql
CREATE DATABASE convidadosdb;
CREATE USER meuusuario WITH PASSWORD 'minhasenha';
GRANT ALL PRIVILEGES ON DATABASE convidadosdb TO meuusuario;
```

---

### 2. Copiar o arquivo .env.example para .env.dev:
- Linux/Mac
```bash
cp .env.example .env.dev
```

- Windows (PowerShell ou CMD)
```powershell
Copy-Item .env.example .env.dev
```

---

### 3. Editar .env.dev com suas credenciais do banco:
```env
SECRET_KEY=dev-secret-key
FLASK_ENV=development
DEBUG=True
DATABASE_URL=postgresql://meuusuario:minhasenha@localhost/convidadosdb
```

---

## 🗄️ Criando as tabelas

### Gerar migrations e aplicar no banco:
```bash
flask db init      # apenas na primeira vez
flask db migrate -m "Criar tabela Guest"
flask db upgrade
```

---

## ▶️ Rodando a aplicação
Ambiente de desenvolvimento:
```bash
python run.py
```
Ambiente de produção:
```bash
gunicorn -w 4 -b 0.0.0.0:8000 run:app
```

---

## 🌐 Rotas principais
### Web (HTML)
- / → formulário de cadastro
- /convidados → lista todos os convidados
- /quantidade → mostra quantidade total
- /confirmados → lista quem já confirmou

### API REST (JSON)
- GET /api/convidados → lista convidados
- POST /api/convidados → cria convidado
- GET /api/convidados/<id> → retorna convidado
- PUT /api/convidados/<id> → atualiza convidado
- DELETE /api/convidados/<id> → remove convidado
- PUT /api/convidados/<id>/confirmar → confirma presença

---

## 👨‍🏫 Observações para o professor
- O projeto usa PostgreSQL.
- É preciso editar o arquivo .env.dev com usuário e senha do banco antes de rodar.
- Todas as migrations estão configuradas com Flask-Migrate.
