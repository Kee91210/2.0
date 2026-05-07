import { useEffect, useState } from "react";
import { initializeApp } from "firebase/app";
import { getFirestore, collection, getDocs, addDoc } from "firebase/firestore";

/* ---------------- FIREBASE ---------------- */

const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_AUTH_DOMAIN",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_BUCKET",
  messagingSenderId: "YOUR_ID",
  appId: "YOUR_APP_ID"
};

const app = initializeApp(firebaseConfig);
const db = getFirestore(app);

/* ---------------- LUXURY STORE ---------------- */

export default function App() {
  const [products, setProducts] = useState([]);
  const [cart, setCart] = useState([]);
  const [page, setPage] = useState("store");

  useEffect(() => {
    const load = async () => {
      const snap = await getDocs(collection(db, "products"));
      setProducts(snap.docs.map(d => ({ id: d.id, ...d.data() })));
    };
    load();
  }, []);

  const addToCart = (p) => setCart([...cart, p]);
  const removeFromCart = (id) => setCart(cart.filter(i => i.id !== id));

  const total = cart.reduce((sum, i) => sum + Number(i.price), 0);

  /* ---------------- CHECKOUT (STRIPE READY STRUCTURE) ---------------- */

  const checkout = async () => {
    await addDoc(collection(db, "orders"), {
      items: cart,
      total,
      status: "pending",
      createdAt: new Date()
    });

    alert("Order placed! Payment integration ready for Stripe/PayFast next step.");
    setCart([]);
  };

  /* ---------------- UI ---------------- */

  return (
    <div style={styles.body}>

      {/* NAVBAR */}
      <div style={styles.nav}>
        <h2>SETTLERS WAY SNEAKERS</h2>
        <p>Founded by Keenan Morrow</p>

        <div>
          <button onClick={() => setPage("store")}>Store</button>
          <button onClick={() => setPage("cart")}>Cart ({cart.length})</button>
        </div>
      </div>

      {/* STORE PAGE */}
      {page === "store" && (
        <div style={styles.grid}>
          {products.map(p => (
            <div key={p.id} style={styles.card}>
              <img src={p.img} style={styles.img} />
              <h3>{p.name}</h3>
              <p>R {p.price}</p>
              <button onClick={() => addToCart(p)}>Add to Cart</button>
            </div>
          ))}
        </div>
      )}

      {/* CART PAGE */}
      {page === "cart" && (
        <div style={styles.cart}>
          <h2>Your Cart</h2>

          {cart.map((c, i) => (
            <div key={i} style={styles.cartItem}>
              <p>{c.name} - R {c.price}</p>
              <button onClick={() => removeFromCart(c.id)}>Remove</button>
            </div>
          ))}

          <h3>Total: R {total}</h3>

          <button onClick={checkout} style={styles.checkout}>
            Checkout (PayFast / Stripe Ready)
          </button>
        </div>
      )}

      {/* WHATSAPP SUPPORT */}
      <a
        href="https://wa.me/27YOURNUMBER"
        style={styles.whatsapp}
        target="_blank"
      >
        WhatsApp Support
      </a>

    </div>
  );
}

/* ---------------- STYLES (LUXURY STREETWEAR LOOK) ---------------- */

const styles = {
  body: {
    fontFamily: "Arial",
    background: "#0a0a0a",
    color: "white",
    minHeight: "100vh"
  },

  nav: {
    padding: 20,
    background: "linear-gradient(90deg,#000,#1a1a1a)",
    textAlign: "center"
  },

  grid: {
    display: "grid",
    gridTemplateColumns: "repeat(auto-fit, minmax(220px, 1fr))",
    gap: 20,
    padding: 20
  },

  card: {
    background: "#161616",
    padding: 15,
    borderRadius: 12,
    textAlign: "center"
  },

  img: {
    width: "100%",
    borderRadius: 10
  },

  cart: {
    padding: 20
  },

  cartItem: {
    display: "flex",
    justifyContent: "space-between",
    marginBottom: 10
  },

  checkout: {
    padding: 10,
    background: "white",
    color: "black",
    border: "none",
    cursor: "pointer"
  },

  whatsapp: {
    position: "fixed",
    bottom: 20,
    right: 20,
    background: "green",
    padding: 12,
    borderRadius: 50,
    color: "white",
    textDecoration: "none"
  }
};
