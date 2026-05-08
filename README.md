import { useEffect, useState } from "react";
import { initializeApp } from "firebase/app";
import {
  getFirestore,
  collection,
  getDocs,
  addDoc,
} from "firebase/firestore";

/* ---------------- FIREBASE ---------------- */

const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_AUTH_DOMAIN",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_BUCKET",
  messagingSenderId: "YOUR_ID",
  appId: "YOUR_APP_ID",
};

const app = initializeApp(firebaseConfig);
const db = getFirestore(app);

/* ---------------- LUXURY STORE ---------------- */

export default function App() {
  const [products, setProducts] = useState([]);
  const [cart, setCart] = useState([]);
  const [page, setPage] = useState("store");

  useEffect(() => {
    const loadProducts = async () => {
      try {
        const snap = await getDocs(collection(db, "products"));

        const items = snap.docs.map((doc) => ({
          id: doc.id,
          ...doc.data(),
        }));

        setProducts(items);
      } catch (err) {
        console.log("Firebase not connected yet.");

        /* DEMO PRODUCTS */
        setProducts([
          {
            id: 1,
            name: "Nike Air Force 1",
            price: 2499,
            img: "https://images.unsplash.com/photo-1542291026-7eec264c27ff",
          },
          {
            id: 2,
            name: "Jordan 4 Retro",
            price: 3999,
            img: "https://images.unsplash.com/photo-1600185365483-26d7a4cc7519",
          },
          {
            id: 3,
            name: "Yeezy Boost",
            price: 4999,
            img: "https://images.unsplash.com/photo-1605348532760-6753d2c43329",
          },
        ]);
      }
    };

    loadProducts();
  }, []);

  /* ---------------- CART ---------------- */

  const addToCart = (product) => {
    setCart([...cart, product]);
  };

  const removeFromCart = (id) => {
    setCart(cart.filter((item) => item.id !== id));
  };

  const total = cart.reduce(
    (sum, item) => sum + Number(item.price),
    0
  );

  /* ---------------- CHECKOUT ---------------- */

  const checkout = async () => {
    try {
      await addDoc(collection(db, "orders"), {
        items: cart,
        total,
        status: "pending",
        createdAt: new Date(),
      });

      alert("Order placed successfully!");
    } catch (err) {
      alert("Demo checkout complete!");
    }

    setCart([]);
  };

  /* ---------------- UI ---------------- */

  return (
    <div style={styles.body}>
      {/* NAVBAR */}
      <div style={styles.nav}>
        <h1 style={styles.logo}>SETTLERS WAY SNEAKERS</h1>

        <p style={styles.subtitle}>
          Founded by Keenan Morrow
        </p>

        <div style={styles.navButtons}>
          <button
            style={styles.button}
            onClick={() => setPage("store")}
          >
            Store
          </button>

          <button
            style={styles.button}
            onClick={() => setPage("cart")}
          >
            Cart ({cart.length})
          </button>
        </div>
      </div>

      {/* STORE PAGE */}
      {page === "store" && (
        <div style={styles.grid}>
          {products.map((p) => (
            <div key={p.id} style={styles.card}>
              <img
                src={p.img}
                alt={p.name}
                style={styles.img}
              />

              <h3>{p.name}</h3>

              <p style={styles.price}>R {p.price}</p>

              <button
                style={styles.addBtn}
                onClick={() => addToCart(p)}
              >
                Add to Cart
              </button>
            </div>
          ))}
        </div>
      )}

      {/* CART PAGE */}
      {page === "cart" && (
        <div style={styles.cart}>
          <h2>Your Cart</h2>

          {cart.length === 0 && (
            <p>Your cart is empty.</p>
          )}

          {cart.map((item, index) => (
            <div key={index} style={styles.cartItem}>
              <span>
                {item.name} - R {item.price}
              </span>

              <button
                style={styles.removeBtn}
                onClick={() => removeFromCart(item.id)}
              >
                Remove
              </button>
            </div>
          ))}

          <h2>Total: R {total}</h2>

          {cart.length > 0 && (
            <button
              style={styles.checkout}
              onClick={checkout}
            >
              Checkout
            </button>
          )}
        </div>
      )}

      {/* WHATSAPP SUPPORT */}
      <a
        href="https://wa.me/27700000000"
        target="_blank"
        rel="noreferrer"
        style={styles.whatsapp}
      >
        WhatsApp
      </a>
    </div>
  );
}

/* ---------------- STYLES ---------------- */

const styles = {
  body: {
    fontFamily: "Arial, sans-serif",
    background: "#0a0a0a",
    color: "white",
    minHeight: "100vh",
    margin: 0,
  },

  nav: {
    background: "linear-gradient(90deg,#000,#1a1a1a)",
    padding: 20,
    textAlign: "center",
    borderBottom: "1px solid #333",
  },

  logo: {
    margin: 0,
    fontSize: 32,
    letterSpacing: 2,
  },

  subtitle: {
    color: "#999",
    marginBottom: 20,
  },

  navButtons: {
    display: "flex",
    justifyContent: "center",
    gap: 10,
  },

  button: {
    padding: "10px 20px",
    border: "none",
    background: "white",
    color: "black",
    cursor: "pointer",
    borderRadius: 6,
    fontWeight: "bold",
  },

  grid: {
    display: "grid",
    gridTemplateColumns: "repeat(auto-fit,minmax(250px,1fr))",
    gap: 20,
    padding: 20,
  },

  card: {
    background: "#161616",
    borderRadius: 12,
    padding: 15,
    textAlign: "center",
    boxShadow: "0 0 10px rgba(0,0,0,0.4)",
  },

  img: {
    width: "100%",
    height: 250,
    objectFit: "cover",
    borderRadius: 10,
  },

  price: {
    fontSize: 20,
    fontWeight: "bold",
  },

  addBtn: {
    padding: "10px 20px",
    background: "white",
    color: "black",
    border: "none",
    cursor: "pointer",
    borderRadius: 6,
    fontWeight: "bold",
  },

  cart: {
    padding: 20,
    maxWidth: 700,
    margin: "auto",
  },

  cartItem: {
    display: "flex",
    justifyContent: "space-between",
    alignItems: "center",
    background: "#1a1a1a",
    padding: 15,
    marginBottom: 10,
    borderRadius: 8,
  },

  removeBtn: {
    background: "red",
    color: "white",
    border: "none",
    padding: "8px 12px",
    borderRadius: 6,
    cursor: "pointer",
  },

  checkout: {
    marginTop: 20,
    padding: "12px 20px",
    background: "limegreen",
    color: "white",
    border: "none",
    borderRadius: 8,
    cursor: "pointer",
    fontWeight: "bold",
    fontSize: 16,
  },

  whatsapp: {
    position: "fixed",
    bottom: 20,
    right: 20,
    background: "#25D366",
    color: "white",
    padding: "12px 18px",
    borderRadius: 50,
    textDecoration: "none",
    fontWeight: "bold",
    boxShadow: "0 0 10px rgba(0,0,0,0.4)",
  },
};
