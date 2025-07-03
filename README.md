<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>SONIQUE | Professional Music Experience</title>
  <style>
    body { margin: 0; font-family: 'Poppins', sans-serif; background: #0a0a0a; color: white; }
    header { background: #111; padding: 1rem 2rem; display: flex; justify-content: space-between; align-items: center; position: sticky; top: 0; z-index: 1000; }
    header h1 { color: #00ffff; font-size: 1.8rem; }
    nav a { margin: 0 1rem; color: white; text-decoration: none; font-weight: 500; }
    .hero { text-align: center; padding: 5rem 2rem; background: radial-gradient(circle at center, #1f1f1f, #0a0a0a); }
    .hero h2 { font-size: 3rem; margin-bottom: 1rem; color: #00ffff; }
    .hero p { font-size: 1.2rem; color: #ccc; max-width: 600px; margin: 0 auto; }
    .btn { background: #00ffff; padding: 0.75rem 1.5rem; color: black; font-weight: bold; border: none; border-radius: 5px; cursor: pointer; margin-top: 1.5rem; }
    .products { display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 2rem; padding: 3rem 2rem; background: #121212; }
    .product { background: #1a1a1a; padding: 1rem; border-radius: 10px; text-align: center; box-shadow: 0 0 10px rgba(0,255,255,0.2); transition: transform 0.2s ease; }
    .product:hover { transform: scale(1.03); }
    .product img { width: 100%; border-radius: 10px; }
    .product h3 { margin: 1rem 0 0.5rem; }
    .product p { color: #aaa; font-size: 0.9rem; }
    .product form { margin-top: 1rem; }
    .product button { background: #00ffff; color: black; border: none; padding: 0.6rem 1.2rem; font-weight: bold; border-radius: 5px; cursor: pointer; }
    .section-title { text-align: center; font-size: 2rem; margin-bottom: 2rem; color: #00ffff; }
    #cart { padding: 2rem; background: #0f0f0f; }
    #cart h2 { color: #00ffff; }
    #cart ul { list-style: none; padding: 0; }
    #cart ul li { padding: 0.5rem 0; border-bottom: 1px solid #333; display: flex; justify-content: space-between; }
    #cart button { margin-top: 1rem; }
    footer { background: #111; text-align: center; padding: 2rem; font-size: 0.8rem; color: #777; margin-top: 3rem; }
  </style>
</head>
<body>
  <header>
    <h1>SONIQUE</h1>
    <nav>
      <a href="#home">Home</a>
      <a href="#products">Products</a>
      <a href="#about">About</a>
      <a href="#contact">Contact</a>
      <a href="#cart">Cart</a>
    </nav>
  </header>  <section class="hero" id="home">
    <h2>Elevate Your Music Experience</h2>
    <p>Discover professional audio gear built for audiophiles, producers, and everyday music lovers.</p>
    <a href="#products"><button class="btn">Explore Products</button></a>
  </section>  <section id="products">
    <h2 class="section-title">Featured Products</h2>
    <div class="products">
      <div class="product">
        <img src="https://via.placeholder.com/300x200" alt="Sonique Pulse">
        <h3>Sonique Pulse</h3>
        <p>Wireless headphones with studio-grade clarity and deep bass.</p>
        <form onsubmit="addToCart('Sonique Pulse', 4999); return false;">
          <button type="submit">Add to Cart ₹4,999</button>
        </form>
      </div>
      <div class="product">
        <img src="https://via.placeholder.com/300x200" alt="Sonique Air">
        <h3>Sonique Air</h3>
        <p>Ultra-light earbuds with ANC and high-fidelity audio output.</p>
        <form onsubmit="addToCart('Sonique Air', 2999); return false;">
          <button type="submit">Add to Cart ₹2,999</button>
        </form>
      </div>
      <div class="product">
        <img src="https://via.placeholder.com/300x200" alt="Sonique Boom">
        <h3>Sonique Boom</h3>
        <p>High-output Bluetooth speaker designed for portable power and clarity.</p>
        <form onsubmit="addToCart('Sonique Boom', 3499); return false;">
          <button type="submit">Add to Cart ₹3,499</button>
        </form>
      </div>
    </div>
  </section>  <section class="hero" id="about" style="background:#0f0f0f">
    <h2>About SONIQUE</h2>
    <p>Founded with a passion for immersive sound, SONIQUE engineers top-tier audio devices that redefine the music listening experience. Our products are used by professionals and loved by all.</p>
  </section>  <section class="hero" id="contact" style="background:#1a1a1a">
    <h2>Contact Us</h2>
    <p>Have a question or need help? Reach out at <a href="mailto:support@sonique.com" style="color:#00ffff">support@sonique.com</a></p>
  </section>  <section id="cart">
    <h2>Your Cart</h2>
    <ul id="cart-items"></ul>
    <p>Total: ₹<span id="cart-total">0</span></p>
    <button onclick="checkout()">Checkout</button>
  </section>  <footer>
    &copy; 2025 SONIQUE. All rights reserved. | Privacy Policy | Terms & Conditions
  </footer>  <script>
    let cart = [];

    function addToCart(product, price) {
      cart.push({ product, price });
      renderCart();
      alert(${product} added to cart.);
    }

    function renderCart() {
      const cartItems = document.getElementById('cart-items');
      const cartTotal = document.getElementById('cart-total');
      cartItems.innerHTML = '';
      let total = 0;
      cart.forEach((item, index) => {
        const li = document.createElement('li');
        li.innerHTML = ${item.product} - ₹${item.price} <button onclick="removeItem(${index})">Remove</button>;
        cartItems.appendChild(li);
        total += item.price;
      });
      cartTotal.textContent = total;
    }

    function removeItem(index) {
      cart.splice(index, 1);
      renderCart();
    }

    function checkout() {
      if (cart.length === 0) {
        alert('Your cart is empty.');
        return;
      }
      let orderDetails = cart.map(item => ${item.product} - ₹${item.price}).join('\n');
      alert(Thank you for your purchase!\n\nOrder Summary:\n${orderDetails});
      cart = [];
      renderCart();
    }
  </script></body>
</html>
