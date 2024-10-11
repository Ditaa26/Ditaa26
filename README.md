- 👋 Hi, I’m @Ditaa26
```sh
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Permanan's Food</title>
    <link rel="stylesheet" href="styless.css">
</head>
<body>

    <section id="banner">
        <img src="restaurant.jpg" alt="Restaurant Banner" class="banner-img">
        <div class="banner-text">
            <h1>Welcome to Permanan's Restaurant</h1>
            <p>Authentic Indonesian Cuisine with a Modern Twist</p>
        </div>
    </section>

    <!-- Home Section -->
    <section id="home">
        <h1>Permanan's Zone!</h1>
        <input type="text" placeholder="Apa yang anda cari?">
    </section>

    <!-- Menu Favorit Section -->
<section id="menu-favorit">
    <h2>Menu Favorit</h2>
    <div class="food-items">
        <div class="food-item">
            <img src="soto.jpg" alt="Soto Sapi" class="menu-img">
            <h3>Soto Sapi Anti Galau</h3>
            <p>Rp 150.000</p>
            <p>Kalori: 500 kcal</p>
            <div class="quantity-controls">
                <button onclick="decreaseQuantity('Soto Sapi Anti Galau', 150000, 500, 25, 30, 'green')">-</button>
                <span id="quantity-Soto-Sapi-Anti-Galau">0</span>
                <button onclick="increaseQuantity('Soto Sapi Anti Galau', 150000, 500, 25, 30, 'green')">+</button>
            </div>
        </div>
        <div class="food-item">
            <img src="ayam_bakar.jpg" alt="Ayam Bakar" class="menu-img">
            <h3>Ayam Bakar dengan Sambal</h3>
            <p>Rp 100.000</p>
            <p>Kalori: 600 kcal</p>
            <div class="quantity-controls">
                <button onclick="decreaseQuantity('Ayam Bakar dengan Sambal', 100000, 600, 35, 20, 'red')">-</button>
                <span id="quantity-Ayam-Bakar-dengan-Sambal">0</span>
                <button onclick="increaseQuantity('Ayam Bakar dengan Sambal', 100000, 600, 35, 20, 'red')">+</button>
            </div>
        </div>
    </div>
</section>

  <!-- Menu Biasa Section -->
<section id="menu-biasa">
    <h2>Menu Biasa</h2>
    <div class="food-items">
        <div class="food-item">
            <img src="seblak.jpg" alt="Seblak Kaki Tua" class="menu-img">
            <h3>Seblak Kaki Tua</h3>
            <p>Rp 50.000</p>
            <p>Kalori: 300 kcal</p>
            <div class="quantity-controls">
                <button onclick="decreaseQuantity('Seblak Kaki Tua', 50000, 300, 10, 15, 'yellow')">-</button>
                <span id="quantity-Seblak-Kaki-Tua">0</span>
                <button onclick="increaseQuantity('Seblak Kaki Tua', 50000, 300, 10, 15, 'yellow')">+</button>
            </div>
        </div>
        <div class="food-item">
            <img src="esteh.jpg" alt="Es Teh Manis" class="menu-img">
            <h3>Es Teh Manis</h3>
            <p>Rp 5.000</p>
            <p>Kalori: 90 kcal</p>
            <div class="quantity-controls">
                <button onclick="decreaseQuantity('Es Teh Manis', 5000, 90, 0, 0, 'green')">-</button>
                <span id="quantity-Es-Teh-Manis">0</span>
                <button onclick="increaseQuantity('Es Teh Manis', 5000, 90, 0, 0, 'green')">+</button>
            </div>
        </div>
    </div>
</section>

    <!-- Nutrition Information -->
    <section id="nutrition-info">
        <h3>Nutrition Details</h3>
        <p id="selected-item">Select an item to see its nutrition details.</p>
        <div id="nutrition-details">
            <p id="calories"></p>
            <p id="protein"></p>
            <p id="fat"></p>
        </div>
        <div id="nutrition-color"></div>
    </section>

    <!-- Payment Section -->
    <section id="payment">
        <h2>Menu Pembayaran</h2>
        <form>
            <input type="text" placeholder="Masukkan Nama" required>
            <input type="text" placeholder="Nomor Meja" required>
            <button type="submit">Bayar Sekarang</button>
        </form>
    </section>

    <!-- Cart Section -->
    <section id="cart">
        <h2>Keranjang Belanja</h2>
        <ul id="cart-items"></ul>
        <p id="cart-total">Total: Rp 0</p>
    </section>

    <!-- Tentang Restoran Section -->
<section id="tentang-restoran">
    <h2>Tentang Restoran</h2>
    <div class="about-resto">
        <div class="owner-info">
            <h3>Pemilik: Pak Permana</h3>
            <p>Pak Permana telah berpengalaman lebih dari 20 tahun di bidang kuliner, menciptakan menu-menu spesial yang terkenal dengan cita rasa otentik dan bahan-bahan segar.</p>
        </div>
        <div class="resto-info">
            <h3>Tentang Restoran</h3>
            <p>Restoran kami menawarkan beragam makanan khas Indonesia dengan suasana yang nyaman dan layanan terbaik. Kami menggunakan bahan lokal yang berkualitas dan menjamin kepuasan pelanggan dalam setiap hidangan yang disajikan.</p>
        </div>
    </div>
</section>

<!-- Ratings Section -->
<section id="ratings">
    <h2>Penilaian</h2>

    <div class="rating">
        <h3>Penilaian Restoran</h3>
        <p>⭐⭐⭐⭐⭐</p>
    </div>

    <div class="rating">
        <h3>Penilaian Makanan</h3>
        <p>⭐⭐⭐⭐</p>
    </div>
</section>

    <script>
        let cart = [];
let total = 0;

// Function to increase quantity and update cart
function increaseQuantity(item, price, calories, protein, fat, color) {
    let quantityElement = document.getElementById('quantity-' + item.replace(/\s/g, '-'));
    let currentQuantity = parseInt(quantityElement.textContent);
    quantityElement.textContent = currentQuantity + 1;

    cart.push({ item, price });
    total += price;

    updateCart();
    updateNutrition(item, price, calories, protein, fat, color);
}

// Function to decrease quantity and update cart
function decreaseQuantity(item, price, calories, protein, fat, color) {
    let quantityElement = document.getElementById('quantity-' + item.replace(/\s/g, '-'));
    let currentQuantity = parseInt(quantityElement.textContent);
    
    if (currentQuantity > 0) {
        quantityElement.textContent = currentQuantity - 1;

        // Remove one instance of the item from the cart and subtract from total
        let itemIndex = cart.findIndex(cartItem => cartItem.item === item);
        if (itemIndex > -1) {
            cart.splice(itemIndex, 1);
            total -= price;
        }

        updateCart();
        updateNutrition(item, price, calories, protein, fat, color);
    }
}

// Update Cart Section
function updateCart() {
    const cartItems = document.getElementById('cart-items');
    const cartTotal = document.getElementById('cart-total');

    cartItems.innerHTML = cart.map(cartItem => `<li>${cartItem.item} - Rp ${cartItem.price}</li>`).join('');
    cartTotal.textContent = `Total: Rp ${total}`;
}

// Update Nutrition Information
function updateNutrition(item, price, calories, protein, fat, color) {
    document.getElementById('selected-item').textContent = `Selected: ${item}`;
    document.getElementById('calories').textContent = `Kalori: ${calories} kcal`;
    document.getElementById('protein').textContent = `Protein: ${protein} g`;
    document.getElementById('fat').textContent = `Lemak: ${fat} g`;

    const nutritionColor = document.getElementById('nutrition-color');
    nutritionColor.style.backgroundColor = color;
    nutritionColor.textContent = `${calories} kcal`;
}

    </script>

</body>
</html>
```

