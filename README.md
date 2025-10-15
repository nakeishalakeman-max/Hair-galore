# Hair-galore
100% human hair 
/* Reset & basic styles */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Arial', sans-serif;
}

body {
    background: #fff0f5; /* light pink background */
    color: #333;
    line-height: 1.6;
}

a {
    text-decoration: none;
    color: inherit;
}

/* Header & Navigation */
header {
    background: #d16ba5; /* pink/purple gradient */
    color: white;
    padding: 20px 50px;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

header h1 {
    font-family: 'Georgia', serif;
}

nav a {
    margin: 0 15px;
    font-weight: bold;
    color: white;
}

nav a:hover {
    text-decoration: underline;
}

/* Hero Section */
.hero {
    background: linear-gradient(to right, #ffb6c1, #d16ba5);
    color: white;
    text-align: center;
    padding: 100px 20px;
}

.hero h2 {
    font-size: 3em;
    margin-bottom: 20px;
}

.hero button {
    padding: 10px 25px;
    font-size: 1.2em;
    border: none;
    border-radius: 5px;
    background: white;
    color: #d16ba5;
    cursor: pointer;
}

.hero button:hover {
    background: #f0c0d5;
}

/* Pages Layout */
.container {
    max-width: 1200px;
    margin: 40px auto;
    padding: 0 20px;
}

/* Shop Page */
.products {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
    gap: 30px;
}

.product-card {
    background: white;
    border-radius: 10px;
    padding: 15px;
    text-align: center;
    box-shadow: 0 2px 8px rgba(0,0,0,0.1);
}

.product-card img {
    width: 100%;
    border-radius: 10px;
}

.product-card button {
    margin-top: 10px;
    padding: 8px 15px;
    border: none;
    background: #d16ba5;
    color: white;
    border-radius: 5px;
    cursor: pointer;
}

.product-card button:hover {
    background: #ffb6c1;
}

/* Cart */
#cart {
    position: fixed;
    top: 100px;
    right: 20px;
    width: 300px;
    background: white;
    border: 2px solid #d16ba5;
    border-radius: 10px;
    padding: 15px;
    display: none;
    z-index: 1000;
}

#cart h3 {
    margin-bottom: 10px;
}

.cart-item {
    display: flex;
    justify-content: space-between;
    margin-bottom: 8px;
}

/* Contact Page */
form {
    display: flex;
    flex-direction: column;
}

form input, form textarea {
    padding: 10px;
    margin-bottom: 15px;
    border-radius: 5px;
    border: 1px solid #ccc;
}

