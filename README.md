# Laba-3-DB
## Что нужно сделать чтобы все заработало
Для начала нужно скачать нужные библиотеки,
для этого в командной строке нужно прописать следующие команды:
```
pip install psycopg2
```
```
pip install sqlalchemy
```
```
pip install duckdb
```
```
pip install pandas
```
### Создание таблицы в PostgreSQL
```
import sqlalchemy
from sqlalchemy import create_engine
import pandas as pd

engine = create_engine('postgresql://postgres:password@localhost:5432/postgres')
tiny = 'C:\\Users\\Legion\\bd laba 3\\nyc_yellow_tiny.csv' #путь к файлу
df=pd.read_csv(tiny)
df["tpep_pickup_datetime"]=pd.to_datetime(df["tpep_pickup_datetime"])
df.to_sql('taxi',engine,if_exists='replace',index=False)
```
## Результаты запусков и сравнительный график
![](https://github.com/GorylevIvan/Laba-3-DB/blob/main/%D0%B3%D1%80%D0%B0%D1%84%20%D0%B8%20%D1%80%D0%B5%D0%B7%D1%83%D0%BB%D1%8C%D1%82%D0%B0%D1%82%D1%8B/%D0%93%D1%80%D0%B0%D1%84%D0%B8%D0%BA.png)
