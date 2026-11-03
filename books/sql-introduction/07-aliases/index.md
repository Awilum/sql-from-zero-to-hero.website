---
title: "Псевдонимы (Ключевое слово AS)"
seo_title: "Псевдонимы (Ключевое слово AS) — SQL Введение — SQL с нуля до результата"
description: "Глава книги «SQL Введение»: Псевдонимы (Ключевое слово AS). Бесплатный учебник по SQL на русском языке."
canonical_url: "https://sql.sergeyromanenko.com/books/sql-introduction/07-aliases/"
markdown_url: "https://sql.sergeyromanenko.com/books/sql-introduction/07-aliases/index.md"
section: "Site"
language: "ru"
robots: "index, follow, max-image-preview:large"
---

1. [Книги](https://sql.sergeyromanenko.com/books/)
2. [SQL Введение](https://sql.sergeyromanenko.com/books/sql-introduction/)
3. Псевдонимы (Ключевое слово AS)

SQL Введение

·

Глава 08

Часть бесплатной книги «SQL Введение» · [Перейти к содержанию](https://sql.sergeyromanenko.com/books/sql-introduction/)

# Псевдонимы (Ключевое слово AS)

**Alias (псевдоним)** — это временное имя, которое присваивается столбцу или таблице в SQL-запросе. Псевдонимы делают итоговый отчет более понятным для человека, а сам код запроса — более компактным и удобным для чтения, особенно если оригинальные названия полей или таблиц слишком длинные.

В SQL псевдонимы создаются с помощью ключевого слова **`AS`** .

## Псевдонимы для столбцов (Переименование полей в отчете)

Когда мы выводим данные для аналитиков или в интерфейс приложения, технические названия столбцов вроде `nickname` или `rank_title` могут выглядеть не совсем презентабельно. Мы можем переименовать их «на лету» прямо в блоке `SELECT`.

**Наш запрос:**

```sql
SELECT id AS player_id,
       nickname AS player_name,
       level AS player_level,
       rank_title AS player_rank,
       rating AS competitive_rating
FROM players;
```

**Результат (срез, первые 5 строк):**

База данных вернет привычные данные из таблицы `players`, но заголовки столбцов в итоговой таблице изменятся на те, что мы указали после `AS`:

| player_id | player_name | player_level | player_rank | competitive_rating |
| --- | --- | --- | --- | --- |
| 1 | AlphaKnight | 45 | Gold | 2100 |
| 2 | CatQueen | 12 | Bronze | 850 |
| 3 | ThunderStrike | 89 | Diamond | 3450 |
| 4 | AliceFox | 31 | Silver | 1500 |
| 5 | MaxDrive | 55 | Gold | 2400 |

***Важно помнить:***
Ключевое слово `AS` не меняет структуру самой таблицы в базе данных. Изменения происходят только в выводимом результате конкретного запроса.

## Псевдонимы для таблиц (Сокращение кода)

Если имя таблицы длинное или в будущем мы начнем связывать несколько таблиц между собой, писать каждый раз полное имя перед столбцом становится неудобно. Мы можем присвоить короткую букву-псевдоним всей таблице в блоке `FROM`.

Давай присвоим таблице `players` короткий псевдоним **`p`** :

**Наш запрос:**

```sql
SELECT p.id,
       p.nickname AS player_name,
       p.city
FROM players AS p;
```

**Как это работает:**

Запись `players AS p` указывает SQL, что внутри этого запроса к таблице можно обращаться просто по букве `p`. Точка после псевдонима (`p.id`, `p.nickname`) явно указывает базе данных: *«Возьми поле id именно из таблицы p (players)»*. Подобный подход считается стандартом хорошего тона у разработчиков, так как он защищает код от путаницы.

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

← Фильтрация данных (Оператор WHERE)

Группировка данных (Оператор GROUP BY) →
