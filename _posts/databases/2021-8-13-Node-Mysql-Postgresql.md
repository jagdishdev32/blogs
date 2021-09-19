---
categories: [node, postgresql, sql, mysql]
tags: [node, mysql, postgresql, docker, database, notes]
---

# MySQL / PostgreSQL with Nodejs

{% raw %}

## Prerequisites

- MySQL database
- Phpmyadmin (Optional)
- Postgresql (Optional)

### Installing Prerequisites with docker

```bash
# Running mysql docker container
docker run --name mysql \
  -p 8080:3306 \
  -e MYSQL_ROOT_PASSWORD=secret \
  -d mysql

# (Optional) Running phpmyadmin server for mysql
docker run --name phpmyadmin \
  -d --link mysql:db \
  -p 8081:80 \
  phpmyadmin/phpmyadmin

# # (Optional) Running postgresql with docker
docker run --name \
  postgres -p 8081:5432 \
  -e POSTGRES_PASSWORD=secret \
  -d postgres

```

## Installation

```bash
npm init -y
npm install express
# npm install mysql
npm install mysql2 # mysql may give auth error

# For Postgresql
npm install pg
```

## Initialization

```js
const express = require("express");

// For MySQL
const mysql = require("mysql2");
const db = mysql.createConnection({
  host: "localhost",
  port: "8080", // Default is 3306
  user: "root", // Use other user than root for security
  password: "secret", // User password

  // If connecting to existing database
  // If not create it first then connect to it.
  database: "myappdb",
});

// // For Postgresql
// const Pool = require("pg").Pool;
// const db = new Pool({
//   host: "localhost",
//   port: "8081",
//   user: "postgres", // Use other user than root for security
//   password: "secret", // User password

//   // If connecting to existing database
//   // If not create it first then connect to it.
//   database: "myappdb",
// });

db.connect((err) => {
  if (err) {
    throw error;
  }
  console.log("Connecting with DB");
});

app.get("/", (req, res) => {
  res.send("Welcome to HomePage!");
});

app.listen(3000, () => {
  console.log("App running at port 3000");
});
```

## Basic Working

Basic/Universal/Syntax

```js
db.query(QUERY, (error, result) => {
  if (error) throw error;
  console.log(result);
});
```

## Creating database

Creating database in mysql with nodejs

```js
app.get("/createDatabase", (req, res) => {
  let sql = `CREATE DATABASE myappdb`;
  let query = db.query((err, result) => {
    if (err) throw err; // Not a best pratice
    console.log(result);
    res.send("Database myappdb Created");
  });
});
```

**Before Moving Forward Connect with the database if new database is created**

## Creating Table

Creating Table inside database

```js
app.get("/createtable", (req, res) => {
  let sql =
    "CREATE TABLE posts(id int AUTO_INCREMENT, title VARCHAR(255), body VARCHAR(255), PRIMARY KEY(id))";
  let query = db.query((err, result) => {
    if (err) throw err; // Not a best pratice
    console.log(result);
    res.send("Database myappdb Created");
  });
});
```

## CRUD - CREATE READ UPDATE DELETE IN TABLE

Inserting, Reading, Updating, Deleting data in/from table

```js
// Insert post 1
app.get("/addpost:num", (req, res) => {
  let { num } = req.params;
  let post = { title: "Post " + num, body: "This is post number " + num };
  let sql = "INSERT INTO posts SET ?";
  let query = db.query(sql, post, (err, result) => {
    if (err) throw err;
    console.log(result);
    res.send(`Posts added num:${num}`);
  });
});

// Select posts
app.get("/getposts", (req, res) => {
  let sql = "SELECT * FROM posts";

  let query = db.query(sql, (err, result) => {
    if (err) throw err;
    console.log(result);
    res.send(result);
  });
});

// Select single post
app.get("/getpost/:id", (req, res) => {
  let { id } = req.params;
  let sql = `SELECT * FROM posts WHERE id=${id}`;
  let query = db.query(sql, (err, result) => {
    if (err) throw err;
    console.log(result);
    res.send(result);
  });
});

// Update post
app.get("/updatepost/:id", (req, res) => {
  let { id } = req.params;
  let newTitle = "New Title";
  let sql = `UPDATE posts SET title='${newTitle}' WHERE id=${id}`;
  let query = db.query(sql, (err, result) => {
    if (err) throw err;
    // console.log(result);
    // res.send(result);
    res.send("Post Updated...");
  });
});

// Delete post
app.get("/deletepost/:id", (req, res) => {
  let { id } = req.params;
  let newTitle = "New Title";
  let sql = `DELETE FROM posts WHERE id=${id}`;
  let query = db.query(sql, (err, result) => {
    if (err) throw err;
    // console.log(result);
    // res.send(result);
    res.send("Post deleted...");
  });
});
```

{% endraw %}
