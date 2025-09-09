# SQL Команды: Полный обзор

## 1. DDL (Data Definition Language) — Определение структуры данных

```sql
-- Создание таблицы
CREATE TABLE users (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    age INT
);

-- Удаление таблицы
DROP TABLE users;

-- Изменение таблицы (добавление колонки)
ALTER TABLE users ADD email VARCHAR(100);

-- Изменение таблицы (удаление колонки)
ALTER TABLE users DROP COLUMN age;

-- Переименование таблицы
ALTER TABLE users RENAME TO customers;

-- Создание индекса
CREATE INDEX idx_name ON users(name);

-- Удаление индекса
DROP INDEX idx_name;
```

## 2. DML (Data Manipulation Language) — Манипуляция данными

```sql
-- Вставка данных
INSERT INTO users (id, name, age) VALUES (1, 'Alex', 25);

-- Обновление данных
UPDATE users SET age = 30 WHERE id = 1;

-- Удаление данных
DELETE FROM users WHERE id = 1;
```

## 3. DQL (Data Query Language) — Запросы к данным

```sql
-- Получение всех данных
SELECT * FROM users;

-- Получение конкретных колонок
SELECT name, age FROM users;

-- Уникальные значения
SELECT DISTINCT age FROM users;

-- Фильтрация данных
SELECT * FROM users WHERE age > 18;

-- Сортировка
SELECT * FROM users ORDER BY age DESC;

-- Группировка
SELECT age, COUNT(*) FROM users GROUP BY age;

-- Группировка с условием
SELECT age, COUNT(*) FROM users GROUP BY age HAVING COUNT(*) > 1;

-- Соединение таблиц
SELECT u.id, u.name, o.amount
FROM users u
JOIN orders o ON u.id = o.user_id;

-- Левое соединение
SELECT u.id, u.name, o.amount
FROM users u
LEFT JOIN orders o ON u.id = o.user_id;

-- Правое соединение
SELECT u.id, u.name, o.amount
FROM users u
RIGHT JOIN orders o ON u.id = o.user_id;

-- Полное соединение (если поддерживается)
SELECT u.id, u.name, o.amount
FROM users u
FULL OUTER JOIN orders o ON u.id = o.user_id;
```

## 4. DCL (Data Control Language) — Управление доступом

```sql
-- Создание пользователя
CREATE USER 'ruslan' IDENTIFIED BY 'mypassword';

-- Удаление пользователя
DROP USER 'ruslan';

-- Выдача прав
GRANT SELECT, INSERT ON users TO 'ruslan';

-- Отзыв прав
REVOKE INSERT ON users FROM 'ruslan';
```

## 5. TCL (Transaction Control Language) — Управление транзакциями

```sql
-- Начало транзакции
BEGIN;

-- Фиксация изменений
COMMIT;

-- Отмена изменений
ROLLBACK;

-- Точка сохранения
SAVEPOINT sp1;

-- Откат к точке сохранения
ROLLBACK TO sp1;

-- Автоматическая фиксация (вкл/выкл)
SET AUTOCOMMIT = ON;
SET AUTOCOMMIT = OFF;
```

## Индексы

```sql
-- Простой индекс (ускоряет поиск по колонке)
CREATE INDEX idx_name ON users(name);


-- Индекс сразу по нескольким колонкам
CREATE INDEX idx_name_age ON users

-- Удалить индекс
DROP INDEX idx_name;
(name, age);
```
