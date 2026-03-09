# goit-rdb-hw-04

Код до 1 та 2 завдання:

CREATE SCHEMA IF NOT EXISTS LibraryManagement;
USE LibraryManagement;

CREATE TABLE IF NOT EXISTS authors (
  author_id INT AUTO_INCREMENT PRIMARY KEY,
  author_name VARCHAR(255) NOT NULL
);

INSERT INTO authors (author_name)
VALUES ('Ivan Petrenko'), ('Oksana Kovalenko');

CREATE TABLE IF NOT EXISTS genres (
  genre_id INT AUTO_INCREMENT PRIMARY KEY,
  genre_name VARCHAR(100) NOT NULL
);

INSERT INTO genres (genre_name)
VALUES ('Roman'), ('Pryhody');

CREATE TABLE IF NOT EXISTS books (
  book_id INT AUTO_INCREMENT PRIMARY KEY,
  title VARCHAR(255) NOT NULL,
  publication_year YEAR,
  author_id INT NOT NULL,
  genre_id INT NOT NULL,
  CONSTRAINT fk_books_authors
    FOREIGN KEY (author_id) REFERENCES authors(author_id),
  CONSTRAINT fk_books_genres
    FOREIGN KEY (genre_id) REFERENCES genres(genre_id)
);

INSERT INTO books (title, publication_year, author_id, genre_id)
VALUES ('Tayemnytsia mista', 2018, 1, 1),
       ('Podorozh u gory', 2020, 2, 2);

CREATE TABLE IF NOT EXISTS users (
  user_id INT AUTO_INCREMENT PRIMARY KEY,
  username VARCHAR(100) NOT NULL,
  email VARCHAR(255) NOT NULL
);

INSERT INTO users (username, email)
VALUES ('dmytro', 'dmytro@gmail.com'), ('olena', 'olena@gmail.com');

CREATE TABLE IF NOT EXISTS borrowed_books (
  borrow_id INT AUTO_INCREMENT PRIMARY KEY,
  book_id INT NOT NULL,
  user_id INT NOT NULL,
  borrow_date DATE NOT NULL,
  return_date DATE,
  CONSTRAINT fk_borrowed_books_books
    FOREIGN KEY (book_id) REFERENCES books(book_id),
  CONSTRAINT fk_borrowed_books_users
    FOREIGN KEY (user_id) REFERENCES users(user_id)
);

INSERT INTO borrowed_books (book_id, user_id, borrow_date, return_date)
VALUES (1, 1, '2026-01-10', NULL),
       (2, 2, '2026-01-15', '2026-01-25');

2.1
<img width="1919" height="1035" alt="task 2 1" src="https://github.com/user-attachments/assets/79dbdac5-a30a-4759-ab92-1347b19815d5" />
2.2
<img width="1919" height="1029" alt="task 2 2" src="https://github.com/user-attachments/assets/621b718f-ff9e-4d8c-843d-6d63f5a36590" />
2.3
<img width="1919" height="1028" alt="task 2 3" src="https://github.com/user-attachments/assets/0744747d-dfcd-4fd0-8a11-a956768392a3" />
2.4
<img width="1919" height="1034" alt="task 2 4" src="https://github.com/user-attachments/assets/42ed8b08-a3f7-46d5-b465-d149c9cfdb37" />
2.5
<img width="1919" height="1025" alt="task 2 5" src="https://github.com/user-attachments/assets/e39cc2ef-9ca7-48c9-97d9-28af686f09f1" />
3
<img width="1919" height="1035" alt="task 3" src="https://github.com/user-attachments/assets/ba98a5ef-112e-4ab3-b933-429301338800" />
4.1
<img width="1919" height="1029" alt="task 4 1" src="https://github.com/user-attachments/assets/3904705e-697f-47fd-b85f-2be5ecf937d3" />
Після заміни деяких INNER JOIN на LEFT JOIN кількість рядків не змінилася. 
У обох випадках результат становить 518 рядків.

Це означає, що для кожного запису в таблиці order_details існують відповідні записи в інших таблицях. 
INNER JOIN повертає лише ті рядки, де є відповідність у всіх таблицях, а LEFT JOIN повертає всі рядки з лівої таблиці.

Оскільки в базі даних усі записи мають відповідності, LEFT JOIN не додав нових рядків і результат залишився таким самим.
4.2
<img width="1917" height="1029" alt="task 4 2" src="https://github.com/user-attachments/assets/9e943fd5-6bbd-4aca-a947-7dce50f51a95" />
4.3
<img width="1919" height="1033" alt="task 4 3" src="https://github.com/user-attachments/assets/13adf364-c863-41b2-aa5b-33e038d0aabc" />
4.4-7
<img width="1919" height="1030" alt="task 4 4-7" src="https://github.com/user-attachments/assets/7a81f2fd-d837-4899-8667-16c294ff8edf" />
