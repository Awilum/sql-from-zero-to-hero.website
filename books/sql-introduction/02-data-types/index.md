---
title: "Типы данных"
seo_title: "Типы данных — SQL Введение — SQL с нуля до результата"
description: "Глава книги «SQL Введение»: Типы данных. Бесплатный учебник по SQL на русском языке."
canonical_url: "https://sql.sergeyromanenko.com/books/sql-introduction/02-data-types/"
markdown_url: "https://sql.sergeyromanenko.com/books/sql-introduction/02-data-types/index.md"
section: "Site"
language: "ru"
robots: "index, follow, max-image-preview:large"
---

1. [Книги](https://sql.sergeyromanenko.com/books/)
2. [SQL Введение](https://sql.sergeyromanenko.com/books/sql-introduction/)
3. Типы данных

SQL Введение

·

Глава 03

Часть бесплатной книги «SQL Введение» · [Перейти к содержанию](https://sql.sergeyromanenko.com/books/sql-introduction/)

# Типы данных

При создании таблицы необходимо указать, какие данные будут храниться в каждом столбце.

Для этого используются типы данных.

Тип данных определяет, какие значения можно записывать в столбец таблицы.

Рассмотрим таблицу игроков:

| **Столбец** | **Тип данных** |
| --- | --- |
| id | INT |
| nickname | VARCHAR(50) |
| email | VARCHAR(100) |
| level | INT |
| rating | INT |
| win_rate | DECIMAL(5,2) |
| last_login | DATE |
| registration_date | DATE |

Каждый столбец хранит определенный тип информации, поэтому для него выбирается подходящий тип данных.

## Целые числа

Для хранения целых чисел используются числовые типы данных.

В нашей таблице это:

```sql
id INT
level INT
rating INT
wins INT
losses INT
```

Примеры значений:

| **level** |
| --- |
| 1 |
| 25 |
| 100 |

Тип **INT** используется очень часто и подходит для хранения большинства целых чисел.

## Строковые данные

Для хранения текста используются строковые типы данных.

В нашей таблице это:

```sql
nickname VARCHAR(50)
email VARCHAR(100)
city VARCHAR(50)
country VARCHAR(50)
rank_title VARCHAR(50)
guild VARCHAR(50)
```

Примеры значений:

| **nickname** |
| --- |
| Dragon |
| Shadow |
| Warrior77 |

Тип **VARCHAR** хранит строки переменной длины.

Например:

```sql
VARCHAR(50)
```

Число в скобках указывает максимальное количество символов, которое может храниться в поле.

Для столбца:

```sql
nickname VARCHAR(50)
```

можно сохранить ник длиной до 50 символов.

## Числа с дробной частью

Для хранения чисел с дробной частью используются специальные типы данных.

В нашей таблице используется:

```sql
win_rate DECIMAL(5,2)
```

Примеры значений:

| **win_rate** |
| --- |
| 52.30 |
| 75.50 |
| 100.00 |

Тип:

```sql
DECIMAL(5,2)
```

означает:

- всего можно хранить 5 цифр;
- из них 2 цифры находятся после десятичной точки.

Например:

```sql
99.99
12.50
100.00
```

Такой тип данных часто используется для процентов и денежных значений.

## Дата

Для хранения даты используется тип данных:

```sql
DATE
```

В нашей таблице это:

```sql
last_login DATE
registration_date DATE
```

Примеры значений:

```sql
2025-01-15
2025-06-20
2026-01-01
```

Формат даты:

```sql
ГГГГ-ММ-ДД
```

Например:

```sql
2026-06-25
```

## NULL

Некоторые поля могут не содержать значения.

В таком случае используется специальное значение:

```sql
NULL
```

Например, игрок может еще не состоять в гильдии:

| **nickname** | **guild** |
| --- | --- |
| Dragon | NULL |

Или игрок еще не получил звание:

| **nickname** | **rank_title** |
| --- | --- |
| Shadow | NULL |

NULL означает, что значение отсутствует или пока неизвестно.

Важно понимать разницу:

| **Значение** | **Смысл** |
| --- | --- |
| NULL | значение отсутствует |
| ‘’ | пустая строка |
| 0 | число ноль |

Это разные значения.

## Что важно запомнить

- Тип данных определяет, какие значения можно хранить в столбце.
- Для целых чисел в нашей таблице используется тип INT.
- Для текста используется VARCHAR.
- Для процентов побед используется DECIMAL.
- Для хранения даты используется DATE.
- NULL означает отсутствие значения.

Практика: пройти курс на Stepik →

Вернуться к содержанию

Полная программа SQL с нуля до результата →

Навигация

1. [01. Предисловие](https://sql.sergeyromanenko.com/books/sql-introduction/00-preface/)
2. [02. Учебная база данных «Игроки»](https://sql.sergeyromanenko.com/books/sql-introduction/01-database-overview/)
3. [03. Типы данных](https://sql.sergeyromanenko.com/books/sql-introduction/02-data-types/)
4. [04. Введение в SQL](https://sql.sergeyromanenko.com/books/sql-introduction/03-introduction/)
5. [05. Выборка данных (Оператор SELECT)](https://sql.sergeyromanenko.com/books/sql-introduction/04-querying-data/)
6. [06. Сортировка данных (Оператор ORDER BY)](https://sql.sergeyromanenko.com/books/sql-introduction/05-sorting-data/)
7. [07. Фильтрация данных (Оператор WHERE)](https://sql.sergeyromanenko.com/books/sql-introduction/06-filtering-data/)
8. [08. Псевдонимы (Ключевое слово AS)](https://sql.sergeyromanenko.com/books/sql-introduction/07-aliases/)
9. [09. Группировка данных (Оператор GROUP BY)](https://sql.sergeyromanenko.com/books/sql-introduction/08-grouping-data/)
10. [10. Агрегатные функции](https://sql.sergeyromanenko.com/books/sql-introduction/09-aggregate-functions/)
11. [11. Что дальше?](https://sql.sergeyromanenko.com/books/sql-introduction/10-summary/)
12. [12. Об авторе](https://sql.sergeyromanenko.com/books/sql-introduction/11-about/)

Предыдущая / Следующая

← Учебная база данных «Игроки»

Введение в SQL →
