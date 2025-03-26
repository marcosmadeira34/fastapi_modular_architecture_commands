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

# Criar a estrutura de diretórios
mkdir -p app/api/v1
mkdir -p app/models
mkdir -p app/services
mkdir -p app/db
mkdir -p app/core
mkdir -p app/utils
mkdir -p tests

# Criar arquivos iniciais com código

# app/main.py
echo "from fastapi import FastAPI
from app.api.v1 import users, items

app = FastAPI()

app.include_router(users.router, prefix='/users', tags=['users'])
app.include_router(items.router, prefix='/items', tags=['items'])" > app/main.py

# app/api/v1/users.py
echo "from fastapi import APIRouter
from app.models.user import User

router = APIRouter()

@router.get('/')
async def get_users():
    return {'message': 'List of users'}" > app/api/v1/users.py

# app/api/v1/items.py
echo "from fastapi import APIRouter
from app.models.item import Item

router = APIRouter()

@router.get('/')
async def get_items():
    return {'message': 'List of items'}" > app/api/v1/items.py

# app/models/user.py
echo "from pydantic import BaseModel

class User(BaseModel):
    id: int
    name: str
    email: str" > app/models/user.py

# app/models/item.py
echo "from pydantic import BaseModel

class Item(BaseModel):
    id: int
    name: str
    description: str" > app/models/item.py

# app/services/user_service.py
echo "from app.models.user import User

def get_user_by_id(user_id: int) -> User:
    return User(id=user_id, name='John Doe', email='johndoe@example.com')" > app/services/user_service.py

# app/services/item_service.py
echo "from app.models.item import Item

def get_item_by_id(item_id: int) -> Item:
    return Item(id=item_id, name='Laptop', description='A powerful laptop')" > app/services/item_service.py

# app/db/session.py
echo "from sqlalchemy import create_engine
from sqlalchemy.ext.declarative import declarative_base
from sqlalchemy.orm import sessionmaker

SQLALCHEMY_DATABASE_URL = 'sqlite:///./test.db'

engine = create_engine(SQLALCHEMY_DATABASE_URL, connect_args={'check_same_thread': False})
SessionLocal = sessionmaker(autocommit=False, autoflush=False, bind=engine)

Base = declarative_base()" > app/db/session.py

# app/core/config.py
echo "import os

class Settings:
    SECRET_KEY = os.getenv('SECRET_KEY', 'mysecretkey')

settings = Settings()" > app/core/config.py

# app/core/security.py
echo "from app.core.config import settings
from passlib.context import CryptContext

pwd_context = CryptContext(schemes=['bcrypt'], deprecated='auto')

def hash_password(password: str) -> str:
    return pwd_context.hash(password)

def verify_password(plain_password: str, hashed_password: str) -> bool:
    return pwd_context.verify(plain_password, hashed_password)" > app/core/security.py

# app/utils/hashing.py
echo "from app.core.security import hash_password

def secure_user_password(password: str) -> str:
    return hash_password(password)" > app/utils/hashing.py

# app/utils/validation.py
echo "from pydantic import BaseModel, validator

class UserCreate(BaseModel):
    name: str
    email: str

    @validator('email')
    def validate_email(cls, value):
        if '@' not in value:
            raise ValueError('Invalid email address')
        return value" > app/utils/validation.py

# tests/test_users.py
echo "from fastapi.testclient import TestClient
from app.main import app

client = TestClient(app)

def test_get_users():
    response = client.get('/users/')
    assert response.status_code == 200
    assert 'message' in response.json()" > tests/test_users.py

# tests/test_items.py
echo "from fastapi.testclient import TestClient
from app.main import app

client = TestClient(app)

def test_get_items():
    response = client.get('/items/')
    assert response.status_code == 200
    assert 'message' in response.json()" > tests/test_items.py

# tests/test_services.py
echo "from app.services.user_service import get_user_by_id
from app.services.item_service import get_item_by_id

def test_get_user_by_id():
    user = get_user_by_id(1)
    assert user.name == 'John Doe'

def test_get_item_by_id():
    item = get_item_by_id(1)
    assert item.name == 'Laptop'" > tests/test_services.py

# tests/test_utils.py
echo "from app.utils.validation import UserCreate
from pydantic import ValidationError

def test_valid_email():
    user = UserCreate(name='John', email='john@example.com')
    assert user.email == 'john@example.com'

def test_invalid_email():
    try:
        user = UserCreate(name='John', email='invalidemail')
    except ValidationError as e:
        assert len(e.errors()) > 0" > tests/test_utils.py

# Criar arquivos de configuração
touch .env
touch requirements.txt
touch alembic.ini
touch README.md

echo "Estrutura de diretórios e arquivos com código inicial criada com sucesso!"


