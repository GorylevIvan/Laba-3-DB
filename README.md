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
![](https://github.com/GorylevIvan/Laba-3-DB/blob/main/%D0%B3%D1%80%D0%B0%D1%84%20%D0%B8%20%D1%80%D0%B5%D0%B7%D1%83%D0%BB%D1%8C%D1%82%D0%B0%D1%82%D1%8B/psycopg2.png)
![](https://github.com/GorylevIvan/Laba-3-DB/blob/main/%D0%B3%D1%80%D0%B0%D1%84%20%D0%B8%20%D1%80%D0%B5%D0%B7%D1%83%D0%BB%D1%8C%D1%82%D0%B0%D1%82%D1%8B/sqlite3.png)
![](https://github.com/GorylevIvan/Laba-3-DB/blob/main/%D0%B3%D1%80%D0%B0%D1%84%20%D0%B8%20%D1%80%D0%B5%D0%B7%D1%83%D0%BB%D1%8C%D1%82%D0%B0%D1%82%D1%8B/duckdb.png)
![](https://github.com/GorylevIvan/Laba-3-DB/blob/main/%D0%B3%D1%80%D0%B0%D1%84%20%D0%B8%20%D1%80%D0%B5%D0%B7%D1%83%D0%BB%D1%8C%D1%82%D0%B0%D1%82%D1%8B/pandas.png)
## Впечатления
### psycopg2
Не самая эфективная по скорости, так как проигрывает по скорости duckdb и pandas, но все еще довольно быстрая по сравнению с sqlite3. Скорее всего это из-за PostgreSQL, так как psycopg2 необходимо выполнить подключение по сети.
### duckdb
Самая быстрая по скорости из всех библиотек, так как он имеет широкий спектр функций, позволяющих без лишних проблем управлять данными. Он мне показался довольно удобным в использовании и простым в понимании.
### sqlite3
Самая медленная из всех библиотек, она показала худший результат по скорости, но одновременно с этим она весьма лёгкая в использовании и встроенна в Python. К тому же время может быть улучшено различными методами оптимизации. Не требует отдельного сервера и хранит всю информацию локально, в отдельном файле .db.
### pandas
Вторая по скорости библиотека так как в работе был подключён к PostgreSQL. Pandas очень удобная, так как обладает целым набором полезных и интуитивно понятных функций.
## Вывод
В результате данной лабораторной работы был написан бенчмарк для 4 различных библиотек языка python. Самые лучшие показатель показал duckdb, следом за ним идет pandas, потом не поспевающий за ними psycopg2, ну и наконец аутсайдер по времени - sqlite3. По простоте использования для меня все еще лидирует duckdb, затем pandas, ну и следом вмести идут psycopg2 и sqlite3
