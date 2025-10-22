<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>دكانك Pro - متجرك الشخصي</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">
  <style>
    :root {
      --primary: #e74c3c;
      --dark: #2c3e50;
      --light: #f8f9fa;
      --gray: #95a5a6;
      --success: #27ae60;
    }
    * { margin: 0; padding: 0; box-sizing: border-box; font-family: 'Tajawal', Tahoma, sans-serif; }
    body {
      background: #fafafa;
      color: var(--dark);
      overflow-x: hidden;
    }
    .screen {
      display: none;
      min-height: 100vh;
    }
    .active {
      display: block;
    }
    .center-box {
      max-width: 450px;
      margin: 0 auto;
      background: white;
      padding: 40px;
      border-radius: 20px;
      box-shadow: 0 10px 30px rgba(0,0,0,0.1);
      text-align: center;
    }
    .logo {
      font-size: 32px;
      color: var(--primary);
      margin-bottom: 25px;
      font-weight: 800;
    }
    .logo i { margin-left: 10px; }
    .btn {
      display: block;
      width: 100%;
      padding: 16px;
      margin: 15px 0;
      border: none;
      border-radius: 12px;
      font-size: 17px;
      font-weight: 700;
      cursor: pointer;
      transition: 0.3s;
    }
    .btn-primary {
      background: var(--primary);
      color: white;
    }
    .btn-primary:hover {
      background: #c0392b;
    }
    .btn-outline {
      background: transparent;
      color: var(--primary);
      border: 2px solid var(--primary);
    }
    .btn-outline:hover {
      background: #fdf7f7;
    }
    .back-link {
      display: inline-block;
      margin-top: 20px;
      color: #3498db;
      text-decoration: none;
      font-weight: 600;
    }
    .form-group {
      margin: 15px 0;
      text-align: right;
    }
    .form-group label {
      display: block;
      margin-bottom: 8px;
      font-weight: 600;
    }
    .form-group input {
      width: 100%;
      padding: 14px;
      border: 1px solid #ddd;
      border-radius: 10px;
      font-size: 16px;
      direction: ltr;
      text-align: left;
    }
    .form-group input::placeholder {
      direction: rtl;
      text-align: right;
    }
    .alert {
      padding: 12px;
      margin: 15px 0;
      border-radius: 10px;
      text-align: center;
      font-weight: 600;
      display: none;
    }
    .alert-error {
      background: #ffebee;
      color: #c62828;
    }
    .alert-success {
      background: #e8f5e9;
      color: #2e7d32;
    }

    /* =============== لوحة التحكم =============== */
    #dashboard {
      background: #f5f7fa;
    }
    header {
      background: white;
      box-shadow: 0 2px 12px rgba(0,0,0,0.1);
      padding: 16px 5%;
      display: flex;
      justify-content: space-between;
      align-items: center;
      position: sticky;
      top: 0;
      z-index: 100;
    }
    .nav-links {
      display: flex;
      gap: 20px;
    }
    .nav-links button {
      background: none;
      border: none;
      font-size: 16px;
      font-weight: 600;
      color: var(--dark);
      cursor: pointer;
      padding: 6px 0;
    }
    .nav-links button.active {
      color: var(--primary);
      border-bottom: 2px solid var(--primary);
    }
    .cart-icon {
      position: relative;
      font-size: 24px;
      cursor: pointer;
      color: var(--dark);
    }
    .cart-count {
      position: absolute;
      top: -8px;
      left: -8px;
      background: var(--primary);
      color: white;
      border-radius: 50%;
      width: 20px;
      height: 20px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 12px;
      font-weight: bold;
    }
    .logout-btn {
      background: none;
      border: none;
      color: var(--gray);
      cursor: pointer;
      font-size: 18px;
      margin-left: 15px;
    }

    main {
      max-width: 1200px;
      margin: 30px auto;
      padding: 0 20px;
    }

    .section-title {
      font-size: 22px;
      margin: 25px 0 20px;
      color: var(--dark);
      display: flex;
      align-items: center;
      gap: 10px;
    }

    /* =============== لوحة التحكم =============== */
    .admin-form {
      background: white;
      padding: 25px;
      border-radius: 16px;
      box-shadow: 0 6px 18px rgba(0,0,0,0.08);
      margin-bottom: 30px;
    }
    .form-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 20px;
      margin-bottom: 20px;
    }
    .image-preview {
      width: 120px;
      height: 120px;
      border: 2px dashed #ccc;
      border-radius: 10px;
      display: flex;
      align-items: center;
      justify-content: center;
      margin-top: 10px;
      overflow: hidden;
    }
    .image-preview img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
    .image-preview i {
      font-size: 30px;
      color: #ccc;
    }

    /* =============== المنتجات =============== */
    .products-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
      gap: 25px;
    }
    .product-card {
      background: white;
      border-radius: 14px;
      overflow: hidden;
      box-shadow: 0 4px 12px rgba(0,0,0,0.08);
      transition: transform 0.3s;
    }
    .product-card:hover { transform: translateY(-5px); }
    .product-img {
      width: 100%;
      height: 180px;
      object-fit: cover;
      background: #f0f0f0;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 40px;
      color: #ddd;
    }
    .product-info {
      padding: 18px;
    }
    .product-info h3 {
      font-size: 18px;
      margin-bottom: 8px;
      min-height: 48px;
    }
    .price { color: var(--primary); font-weight: 800; font-size: 20px; margin: 10px 0; }
    .add-btn {
      width: 100%;
      padding: 10px;
      background: #f8f9fa;
      color: var(--primary);
      border: 1px solid var(--primary);
      border-radius: 8px;
      cursor: pointer;
      font-weight: 600;
    }

    /* =============== الإحصائيات =============== */
    .stats-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
      gap: 20px;
      margin-bottom: 30px;
    }
    .stat-card {
      background: white;
      padding: 20px;
      border-radius: 14px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.05);
      text-align: center;
    }
    .stat-value {
      font-size: 28px;
      font-weight: 800;
      margin: 10px 0;
      color: var(--primary);
    }
    .stat-label { color: var(--gray); font-size: 15px; }

    /* =============== السلة =============== */
    .modal {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0,0,0,0.7);
      z-index: 2000;
      justify-content: center;
      align-items: center;
    }
    .modal-content {
      background: white;
      width: 90%;
      max-width: 550px;
      border-radius: 18px;
      max-height: 85vh;
      overflow-y: auto;
    }
    .modal-header {
      padding: 20px;
      border-bottom: 1px solid #eee;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }
    .close-modal { font-size: 28px; cursor: pointer; color: #aaa; }
    .cart-items { padding: 0 20px; }
    .cart-item {
      display: flex;
      justify-content: space-between;
      padding: 14px 0;
      border-bottom: 1px solid #f5f5f5;
    }
    .total {
      padding: 20px;
      font-size: 22px;
      font-weight: 800;
      text-align: right;
      border-top: 2px solid #eee;
      color: var(--primary);
    }
    .checkout-btn {
      width: 100%;
      padding: 16px;
      background: var(--success);
      color: white;
      border: none;
      font-size: 18px;
      font-weight: 800;
      border-radius: 0 0 18px 18px;
      cursor: pointer;
    }

    .empty { text-align: center; padding: 50px 20px; color: var(--gray); }
    footer { text-align: center; padding: 30px; color: var(--gray); font-size: 14px; margin-top: 40px; border-top: 1px solid #eee; }

    @media (max-width: 768px) {
      .nav-links { display: none; }
      .form-grid { grid-template-columns: 1fr; }
    }
  </style>
</head>
<body>

<!-- شاشة البداية -->
<div id="welcome" class="screen active">
  <div class="center-box">
    <div class="logo"><i class="fas fa-store"></i> دكانك Pro</div>
    <p style="margin: 20px 0; color: #7f8c8d;">أنشئ متجرك الإلكتروني الاحترافي في دقائق!</p>
    <button class="btn btn-primary" onclick="showScreen('signup')">
      <i class="fas fa-user-plus"></i> إنشاء حساب
    </button>
    <button class="btn btn-outline" onclick="showScreen('login')">
      <i class="fas fa-sign-in-alt"></i> تسجيل الدخول
    </button>
  </div>
</div>

<!-- شاشة التسجيل -->
<div id="signup" class="screen">
  <div class="center-box">
    <div class="logo"><i class="fas fa-user-plus"></i> إنشاء حساب</div>
    <div id="signup-error" class="alert alert-error"></div>
    <div id="signup-success" class="alert alert-success"></div>
    
    <div class="form-group">
      <label for="su-username">اسم المستخدم</label>
      <input type="text" id="su-username" placeholder="اختر اسمًا فريدًا" autocomplete="off">
    </div>
    <div class="form-group">
      <label for="su-password">كلمة السر</label>
      <input type="password" id="su-password" placeholder="6 أحرف على الأقل">
    </div>
    <button class="btn btn-primary" onclick="handleSignup()">
      <i class="fas fa-user-plus"></i> إنشاء الحساب
    </button>
    <a href="#" class="back-link" onclick="showScreen('welcome')">← العودة</a>
  </div>
</div>

<!-- شاشة الدخول -->
<div id="login" class="screen">
  <div class="center-box">
    <div class="logo"><i class="fas fa-sign-in-alt"></i> تسجيل الدخول</div>
    <div id="login-error" class="alert alert-error"></div>
    
    <div class="form-group">
      <label for="li-username">اسم المستخدم</label>
      <input type="text" id="li-username" placeholder="أدخل اسم المستخدم" autocomplete="off">
    </div>
    <div class="form-group">
      <label for="li-password">كلمة السر</label>
      <input type="password" id="li-password" placeholder="أدخل كلمة السر">
    </div>
    <button class="btn btn-primary" onclick="handleLogin()">
      <i class="fas fa-sign-in-alt"></i> دخول
    </button>
    <a href="#" class="back-link" onclick="showScreen('welcome')">← العودة</a>
  </div>
</div>

<!-- لوحة التحكم (بعد الدخول) -->
<div id="dashboard" class="screen">
  <header>
    <div class="logo"><i class="fas fa-store"></i> دكانك Pro</div>
    <div class="nav-links">
      <button class="tab-btn active" data-tab="shop">المتجر</button>
      <button class="tab-btn" data-tab="admin">إضافة منتج</button>
      <button class="tab-btn" data-tab="stats">الإحصائيات</button>
    </div>
    <div style="display:flex; align-items:center; gap:15px;">
      <div class="cart-icon" onclick="openCart()">
        <i class="fas fa-shopping-cart"></i>
        <span class="cart-count" id="cart-count">0</span>
      </div>
      <button class="logout-btn" onclick="logout()" title="تسجيل الخروج">
        <i class="fas fa-sign-out-alt"></i>
      </button>
    </div>
  </header>

  <main>
    <!-- المتجر -->
    <section id="shop-section" class="tab-content">
      <h2 class="section-title"><i class="fas fa-shopping-bag"></i> منتجاتنا</h2>
      <div class="products-grid" id="products-list"></div>
    </section>

    <!-- لوحة التحكم -->
    <section id="admin-section" class="tab-content" style="display:none;">
      <h2 class="section-title"><i class="fas fa-plus-circle"></i> أضف منتج جديد</h2>
      <div class="admin-form">
        <div class="form-grid">
          <div class="form-group">
            <label>اسم المنتج *</label>
            <input type="text" id="prod-name" placeholder="مثال: قميص رجالي">
          </div>
          <div class="form-group">
            <label>السعر (درهم) *</label>
            <input type="number" id="prod-price" placeholder="مثال: 150" min="1">
          </div>
          <div class="form-group">
            <label>الصورة *</label>
            <input type="file" id="prod-image" accept="image/*" onchange="previewImage(event)">
            <div class="image-preview" id="image-preview">
              <i class="fas fa-cloud-upload-alt"></i>
            </div>
          </div>
        </div>
        <button class="btn btn-primary" onclick="addProduct()">
          <i class="fas fa-save"></i> حفظ المنتج
        </button>
      </div>
    </section>

    <!-- الإحصائيات -->
    <section id="stats-section" class="tab-content" style="display:none;">
      <h2 class="section-title"><i class="fas fa-chart-bar"></i> إحصائيات المبيعات</h2>
      <div class="stats-grid">
        <div class="stat-card">
          <div class="stat-label">إجمالي المبيعات</div>
          <div class="stat-value" id="total-sales">0</div>
          <div>درهم</div>
        </div>
        <div class="stat-card">
          <div class="stat-label">عدد الطلبات</div>
          <div class="stat-value" id="total-orders">0</div>
        </div>
        <div class="stat-card">
          <div class="stat-label">أكثر منتج مبيعاً</div>
          <div class="stat-value" id="best-seller">-</div>
        </div>
        <div class="stat-card">
          <div class="stat-label">أقل منتج مبيعاً</div>
          <div class="stat-value" id="worst-seller">-</div>
        </div>
      </div>

      <h3 class="section-title"><i class="fas fa-list"></i> سجل المبيعات</h3>
      <div id="sales-log" style="background:white;padding:20px;border-radius:12px;box-shadow:0 4px 12px rgba(0,0,0,0.05);">
        <div id="sales-list" style="max-height:300px;overflow-y:auto;"></div>
        <div id="no-sales" class="empty" style="padding:20px;">لا توجد مبيعات بعد</div>
      </div>
    </section>
  </main>

  <!-- سلة التسوق -->
  <div class="modal" id="cart-modal">
    <div class="modal-content">
      <div class="modal-header">
        <h2><i class="fas fa-shopping-cart"></i> سلة التسوق</h2>
        <span class="close-modal" onclick="closeCart()">&times;</span>
      </div>
      <div class="cart-items" id="cart-items"></div>
      <div class="total">المجموع: <span id="cart-total">0</span> درهم</div>
      <button class="checkout-btn" onclick="checkout()">
        <i class="fas fa-check-circle"></i> اتمام الطلب
      </button>
    </div>
  </div>

  <footer>
    <p>© 2025 دكانك Pro — متجرك الإلكتروني الشخصي</p>
  </footer>
</div>

<script>
  // === دوال مساعدة ===
  function getCurrentUser() {
    return localStorage.getItem('current_user');
  }

  function getUserKey() {
    const user = getCurrentUser();
    return user ? 'user_' + user : null;
  }

  function saveData(key, data) {
    localStorage.setItem(key, JSON.stringify(data));
  }

  function loadData(key) {
    const data = localStorage.getItem(key);
    return data ? JSON.parse(data) : null;
  }

  // === عرض الشاشات ===
  function showScreen(screenId) {
    document.querySelectorAll('.screen').forEach(el => {
      el.classList.remove('active');
    });
    document.getElementById(screenId).classList.add('active');
  }

  // === إنشاء حساب ===
  function handleSignup() {
    const username = document.getElementById('su-username').value.trim();
    const password = document.getElementById('su-password').value;
    const errorEl = document.getElementById('signup-error');
    const successEl = document.getElementById('signup-success');

    errorEl.style.display = 'none';
    successEl.style.display = 'none';

    if (!username || !password) {
      showError(errorEl, 'الرجاء ملء جميع الحقول.');
      return;
    }

    if (password.length < 6) {
      showError(errorEl, 'كلمة السر يجب أن تكون 6 أحرف على الأقل.');
      return;
    }

    const userKey = 'user_' + username;
    if (loadData(userKey)) {
      showError(errorEl, 'اسم المستخدم موجود مسبقاً.');
      return;
    }

    saveData(userKey, { username, password, createdAt: new Date().toISOString() });
    saveData(userKey + '_products', []);
    saveData(userKey + '_cart', []);
    saveData(userKey + '_sales', []);

    showSuccess(successEl, 'تم إنشاء الحساب بنجاح!');
    setTimeout(() => {
      document.getElementById('li-username').value = username;
      showScreen('login');
    }, 1500);
  }

  // === تسجيل الدخول ===
  function handleLogin() {
    const username = document.getElementById('li-username').value.trim();
    const password = document.getElementById('li-password').value;
    const errorEl = document.getElementById('login-error');

    errorEl.style.display = 'none';

    if (!username || !password) {
      showError(errorEl, 'الرجاء إدخال اسم المستخدم وكلمة السر.');
      return;
    }

    const userKey = 'user_' + username;
    const user = loadData(userKey);

    if (!user || user.password !== password) {
      showError(errorEl, 'بيانات الدخول غير صحيحة.');
      return;
    }

    localStorage.setItem('current_user', username);
    showScreen('dashboard');
    renderProducts();
    updateCartUI();
  }

  // === تسجيل الخروج ===
  function logout() {
    localStorage.removeItem('current_user');
    showScreen('welcome');
  }

  // === حذف الحساب ===
  function deleteAccount() {
    if (!confirm('هل أنت متأكد؟ سيتم حذف حسابك وجميع بياناتك نهائياً!')) return;

    const user = getCurrentUser();
    if (user) {
      const userKey = 'user_' + user;
      localStorage.removeItem(userKey);
      localStorage.removeItem(userKey + '_products');
      localStorage.removeItem(userKey + '_cart');
      localStorage.removeItem(userKey + '_sales');
      localStorage.removeItem('current_user');
    }

    alert('تم حذف حسابك بنجاح.');
    showScreen('welcome');
  }

  // === رفع الصورة ===
  let currentImageBase64 = '';
  function previewImage(event) {
    const file = event.target.files[0];
    if (!file) return;
    const reader = new FileReader();
    reader.onload = function(e) {
      currentImageBase64 = e.target.result;
      document.getElementById('image-preview').innerHTML = `<img src="${e.target.result}" alt="Preview">`;
    };
    reader.readAsDataURL(file);
  }

  // === إدارة المنتجات ===
  function getProducts() {
    const userKey = getUserKey();
    return userKey ? loadData(userKey + '_products') || [] : [];
  }

  function saveProducts(products) {
    const userKey = getUserKey();
    if (userKey) saveData(userKey + '_products', products);
  }

  function addProduct() {
    const userKey = getUserKey();
    if (!userKey) return;

    const name = document.getElementById('prod-name').value.trim();
    const price = parseFloat(document.getElementById('prod-price').value);
    if (!name || isNaN(price) || price <= 0 || !currentImageBase64) {
      alert('الرجاء ملء جميع الحقول بشكل صحيح.');
      return;
    }

    const products = getProducts();
    const newProd = {
      id: Date.now(),
      name,
      price,
      image: currentImageBase64,
      salesCount: 0
    };
    products.push(newProd);
    saveProducts(products);

    renderProducts();
    // تنظيف
    document.getElementById('prod-name').value = '';
    document.getElementById('prod-price').value = '';
    document.getElementById('prod-image').value = '';
    document.getElementById('image-preview').innerHTML = '<i class="fas fa-cloud-upload-alt"></i>';
    currentImageBase64 = '';
    switchTab('shop');
    alert('✅ تم حفظ المنتج بنجاح!');
  }

  function renderProducts() {
    const products = getProducts();
    const list = document.getElementById('products-list');
    if (products.length === 0) {
      list.innerHTML = '<div class="empty"><i class="fas fa-box-open" style="font-size:60px;"></i><br>لا توجد منتجات بعد</div>';
      return;
    }
    list.innerHTML = products.map(p => `
      <div class="product-card">
        <img src="${p.image}" class="product-img" onerror="this.parentElement.innerHTML='<div class=\"product-img\">📦</div>'">
        <div class="product-info">
          <h3>${p.name}</h3>
          <div class="price">${p.price} درهم</div>
          <button class="add-btn" onclick="addToCart(${p.id})">
            <i class="fas fa-cart-plus"></i> أضف للسلة
          </button>
        </div>
      </div>
    `).join('');
  }

  // === سلة التسوق ===
  function getCart() {
    const userKey = getUserKey();
    return userKey ? loadData(userKey + '_cart') || [] : [];
  }

  function saveCart(cart) {
    const userKey = getUserKey();
    if (userKey) saveData(userKey + '_cart', cart);
  }

  function addToCart(productId) {
    const userKey = getUserKey();
    if (!userKey) return;

    const products = getProducts();
    const product = products.find(p => p.id === productId);
    if (!product) return;

    let cart = getCart();
    const existing = cart.find(item => item.id === productId);
    if (existing) {
      existing.qty++;
    } else {
      cart.push({ ...product, qty: 1 });
    }
    saveCart(cart);
    updateCartUI();
  }

  function updateCartUI() {
    const cart = getCart();
    const count = cart.reduce((sum, item) => sum + item.qty, 0);
    document.getElementById('cart-count').textContent = count || '0';
  }

  function openCart() {
    const cart = getCart();
    const itemsEl = document.getElementById('cart-items');
    const totalEl = document.getElementById('cart-total');
    if (cart.length === 0) {
      itemsEl.innerHTML = '<div class="empty"><i class="fas fa-shopping-cart"></i><br>سلة فارغة</div>';
      totalEl.textContent = '0';
    } else {
      const total = cart.reduce((sum, item) => sum + (item.price * item.qty), 0);
      totalEl.textContent = total;
      itemsEl.innerHTML = cart.map(item => `
        <div class="cart-item">
          <div><strong>${item.name}</strong> × ${item.qty}</div>
          <div>${item.price * item.qty} درهم</div>
        </div>
      `).join('');
    }
    document.getElementById('cart-modal').style.display = 'flex';
  }

  function closeCart() {
    document.getElementById('cart-modal').style.display = 'none';
  }

  function checkout() {
    const userKey = getUserKey();
    if (!userKey) return;

    let cart = getCart();
    if (cart.length === 0) return;

    const total = cart.reduce((sum, item) => sum + (item.price * item.qty), 0);
    
    // تحديث المبيعات
    let products = getProducts();
    cart.forEach(item => {
      const prod = products.find(p => p.id === item.id);
      if (prod) prod.salesCount += item.qty;
    });
    saveProducts(products);

    // حفظ عملية بيع
    let sales = loadData(userKey + '_sales') || [];
    const sale = {
      id: Date.now(),
      items: [...cart],
      total,
      date: new Date().toLocaleString('ar-MA')
    };
    sales.push(sale);
    saveData(userKey + '_sales', sales);

    // تنظيف السلة
    cart = [];
    saveCart(cart);
    updateCartUI();
    closeCart();
    updateStats();
    alert(`✅ تم تأكيد طلبك بنجاح!\nالمجموع: ${total} درهم`);
  }

  // === الإحصائيات ===
  function updateStats() {
    const userKey = getUserKey();
    if (!userKey) return;

    const sales = loadData(userKey + '_sales') || [];
    const products = getProducts();

    const totalSales = sales.reduce((sum, s) => sum + s.total, 0);
    const totalOrders = sales.length;
    
    document.getElementById('total-sales').textContent = totalSales || '0';
    document.getElementById('total-orders').textContent = totalOrders || '0';
    
    if (products.length > 0) {
      const best = products.reduce((a, b) => a.salesCount > b.salesCount ? a : b);
      const worst = products.reduce((a, b) => a.salesCount < b.salesCount ? a : b);
      document.getElementById('best-seller').textContent = best.salesCount > 0 ? best.name : '-';
      document.getElementById('worst-seller').textContent = worst.salesCount > 0 ? worst.name : '-';
    } else {
      document.getElementById('best-seller').textContent = '-';
      document.getElementById('worst-seller').textContent = '-';
    }
    
    // سجل المبيعات
    const salesListEl = document.getElementById('sales-list');
    const noSalesEl = document.getElementById('no-sales');
    if (sales.length === 0) {
      salesListEl.innerHTML = '';
      noSalesEl.style.display = 'block';
    } else {
      noSalesEl.style.display = 'none';
      salesListEl.innerHTML = sales.slice().reverse().map(s => `
        <div style="padding:12px 0; border-bottom:1px solid #f0f0f0;">
          <strong>طلب #${s.id}</strong> | ${s.date}<br>
          المجموع: ${s.total} درهم
        </div>
      `).join('');
    }
  }

  // === التبويبات ===
  function switchTab(tabName) {
    document.querySelectorAll('.tab-content').forEach(el => el.style.display = 'none');
    
    if (tabName === 'admin') {
      document.getElementById('admin-section').style.display = 'block';
    } else if (tabName === 'stats') {
      document.getElementById('stats-section').style.display = 'block';
      updateStats();
    } else {
      document.getElementById('shop-section').style.display = 'block';
      renderProducts();
    }

    document.querySelectorAll('.tab-btn').forEach(btn => btn.classList.remove('active'));
    document.querySelector(`.tab-btn[data-tab="${tabName}"]`).classList.add('active');
  }

  // === أحداث ===
  document.querySelectorAll('.tab-btn').forEach(btn => {
    btn.addEventListener('click', () => switchTab(btn.dataset.tab));
  });

  document.getElementById('cart-modal').addEventListener('click', (e) => {
    if (e.target === document.getElementById('cart-modal')) closeCart();
  });

  // === تهيئة ===
  window.onload = function() {
    const user = getCurrentUser();
    if (user && loadData('user_' + user)) {
      showScreen('dashboard');
      renderProducts();
      updateCartUI();
    } else {
      showScreen('welcome');
    }
  };

  // === دوال مساعدة للإشعارات ===
  function showError(el, msg) {
    el.textContent = msg;
    el.style.display = 'block';
  }

  function showSuccess(el, msg) {
    el.textContent = msg;
    el.style.display = 'block';
  }

  // === جعل الدوال متاحة عالمياً ===
  window.showScreen = showScreen;
  window.handleSignup = handleSignup;
  window.handleLogin = handleLogin;
  window.logout = logout;
  window.deleteAccount = deleteAccount;
  window.previewImage = previewImage;
  window.addProduct = addProduct;
  window.renderProducts = renderProducts;
  window.addToCart = addToCart;
  window.updateCartUI = updateCartUI;
  window.openCart = openCart;
  window.closeCart = closeCart;
  window.checkout = checkout;
  window.updateStats = updateStats;
  window.switchTab = switchTab;
</script>

</body>
</html>
