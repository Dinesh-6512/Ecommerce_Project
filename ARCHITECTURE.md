# Architecture Document
## E-Commerce Application

### 1. Technology Flow
The application follows a simple 3-tier architecture:

**ReactJS Frontend (User Interface)**
        ↓ (Sends API Requests)
**FastAPI Backend (Python Logic)**
        ↓ (Executes SQL Queries)
**PostgreSQL Database (Data Storage)**

### 2. Logic Separation

- **Authentication Logic:** Handled by the FastAPI Backend. It checks passwords and creates secure access tokens. The ReactJS Frontend receives the token and sends it along with future requests to prove who the user is.
- **Product Logic:** Handled by the FastAPI Backend. It asks the PostgreSQL database for product data and sends it back to the ReactJS Frontend to be displayed.
- **Cart Logic:** Mostly handled by the ReactJS Frontend for a fast experience while browsing. The items are remembered in the browser until the user is ready to pay.
- **Checkout/Order Logic:** Handled by the FastAPI Backend. It receives the final cart from ReactJS, calculates totals, and saves the official order into PostgreSQL.
- **Database Access:** ONLY the FastAPI Backend talks to the PostgreSQL Database. The ReactJS Frontend NEVER connects directly to the database.

### 3. Application Flows

#### Customer Flow
1. **ReactJS:** Customer browses products and adds them to the cart.
2. **ReactJS -> FastAPI:** Customer clicks checkout. ReactJS sends the cart items and shipping info to FastAPI.
3. **FastAPI -> PostgreSQL:** FastAPI verifies the data and saves the new order in the database.
4. **FastAPI -> ReactJS:** FastAPI sends a "Success" message back.
5. **ReactJS:** Customer sees the Order Confirmation screen.

#### Admin Flow
1. **ReactJS:** Admin logs in and opens the Admin Dashboard.
2. **ReactJS -> FastAPI:** Admin fills out a "New Product" form and clicks save. ReactJS sends the product details to FastAPI.
3. **FastAPI -> PostgreSQL:** FastAPI verifies the admin is authorized and saves the new product in the database.
4. **FastAPI -> ReactJS:** FastAPI replies with a "Product Added" message.
5. **ReactJS:** Admin sees the updated product list.

### 4. Required API Areas

To allow the Frontend and Backend to communicate, FastAPI will provide the following API endpoints:

**Register and Login**
- `POST /api/register` - Create a new user account
- `POST /api/login` - Verify password and login

**Profile**
- `GET /api/profile` - Get logged-in user's details

**Products & Categories (Public)**
- `GET /api/products` - List all products
- `GET /api/products/{id}` - Get details of one product
- `GET /api/categories` - List all categories

**Cart & Checkout**
- `POST /api/checkout` - Submit cart items and create an order

**Orders (Customer)**
- `GET /api/orders` - View past orders for the logged-in customer

**Admin Actions (Requires Admin Access)**
- `POST /api/admin/products` - Add a new product
- `PUT /api/admin/products/{id}` - Edit a product
- `DELETE /api/admin/products/{id}` - Delete a product
- `POST /api/admin/categories` - Add a new category
- `PUT /api/admin/categories/{id}` - Edit a category
- `DELETE /api/admin/categories/{id}` - Delete a category
- `GET /api/admin/orders` - View all customer orders
- `PUT /api/admin/orders/{id}/status` - Update an order's status
