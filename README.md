<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Settlers Sneaks by Keenan Morrow</title>
<style>
* {margin:0; padding:0; box-sizing:border-box}
body {font-family:Arial, sans-serif; background:#f5f5f5; color:#111}
header {background:#0a0a0a; color:#fff; padding:30px 0; text-align:center}
.logo {font-size:48px; font-weight:900; text-transform:uppercase; letter-spacing:3px}
.tagline {font-size:16px; color:#aaa; margin:5px 0 15px}
.contact a {color:#25D366; text-decoration:none; font-weight:bold}
nav {margin-top:20px}
nav a {color:#fff; margin:0 12px; text-decoration:none; font-weight:600; cursor:pointer}
nav a:hover {color:#25D366}
.container {max-width:1200px; margin:auto; padding:40px 20px}
h2 {text-align:center; font-size:28px; margin-bottom:30px}
.grid {display:grid; grid-template-columns:repeat(auto-fit, minmax(260px, 1fr)); gap:25px}
.card {background:#fff; border-radius:8px; padding:15px; text-align:center; box-shadow:0 2px 8px rgba(0,0,0,0.1)}
.card img {width:100%; height:260px; object-fit:cover; border-radius:5px}
.card h3 {margin:12px 0 5px; font-size:18px}
.price {font-size:20px; font-weight:bold; color:#0a0a0a; margin-bottom:10px}
.btn {background:#0a0a0a; color:#fff; border:none; padding:10px 20px; border-radius:5px; cursor:pointer; font-weight:bold}
.btn:hover {background:#25D366; color:#000}
.cart-box {position:fixed; top:20px; right:20px; background:#0a0a0a; color:#fff; padding:12px 20px; border-radius:50px; font-weight:bold}
footer {background:#000; color:#ccc; text-align:center; padding:40px 20px; margin-top:60px}
footer a {color:#25D366}
</style>
</head>
<body>

<header>
  <h1 class="logo">Settlers Sneaks</h1>
  <p class="tagline">by Keenan Morrow</p>
  <p class="contact">Orders/Queries: <a href="https://wa.me/27738303480" target="_blank">WhatsApp 073 830 3480</a></p>
  <nav>
    <a onclick="alert('All sneakers showing below 🔥')">All Sneakers</a>
    <a onclick="alert('Nike section - add products in Shopify later')">Nike</a>
    <a onclick="alert('Jordan section - add products in Shopify later')">Jordan</a>
    <a onclick="alert('Cart is demo only for class')">Cart (<span id="cart-count">0</span>)</a>
  </nav>
</header>

<div class="cart-box">Cart: R<span id="cart-total">0</span></div>

<main class="container">
  <h2>Streetwear Heat 🔥</h2>
  <div class="grid">
    
    <div class="card">
      <img src="https://images.unsplash.com/photo-1542291026-7eec264c27ff?w=500" alt="Nike Dunk">
      <h3>Nike Dunk Low Retro</h3>
      <p class="price">R2,499</p>
      <button class="btn" onclick="addToCart('Nike Dunk Low Retro', 2499)">Add to Cart</button>
    </div>

    <div class="card">
      <img src="https://images.unsplash.com/photo-1606107557195-0e29a4b5b4aa?w=500" alt="Jordan 1">
      <h3>Air Jordan 1 Retro High</h3>
      <p class="price">R3,299</p>
      <button class="btn" onclick="addToCart('Air Jordan 1 Retro High', 3299)">Add to Cart</button>
    </div>

    <div class="card">
      <img src="https://images.unsplash.com/photo-1600185365926-3a2ce3cdb9eb?w=500" alt="Adidas Samba">
      <h3>Adidas Samba OG</h3>
      <p class="price">R1,899</p>
      <button class="btn" onclick="addToCart('Adidas Samba OG', 1899)">Add to Cart</button>
    </div>

    <div class="card">
      <img src="https://images.unsplash.com/photo-1560769629-975ec94e6a86?w=500" alt="Air Force 1">
      <h3>Nike Air Force 1 White</h3>
      <p class="price">R2,199</p>
      <button class="btn" onclick="addToCart('Nike Air Force 1 White', 2199)">Add to Cart</button>
    </div>

    <div class="card">
      <img src="https://images.unsplash.com/photo-1551107696-a4b0c3a0d9a2?w=500" alt="New Balance 550">
      <h3>New Balance 550</h3>
      <p class="price">R2,599</p>
      <button class="btn" onclick="addToCart('New Balance 550', 2599)">Add to Cart</button>
    </div>

    <div class="card">
      <img src="https://images.unsplash.com/photo-1525966222134-fcfa99b8ae77?w=500" alt="Vans Old Skool">
      <h3>Vans Old Skool</h3>
      <p class="price">R1,499</p>
      <button class="btn" onclick="addToCart('Vans Old Skool', 1499)">Add to Cart</button>
    </div>

  </div>
</main>

<footer>
  <p>© 2026 Settlers Sneaks by Keenan Morrow</p>
  <p>Need help? WhatsApp <a href="https://wa.me/27738303480">073 830 3480</a></p>
  <p><small>This is a demo site for class. Real payments via Shopify + PayFast later.</small></p>
</footer>

<script>
let cart = [];
let total = 0;

function addToCart(name, price) {
  cart.push({name, price});
  total += price;
  document.getElementById('cart-count').innerText = cart.length;
  document.getElementById('cart-total').innerText = total;
  alert(name + ' added to cart! Demo only - no real payment yet.');
}
</script>

</body>
</html>
