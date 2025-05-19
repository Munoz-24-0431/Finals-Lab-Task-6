# [Finals Lab Task 6](https://github.com/user-attachments/files/20273938/MongoDB.Practice.Task-Munoz.docx) - MongoDB CRUD

## Project Description

This project demonstrates basic MongoDB CRUD operations using the `mongo` shell. The goal is to practice creating a database, inserting documents into collections, and executing queries including find, update, search, and delete. Additionally, relationships between collections are explored using embedded and referenced documents.

---

## Step-by-Step Process

### 1. Create a Database

Use the following command to create or switch to a MongoDB database named `mongo_practice`.

```js
use mongo_practice
```

---

### 2. Insert Documents

Create a `movies` collection and insert multiple documents with fields such as `title`, `writer`, `year`, `actors`, and `franchise`.

```js
db.movies.insert({
  title: "Fight Club",
  writer: "Chuck Palahniuk",
  year: 1999,
  actors: ["Brad Pitt", "Edward Norton"]
})
```

*Repeat for additional movies (e.g., "Pulp Fiction", "Inglorious Basterds", "The Hobbit" series, "Avatar")*

---

### 3. FIND Documents

#### a. Get all documents in `movies`:

```js
db.movies.find()
```

#### b. Filter by writer:

```js
db.movies.find({ writer: "Quentin Tarantino" })
```

#### c. Filter by actor:

```js
db.movies.find({ actors: "Brad Pitt" })
```

#### d. Filter by franchise:

```js
db.movies.find({ franchise: "The Hobbit" })
```

#### e. Released in the 1990s:

```js
db.movies.find({ year: { $gt: "1990", $lt: "2000" } })
```

---

### 4. UPDATE Documents

#### a. Add synopsis to "The Hobbit: An Unexpected Journey":

```js
db.movies.update(
  { title: "The Hobbit: An unexpected Journey" },
  { $set: { synopsis: "A reluctant hobbit, Bilbo Baggins..." } }
)
```

#### b. Add actor to "Pulp Fiction":

```js
db.movies.update(
  { title: "Pulp Fiction" },
  { $push: { actors: "Samuel L. Jackson" } }
)
```

---

### 5. SEARCH Documents

#### a. Search by word in synopsis:

```js
db.movies.find({ synopsis: /Bilbo/ })
```

#### b. Multiple search conditions:

```js
db.movies.find({ $and: [{ synopsis: /gold/ }, { synopsis: /dragon/ }] })
```

---

### 6. DELETE Documents

#### a. Delete movie by title:

```js
db.movies.remove({ title: "Avatar" })
```

---

### 7. Relationships

#### a. Insert into `users` collection:

```js
db.users.insert({ username: "GoodGuyGreg", first_name: "Good Guy", last_name: "Greg" })
```

#### b. Insert related `posts` and `comments` with reference to ObjectId of a post.

```js
db.comments.insert({
  username: "GoodGuyGreg",
  comment: "Hope you got a good deal!",
  post: ObjectId("POST_ID_HERE")
})
```

---

### 8. Querying Related Collections

```js
// All users
db.users.find().pretty()

// Posts by a user
db.posts.find({ username: "ScumbagSteve" })

// Comments on a specific post
db.comments.find({ post: ObjectId("POST_ID_HERE") })
```

---
### 9. Entity-Relationship (ER) Diagram

* **users**

  * `_id`
  * `username`
  * `first_name`
  * `last_name`

* **posts**

  * `_id`
  * `username` (FK → users.username)
  * `title`
  * `body`

* **comments**

  * `_id`
  * `username` (FK → users.username)
  * `comment`
  * `post` (FK → posts.\_id)
---
## Screenshots/Queries

## 1. Create a Database

![image](https://github.com/user-attachments/assets/9940ce55-55ab-4ef6-84f0-4fc0953074b4)

---

## 2. Insert Documents

![image](https://github.com/user-attachments/assets/80ae349b-f306-4fc2-b861-771550df3895)

---

## 3. FIND Documents**

![image](https://github.com/user-attachments/assets/00cf543d-bca6-41c4-ab14-f22133ce901f)

![image](https://github.com/user-attachments/assets/b0c8878d-3bd6-4ad2-9293-1fbc18dabc03)

![image](https://github.com/user-attachments/assets/93125b14-cde4-407e-bcc0-a67c642fec3d)

![image](https://github.com/user-attachments/assets/4cb76ea4-d863-4ae7-96bb-70d9b440c045)

![image](https://github.com/user-attachments/assets/8b61b09f-c4a7-4d00-afc8-6a76a31cb1ff)

![image](https://github.com/user-attachments/assets/3ca5db71-43bf-474a-9847-ac6b7ce27ff8)

---

## 4. UPDATE Documents

![image](https://github.com/user-attachments/assets/5d16bb71-047f-424a-b50a-f458f2f7ac75)

![image](https://github.com/user-attachments/assets/f62b2d6a-0518-462a-a013-e9d9add3a5b6)

![image](https://github.com/user-attachments/assets/ad78e0a2-29b8-4fbe-abbb-844b776f6d23)

---
## 5. SEARCH Documents

![image](https://github.com/user-attachments/assets/4fd883c4-0289-4d90-88ae-aeef7df26c70)

![image](https://github.com/user-attachments/assets/5d1f323d-05c9-407a-90ee-cc86b3ea855c)

![image](https://github.com/user-attachments/assets/92abbcbe-7da4-42a8-a911-48def492821b)

![image](https://github.com/user-attachments/assets/0faab109-178f-44bb-b1ec-c45da324be95)

![image](https://github.com/user-attachments/assets/0185dc4e-a8fa-41f0-a080-15baa87e6c62)

---
### 6. DELETE Documents

![image](https://github.com/user-attachments/assets/e7df5563-f931-438f-b319-8cd1b495277b)

![image](https://github.com/user-attachments/assets/f648d117-5fe6-4b3b-a574-fbb7964488c3)

---

## 7. Relationships

![image](https://github.com/user-attachments/assets/4cd94de0-63be-4a93-a263-7030cd8f3802)

![image](https://github.com/user-attachments/assets/5bcaf272-29a8-40dd-8422-73eb15e0d6b7)

![image](https://github.com/user-attachments/assets/950f0958-fc2e-4539-ba86-5a3c45b694e5)

---
## 8. Querying Related Collections

![image](https://github.com/user-attachments/assets/a1c66687-8559-4253-a5ef-9b00c6b12857)

![image](https://github.com/user-attachments/assets/6039b5e8-41c7-437d-a007-410a6336f3d7)

![image](https://github.com/user-attachments/assets/a9c2438b-4646-4006-8f3c-c863dd299011)

![image](https://github.com/user-attachments/assets/f7e3eeb6-c685-46cd-a052-f95526ab9b71)

![image](https://github.com/user-attachments/assets/255e0cd9-bb9e-49cd-987c-42ec3baa16eb)

![image](https://github.com/user-attachments/assets/6b9505cc-b2d2-43ea-bded-455619a4aa64)

![image](https://github.com/user-attachments/assets/d37a418a-7e89-451b-b91a-4f3c3969c503)

![image](https://github.com/user-attachments/assets/7b528658-21d2-4571-9903-6240a2dea30f)

---
## 9. Entity-Relationship (ER) Diagram

![image](https://github.com/user-attachments/assets/0bce4b7a-3217-416a-b8ab-5b0f6c06c1e1)



