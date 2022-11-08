# blogAPI
## Overview
This api has a general endpoint that shows a list of articles that have been created by different people, and anybody
that calls this endpoint, should be able to read a blog created
by them or other users.

Requirements:
___
1. Users should have a first_name, last_name, email, password, (you can add other attributes you want to store about the user)
2. A user should be able to sign up and sign in into the blog app
3. Use JWT as authentication strategy and expire the token after 1 hour
4. A blog can be in two states; draft and published
5. Logged in and not logged in users should be able to get a list of published blogs created
6. Logged in and not logged in users should be able to get a published blog
7. Logged in users should be able to create a blog.
8. When a blog is created, it is in draft state
9. The owner of the blog should be able to update the state of the blog to published
10. The owner of a blog should be able to edit the blog in draft or published state
11. The owner of the blog should be able to delete the blog in draft or published state

12. The owner of the blog should be able to get a list of their blogs.
- The endpoint should be paginated
- It should be filterable by state
13. Blogs created should have title, description, tags, author, timestamp, state, read_count, reading_time and body.
14. The list of blogs endpoint that can be accessed by both logged in and not logged in users should be paginated,
- default it to 20 blogs per page.

- It should also be searchable by author, title and tags.
- It should also be orderable by read_count, reading_time and timestamp
15. When a single blog is requested, the api should return the user information with the blog. The read_count of the blog too should be updated by 1
16. Come up with any algorithm for calculating the reading_time of the blog.

Note:
The owner of the blog should be logged in to perform actions.

Use the MVC pattern

Database
- Use MongoDB

Data Models

___
User
- email is required and should be unique
- first_name and last_name is required
- password

Blog/Article
- title is required and unique
- description
- author
- state
- read_count
- reading_time
- tags
- body is required
- timestamp


### Installation
------

To run this project,

1. fork this repo
2. clone the repo to your local machine
3. Open th folder in your favourite text editor
4. cd into the directory where the project is located.
5. install it locally using npm:

`$ npm install`

```
node index.js or nodemon index.js
```

### THE ENDPOINTS
-------


| S.no   | route            | Method |  Access       | Description  |
| :---   |    :----        | ---:   |   :---:        |   :---        |
| 1      | "/signup"        | POST   | PRIVATE       |     create a new user      |
| 2      | "/login"         | POST   | PRIVATE       |      log in to the app   |
| 3      | "/blogs"         | POST   | PRIVATE       |  post a new Blog           |
| 4      | "/blogs"         | GET    | PUBLIC        |    get all published blogs on the app   |
| 5      | "/blogs/published"| GET   | PRIVATE       |   get published Blogs by current user   |
| 6      | "/blogs/draft    | GET    | PRIVATE       |  get all blogs in draft for current user  |
| 7      | "/blogs/:id      | GET    | PUBLIC        |  get Blog By Id |
| 8      | "/blogs/:id"     | DELETE | PRIVATE       |  delete Blog By Id     |
| 9      | "/blogs/user/articles"| GET |PRIVATE      |  get All Blogs By current user   |
| 10     | "/blogs/update/:id| PATCH | PRIVATE       | update Blog By Id
| 11     | "/blogs/tags/:tags"| GET   | PRIVATE      |   get Blogs by Tags    |
| 12     | "/blogs/title/:title"| GET| PRIVATE       |      get blogs by Title |


### Here is a guide to using the application.
-----

- [x] create a new user 
```json
{
  "firstname": "Mary",
  "lastname": "Martha",
  "username": "user3",
  "email": "user3@sample.com,
  "password": "abcdefghi"
}
```
- [x] Log into the application

```json
{
  "username": "user3",
  "password": "myverystrongpassword"
}
```

- [x] Post a new blog

```json
{
    title: "A new day",
    "description": "A blog app",
    "body": "lorem ipsum lorem ipsum lorem ipsum, lorem ipsum lorem ipsum lorem ipsum lorem ipsum lorem ipsum lorem ipsum lorem ipsum lorem ipsum lorem ipsum lorem ipsum lorem ipsum lorem ipsum lorem ipsum lorem ipsum lorem ipsum lorem ipsum lorem ipsum lorem ipsumlorem ipsum lorem ipsum lorem ipsum lorem ipsum lorem ipsum lorem ipsum lorem ipsum lorem ipsum lorem ipsumlorem ipsum lorem ipsum lorem ipsum lorem ipsum lorem ipsum lorem ipsum lorem ipsum lorem ipsum lorem ipsum",
    tags: ["cars", "fruits", "vegs"]
 }
```
    
- [x] Update the state of the blog to published

```json
{
  "state": "published"
}
```
Explore the rest of the endpoints
