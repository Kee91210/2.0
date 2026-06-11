<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Settlers Sneaks</title>
<link href="https://fonts.googleapis.com/css2?family=Anton&family=Montserrat:wght@500;700;900&display=swap" rel="stylesheet">
<style>
  *{margin:0;padding:0;box-sizing:border-box}
  body{
    background: #050505;
    background-image: 
      radial-gradient(circle at 10% 20%, rgba(0,255,100,0.12) 0%, transparent 40%),
      radial-gradient(circle at 90% 80%, rgba(0,200,80,0.08) 0%, transparent 50%);
    color: #fff;
    font-family: 'Montserrat', sans-serif;
    padding: 40px 20px;
    min-height: 100vh;
  }
  h1{
    font-family: 'Anton', sans-serif;
    font-size: 4.5rem;
    text-align: center;
    letter-spacing: 4px;
    color: #00ff64;
    text-shadow: 0 0 20px rgba(0,255,100,0.6);
    margin-bottom: 8px;
    text-transform: uppercase;
  }
  .sub{
    text-align: center;
    color: #66ff99;
    margin-bottom: 60px;
    font-size: 1rem;
    font-weight: 500;
    letter-spacing: 2px;
  }
  .grid{
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
    gap: 35px;
    max-width: 1100px;
    margin: 0 auto;
  }
  .card{
    background: #0f0f0f;
    border: 2px solid #1a1a1a;
    border-radius: 18px;
    overflow: hidden;
    transition: all 0.3s;
    position: relative;
  }
  .card:hover{
    border-color: #00ff64;
    transform: translateY(-10px);
    box-shadow: 0 25px 50px rgba(0,255,100,0.25);
  }
  .badge{
    position: absolute;
    top: 18px;
    left: 18px;
    background: #00ff64;
    color: #000;
    padding: 7px 16px;
    font-size: 0.8rem;
    font-weight: 900;
    letter-spacing: 1.5px;
    border-radius: 8px;
    z-index: 2;
    box-shadow: 0 4px 15px rgba(0,255,100,0.4);
  }
  .card img{
    width: 100%;
    height: 290px;
    object-fit: cover;
    background: #111;
    border-bottom: 2px solid #00ff64;
  }
  .info{padding: 28px}
  .name{
    font-family: 'Anton', sans-serif;
    font-size: 1.9rem;
    letter-spacing: 1px;
    margin-bottom: 10px;
    color: #fff;
  }
  .sizes{
    color: #00ff64;
    font-size: 0.95rem;
    margin-bottom: 18px;
    font-weight: 700;
    letter-spacing: 0.5px;
  }
  .price-row{
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin: 22px 0;
  }
  .price{
    font-size: 2.2rem;
    font-weight: 900;
    color: #fff;
  }
  .deposit{
    background: rgba(0,255,100,0.18);
    border: 1.5px solid #00ff64;
    color: #00ff64;
    padding: 6px 12px;
    border-radius: 8px;
    font-size: 0.9rem;
    font-weight: 800;
  }
  .profit{
    color: #66ff99;
    font-size: 0.95rem;
    margin-bottom: 18px;
    font-weight: 600;
  }
  .btn{
    display: block;
    width: 100%;
    background: linear-gradient(135deg, #00ff64 0%, #00cc50 100%);
    color: #000;
    text-align: center;
    padding: 18px;
    border-radius: 12px;
    text-decoration: none;
    font-weight: 900;
    font-size: 1.15rem;
    letter-spacing: 1.5px;
    text-transform: uppercase;
    transition: all 0.2s;
    box-shadow: 0 8px 25px rgba(0,255,100,0.35);
  }
  .btn:hover{
    transform: scale(1.04);
    box-shadow: 0 12px 35px rgba(0,255,100,0.55);
  }
  .delivery{
    text-align: center;
    color: #777;
    font-size: 0.9rem;
    margin-top: 14px;
    font-weight: 500;
  }
</style>
</head>
<body>

<h1>Settlers Sneaks</h1>
<p class="sub">Pre-Order Only | 7-10 Days | 50% Deposit Secures</p>

<div class="grid">
  
  <!-- Product 1: AF1 Triple White -->
  <div class="card">
    <span class="badge">PRE-ORDER</span>
    <img src="PASTE_AF1_PIC_URL_HERE" alt="Nike AF1 Triple White">
    <div class="info">
      <div class="name">Nike Air Force 1 '07 Triple White</div>
      <div class="sizes">Sizes: UK 6, 7, 8, 9, 10, 11</div>
      <div class="price-row">
        <div class="price">R2,899.95</div>
        <div class="deposit">Deposit R1,450</div>
      </div>
      <div class="profit">Your Profit: R500 per pair</div>
      <a href="https://wa.me/27738303480?text=Hi Keenan, I want to pre-order Nike AF1 Triple White Size ___" class="btn">Order on WhatsApp</a>
      <div class="delivery">Delivery in 7-10 Days</div>
    </div>
  </div>

  <!-- Product 2: Uplift SC -->
  <div class="card">
    <span class="badge">PRE-ORDER</span>
    <img src="PASTE_UPLIFT_PIC_URL_HERE" alt="Nike Uplift SC">
    <div class="info">
      <div class="name">Nike Mens Uplift SC Black/Red</div>
      <div class="sizes">Sizes: UK 4, 6, 7, 8, 8.5, 9, 9.5</div>
      <div class="price-row">
        <div class="price">R1,899.95</div>
        <div class="deposit">Deposit R950</div>
      </div>
      <div class="profit">Your Profit: R500 per pair</div>
      <a href="https://wa.me/27738303480?text=Hi Keenan, I want to pre-order Nike Uplift SC Black/Red Size ___" class="btn">Order on WhatsApp</a>
      <div class="delivery">Delivery in 7-10 Days</div>
    </div>
  </div>

</div>

</body>
</html>
