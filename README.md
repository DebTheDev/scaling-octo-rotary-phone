# Node, Express, and PostgreSQL: Assignment

This starter code is intended to be run for the Node.js, Express, & PostgreSQL module in the Thinkful curriculum.

## Instructions

You are a backend developer at a blogging platform called "Blogful", and you've been tasked to create an API that returns data about the users, comments, and posts stored in their database. Their backend technology stack is currently Node.js/Express, PostgreSQL, and Knex. You are given the following ERD:

| Folder/file path                 | Description                                                                                                           |
| -------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| `src/app.js`                     | Directs requests to the appropriate routers.                                                                          |
| `src/server.js`                  | Starts the server on `localhost:5000` by default.                                                                     |
| `src/comments/`                  | A folder that contains the `comments.controller.js` and `comments.router.js` files for the `comments` resource.       |
| `src/posts/`                | A folder that contains the `posts.controller.js` and `posts.router.js` files for the `posts` resource. |
| `src/users/`                 | A folder that contains the `users.controller.js` and `users.router.js` files for the `users` resource.    |
| `src/db/`                        | A folder where you will add migration and seed files for your database later on.                                      |
| `src/db/migrations`                | A folder containing sample data you will seed your database with later on.                                            |
| `src/errors/` | An error handler for forbidden request methods                                                                        |


In the `*.controller.js` files, the route handlers return hard-coded data for now, but later on, you will modify the controllers to manipulate and return data from a PostgreSQL database.

This starter code closely follows the best practices and patterns established in the Robust Server Structure module.


Blogful Routes
GET /comments
should return a list of all comments by default
should return the comment count, grouped by commenter_email, for the path `/comments/commenter-count`
GET /comments/:commentId
should return a 404 if the ID given does not match any ID in the database
should include specified columns from comments, users, and posts
POST /posts
should create a new post
PUT /posts/:postId
should update a post
DELETE /posts/:postId
should delete the post record with the given ID

## Database setup

1. Set up a new ElephantSQL database instance by following the instructions in the "PostgreSQL: Creating & Deleting Databases" checkpoint.
1. After setting up your database instance, connect DBeaver to your new database instance by following the instructions in the "PostgreSQL: Installing DBeaver" checkpoint.

## Installation

1. Fork and clone this repository.
1. Run `cp .env.sample .env`.
1. Update your `.env` file with a connection URL to your ElephantSQL database instance.
1. Run `npm install` to install project dependencies.
1. Run `npm run start:dev` to start your server in development mode.
1. In your browser or Postman, navigate to `localhost:5000/comments`. If your server is running properly, you should get back the following json response:

```json
{
  "data": [
    {
      "comment_id": 1,
      "commenter_id": 3,
      "post_id": 96,
      "comment": "Morbi quis tortor id nulla ultrices aliquet. Maecenas leo odio, condimentum id, luctus nec, molestie sed, justo.",
      "created_at": "2021-04-14T21:18:59.675Z",
      "updated_at": "2021-04-14T21:18:59.675Z"
    },
    {
      "comment_id": 2,
      "commenter_id": 1,
      "post_id": 89,
      "comment": "Integer a nibh. In quis justo. Maecenas rhoncus aliquam lacus. Morbi quis tortor id nulla ultrices aliquet.",
      "created_at": "2021-04-14T21:18:59.675Z",
      "updated_at": "2021-04-14T21:18:59.675Z"
    },
    {
      "comment_id": 3,
      "commenter_id": 3,
      "post_id": 2,
      "comment": "Mauris lacinia sapien quis libero. Nullam sit amet turpis elementum ligula vehicula consequat. Morbi a ipsum. Integer a nibh. In quis justo.",
      "created_at": "2021-04-14T21:18:59.675Z",
      "updated_at": "2021-04-14T21:18:59.675Z"
    },
    {
      "comment_id": 4,
      "commenter_id": 2,
      "post_id": 4,
      "comment": "Duis consequat dui nec nisi volutpat eleifend. Donec ut dolor.",
      "created_at": "2021-04-14T21:18:59.675Z",
      "updated_at": "2021-04-14T21:18:59.675Z"
    },
    {
      "comment_id": 5,
      "commenter_id": 1,
      "post_id": 14,
      "comment": "Morbi non quam nec dui luctus rutrum. Nulla tellus. In sagittis dui vel nisl. Duis ac nibh.",
      "created_at": "2021-04-14T21:18:59.675Z",
      "updated_at": "2021-04-14T21:18:59.675Z"
    },
    {
      "comment_id": 6,
      "commenter_id": 5,
      "post_id": 33,
      "comment": "Duis consequat dui nec nisi volutpat eleifend. Donec ut dolor. Morbi vel lectus in quam fringilla rhoncus. Mauris enim leo, rhoncus sed, vestibulum sit amet, cursus id, turpis.",
      "created_at": "2021-04-14T21:18:59.675Z",
      "updated_at": "2021-04-14T21:18:59.675Z"
    },
    {
      "comment_id": 7,
      "commenter_id": 5,
      "post_id": 79,
      "comment": "Phasellus in felis. Donec semper sapien a libero. Nam dui. Proin leo odio, porttitor id, consequat in, consequat ut, nulla.",
      "created_at": "2021-04-14T21:18:59.675Z",
      "updated_at": "2021-04-14T21:18:59.675Z"
    },
    ......
```