css   
```sh
body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    background-color: #f7f7f7;
}

h1, h2 {
    text-align: center;
    background-color: #ffcc00;
    padding: 10px;
    margin: 0;
}

section {
    padding: 20px;
}

/* Banner Section */
#banner {
    position: relative;
    text-align: center;
    color: white;
    overflow: hidden;
}

/* Banner Image Styling */
.banner-img {
    width: 100%;
    max-height: 400px;
    height: auto;
    object-fit: cover;
}

/* Text Overlay */
.banner-text {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.7);
}

/* Banner Text Styling */
#banner h1 {
    font-size: 3em;
    margin: 0;
}

#banner p {
    font-size: 1.2em;
    margin: 10px 0 0;
}

/* Home Section */
#home {
    background-color: #ffeaa7;
    padding: 20px;
}

input[type="text"] {
    width: 100%;
    padding: 10px;
    margin-top: 10px;
    font-size: 16px;
}

/* Menu Section */
#menu-favorit, #menu-biasa {
    padding: 20px;
    background-color: #fff;
    border: 1px solid #ddd;
    border-radius: 10px;
    max-width: 800px;
    margin: 20px auto;
}

/* Food Items Styling */
.food-items {
    display: flex;
    justify-content: space-around;
    gap: 20px;
    flex-wrap: wrap;
}

.food-item {
    background-color: #f8f9fa;
    padding: 15px;
    width: 30%;
    text-align: center;
    box-shadow: 0px 4px 6px rgba(0,0,0,0.1);
    cursor: pointer;
    transition: transform 0.3s ease;
    border-radius: 8px;
}

.food-item:hover {
    transform: scale(1.05);
}

.food-item h3 {
    margin: 0;
    font-size: 1.2em;
    color: #2d3436;
}

.food-item p {
    margin: 8px 0;
}

/* Menu Item Image Styling */
.menu-img {
    width: 100%;
    height: auto;
    border-radius: 8px;
    margin-bottom: 10px;
}

/* Quantity Controls */
.quantity-controls {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 10px;
}

.quantity-controls button {
    background-color: #00b894;
    color: white;
    border: none;
    padding: 5px 10px;
    font-size: 16px;
    cursor: pointer;
    margin: 0 5px;
    border-radius: 5px;
}

.quantity-controls button:hover {
    background-color: #00976c;
}

.quantity-controls span {
    font-size: 18px;
    margin: 0 10px;
}

/* Nutrition Information */
#nutrition-info {
    margin-top: 20px;
    padding: 10px;
    background-color: #f1f1f1;
    border-radius: 10px;
    text-align: center;
}

#nutrition-info h3 {
    margin-bottom: 10px;
}

#nutrition-details {
    margin-top: 10px;
}

#nutrition-color {
    width: 100px;
    height: 100px;
    margin: 10px auto;
    border-radius: 50%;
    text-align: center;
    line-height: 100px;
    font-size: 18px;
    color: #fff;
}

/* Payment Section */
#payment {
    padding: 20px;
    background-color: #fff;
    border-radius: 10px;
    max-width: 800px;
    margin: 20px auto;
}

.menu-item {
    margin-bottom: 10px;
}

button {
    padding: 10px 20px;
    background-color: #00b894;
    color: white;
    border: none;
    cursor: pointer;
    font-size: 16px;
    border-radius: 5px;
}

button:hover {
    background-color: #00976c;
}

/* Cart Section */
#cart {
    padding: 20px;
    background-color: #fff;
    border-radius: 10px;
    max-width: 800px;
    margin: 20px auto;
}

#cart ul {
    list-style: none;
    padding: 0;
}

#cart li {
    margin-bottom: 10px;
}

#cart p {
    font-size: 18px;
}

/* Tentang Restoran Section */
#tentang-restoran {
    background-color: #fff;
    padding: 20px;
    border-radius: 10px;
    margin: 20px auto;
    max-width: 800px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.about-resto {
    display: flex;
    justify-content: space-between;
    gap: 20px;
}

.owner-info, .resto-info {
    flex: 1;
}

.owner-info h3, .resto-info h3 {
    margin-top: 0;
}

/* Ratings Section */
#ratings {
    background-color: #f9f9f9;
    padding: 20px;
    border-radius: 10px;
    margin: 20px auto;
    max-width: 800px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

.rating {
    margin-bottom: 15px;
}

.rating h3 {
    margin: 0;
}
```

<!---
Ditaa26/Ditaa26 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
