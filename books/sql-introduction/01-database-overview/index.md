---
title: "Учебная база данных «Игроки»"
seo_title: "Учебная база данных «Игроки» — SQL Введение — SQL с нуля до результата"
description: "Глава книги «SQL Введение»: Учебная база данных «Игроки». Бесплатный учебник по SQL на русском языке."
canonical_url: "https://sql.sergeyromanenko.com/books/sql-introduction/01-database-overview/"
markdown_url: "https://sql.sergeyromanenko.com/books/sql-introduction/01-database-overview/index.md"
section: "Site"
language: "ru"
robots: "index, follow, max-image-preview:large"
---

1. [Книги](https://sql.sergeyromanenko.com/books/)
2. [SQL Введение](https://sql.sergeyromanenko.com/books/sql-introduction/)
3. Учебная база данных «Игроки»

SQL Введение

·

Глава 02

Часть бесплатной книги «SQL Введение» · [Перейти к содержанию](https://sql.sergeyromanenko.com/books/sql-introduction/)

# Учебная база данных «Игроки»

В этой книге используется единая учебная база данных «Игроки».

Все примеры и SQL-запросы основаны на таблице `players`.

Если вы хотите не только читать книгу, но и выполнять все запросы самостоятельно, воспользуйтесь интерактивной SQL-песочницей, доступной в рамках курса «SQL Введение».

В песочнице вы сможете:

- выполнять любые SQL-запросы;
- изучать структуру таблицы;
- экспериментировать с данными;
- проверять собственные решения;
- закреплять материал на практике.

Доступ к курсу и SQL-песочнице: [Записаться на курс «SQL Введение»](https://stepik.org/a/290855?utm_source=ebook&utm_medium=book&utm_campaign=sql_introduction_book&utm_content=sql_introduction)

## Структура таблицы

| Поле | Тип данных | Описание |
| --- | --- | --- |
| id | INT | Уникальный идентификатор игрока |
| nickname | VARCHAR(50) | Игровой ник |
| email | VARCHAR(100) | Электронная почта |
| city | VARCHAR(50) | Город проживания |
| country | VARCHAR(50) | Страна проживания |
| level | INT | Уровень персонажа |
| rating | INT | Игровой рейтинг |
| rank_title | VARCHAR(50) | Ранг игрока (Bronze, Silver, Gold, Platinum, Diamond, Master) |
| guild | VARCHAR(50) | Гильдия или клан игрока |
| wins | INT | Количество побед |
| losses | INT | Количество поражений |
| win_rate | DECIMAL(5,2) | Процент побед |
| last_login | DATE | Дата последнего входа |
| registration_date | DATE | Дата регистрации аккаунта |

## Пример записи

| id | nickname | city | level | rating | rank_title | guild |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | AlphaKnight | Москва | 45 | 2100 | Gold | Грифоны Эрафии |

## Особенности данных

При работе с таблицей обратите внимание на несколько важных моментов:

- Некоторые игроки не состоят в гильдиях. В поле `guild` для них хранится значение `NULL`.
- В таблице представлены игроки разных уровней — от новичков до опытных пользователей.
- Несколько игроков могут проживать в одном городе.
- В одной гильдии может состоять сразу несколько игроков.
- Даты регистрации и последних входов позволяют выполнять запросы по времени.
- Таблица содержит как числовые, так и текстовые данные.

## Работа с таблицей

Во всех главах этой книги запросы будут выполняться к одной и той же таблице:

```sql
players
```

Перед началом изучения книги рекомендуется ознакомиться со структурой таблицы и понять назначение каждого столбца. Это поможет лучше понимать примеры и быстрее освоить SQL.

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

← Предисловие

Типы данных →
