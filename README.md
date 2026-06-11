<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Settlers Sneaks | Premium Streetwear</title>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=Inter:wght@300;400;600;700&display=swap" rel="stylesheet">
<style>
* {margin:0; padding:0; box-sizing:border-box}
body {font-family:'Inter', sans-serif; background:#fff; color:#111}
a {text-decoration:none; color:inherit}

/* Header */
header {background:#fff; border-bottom:1px solid #eee; position:sticky; top:0; z-index:100}
.top-bar {background:#000; color:#fff; text-align:center; font-size:12px; padding:8px; letter-spacing:1px}
.nav {max-width:1300px; margin:auto; display:flex; justify-content:space-between; align-items:center; padding:20px}
.logo-wrap h1 {font-family:'Bebas Neue', sans-serif; font-size:36px; letter-spacing:2px}
.logo-wrap .tagline {font-size:13px; color:#777; margin-top:-5px}
.nav-links {display:flex; gap:30px; font-weight:600; font-size:14px}
.nav-links a:hover {border-bottom:2px solid #000}
.cart-btn {background:#000; color:#fff; padding:10px 20px; border-radius:4px; font-weight:600; cursor:pointer}

/* Hero */
.hero {background:linear-gradient(rgba(0,0,0,0.4), rgba(0,0,0,0.4)), url('https://images.unsplash.com/photo-1552346154-21d32810aba3?w=1600') center/cover; color:#fff; text-align:center; padding:100px 20px}
.hero h2 {font-family:'Bebas Neue', sans-serif; font-size:64px; letter-spacing:3px; margin-bottom:15px}
.hero p {font-size:18px; margin-bottom:30px; font-weight:300}
.hero-btn {background:#fff; color:#000; padding:14px 35px; display:inline-block; font-weight:700; border-radius:4px; transition:0.3s}
.hero-btn:hover {transform:translateY(-2px); box-shadow:0 5px 20px rgba(0,0,0,0.3)}

/* Products */
.container {max-width:1300px; margin:auto; padding:70px 20px}
.section-title {text-align:center; font-family:'Bebas Neue', sans-serif; font-size:42px; margin-bottom:50px; letter-spacing:2px}
.grid {display:grid; grid-template-columns:repeat(auto-fit, minmax(280px, 1fr)); gap:30px}
.card {background:#fff; border:1px solid #eee; border-radius:8px; overflow:hidden; transition:0.3s}
.card:hover {transform:translateY(-5px); box-shadow:0 10px 30px rgba(0,0,0,0.1)}
.card img {width:100%; height:320px; object-fit:cover}
.card-body {padding:20px}
.card h3 {font-size:18px; font-weight:600; margin-bottom:8px}
.price {font-size:22px; font-weight:700; color:#000; margin-bottom:15px}
.btn {width:100%; background:#000; color:#fff; border:none; padding:12px; border-radius:4px; font-weight:600; cursor:pointer; transition:0.2s}
.btn:hover {background:#333}

/* WhatsApp float */
.whatsapp {position:fixed; bottom:25px; right:25px; background:#25D366; width:60px; height:60px; border-radius:50%; display:flex; align-items:center; justify-content:center; box-shadow:0 4px 12px rgba(0,0,0,0.2); z-index:99}
.whatsapp svg {width:32px; height:32px; fill:#fff}

/* Footer */
footer {background:#111; color:#aaa; padding:60px 20px; margin-top:80px}
.footer-grid {max-width:1300px; margin:auto; display:grid; grid-template-columns:repeat(auto-fit, minmax(250px, 1fr)); gap:40px}
footer h4 {color:#fff; margin-bottom:15px; font-size:16px}
footer a {display:block; margin:8px 0; color:#aaa}
footer a:hover {color:#fff}
.copy {text-align:center; border-top:1px solid #333; margin-top:40px; padding-top:20px; font-size:13px}
</style>
</head>
<body>

<div class="top-bar">FREE DELIVERY ON ORDERS OVER R1500 | WHATSAPP 073 830 3480</div>

<header>
  <div class="nav">
    <div class="logo-wrap">
      <h1>Settlers Sneaks</h1>
      <div class="tagline">by Keenan Morrow</div>
    </div>
    <div class="nav-links">
      <a href="#">New Drops</a>
      <a href="#">Nike</a>
      <a href="#">Jordan</a>
      <a href="#">Adidas</a>
      <a href="#">Sale</a>
    </div>
    <div class="cart-btn">Cart (<span id="count">0</span>) R<span id="total">0</span></div>
  </div>
</header>

<section class="hero">
  <h2>Streetwear That Moves You</h2>
  <p>Authentic sneakers. Limited drops. Cape Town based.</p>
  <a href="#products" class="hero-btn">Shop Now</a>
</section>

<main class="container" id="products">
  <h2 class="section-title">Latest Drops</h2>
  <div class="grid">
    
    <div class="card">
      <img src="https://images.unsplash.com/photo-1542291026-7eec264c27ff?w=600" alt="Nike Dunk">
      <div class="card-body">
        <h3>Nike Dunk Low Retro</h3>
        <div class="price">R2,499</div>
        <button class="btn" onclick="addCart('Nike Dunk Low Retro', 2499)">Add to Cart</button>
      </div>
    </div>

    <div class="card">
      <img src="https://images.unsplash.com/photo-1606107557195-0e29a4b5b4aa?w=600" alt="Jordan 1">
      <div class="card-body">
        <h3>Air Jordan 1 Retro High</h3>
        <div class="price">R3,299</div>
        <button class="btn" onclick="addCart('Air Jordan 1 Retro High', 3299)">Add to Cart</button>
      </div>
    </div>

    <div class="card">
      <img src="https://images.unsplash.com/photo-1600185365926-3a2ce3cdb9eb?w=600" alt="Adidas Samba">
      <div class="card-body">
        <h3>Adidas Samba OG</h3>
        <div class="price">R1,899</div>
        <button class="btn" onclick="addCart('Adidas Samba OG', 1899)">Add to Cart</button>
      </div>
    </div>

    <div class="card">
      <img src="https://images.unsplash.com/photo-1560769629-975ec94e6a86?w=600" alt="Air Force 1">
      <div class="card-body">
        <h3>Nike Air Force 1 '07</h3>
        <div class="price">R2,199</div>
        <button class="btn" onclick="addCart('Nike Air Force 1 07', 2199)">Add to Cart</button>
      </div>
    </div>

    <div class="card">
      <img src="https://images.unsplash.com/photo-1551107696-a4b0c3a0d9a2?w=600" alt="New Balance">
      <div class="card-body">
        <h3>New Balance 550</h3>
        <div class="price">R2,599</div>
        <button class="btn" onclick="addCart('New Balance 550', 2599)">Add to Cart</button>
      </div>
    </div>

    <div class="card">
      <img src="https://images.unsplash.com/photo-1525966222134-fcfa99b8ae77?w=600" alt="Vans">
      <div class="card-body">
        <h3>Vans Old Skool</h3>
        <div class="price">R1,499</div>
        <button class="btn" onclick="addCart('Vans Old Skool', 1499)">Add to Cart</button>
      </div>
    </div>

  </div>
</main>

<a href="https://wa.me/27738303480" target="_blank" class="whatsapp">
  <svg viewBox="0 0 24 24"><path d="M20.52 3.48A11.87 11.87 0 0 0 12 0C5.37 0 0 5.37 0 12c0 2.11.55 4.17 1.6 6L0 24l6.22-1.63A11.94 11.94 0 0 0 12 24c6.63 0 12-5.37 12-12a11.87 11.87 0 0 0-3.48-8.52ZM12 22c-1.88 0-3.72-.5-5.33-1.45l-.38-.23-3.69.97.98-3.59-.24-.37A9.94 9.94 0 0 1 2 12c0-5.52 4.48-10 10-10s10 4.48 10 10-4.48 10-10 10Zm5.2-7.5c-.28-.14-1.65-.81-1.91-.9-.25-.1-.44-.14-.62.14-.18.28-.7.9-.86 1.08-.16.18-.32.2-.6.06-.28-.14-1.19-.44-2.27-1.4-.84-.75-1.4-1.67-1.56-1.95-.16-.28-.02-.43.12-.57.12-.12.28-.32.42-.48.14-.16.18-.28.28-.46.1-.18.05-.35-.02-.49-.07-.14-.62-1.5-.85-2.05-.22-.54-.46-.47-.62-.48l-.53-.01c-.18 0-.47.07-.72.33-.25.25-.95.93-.95 2.27s.97 2.63 1.1 2.81c.14.18 1.91 2.92 4.63 4.1.65.28 1.15.45 1.55.57.65.21 1.24.18 1.71.11.52-.08 1.65-.67 1.88-1.32.23-.65.23-1.2.16-1.32-.07-.12-.25-.19-.53-.33Z"/></svg>
</a>

<footer>
  <div class="footer-grid">
    <div>
      <h4>Settlers Sneaks</h4>
      <p style="margin-top:10px; font-size:14px">by Keenan Morrow<br>Premium streetwear & sneakers in Cape Town</p>
    </div>
    <div>
      <h4>Shop</h4>
      <a href="#">All Sneakers</a>
      <a href="#">Nike</a>
      <a href="#">Jordan</a>
      <a href="#">Adidas</a>
    </div>
    <div>
      <h4>Support</h4>
      <a href="https://wa.me/27738303480">WhatsApp 073 830 3480</a>
      <a href="#">Shipping Info</a>
      <a href="#">Returns</a>
      <a href="#">Size Guide</a>
    </div>
  </div>
  <div class="copy">© 2026 Settlers Sneaks. Demo site for class. Real payments via Shopify + PayFast later.</div>
</footer>

<script>
let count = 0, total = 0;
function addCart(name, price) {
  count++; total += price;
  document.getElementById('count').innerText = count;
  document.getElementById('total').innerText = total;
  alert(name + ' added! Demo cart only.');
}
</script>
</body>
</html>
