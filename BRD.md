# Business Requirements Document (BRD)
## E-Commerce Application

### 1. Project Goal
To build a simple, functional e-commerce web application that allows customers to browse and purchase products, and allows administrators to manage the product catalog and customer orders.

### 2. Users
- **Customer:** A shopper who visits the website to browse and purchase products.
- **Admin:** A store owner or manager who manages products, categories, and fulfills orders.

### 3. Features In Scope

#### Customer Features
- Register for a new account
- Login to an existing account
- Browse products
- Search for products
- View product details
- Add a product to the cart
- Change the quantity of a product in the cart
- Remove a product from the cart
- Checkout
- Place an order
- View order history

#### Admin Features
- Login to the admin dashboard
- Add, edit, and delete products
- Add, edit, and delete categories
- View customer orders
- Update order status

### 4. Main User Journeys

#### Customer Journey
1. Customer visits the website and creates an account (Registers) or Logs in.
2. Customer browses or searches for a product.
3. Customer clicks on a product to view its details.
4. Customer adds the product to their shopping cart.
5. Customer proceeds to checkout and places the order.
6. Customer can later view their placed order in their order history.

#### Admin Journey
1. Admin logs into the admin portal.
2. Admin creates a new product category.
3. Admin adds a new product and assigns it to a category.
4. Admin reviews a list of recent customer orders.
5. Admin updates the status of an order (e.g., to indicate it was shipped).

### 5. Out of Scope
- Real payment gateway integration (e.g., Stripe, PayPal - checkout will be simulated)
- Email notifications and SMS alerts
- Product reviews, ratings, or wishlists
- Discount codes and coupons
- Guest checkout (users must register/login to buy)
- Complex shipping and tax calculations

### 6. Success Criteria
- A customer can successfully register, find a product, add it to their cart, and place an order without any errors.
- An admin can successfully add a product to the catalog, and it becomes immediately visible to customers.
- An admin can successfully view and update the status of a customer's order.
- The ReactJS frontend, FastAPI backend, and PostgreSQL database communicate with each other seamlessly.
