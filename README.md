# Projeto Login Python

Aplicação didática de login feita com Python, Flask, HTML e CSS. O sistema usa variáveis de ambiente para as credenciais e não utiliza banco de dados.

## Estrutura

```text
projeto-login-python/
├── app.py
├── requirements.txt
├── .gitignore
├── .env.example
├── README.md
├── templates/
│   ├── login.html
│   └── boas_vindas.html
└── static/
    └── style.css
```

## Executar no Windows (PowerShell)

```powershell
python -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
```

Gere o hash da senha:

```powershell
.\.venv\Scripts\python.exe -c "from werkzeug.security import generate_password_hash; print(generate_password_hash('SUA_SENHA_DE_TESTE'))"
```

Gere uma chave secreta:

```powershell
.\.venv\Scripts\python.exe -c "import secrets; print(secrets.token_hex(32))"
```

Configure as variáveis no terminal, substituindo os valores pelos seus:

```powershell
$env:LOGIN_USER = 'aluno'
$env:LOGIN_PASSWORD_HASH = 'COLE_O_HASH_GERADO'
$env:SECRET_KEY = 'COLE_A_CHAVE_GERADA'
$env:COOKIE_SECURE = '0'
.\.venv\Scripts\python.exe app.py
```

Acesse http://127.0.0.1:5000.

## Publicar no GitHub

Envie o conteúdo desta pasta para um repositório chamado `projeto-login-python`. Preserve as pastas `templates` e `static`. Não envie `.env`, credenciais, hashes, chaves secretas ou a pasta `.venv`.

## Publicar no Render

Crie um **Web Service** conectado ao repositório GitHub e use:

- Language: Python 3
- Build Command: `pip install -r requirements.txt`
- Start Command: `gunicorn app:app`
- Root Directory: vazio, se os arquivos estiverem na raiz do repositório

Cadastre no painel Environment as variáveis `LOGIN_USER`, `LOGIN_PASSWORD_HASH`, `SECRET_KEY` e `COOKIE_SECURE`. No Render, use `COOKIE_SECURE=1`. Gere seu próprio hash e sua própria chave. Nunca publique esses valores no GitHub.

## Rotas

- `/` redireciona para `/login`.
- `/login` exibe e processa o formulário.
- `/boas-vindas` exige uma sessão autenticada.
- `/sair` encerra a sessão por POST e valida token CSRF.

Este projeto é um exercício educacional. Para uso real, seriam necessárias outras proteções, como limitação de tentativas e gerenciamento adequado de contas.
