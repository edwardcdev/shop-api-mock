# Shop API Mockup

## Specification

- Nodejs
- PostgreSQL
- Sequelize
- Redis
- Docker

## Features

- Users can
  - Sign in
  - Add products to carts
  - Remove products from carts
  - view carts
- Admin can
  - Sign in
  - manage products (add, remove, edit, view)

## Running
- run api
  ```
  cd api
  npm install
  ```
- create a `.env` file with this template

  ```
  DATABASE_URL = 'Your postgres database url'
  DATABASE_URL_TEST = 'Your postgres test database url'
  DATABASE_URL_DEVELOPMENT = 'Your postgres database url'
  PORT = 'Your local port'
  SECRET = 'Your secret phrase'
  CLOUD_NAME = 'Your cloudinary cloud name'
  CLOUDINARY_API_KEY = 'cloudinary api key'
  CLOUDINARY_API_SECRET = 'cloudinary api secret'
  ```

- run migrations and seeding

  ```
  sequelize db:migrate
  ```

  ```
  sequelize db:seed:all
  ```

- start app
  ```
  npm run start:dev
  ```
- api is under this URL `localhost:3000/api/v1/`

- run test
  ```
  npm run test
  ```

## API endpoints

| Endpoints                         | Functionality               |
| --------------------------------- | --------------------------- |
| POST /auth/create-user            | Create new user account     |
| POST /auth/signin                 | Login a user                |
| POST /products                    | Create a product            |
| POST /carts                       | Add products to a cart      |
| PATCH /products/:productId        | Edit a product              |
| PATCH /products/:productId/upload | Update a product with image |
| DELETE /carts/:productId          | Remove a product from cart  |
| DELETE /products/:productId       | Delete a specific product   |
| GET /carts/                       | View cart                   |
| GET /products/                    | View all products           |

- create a new user
`POST` request to `/api/v1/auth/create-user`

```json
{
  "firstName": "Sensei",
  "lastName": "Saitama",
  "email": "saitama@mail.com",
  "password": "password",
  "isAdmin": "true"
}
```
- sign in 
`POST` request to `/api/v1/auth/signin`

```json
{
	"email": ,
	"password":
}
```
- create a new product
`POST` request to `/api/v1/products`

```json
{
  "name": "bread",
  "description": "food",
  "category": "Bromate free",
  "price": 350,
  "inStock": true
}
```
- update a product with an image
`PATCH` request in a multipart form to `/api/v1/products/:productId/upload`
```json
{ 
  ...
  "image": picture file
  ...
}
```