form button {
    padding: 10px;
    background: #d16ba5;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

form button:hover {
    background: #ffb6c1;
}

/* Footer */
footer {
    background: #d16ba5;
    color: white;
    text-align: center;
    padding: 20px;
    margin-top: 50px;
}
// Load cart from localStorage or initialize empty
let cart = JSON.parse(localStorage.getItem('hairGaloreCart')) || [];

// Update cart display on page load
document.addEventListener('DOMContentLoaded', updateCart);

function addToCart(name, price) {
    cart.push({name, price});
    saveCart();
    updateCart();
}

function removeFromCart(index) {
    cart.splice(index, 1);
    saveCart();
    updateCart();
}

function saveCart() {
    localStorage.setItem('hairGaloreCart', JSON.stringify(cart));
}

function updateCart() {
    const cartEl = document.getElementById('cart');
    if (!cartEl) return;

    cartEl.innerHTML = '<h3>Shopping Cart</h3>';

    if (cart.length === 0) {
        cartEl.innerHTML += '<p>Your cart is empty</p>';
    } else {
        let total = 0;
        cart.forEach((item, index) => {
            total += item.price;
            cartEl.innerHTML += `
                <div class="cart-item">
                    ${item.name} - $${item.price.toFixed(2)} 
                    <button onclick="removeFromCart(${index})">x</button>
                </div>`;
        });
        cartEl.innerHTML += `<hr><p>Total: $${total.toFixed(2)}</p>`;
        cartEl.innerHTML += '<button onclick="checkout()">Checkout</button>';
    }

    cartEl.style.display = 'block';
}

function checkout() {
    alert('Thank you for your purchase!');
    cart = [];
    saveCart();
    updateCart();
}
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Hair Galore</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <h1>Hair Galore</h1>
        <nav>
            <a href="index.html">Home</a>
            <a href="about.html">About</a>
            <a href="shop.html">Shop</a>
            <a href="contact.html">Contact</a>
        </nav>
    </header>

    <section class="hero">
        <h2>Welcome to Hair Galore</h2>
        <p>Your one-stop shop for gorgeous hair extensions!</p>
        <button onclick="location.href='shop.html'">Shop Now</button>
    </section>

    <section class="container">
        <h2>Featured Products</h2>
        <div class="products">
            <div class="product-card">
                <img src="images/product1.jpg" alt="Hair Product">
                <h3>Beautiful Hair 1</h3>
                <p>$49.99</p>
                <button onclick="addToCart('Beautiful Hair 1', 49.99)">Add to Cart</button>
            </div>
            <div class="product-card">
                <img src="images/product2.jpg" alt="Hair Product">
                <h3>Beautiful Hair 2</h3>
                <p>$59.99</p>
                <button onclick="addToCart('Beautiful Hair 2', 59.99)">Add to Cart</button>
            </div>
        </div>
    </section>

    <div id="cart"></div>

    <footer>
        <p>&copy; 2025 Hair Galore</p>
    </footer>

    <script src="script.js"></script>
</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>About - Hair Galore</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <h1>Hair Galore</h1>
        <nav>
            <a href="index.html">Home</a>
            <a href="about.html">About</a>
            <a href="shop.html">Shop</a>
            <a href="contact.html">Contact</a>
        </nav>
    </header>

    <section class="container">
        <h2>About Hair Galore</h2>
        <p>Hair Galore is dedicated to bringing you the highest quality hair extensions for every style and occasion. Our mission is to help you feel confident, glamorous, and unstoppable with every strand.</p>
        <p>We carefully source and select our hair to ensure premium quality, easy styling, and long-lasting beauty. Join the Hair Galore family and transform your look today!</p>
    </section>

    <footer>
        <p>&copy; 2025 Hair Galore</p>
    </footer>
</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Shop - Hair Galore</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <h1>Hair Galore</h1>
        <nav>
            <a href="index.html">Home</a>
            <a href="about.html">About</a>
            <a href="shop.html">Shop</a>
            <a href="contact.html">Contact</a>
        </nav>
    </header>

    <section class="container">
        <h2>Shop Our Products</h2>
        <div class="products">
            <div class="product-card">
                <img src="images/product1.jpg" alt="Hair Product">
                <h3>Beautiful Hair 1</h3>
                <p>$49.99</p>
                <button onclick="addToCart('Beautiful Hair 1', 49.99)">Add to Cart</button>
                <p>⭐⭐⭐⭐⭐</p>
            </div>
            <div class="product-card">
                <img src="images/product2.jpg" alt="Hair Product">
                <h3>Beautiful Hair 2</h3>
                <p>$59.99</p>
                <button onclick="addToCart('Beautiful Hair 2', 59.99)">Add to Cart</button>
                <p>⭐⭐⭐⭐</p>
            </div>
            <!-- Add more products here -->
        </div>
    </section>

    <div id="cart"></div>

    <footer>
        <p>&copy; 2025 Hair Galore</p>
    </footer>

    <script src="script.js"></script>
</body>
</html>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Contact - Hair Galore</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <header>
        <h1>Hair Galore</h1>
        <nav>
            <a href="index.html">Home</a>
            <a href="about.html">About</a>
            <a href="shop.html">Shop</a>
            <a href="contact.html">Contact</a>
        </nav>
    </header>

    <section class="container">
        <h2>Contact Us</h2>
        <form>
            <input type="text" placeholder="Your Name" required>
            <input type="email" placeholder="Your Email" required>
            <textarea placeholder="Your Message" rows="5" required></textarea>
            <button type="submit">Send Message</button>
        </form>

        <h3>Sign Up for Updates</h3>
        <form>
            <input type="email" placeholder="Enter your email">
            <button type="submit">Subscribe</button>
        </form>
    </section>

    <footer>
        <p>&copy; 2025 Hair Galore</p>
    </footer>
</body>
</html>
