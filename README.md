# Laba-3-DB
## Что нужно сделать чтобы все заработало
Для начала нужно скачать нужные библиотеки,
для этого в командной строке нужно прописать следующие команды:
```
pip install psycopg2
```
pip install sqlalchemy
```
pip install duckdb
```
pip install pandas

### Создание таблицы в PostgreSQL
```
import sqlalchemy
from sqlalchemy import create_engine
import pandas as pd

engine = create_engine('postgresql://postgres:password@localhost:5432/postgres')
tiny = 'C:\\Users\\Legion\\bd laba 3\\nyc_yellow_tiny.csv'
df=pd.read_csv(tiny)
df["tpep_pickup_datetime"]=pd.to_datetime(df["tpep_pickup_datetime"])
df.to_sql('taxi',engine,if_exists='replace',index=False)
```
## Результаты запусков и сравнительный график
