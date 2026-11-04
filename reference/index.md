---
title: "Справочник по SQL: синтаксис под рукой"
seo_title: "Справочник по SQL: синтаксис и примеры — SQL с нуля до результата"
description: "Шпаргалка по SQL: SELECT, WHERE, JOIN, GROUP BY, CTE, оконные функции, INSERT и DELETE. Короткие примеры для SQLite, копирование и проверка в песочнице."
canonical_url: "https://sql.sergeyromanenko.com/reference/"
markdown_url: "https://sql.sergeyromanenko.com/reference/index.md"
section: "Site"
language: "ru"
robots: "index, follow, max-image-preview:large"
---

1. Справочник

# Справочник по SQL: синтаксис под рукой

Форма записи, готовый пример и две заметки о том, где чаще всего ошибаются. Примеры выполняются в SQLite, если не указано иное.

Программа обучения →

Песочница SQLite →

Справочник не заменяет курс: здесь нет пошаговых объяснений и упражнений. Начать бесплатно можно с курса [«SQL Введение»](https://sql.sergeyromanenko.com/courses/sql-introduction/).

Как пользоваться

1. 01Найдите тему в содержании.
2. 02Скопируйте пример кнопкой в блоке.
3. 03Вставьте его в песочницу и выполните.

Шаблон — форма записи с русскими подсказками.

Пример — готовый запрос для копирования.

Открыть песочницу →

Содержание

14 тем · обновлено 31 октября 2026

Основы выборки

1. SELECT
2. WHERE
3. ORDER BY и LIMIT
4. DISTINCT

Группировка

1. GROUP BY и HAVING

Соединения

1. JOIN

Логика и значения

1. NULL
2. CASE
3. IN, BETWEEN, LIKE

Сложные запросы

1. UNION и UNION ALL
2. Подзапросы и CTE
3. Оконные функции

Изменение данных

1. INSERT, UPDATE, DELETE

Диалекты

1. Диалекты SQL

**Содержание14 тем**

Основы выборки

1. SELECT
2. WHERE
3. ORDER BY и LIMIT
4. DISTINCT

Группировка

1. GROUP BY и HAVING

Соединения

1. JOIN

Логика и значения

1. NULL
2. CASE
3. IN, BETWEEN, LIKE

Сложные запросы

1. UNION и UNION ALL
2. Подзапросы и CTE
3. Оконные функции

Изменение данных

1. INSERT, UPDATE, DELETE

Диалекты

1. Диалекты SQL

Основы выборки

4

## SELECT

#select

Выбирает столбцы и вычисляемые выражения из таблицы.

Шаблон синтаксиса

Копировать — Шаблон синтаксиса: SELECT

```
SELECT столбец, выражение AS псевдоним
FROM таблица
WHERE условие
ORDER BY столбец
LIMIT количество;
```

Пример

SQLite

Копировать — Пример: SELECT

```
SELECT name, city
FROM customers
WHERE city = 'Москва'
ORDER BY name;
```

- Перечисляйте нужные столбцы явно: «*» ломается, когда меняется схема таблицы.
- Порядок выполнения: FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY → LIMIT.

Курс [«SQL Введение» →](https://sql.sergeyromanenko.com/courses/sql-introduction/)

## WHERE

#where

Оставляет строки, для которых условие истинно.

Шаблон синтаксиса

Копировать — Шаблон синтаксиса: WHERE

```
WHERE условие
  AND (условие OR условие)
```

Пример

SQLite

Копировать — Пример: WHERE

```
SELECT name, price
FROM products
WHERE price BETWEEN 5000 AND 50000
  AND stock > 0;
```

- AND имеет более высокий приоритет, чем OR; группируйте условия скобками.
- NULL не сравнивается через = или <>: используйте IS NULL и IS NOT NULL.

Курс [«SQL Условная логика» →](https://sql.sergeyromanenko.com/courses/sql-conditional-logic/)

## ORDER BY и LIMIT

#order-limit

Сортирует результат и ограничивает число строк.

Шаблон синтаксиса

Копировать — Шаблон синтаксиса: ORDER BY и LIMIT

```
ORDER BY столбец ASC | DESC
LIMIT количество OFFSET пропустить;
```

Пример

SQLite

Копировать — Пример: ORDER BY и LIMIT

```
SELECT name, price
FROM products
ORDER BY price DESC
LIMIT 3;
```

- Без ORDER BY порядок строк не гарантирован, даже если он кажется стабильным.
- LIMIT без сортировки не отвечает на вопрос «самые дорогие»: сначала задайте порядок.

## DISTINCT

#distinct

Удаляет одинаковые строки из результата.

Шаблон синтаксиса

Копировать — Шаблон синтаксиса: DISTINCT

```
SELECT DISTINCT столбец1, столбец2
FROM таблица;
```

Пример

SQLite

Копировать — Пример: DISTINCT

```
SELECT DISTINCT city
FROM customers
ORDER BY city;
```

- DISTINCT сравнивает всю строку результата, а не отдельный столбец.
- COUNT(DISTINCT столбец) считает уникальные значения и пропускает NULL.

Группировка

1

## GROUP BY и HAVING

#group-having

Собирает строки в группы и фильтрует уже готовые группы.

Шаблон синтаксиса

Копировать — Шаблон синтаксиса: GROUP BY и HAVING

```
SELECT столбец, COUNT(*) AS количество
FROM таблица
GROUP BY столбец
HAVING COUNT(*) > 1;
```

Пример

SQLite

Копировать — Пример: GROUP BY и HAVING

```
SELECT status, COUNT(*) AS orders_count
FROM orders
GROUP BY status
HAVING COUNT(*) >= 2
ORDER BY orders_count DESC;
```

- WHERE фильтрует строки до группировки, HAVING — готовые группы.
- Столбец в SELECT должен входить в GROUP BY или быть агрегатом; в MySQL 8 это проверяет ONLY_FULL_GROUP_BY.

Курс [«SQL для начинающих» →](https://sql.sergeyromanenko.com/courses/sql-for-beginners/)

Соединения

1

## JOIN

#join

Соединяет строки двух таблиц по условию ON.

Шаблон синтаксиса

Копировать — Шаблон синтаксиса: JOIN

```
FROM левая AS l
JOIN правая AS r ON r.id = l.foreign_id
```

Пример

SQLite

Копировать — Пример: JOIN

```
SELECT c.name, o.ordered_at, o.status
FROM customers AS c
JOIN orders AS o ON o.customer_id = c.id
ORDER BY o.ordered_at DESC;
```

- INNER JOIN оставляет только совпадения, LEFT JOIN сохраняет все строки левой таблицы.
- RIGHT и FULL OUTER JOIN появились в SQLite 3.39.0; проверяйте, не размножает ли соединение строки.

Курс [«SQL для начинающих» →](https://sql.sergeyromanenko.com/courses/sql-for-beginners/)

Логика и значения

3

## NULL

#null

Отмечает отсутствующее или неизвестное значение.

Шаблон синтаксиса

Копировать — Шаблон синтаксиса: NULL

```
WHERE столбец IS NULL
WHERE столбец IS NOT NULL
```

Пример

SQLite

Копировать — Пример: NULL

```
SELECT name
FROM customers
WHERE city IS NULL;
```

- NULL — не ноль и не пустая строка; сравнение с ним даёт UNKNOWN, а не TRUE.
- COUNT(столбец) и AVG(столбец) пропускают NULL, а COUNT(*) считает все строки.

## CASE

#case

Возвращает значение по первому выполненному условию.

Шаблон синтаксиса

Копировать — Шаблон синтаксиса: CASE

```
CASE
  WHEN условие THEN значение
  ELSE значение
END
```

Пример

SQLite

Копировать — Пример: CASE

```
SELECT
  name,
  CASE
    WHEN price >= 50000 THEN 'дорогой'
    WHEN price >= 10000 THEN 'средний'
    ELSE 'доступный'
  END AS segment
FROM products;
```

- CASE работает в SELECT, ORDER BY, GROUP BY и внутри агрегатных функций.
- Без ELSE результат будет NULL, а не исходное значение.

## IN, BETWEEN, LIKE

#in-between-like

Три коротких способа записать список, диапазон или шаблон.

Шаблон синтаксиса

Копировать — Шаблон синтаксиса: IN, BETWEEN, LIKE

```
WHERE столбец IN (значение1, значение2)
WHERE столбец BETWEEN минимум AND максимум
WHERE столбец LIKE 'шаблон%'
```

Пример

SQLite

Копировать — Пример: IN, BETWEEN, LIKE

```
SELECT name, city
FROM customers
WHERE city IN ('Москва', 'Санкт-Петербург')
  AND name LIKE 'А%';
```

- BETWEEN включает границы; NOT IN с NULL в списке не вернёт ни одной строки.
- В SQLite LIKE без учёта регистра работает только для латиницы: для кириллицы регистр важен.

Сложные запросы

3

## UNION и UNION ALL

#union

Складывает результаты запросов один под другим.

Шаблон синтаксиса

Копировать — Шаблон синтаксиса: UNION и UNION ALL

```
SELECT столбцы FROM таблица1
UNION | UNION ALL
SELECT столбцы FROM таблица2
ORDER BY столбец;
```

Пример

SQLite

Копировать — Пример: UNION и UNION ALL

```
SELECT name AS label FROM customers
UNION
SELECT name FROM products
ORDER BY label;
```

- UNION удаляет дубликаты, UNION ALL оставляет все строки и обычно работает быстрее.
- Число и типы столбцов должны совпадать; ORDER BY пишется один раз в конце.

## Подзапросы и CTE

#cte

Разбивает запрос на именованные шаги.

Шаблон синтаксиса

Копировать — Шаблон синтаксиса: Подзапросы и CTE

```
WITH имя AS (
  SELECT ...
)
SELECT ...
FROM имя;
```

Пример

SQLite

Копировать — Пример: Подзапросы и CTE

```
WITH paid AS (
  SELECT customer_id, id
  FROM orders
  WHERE status = 'paid'
)
SELECT c.name, COUNT(*) AS paid_orders
FROM customers AS c
JOIN paid ON paid.customer_id = c.id
GROUP BY c.id, c.name;
```

- CTE не гарантирует ускорение: PostgreSQL 12+ может встраивать простые CTE в основной запрос.
- Скалярный подзапрос возвращает одно значение; EXISTS проверяет только наличие строк.

Курс [«SQL Общие табличные выражения» →](https://sql.sergeyromanenko.com/courses/sql-common-table-expressions/)

## Оконные функции

#window

Считают по окну строк, не сворачивая результат.

Шаблон синтаксиса

Копировать — Шаблон синтаксиса: Оконные функции

```
функция(...) OVER (
  PARTITION BY столбец
  ORDER BY столбец
)
```

Пример

SQLite

Копировать — Пример: Оконные функции

```
SELECT
  name,
  category,
  price,
  RANK() OVER (
    PARTITION BY category
    ORDER BY price DESC
  ) AS price_rank
FROM products;
```

- Оконные функции нельзя использовать в WHERE: оберните запрос в CTE или подзапрос.
- ORDER BY внутри OVER задаёт порядок вычисления, а не порядок вывода строк.

Курс [«SQL Оконные функции» →](https://sql.sergeyromanenko.com/courses/sql-window-functions/)

Изменение данных

1

## INSERT, UPDATE, DELETE

#dml

Добавляет, изменяет и удаляет строки.

Шаблон синтаксиса

Копировать — Шаблон синтаксиса: INSERT, UPDATE, DELETE

```
INSERT INTO таблица (столбцы) VALUES (значения);
UPDATE таблица SET столбец = значение WHERE условие;
DELETE FROM таблица WHERE условие;
```

Пример

SQLite

Копировать — Пример: INSERT, UPDATE, DELETE

```
UPDATE products
SET stock = stock - 1
WHERE id = 1
  AND stock > 0;
```

- UPDATE и DELETE без WHERE изменяют все строки таблицы.
- Сначала проверьте условие через SELECT, а несколько операций выполняйте в транзакции.

Курс [«Практический тренажёр по SQL» →](https://sql.sergeyromanenko.com/courses/sql-practical-trainer/)

Диалекты

1

## Диалекты SQL

#dialects

Базовый синтаксис общий, функции и ограничения различаются.

Шаблон синтаксиса

Копировать — Шаблон синтаксиса: Диалекты SQL

```
-- SQLite / PostgreSQL / MySQL
SELECT ... LIMIT 10;

-- SQL Server
SELECT TOP 10 ...;
```

Сравнение

SQLite · SQL Server

Копировать — Сравнение: Диалекты SQL

```
-- SQLite и PostgreSQL
SELECT name FROM products
ORDER BY price DESC
LIMIT 3;

-- SQL Server
SELECT TOP 3 name FROM products
ORDER BY price DESC;
```

Не выполняется в песочнице: она поддерживает только SQLite.

- Проверяйте версию СУБД: RIGHT и FULL JOIN появились в SQLite 3.39.0, оконные функции — в 3.25.0.
- Песочница сайта работает на SQLite, курсы — в основном на MySQL: сверяйте функции дат, строк и типы.

Дальше

## Синтаксис — половина дела

Справочник помогает вспомнить форму записи. Уверенность появляется, когда вы сами пишете запросы, разбираете ошибки и понимаете, как СУБД обрабатывает запрос. В курсах есть последовательность и практика с проверкой результата.

Программа обучения →

Открыть песочницу →

Бесплатный курс «SQL Введение» →

Учебный путь по этапам →

Все курсы →

Примеры из справочника проверяются в SQLite. В MySQL, PostgreSQL и SQL Server часть функций отличается; перед переносом сверьтесь с документацией СУБД. Справочник не заменяет документацию.
