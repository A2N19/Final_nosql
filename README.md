# 🏀 Sports Shop API

**Sports Shop API** is a RESTful API for an online sports store.  
It allows users to browse products, add them to a cart, and place orders.

## 🚀 Installation & Setup

### 1️⃣ Clone the Repository
```bash
git clone https://github.com/your-repository.git
cd sports-shop
```

### 2️⃣ Install Dependencies
```bash
npm install
```

### 3️⃣ Configure the `.env` File
Create a `.env` file in the root directory and add:
```env
PORT=3000
MONGO_URI=mongodb://localhost:27017/sportsShop
JWT_SECRET=your_secret_key
EMAIL_USER=your-email@gmail.com
EMAIL_PASS=your-app-password
```
🔹 Replace `your-email@gmail.com` and `your-app-password` with real credentials.

### 4️⃣ Start the Server
```bash
node server.js
```
💪 Now the API is running at `http://localhost:3000`

---

## 📂 Project Structure
```
/sports-shop
│── /models
│   ├── Cart.js
│   ├── Order.js
│   ├── Product.js
│   ├── User.js
│── /routes
│   ├── auth.js
│   ├── cart.js
│   ├── checkout.js
│   ├── products.js
│── /middleware
│   ├── authMiddleware.js
│── /config
│   ├── db.js
│── server.js
│── .env
│── package.json
│── README.md
```

---

## 📊 Database Structure

### 🌂 Collection: `products`
```json
{
  "_id": "65f1d567cde...",
  "name": "Adidas Football",
  "description": "Official World Cup ball",
  "price": 12000,
  "image": "ball.jpg"
}
```

### 🛒 Collection: `cart`
```json
{
  "_id": "65f2a3b9cde...",
  "userId": "65f2b123cde...",
  "products": [
    { "productId": "65f1d567cde...", "quantity": 2 }
  ]
}
```

### 📦 Collection: `orders`
```json
{
  "_id": "65f2a3b9cde...",
  "userId": "65f2b123cde...",
  "products": [
    { "productId": "65f1d567cde...", "quantity": 2 }
  ],
  "total": 24000,
  "status": "Paid"
}
```

---

## 👍 API Endpoints

### 🌐 Products (`/products`)
| Method | Endpoint          | Description       | Access |
|--------|------------------|------------------|--------|
| GET    | /products        | Get all products | Public |
| POST   | /products/add    | Add a new product | Admin |
| PUT    | /products/:id    | Update a product | Admin |
| DELETE | /products/:id    | Delete a product | Admin |

### 🛒 Cart (`/cart`)
| Method | Endpoint        | Description            | Access     |
|--------|----------------|------------------------|------------|
| GET    | /cart          | View user's cart       | Authorized |
| GET    | /cart/add/:id  | Add product to cart    | Authorized |
| GET    | /cart/update/:id/:q | Update product quantity | Authorized |
| GET    | /cart/remove/:id | Remove product from cart | Authorized |

### 📦 Checkout (`/checkout`)
| Method | Endpoint             | Description          | Access     |
|--------|----------------------|----------------------|------------|
| POST   | /checkout/confirm    | Place an order      | Authorized |
| GET    | /checkout/history    | View order history  | Authorized |
| PUT    | /checkout/update/:id | Update order status | Admin      |
| DELETE | /checkout/:id        | Delete an order     | Admin      |

---

## 🔒 Authentication (JWT)
For protected routes, add your JWT token in the Authorization header:
```bash
Authorization: Bearer <your_token>
```
To get a token:
- **Register via** `/auth/register`
- **Log in via** `/auth/login`
- Use the returned token for authentication.

---

## 📧 Email Notifications
Users receive an email confirmation after placing an order.  
Configured via **Gmail SMTP** (credentials in `.env`).

---

## 🛠 Technology Stack
- **Node.js + Express.js** – Backend Server
- **MongoDB + Mongoose** – Database
- **JWT + bcrypt** – Authentication
- **Nodemailer** – Email notifications
- **Postman** – API Testing

---

## 🌟 Project Features
✅ Full REST API with CRUD operations  
✅ JWT Authentication  
✅ Role-based Access Control (User/Admin)  
✅ Shopping Cart & Order Management  
✅ Email Order Confirmation  
✅ Secure Routes with Middleware  

---

## 🎯 Postman Testing
Example **POST** `/products/add`
1. Open Postman
2. Add Authorization Header: `Bearer <TOKEN>`
3. In **Body (JSON):**
```json
{
  "name": "Nike Sneakers",
  "description": "Lightweight and comfortable",
  "price": 25000,
  "image": "nike.jpg"
}
```
4. Click **Send** ✅

---

## 🤝 Contributors
- **Amir Nurseit**  
- **Amir Nurseit and Arlan Mirseiit**  

---

## 📜 License
This project is licensed under the **AITU License**.
