<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kavita Collections</title>
    <style>
        :root { --primary: #2c3e50; --accent: #27ae60; --bg: #f8f9fa; }
        body { font-family: 'Segoe UI', sans-serif; margin: 0; background: var(--bg); color: var(--primary); }
        header { background: white; padding: 20px; text-align: center; box-shadow: 0 2px 10px rgba(0,0,0,0.1); sticky: top; }
        .search-bar { width: 80%; max-width: 400px; padding: 12px; border-radius: 25px; border: 1px solid #ddd; margin-top: 15px; }
        .container { display: grid; grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); gap: 20px; padding: 20px; max-width: 1200px; margin: auto; }
        .product-card { background: white; border-radius: 15px; overflow: hidden; box-shadow: 0 4px 15px rgba(0,0,0,0.05); transition: 0.3s; cursor: pointer; opacity: 0; transform: translateY(20px); }
        .product-card.reveal { opacity: 1; transform: translateY(0); }
        .product-image { width: 100%; height: 350px; object-fit: cover; }
        .product-info { padding: 15px; text-align: center; }
        .product-name { font-weight: 600; font-size: 1.1rem; margin: 5px 0; }
        .product-price { color: var(--accent); font-weight: bold; }
        
        /* Modal Popup */
        #productModal { display: none; position: fixed; top:0; left:0; width:100%; height:100%; background: rgba(0,0,0,0.8); z-index: 1000; align-items: center; justify-content: center; }
        .modal-content { background: white; width: 90%; max-width: 400px; border-radius: 20px; padding: 20px; text-align: center; position: relative; }
        .modal-img { width: 100%; border-radius: 10px; margin-bottom: 15px; }
        .close-btn { position: absolute; top: 15px; right: 20px; font-size: 24px; cursor: pointer; }
        .whatsapp-btn { background: #25D366; color: white; padding: 15px; border-radius: 10px; text-decoration: none; display: block; font-weight: bold; margin-top: 15px; }
    </style>
</head>
<body>

<header>
    <h1>Kavita Collections</h1>
    <input type="text" class="search-bar" placeholder="Search sarees..." onkeyup="searchSarees()">
</header>

<div class="container" id="productGrid">
    <div class="product-card reveal" onclick="openProduct('Beautiful Designer Saree', 'Price: Contact Us', 'https://i.ibb.co/67N5PLmh/IMG-20260325-WA0002.jpg')">
        <img src="https://i.ibb.co/67N5PLmh/IMG-20260325-WA0002.jpg" class="product-image">
        <div class="product-info">
            <p class="product-name">Beautiful Designer Saree</p>
            <p class="product-price">Premium Quality</p>
        </div>
    </div>

    <div class="product-card reveal" onclick="openProduct('Elegant Party Wear', 'Price: Contact Us', 'https://i.ibb.co/B2WyL6MH/IMG-20260325-WA0003.jpg')">
        <img src="https://i.ibb.co/B2WyL6MH/IMG-20260325-WA0003.jpg" class="product-image">
        <div class="product-info">
            <p class="product-name">Elegant Party Wear</p>
            <p class="product-price">New Arrival</p>
        </div>
    </div>

    <div class="product-card reveal" onclick="openProduct('Traditional Silk Saree', 'Price: Contact Us', 'https://i.ibb.co/7NCM19TK/IMG-20260325-WA0004.jpg')">
        <img src="https://i.ibb.co/7NCM19TK/IMG-20260325-WA0004.jpg" class="product-image">
        <div class="product-info">
            <p class="product-name">Traditional Silk Saree</p>
            <p class="product-price">Best Seller</p>
        </div>
    </div>
</div>

<div id="productModal">
    <div class="modal-content">
        <span class="close-btn" onclick="closeModal()">&times;</span>
        <img id="modalImg" class="modal-img">
        <h2 id="modalName"></h2>
        <p id="modalPrice"></p>
        <a id="whatsappLink" href="#" class="whatsapp-btn">Order on WhatsApp</a>
    </div>
</div>

<script>
    function openProduct(name, price, img) {
        document.getElementById('modalName').innerText = name;
        document.getElementById('modalPrice').innerText = price;
        document.getElementById('modalImg').src = img;
        document.getElementById('whatsappLink').href = "https://wa.me/918828060929?text=Hello Kavita Collections, I want to buy: " + name;
        document.getElementById('productModal').style.display = 'flex';
    }

    function closeModal() { document.getElementById('productModal').style.display = 'none'; }

    function searchSarees() {
        let input = document.querySelector('.search-bar').value.toLowerCase();
        let cards = document.querySelectorAll('.product-card');
        cards.forEach(card => {
            let name = card.querySelector('.product-name').innerText.toLowerCase();
            card.style.display = name.includes(input) ? "block" : "none";
        });
    }

    window.onclick = function(event) {
        if (event.target == document.getElementById('productModal')) closeModal();
    }
</script>

</body>
</html>
