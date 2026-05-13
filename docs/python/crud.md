# Python CRUD Examples

Implementing CRUD operations using SQLAlchemy (SQL) and MongoDB (NoSQL).

## 1. SQL CRUD (SQLAlchemy)

```python
from sqlalchemy import create_engine, Column, Integer, String
from sqlalchemy.orm import sessionmaker, declarative_base

Base = declarative_base()
engine = create_engine('sqlite:///example.db')
Session = sessionmaker(bind=engine)
session = Session()

class User(Base):
    __tablename__ = 'users'
    id = Column(Integer, primary_key=True)
    name = Column(String)

Base.metadata.create_all(engine)

# CREATE
new_user = User(name='Alice')
session.add(new_user)
session.commit()

# READ
user = session.query(User).filter_by(name='Alice').first()

# UPDATE
user.name = 'Bob'
session.commit()

# DELETE
session.delete(user)
session.commit()
```
## 2. NoSQL CRUD (PyMongo)

```python
from pymongo import MongoClient

client = MongoClient('mongodb://localhost:27017/')
db = client['test_db']
users = db.users

# CREATE
user_id = users.insert_one({'name': 'Alice', 'age': 25}).inserted_id

# READ
user = users.find_one({'name': 'Alice'})

# UPDATE
users.update_one({'name': 'Alice'}, {'$set': {'age': 26}})

# DELETE
users.delete_one({'name': 'Alice'})
```
## 3. Fast API CRUD Snippet

```python
from fastapi import FastAPI
from pydantic import BaseModel

app = FastAPI()

class Item(BaseModel):
    name: str

@app.post("/items/")
async def create_item(item: Item):
    return item
```
## Code Examples

### Virtualenv + quick run
```bash
python -m venv .venv
source .venv/bin/activate
python -m pip install -U pip
python -c "print('ready')"
```
### Robust file reading
```python
from pathlib import Path

def read_text(path: str) -> str:
    return Path(path).read_text(encoding="utf-8")
```
> [!TIP]
> Use the **Copy** button in the top-right of code blocks to quickly copy commands to your clipboard.
