# fastapi_modular_architecture_commands
Cria rapidamente arquitetura para projetos com FastApi

# Criar a estrutura de diretórios
mkdir -p app/api/v1
mkdir -p app/models
mkdir -p app/services
mkdir -p app/db
mkdir -p app/core
mkdir -p app/utils
mkdir -p tests

# Criar arquivos iniciais
touch app/main.py
touch app/api/v1/users.py
touch app/api/v1/items.py
touch app/models/user.py
touch app/models/item.py
touch app/services/user_service.py
touch app/services/item_service.py
touch app/db/session.py
touch app/core/config.py
touch app/core/security.py
touch app/utils/hashing.py
touch app/utils/validation.py
touch tests/test_users.py
touch tests/test_items.py
touch tests/test_services.py
touch tests/test_utils.py
touch .env
touch requirements.txt
touch alembic.ini
touch README.md

echo "Estrutura de diretórios e arquivos criada com sucesso!"

