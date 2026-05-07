// firebase-seed.js
// Run this after initializing Firebase in your project

const seedProducts = async () => {
  const products = [
    {
      name: "Nike Air Force 1",
      price: 1899,
      type: "sneaker",
      brand: "Nike",
      img: "https://example.com/nike-af1.jpg"
    },
    {
      name: "Air Jordan 1 Retro",
      price: 2599,
      type: "sneaker",
      brand: "Jordan",
      img: "https://example.com/jordan1.jpg"
    },
    {
      name: "New Balance 550 White/Green",
      price: 2199,
      type: "sneaker",
      brand: "New Balance",
      img: "https://example.com/nb550.jpg"
    },
    {
      name: "Adidas Yeezy Boost 350 V2",
      price: 3299,
      type: "sneaker",
      brand: "Yeezy",
      img: "https://example.com/yeezy350.jpg"
    },
    {
      name: "Asics Gel-Lyte III",
      price: 1799,
      type: "sneaker",
      brand: "Asics",
      img: "https://example.com/asics-gel.jpg"
    },
    {
      name: "Timberland Classic Boot",
      price: 2999,
      type: "sneaker",
      brand: "Timberland",
      img: "https://example.com/timberland.jpg"
    },
    {
      name: "Travis Scott x Nike Dunk",
      price: 3999,
      type: "sneaker",
      brand: "Travis Scott",
      img: "https://example.com/travis-dunk.jpg"
    }
  ];

  for (let product of products) {
    try {
      await db.collection("products").add(product);
      console.log(`✅ Added ${product.name}`);
    } catch (err) {
      console.error(`❌ Error adding ${product.name}:`, err);
    }
  }
};

seedProducts();
