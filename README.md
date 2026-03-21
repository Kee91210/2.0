# 2.0
Settlers Way sneaker Shop. Your premier destination for authentic sneakers. Fresh drops, curated collection and streetwear vibes. Visit us for the latest kicks and sneakerhead culture.
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Settlers Way Store | Premium Streetwear</title>

<script src="https://www.gstatic.com/firebasejs/10.7.1/firebase-app-compat.js"></script>
<script src="https://www.gstatic.com/firebasejs/10.7.1/firebase-firestore-compat.js"></script>

<style>
body {font-family: Arial, sans-serif; margin:0; background:#0b0b0b; color:#fff;}
header {background:#000; padding:20px; text-align:center; border-bottom:1px solid #222;}
h1 {margin:0; font-size:2.6em;}
.brand {font-size:0.95em; color:#00ff88; margin-top:6px;}
.topbar {display:flex; justify-content:space-between; align-items:center; padding:10px 15px; background:#111; border-bottom:1px solid #222;}
.admin-btn {background:#333; color:#fff; border:none; padding:8px 12px; border-radius:6px; cursor:pointer;}
.hero {padding:30px 20px; text-align:center; background:linear-gradient(135deg,#111,#000);}
.hero p {color:#aaa;}
.nav {display:flex; justify-content:center; gap:10px; flex-wrap:wrap; margin-top:10px;}
.nav button {background:none; border:1px solid #333; color:#fff; padding:8px 12px; border-radius:20px; cursor:pointer;}
.nav button:hover {border-color:#00ff88;}
.container {padding:20px;}
.search {padding:12px; width:100%; margin-bottom:20px; border-radius:8px; border:none;}
.grid {display:grid; grid-template-columns:repeat(auto-fit,minmax(240px,1fr)); gap:20px;}
.card {background:#141414; padding:15px; border-radius:14px; text-align:center;}
.card img {width:100%; height:220px; object-fit:cover; border-radius:10px;}
.price {color:#00ff88; font-weight:bold;}
select {padding:8px; width:100%; margin-top:8px; border-radius:6px; background:#111; color:#fff; border:1px solid #333;}
button {padding:10px; background:#25D366; border:none; color:#000; font-weight:bold; cursor:pointer; border-radius:6px; margin-top:6px; width:100%;}
.cart {position:fixed; top:20px; right:20px; background:#25D366; padding:12px 16px; border-radius:12px; color:#000; font-weight:bold; cursor:pointer;}
.checkout-form, .admin-panel {display:none; position:fixed; top:0; left:0; width:100%; height:100%; background:rgba(0,0,0,0.95); padding:30px; overflow:auto;}
.form-box {max-width:420px; margin:auto; background:#111; padding:20px; border-radius:12px; border:1px solid #222;}
.form-box input, .form-box select {width:100%; padding:10px; margin:8px 0; border-radius:6px; border:none;}
.footer {text-align:center; padding:30px; color:#777; border-top:1px solid #222; margin-top:40px;}
.whatsapp-banner {position:fixed; bottom:0; width:100%; background:#25D366; color:#000; text-align:center; padding:14px; font-weight:bold;}
</style>
</head>
<body>

<div class="topbar">
<div>Settlers Way Store</div>
<button class="admin-btn" onclick="openAdmin()">Admin</button>
</div>

<header>
<h1>Settlers Way Store</h1>
<p class="brand">by Keenan Morrow</p>
</header>

<div class="hero">
<h2>Luxury Streetwear Store</h2>
<p>Now powered by real cloud database (Firebase)</p>
</div>

<div class="cart" onclick="openCheckout()">🛒 Cart (<span id="cartCount">0</span>)</div>

<div class="container">

<div class="nav">
<button onclick="filter('all')">All</button>
<button onclick="filter('sneaker')">Sneakers</button>
<button onclick="filter('cap')">Caps</button>
<button onclick="filter('accessory')">Accessories</button>
</div>

<input class="search" type="text" id="search" placeholder="Search products..." onkeyup="render()">
<div class="grid" id="products"></div>
</div>

<!-- CHECKOUT -->
<div class="checkout-form" id="checkout">
<div class="form-box">
<h2>Checkout</h2>
<input id="name" placeholder="Full Name">
<input id="address" placeholder="Delivery Address">
<input id="phone" placeholder="Phone Number">
<button onclick="sendOrder()">Send WhatsApp Order</button>
<button onclick="closeCheckout()" style="background:#333;color:#fff;">Close</button>
</div>
</div>

<!-- ADMIN -->
<div class="admin-panel" id="admin">
<div class="form-box">
<h2>Admin Panel (Cloud)</h2>
<input id="adminPass" type="password" placeholder="Password">
<button onclick="checkAdmin()">Login</button>
<hr>
<input id="pname" placeholder="Product Name">
<input id="pprice" placeholder="Price">
<select id="ptype">
<option value="sneaker">Sneaker</option>
<option value="cap">Cap</option>
<option value="accessory">Accessory</option>
</select>
<input type="file" id="pimg">
<button onclick="addProduct()">Upload to Store</button>
<button onclick="closeAdmin()" style="background:#333;color:#fff;">Close</button>
</div>
</div>

<div class="footer">© 2026 Settlers Way Store | Built by Keenan Morrow</div>
<div class="whatsapp-banner">📲 WhatsApp Orders: 073 830 3480</div>

<script>

// 🔥 FIREBASE CONFIG (YOU MUST REPLACE THIS)
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_PROJECT.firebaseapp.com",
  projectId: "YOUR_PROJECT_ID",
};

firebase.initializeApp(firebaseConfig);
const db = firebase.firestore();

let cart = [];
let currentFilter = 'all';

function filter(t){currentFilter=t;render();}

// 🔥 REAL CLOUD PRODUCTS
function render(){
let s=document.getElementById('search').value.toLowerCase();
let html='';

db.collection("products").onSnapshot(snapshot=>{
let items=[];
snapshot.forEach(doc=>items.push({id:doc.id,...doc.data()}));

items
.filter(p=>(currentFilter==='all'||p.type===currentFilter)&&p.name.toLowerCase().includes(s))
.forEach((p,i)=>{
html+=`
<div class='card'>
<img src='${p.img}'>
<h3>${p.name}</h3>
<p class='price'>R${p.price}</p>
${p.type==='sneaker'?`<select><option>UK Size</option><option>6</option><option>7</option><option>8</option><option>9</option></select>`:''}
<button onclick="addToCart('${p.id}','${p.name}',${p.price})">Add to Cart</button>
<button onclick="order('${p.name}')">Buy Now</button>
</div>`;
});

document.getElementById('products').innerHTML=html;
});
}

function addToCart(id,name,price){
cart.push({id,name,price});
document.getElementById('cartCount').innerText=cart.length;
}

function openCheckout(){document.getElementById('checkout').style.display='block';}
function closeCheckout(){document.getElementById('checkout').style.display='none';}

function sendOrder(){
let msg=`Name:${name.value}%0AAddress:${address.value}%0APhone:${phone.value}%0AOrder:%0A`;
cart.forEach(i=>msg+=`- ${i.name} (R${i.price})%0A`);
window.open(`https://wa.me/27738303480?text=${msg}`,'_blank');
}

function order(n){window.open(`https://wa.me/27738303480?text=I want: ${n}`,'_blank');}

function openAdmin(){document.getElementById('admin').style.display='block';}
function closeAdmin(){document.getElementById('admin').style.display='none';}

function checkAdmin(){
if(adminPass.value==='1234') alert('Access granted');
else alert('Wrong password');
}

// 🔥 UPLOAD TO CLOUD DATABASE
function addProduct(){
let file=document.getElementById('pimg').files[0];
let reader=new FileReader();
reader.onload=function(){

let product={
name:pname.value,
price:parseInt(pprice.value),
type:ptype.value,
img:reader.result
};

db.collection("products").add(product);
alert("Product uploaded to cloud store!");
};
reader.readAsDataURL(file);
}

render();
</script>

</body>
</html>
