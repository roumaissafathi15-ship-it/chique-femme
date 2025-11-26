<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Boutique Féminine</title>
  <style>
    body {font-family: Arial, sans-serif;margin: 0;background-color: #f9f9f9;}
    header {background-color: #e91e63;color: white;padding: 20px;text-align: center;font-size: 24px;}
    nav {display: flex;justify-content: center;background-color: #fff;padding: 15px;gap: 20px;border-bottom: 2px solid #eee;}
    nav a {text-decoration: none;color: #e91e63;font-weight: bold;}
    .hero {background-color: #ffe4ec;text-align: center;padding: 60px 20px;font-size: 26px;color: #c2185b;}
    .section {padding: 40px 20px;}
    .products {display: grid;grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));gap: 20px;}
    .product-card {background-color: white;padding: 15px;border-radius: 10px;box-shadow: 0 0 10px rgba(0,0,0,0.1);text-align: center;cursor: pointer;}
    .product-card img {width: 100%;border-radius: 10px;}
    .product-card h3 {color: #e91e63;}
    button {background-color: #e91e63;color: white;padding: 10px 15px;border: none;border-radius: 8px;cursor: pointer;margin-top: 10px;}
    button:hover {opacity: 0.8;}
    footer {background-color: #e91e63;color: white;padding: 20px;text-align: center;margin-top: 40px;}

    /* Contact Form */
    form {display: flex;flex-direction: column;gap: 10px;max-width: 400px;margin: auto;background: white;padding: 20px;border-radius: 10px;box-shadow: 0 0 10px rgba(0,0,0,0.1);}
    input, textarea {padding: 10px;border: 1px solid #ccc;border-radius: 5px;}

    /* Panier */
    #cart {position: fixed;top: 20px;right: 20px;background: white;padding: 20px;border-radius: 10px;box-shadow: 0 0 10px rgba(0,0,0,0.2);width: 260px;max-height: 70vh;overflow:auto;}

    /* Modal Produit */
    #modal {display: none;position: fixed;top: 0;left: 0;width: 100%;height: 100%;background: rgba(0,0,0,0.6);justify-content: center;align-items: center;}
    #modal[aria-hidden="false"] {display:flex;}
    #modal-content {background: white;padding: 20px;border-radius: 10px;width: 350px;text-align: center;max-width:90%;}
    #modal img {width: 100%;border-radius: 10px;}
    .cart-item {display:flex;justify-content:space-between;align-items:center;margin-bottom:8px;}
    .small {font-size:13px;color:#666;}
    .remove-btn {background:#f44336;border:none;color:white;border-radius:6px;padding:4px 8px;cursor:pointer;margin-left:8px;}
  </style>
</head>
<body>
  <header>Boutique Féminine</header>

  <nav>
    <a href="#cuisine">Cuisine</a>
    <a href="#accessoires">Accessoires</a>
    <a href="#vetements">Vêtements</a>
    <a href="#contact">Contact</a>
  </nav>

  <div class="hero">Bienvenue dans votre boutique dédiée aux femmes ❤</div>

  <div id="cart" aria-live="polite">
    <h3>Panier</h3>
    <ul id="cart-list" style="padding:0;margin:0 0 8px 0;list-style:none;"></ul>
    <p>Total: <strong><span id="total">0</span> Dh</strong></p>
    <button onclick="checkout()">Payer</button>
  </div>

  <!-- Modal produit -->
  <div id="modal" aria-hidden="true">
    <div id="modal-content" role="dialog" aria-modal="true">
      <h2 id="modal-title"></h2>
      <img id="modal-img" src="" alt="" />
      <p id="modal-price" class="small"></p>
      <div style="display:flex;gap:8px;justify-content:center;margin-top:10px">
        <button id="modal-add">Ajouter au panier</button>
        <button onclick="closeModal()">Fermer</button>
      </div>
    </div>
  </div>

  <section class="section" id="cuisine">
    <h2>Articles de cuisine</h2>
    <div class="products">
      <div class="product-card" onclick="openModal('Ustensiles Premium',120,'https://via.placeholder.com/200')">
        <img src="https://via.placeholder.com/200" alt="Ustensiles premium" />
        <h3>Ustensiles Premium</h3>
        <p>120 Dh</p>
      </div>
      <div class="product-card" onclick="openModal('Moules à pâtisserie',80,'https://via.placeholder.com/200')">
        <img src="https://via.placeholder.com/200" alt="Moules à pâtisserie" />
        <h3>Moules à pâtisserie</h3>
        <p>80 Dh</p>
      </div>
    </div>
  </section>

  <section class="section" id="accessoires">
    <h2>Accessoires</h2>
    <div class="products">
      <div class="product-card" onclick="openModal('Sac élégant',200,'https://via.placeholder.com/200')">
        <img src="https://via.placeholder.com/200" alt="Sac élégant" />
        <h3>Sac élégant</h3>
        <p>200 Dh</p>
      </div>
      <div class="product-card" onclick="openModal('Montre femme',150,'https://via.placeholder.com/200')">
        <img src="https://via.placeholder.com/200" alt="Montre femme" />
        <h3>Montre femme</h3>
        <p>150 Dh</p>
      </div>
    </div>
  </section>

  <section class="section" id="vetements">
    <h2>Vêtements</h2>
    <div class="products">
      <div class="product-card" onclick="openModal('Robe moderne',300,'https://via.placeholder.com/200')">
        <img src="https://via.placeholder.com/200" alt="Robe moderne" />
        <h3>Robe moderne</h3>
        <p>300 Dh</p>
      </div>
      <div class="product-card" onclick="openModal('Hijab premium',90,'https://via.placeholder.com/200')">
        <img src="https://via.placeholder.com/200" alt="Hijab premium" />
        <h3>Hijab premium</h3>
        <p>90 Dh</p>
      </div>
    </div>
  </section>

  <section class="section" id="contact">
    <h2>Contact</h2>
    <form id="contact-form">
      <input type="text" id="contact-name" placeholder="Votre nom" required />
      <input type="email" id="contact-email" placeholder="Votre email" required />
      <textarea id="contact-msg" placeholder="Votre message" required></textarea>
      <button type="submit">Envoyer</button>
    </form>
  </section>

  <footer>© 2025 Boutique Féminine – Tous droits réservés</footer>

  <script>
    // Persistance simple du panier
    const CART_KEY = 'boutique_feminine_cart_v1';

    function loadCart() {
      try {
        return JSON.parse(localStorage.getItem(CART_KEY)) || [];
      } catch (e) {
        return [];
      }
    }
    function saveCart(cart) {
      localStorage.setItem(CART_KEY, JSON.stringify(cart));
    }

    // UI / logique panier
    function renderCart() {
      const cart = loadCart();
      const list = document.getElementById('cart-list');
      list.innerHTML = '';
      let total = 0;
      cart.forEach((it) => {
        total += it.price * it.qty;
        const li = document.createElement('li');
        li.className = 'cart-item';
        li.innerHTML = `<span>${it.title} <small class="small">(${it.qty}×${it.price})</small></span>
                        <span>
                          <button class="remove-btn" onclick="removeItem('${it.id}')">suppr</button>
                        </span>`;
        list.appendChild(li);
      });
      document.getElementById('total').textContent = total;
    }

    function addToCart(item, price) {
      const cart = loadCart();
      // generate simple id from title (or use timestamp)
      let id = item.replace(/\s+/g, '-').toLowerCase();
      // if same title exists, treat as same product
      let existing = cart.find(c => c.id === id);
      if (existing) {
        existing.qty += 1;
      } else {
        cart.push({ id, title: item, price: price, qty: 1 });
      }
      saveCart(cart);
      renderCart();
    }

    function removeItem(id) {
      let cart = loadCart();
      cart = cart.filter(i => i.id !== id);
      saveCart(cart);
      renderCart();
    }

    function checkout() {
      alert('Système de paiement à venir !');
    }

    // Modal logic
    const modal = document.getElementById('modal');
    function openModal(name, price, img) {
      document.getElementById('modal-title').textContent = name;
      document.getElementById('modal-price').textContent = price + ' Dh';
      const imgEl = document.getElementById('modal-img');
      imgEl.src = img;
      imgEl.alt = name;
      const btn = document.getElementById('modal-add');
      btn.onclick = () => {
        addToCart(name, price);
        closeModal();
      };
      modal.setAttribute('aria-hidden', 'false');
    }

    function closeModal() {
      modal.setAttribute('aria-hidden', 'true');
    }

    // close modal when clicking outside content
    document.getElementById('modal').addEventListener('click', function(e) {
      if (e.target === this) closeModal();
    });
    // close on escape
    document.addEventListener('keydown', function(e) {
      if (e.key === 'Escape') closeModal();
    });

    // contact form: prevent actual submit (demo)
    document.getElementById('contact-form').addEventListener('submit', function(e) {
      e.preventDefault();
      const n = document.getElementById('contact-name').value.trim();
      const em = document.getElementById('contact-email').value.trim();
      const msg = document.getElementById('contact-msg').value.trim();
      if (!n || !em || !msg) {
        alert('Remplis tous les champs s\'il te plaît.');
        return;
      }
      alert('Message envoyé (demo). Merci !');
      this.reset();
    });

    // init
    document.addEventListener('DOMContentLoaded', function() {
      renderCart();
    });
  </script>
</body>
</html>
# chique-femme
