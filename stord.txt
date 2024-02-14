Enter password: **************
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 10
Server version: 8.0.19 MySQL Community Server - GPL

Copyright (c) 2000, 2020, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> SHOW databases;
+--------------------+
| Database           |
+--------------------+
| centre_formation   |
| centreformation    |
| company_management |
| information_schema |
| mysql              |
| performance_schema |
| players            |
| sakila             |
| sys                |
| test2              |
| world              |
+--------------------+
11 rows in set (0.04 sec)

mysql> create database company;
Query OK, 1 row affected (0.01 sec)

mysql> use company;
Database changed
mysql> CREATE TABLE clients (
    ->     id_client INT PRIMARY KEY,
    ->     nom VARCHAR(255),
    ->     prenom VARCHAR(255),
    ->     email VARCHAR(255),
    ->     adresse VARCHAR(255),
    ->     telephone VARCHAR(15)
    -> );
Query OK, 0 rows affected (0.06 sec)

mysql> show tables;
+-------------------+
| Tables_in_company |
+-------------------+
| clients           |
+-------------------+
1 row in set (0.00 sec)

mysql> desc clients;
+-----------+--------------+------+-----+---------+-------+
| Field     | Type         | Null | Key | Default | Extra |
+-----------+--------------+------+-----+---------+-------+
| id_client | int          | NO   | PRI | NULL    |       |
| nom       | varchar(255) | YES  |     | NULL    |       |
| prenom    | varchar(255) | YES  |     | NULL    |       |
| email     | varchar(255) | YES  |     | NULL    |       |
| adresse   | varchar(255) | YES  |     | NULL    |       |
| telephone | varchar(15)  | YES  |     | NULL    |       |
+-----------+--------------+------+-----+---------+-------+
6 rows in set (0.01 sec)

mysql> CREATE TABLE produits (
    ->     id_produit INT PRIMARY KEY,
    ->     nom VARCHAR(255),
    ->     description TEXT,
    ->     prix DECIMAL(10, 2),
    ->     stock INT
    -> );
Query OK, 0 rows affected (0.04 sec)

mysql> show tables;
+-------------------+
| Tables_in_company |
+-------------------+
| clients           |
| produits          |
+-------------------+
2 rows in set (0.00 sec)

mysql> desc produits;
+-------------+---------------+------+-----+---------+-------+
| Field       | Type          | Null | Key | Default | Extra |
+-------------+---------------+------+-----+---------+-------+
| id_produit  | int           | NO   | PRI | NULL    |       |
| nom         | varchar(255)  | YES  |     | NULL    |       |
| description | text          | YES  |     | NULL    |       |
| prix        | decimal(10,2) | YES  |     | NULL    |       |
| stock       | int           | YES  |     | NULL    |       |
+-------------+---------------+------+-----+---------+-------+
5 rows in set (0.01 sec)

mysql> CREATE TABLE commandes (
    ->     id_commande INT PRIMARY KEY,
    ->     id_client INT,
    ->     date_commande DATE,
    ->     statut VARCHAR(20) DEFAULT 'en cours',
    ->     total DECIMAL(10, 2),
    ->     FOREIGN KEY (id_client) REFERENCES clients(id_client),
    ->     CHECK (statut IN ('en cours', 'livrée', 'annulée'))
    -> );
Query OK, 0 rows affected (0.07 sec)

mysql> show tables;
+-------------------+
| Tables_in_company |
+-------------------+
| clients           |
| commandes         |
| produits          |
+-------------------+
3 rows in set (0.00 sec)

mysql> desc commandes;
+---------------+---------------+------+-----+----------+-------+
| Field         | Type          | Null | Key | Default  | Extra |
+---------------+---------------+------+-----+----------+-------+
| id_commande   | int           | NO   | PRI | NULL     |       |
| id_client     | int           | YES  | MUL | NULL     |       |
| date_commande | date          | YES  |     | NULL     |       |
| statut        | varchar(20)   | YES  |     | en cours |       |
| total         | decimal(10,2) | YES  |     | NULL     |       |
+---------------+---------------+------+-----+----------+-------+
5 rows in set (0.00 sec)

mysql>