# Marketplace
Marketplace Coding
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Etsy-Like Marketplace</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header class="header">
        <div class="container">
            <h1 class="logo">Etsy-Like Marketplace</h1>
            <nav class="nav">
                <ul>
                    <li><a href="#home">Home</a></li>
                    <li><a href="#products">Products</a></li>
                    <li><a href="#contact">Contact</a></li>
                    <li><a href="#cart">Cart</a></li>
                </ul>
            </nav>
        </div>
    </header>

    <section id="home" class="hero">
        <div class="container">
            <h2>Welcome to Your Marketplace</h2>
            <p>Discover unique products crafted with love.</p>
        </div>
    </section>

    <section id="products" class="products">
        <div class="container">
            <h2>Explore Our Products</h2>
            <div class="product-grid">
                <!-- Product Cards -->
                <div class="product-card" data-id="1">
                    <img src="https://via.placeholder.com/150" alt="Product 1">
                    <h3>Handmade Mug</h3>
                    <p>$25.00</p>
                    <button class="btn add-to-cart">Add to Cart</button>
                </div>
                <div class="product-card" data-id="2">
                    <img src="https://via.placeholder.com/150" alt="Product 2">
                    <h3>Knitted Scarf</h3>
                    <p>$40.00</p>
                    <button class="btn add-to-cart">Add to Cart</button>
                </div>
                <div class="product-card" data-id="3">
                    <img src="https://via.placeholder.com/150" alt="Product 3">
                    <h3>Ceramic Vase</h3>
                    <p>$30.00</p>
                    <button class="btn add-to-cart">Add to Cart</button>
                </div>
            </div>
        </div>
    </section>

    <section id="cart" class="cart">
        <div class="container">
            <h2>Your Cart</h2>
            <ul id="cart-items">
                <!-- Cart items will be dynamically added here -->
            </ul>
            <p id="total-price">Total: $0.00</p>
            <button class="btn" id="checkout">Checkout</button>
        </div>
    </section>

    <section id="contact" class="contact">
        <div class="container">
            <h2>Contact Us</h2>
            <form id="contact-form">
                <label for="name">Name:</label>
                <input type="text" id="name" name="name" required>

                <label for="email">Email:</label>
                <input type="email" id="email" name="email" required>

                <label for="message">Message:</label>
                <textarea id="message" name="message" rows="4" required></textarea>

                <button type="submit" class="btn">Send</button>
            </form>
        </div>
    </section>

    <footer class="footer">
        <div class="container">
            <p>&copy; 2025 Etsy-Like Marketplace. All rights reserved.</p>
        </div>
    </footer>

    <script>
        // JavaScript for basic cart functionality
        const cart = [];
        const cartItems = document.getElementById('cart-items');
        const totalPrice = document.getElementById('total-price');

        document.querySelectorAll('.add-to-cart').forEach(button => {
            button.addEventListener('click', () => {
                const productCard = button.parentElement;
                const productId = productCard.getAttribute('data-id');
                const productName = productCard.querySelector('h3').textContent;
                const productPrice = parseFloat(productCard.querySelector('p').textContent.replace('$', ''));

                cart.push({ id: productId, name: productName, price: productPrice });
                updateCart();
            });
        });

        function updateCart() {
            cartItems.innerHTML = '';
            let total = 0;

            cart.forEach(item => {
                const li = document.createElement('li');
                li.textContent = `${item.name} - $${item.price.toFixed(2)}`;
                cartItems.appendChild(li);
                total += item.price;
            });

            totalPrice.textContent = `Total: $${total.toFixed(2)}`;
        }

        document.getElementById('checkout').addEventListener('click', () => {
            if (cart.length > 0) {
                alert('Thank you for your purchase!');
                cart.length = 0;
                updateCart();
            } else {
                alert('Your cart is empty.');
            }
        });
    </script>
</body>
</html>
