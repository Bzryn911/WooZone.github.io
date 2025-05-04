
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>WooZone - Digital Products</title>
  <img src="cercle logo for my degital market with black and yellow with add my website name WooZone.jpg" alt="" type="image/x-icon">
  <style>
    body {
      font-family: 'Arial', sans-serif;
      direction: ltr;
      background: #f5f5f5;
      margin: 0;
      padding: 20px;
    }
    .hdr{
        background-color: #131A22;
        border-radius: 15px;
    }
    header {
      text-align: center;
      margin-bottom: 30px;
      color: #3d4958;
    }
    .search-filter {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      margin-bottom: 20px;
      justify-content: center;
    }
    input, select {
      padding: 10px;
      border: 1px solid #ccc;
      border-radius: 5px;
      width: 200px;
    }
    .products {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 20px;
    }
    .product {
      background: white;
      border-radius: 10px;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
      padding: 15px;
    }
    .product img {
      width: 100%;
      border-radius: 10px;
    }
    .product h3 {
      margin: 10px 0 5px;
    }
    .product p {
      color: #666;
    }
    .btn {
      display: inline-block;
      margin-top: 10px;
      background: #ff9900;
      color: white;
      padding: 10px 15px;
      border-radius: 5px;
      text-decoration: none;
    }
    a{
      display:none;
    }
  </style>
</head>
<body>
 <div class="hdr">
    <header>
    <h1>🛍️ WooZone - Top Digital Products</h1>
  </header>

  <div class="search-filter">
    <input type="text" id="searchInput" placeholder="🔎 Search for a product...">
    <select id="categoryFilter">
      <option value="">All Categories</option>
      <option value="Phone">Phones</option>
      <option value="Headphone">Headphones</option>
      <option value="Watch">Watches</option>
    </select>
    <select id="priceFilter">
      <option value="">All Prices</option>
      <option value="low">Less than 100 TND</option>
      <option value="mid">100 - 300 TND</option>
      <option value="high">More than 300 TND</option>
    </select>
  </div>
</div>
  <div class="products" id="productList">
    <div class="product" data-category="Phone" data-price="450">
      <img src="31AxYznKcrL._AC_US100_.jpg/300x200" alt="Phone">
      <h3>Stanley Quencher H2.0 </h3>
      <p>Stanley Quencher H2.0 Tumbler with Handle and Straw 40 oz | Flowstate 3-Position Lid | Cup Holder Compatible for Travel | Insulated Stainless Steel Cup | BPA-Free | Stargaze</p>
      <a class="btn" href="https://kol.jumia.com/yourlink">Buy Now</a>
    </div>

    <div class="product" data-category="Headphone" data-price="80">
      <img src="https://via.placeholder.com/300x200" alt="Headphone">
      <h3>Xiaomi Bluetooth Headset</h3>
      <p>Clear Sound - 20h Battery</p>
      <a class="btn" href="https://kol.jumia.com/yourlink">Buy Now</a>
    </div>

    <div class="product" data-category="Watch" data-price="120">
      <img src="https://via.placeholder.com/300x200" alt="Watch">
      <h3>HW12 Smartwatch</h3>
      <p>Health Tracking - Stylish Design</p>
      <a class="btn" href="https://kol.jumia.com/yourlink">Buy Now</a>
    </div>
  </div>

  <script>
    const searchInput = document.getElementById('searchInput');
    const categoryFilter = document.getElementById('categoryFilter');
    const priceFilter = document.getElementById('priceFilter');
    const products = document.querySelectorAll('.product');

    function filterProducts() {
      const searchText = searchInput.value.toLowerCase();
      const selectedCategory = categoryFilter.value;
      const selectedPrice = priceFilter.value;

      products.forEach(product => {
        const title = product.querySelector('h3').textContent.toLowerCase();
        const category = product.dataset.category;
        const price = parseFloat(product.dataset.price);

        let isVisible = title.includes(searchText);

        if (selectedCategory && category !== selectedCategory) isVisible = false;

        if (selectedPrice === 'low' && price >= 100) isVisible = false;
        if (selectedPrice === 'mid' && (price < 100 || price > 300)) isVisible = false;
        if (selectedPrice === 'high' && price <= 300) isVisible = false;

        product.style.display = isVisible ? 'block' : 'none';
      });
    }

    searchInput.addEventListener('input', filterProducts);
    categoryFilter.addEventListener('change', filterProducts);
    priceFilter.addEventListener('change', filterProducts);
  </script>
</body>
</html>
