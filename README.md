<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>الحريفية — تطبيق الحرفيين</title>
  <link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@400;700;800&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">
  <style>
    :root {
      --bg: #ffffff;
      --text: #0b0b0b;
      --muted: #6b7280;
      --accent: #16a34a;
      --accent-light: #dcf7e6;
      --soft: #f3f6f4;
      --card: #ffffff;
      --shadow: 0 4px 20px rgba(0,0,0,0.06);
      --shadow-strong: 0 10px 30px rgba(2,6,23,0.08);
      --blue-bg: #4F6FFF;
      --blue-light: #6A8BFF;
      --border: rgba(0,0,0,0.08);
      --success: #10b981;
      --error: #ef4444;
      --warning: #f59e0b;
    }

    [data-theme="dark"] {
      --bg: #111827;
      --text: #f9fafb;
      --muted: #9ca3af;
      --soft: #1f2937;
      --card: #1e293b;
      --border: rgba(255,255,255,0.1);
      --shadow: 0 4px 20px rgba(0,0,0,0.2);
      --shadow-strong: 0 10px 30px rgba(0,0,0,0.3);
    }

    * {
      box-sizing: border-box;
      font-family: "Tajawal", system-ui, Arial, sans-serif;
    }

    html, body {
      height: 100%;
      margin: 0;
      background: var(--bg);
      color: var(--text);
      -webkit-font-smoothing: antialiased;
      transition: background-color 0.3s, color 0.3s;
    }

    .app {
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: flex-start;
      padding-bottom: 80px;
    }

    /* Splash */
    .splash {
      width: 100%;
      max-width: 420px;
      height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      flex-direction: column;
      gap: 24px;
      padding: 28px;
      text-align: center;
      background: linear-gradient(180deg, #16a34a 0%, #0ea06b 100%);
      color: white;
      position: relative;
    }
    .logo {
      width: 96px;
      height: 96px;
      border-radius: 24px;
      background: rgba(255,255,255,0.15);
      display: flex;
      align-items: center;
      justify-content: center;
      font-weight: 800;
      font-size: 32px;
      box-shadow: 0 8px 28px rgba(0,0,0,0.22);
    }
    .splash h1 { margin: 0; font-size: 24px; font-weight: 800; }
    .splash p { margin: 0; color: rgba(255,255,255,0.92); font-size: 15px; line-height: 1.5; }
    .btn-start {
      margin-top: 8px;
      padding: 14px 24px;
      border-radius: 14px;
      border: none;
      background: white;
      color: var(--accent);
      font-weight: 800;
      cursor: pointer;
      box-shadow: 0 10px 24px rgba(0,0,0,0.18);
      transition: all 0.3s ease;
    }
    .btn-start:hover {
      transform: scale(1.03);
      box-shadow: 0 12px 28px rgba(0,0,0,0.22);
    }
    .fade-out {
      animation: splashHide 0.6s forwards;
    }
    @keyframes splashHide {
      to { opacity: 0; transform: translateY(-30px); }
    }

    /* Login */
    .login-page {
      width: 100%;
      max-width: 420px;
      height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
      background: linear-gradient(135deg, var(--blue-bg), var(--blue-light));
      padding: 20px;
      position: fixed;
      top: 0;
      left: 0;
      z-index: 1000;
      opacity: 1;
      transition: opacity 0.5s ease;
    }
    .login-card {
      width: 100%;
      max-width: 360px;
      background: var(--card);
      border-radius: 20px;
      padding: 30px;
      box-shadow: 0 20px 40px rgba(0,0,0,0.15);
      text-align: center;
      animation: fadeInUp 0.6s ease-out;
    }
    @keyframes fadeInUp {
      from { opacity: 0; transform: translateY(30px); }
      to { opacity: 1; transform: translateY(0); }
    }
    .login-title {
      font-size: 24px;
      font-weight: 800;
      color: var(--text);
      margin: 0 0 10px 0;
    }
    .login-subtitle {
      font-size: 14px;
      color: var(--muted);
      margin: 0 0 20px 0;
    }
    .form-group {
      margin: 15px 0;
      text-align: right;
    }
    .form-group label {
      display: block;
      font-size: 13px;
      color: var(--muted);
      margin-bottom: 6px;
      font-weight: 600;
    }
    .form-group input {
      width: 100%;
      padding: 12px;
      border-radius: 12px;
      border: 1px solid var(--border);
      font-size: 15px;
      background: var(--soft);
      color: var(--text);
      outline: none;
      transition: border 0.3s, background 0.3s;
    }
    .form-group input:focus {
      border-color: var(--accent);
      background: var(--card);
    }
    .btn-login, .btn-register {
      width: 100%;
      padding: 14px;
      border-radius: 12px;
      border: none;
      cursor: pointer;
      font-weight: 800;
      margin-top: 12px;
      transition: all 0.3s ease;
    }
    .btn-login {
      background: var(--accent);
      color: white;
    }
    .btn-login:hover {
      background: #0f8a4d;
      transform: scale(1.02);
    }
    .btn-register {
      background: transparent;
      color: var(--accent);
      border: 1px solid var(--accent);
    }
    .btn-register:hover {
      background: rgba(22,163,74,0.06);
    }

    /* Main UI */
    .container {
      width: 100%;
      max-width: 420px;
      padding: 16px;
      opacity: 0;
      transition: opacity 0.4s ease;
    }

    .topbar {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 10px 8px;
      margin-bottom: 16px;
    }
    .title {
      font-size: 20px;
      font-weight: 800;
      color: var(--text);
      display: flex;
      align-items: center;
      gap: 8px;
    }
    .title i { color: var(--accent); }
    .sub { font-size: 13px; color: var(--muted); }

    .card {
      background: var(--card);
      border-radius: 16px;
      padding: 16px;
      box-shadow: var(--shadow-strong);
      border: 1px solid var(--border);
      margin-bottom: 16px;
      transition: transform 0.2s ease;
    }
    .card:hover { transform: translateY(-2px); }

    .roles {
      display: flex;
      gap: 12px;
      justify-content: center;
      margin-top: 16px;
    }
    .role-btn {
      flex: 1;
      padding: 14px;
      border-radius: 14px;
      border: none;
      cursor: pointer;
      font-weight: 800;
      background: linear-gradient(180deg, var(--accent), #0f8a4d);
      color: white;
      box-shadow: 0 8px 24px rgba(16,163,122,0.2);
      transition: all 0.2s ease;
    }
    .role-btn:hover { transform: scale(1.02); }
    .role-btn.ghost {
      background: transparent;
      color: var(--accent);
      border: 2px solid var(--accent);
      box-shadow: none;
      font-weight: 700;
    }
    .role-btn.ghost:hover {
      background: rgba(22,163,74,0.06);
    }

    .page { display: none; padding: 8px 0; }
    .page.active { display: block; }

    label {
      display: block;
      font-size: 13px;
      color: var(--muted);
      margin-top: 12px;
      margin-bottom: 6px;
      font-weight: 600;
    }
    input[type="text"], input[type="tel"], input[type="email"], select, textarea {
      width: 100%;
      padding: 12px;
      border-radius: 12px;
      border: 1px solid var(--border);
      font-size: 15px;
      background: var(--soft);
      color: var(--text);
      outline: none;
      transition: border 0.3s, background 0.3s;
    }
    input:focus {
      border-color: var(--accent);
      background: var(--card);
    }

    .actions {
      display: flex;
      gap: 10px;
      margin-top: 16px;
    }
    .btn {
      padding: 14px;
      border-radius: 12px;
      border: none;
      cursor: pointer;
      font-weight: 800;
      background: var(--accent);
      color: white;
      flex: 1;
      transition: all 0.3s ease;
    }
    .btn:hover {
      background: #0f8a4d;
      transform: scale(1.02);
    }
    .btn.ghost {
      background: transparent;
      color: var(--text);
      border: 1px solid var(--border);
      box-shadow: none;
    }
    .btn.ghost:hover {
      background: var(--soft);
    }

    .artisan-list {
      display: flex;
      flex-direction: column;
      gap: 12px;
      margin-top: 8px;
    }
    .artisan {
      display: flex;
      gap: 12px;
      align-items: center;
      padding: 12px;
      background: var(--card);
      border-radius: 12px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.06);
      border: 1px solid var(--border);
      transition: transform 0.2s;
    }
    .artisan:hover { transform: translateX(4px); }
    .avatar {
      width: 72px;
      height: 72px;
      border-radius: 14px;
      background: #eee;
      overflow: hidden;
      flex-shrink: 0;
      border: 2px solid var(--accent);
    }
    .avatar img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      display: block;
    }
    .meta {
      flex: 1;
      text-align: right;
    }
    .meta h4 {
      margin: 0;
      font-size: 16px;
      color: var(--text);
    }
    .meta p {
      margin: 4px 0;
      color: var(--muted);
      font-size: 13px;
    }
    .meta .tag {
      display: inline-block;
      margin-top: 6px;
      padding: 6px 8px;
      border-radius: 8px;
      background: rgba(16,163,122,0.1);
      color: var(--accent);
      font-weight: 700;
      font-size: 12px;
    }

    .bottom {
      position: fixed;
      bottom: 12px;
      left: 50%;
      transform: translateX(-50%);
      width: calc(100% - 40px);
      max-width: 420px;
      display: flex;
      justify-content: space-between;
      gap: 10px;
      padding: 8px;
      background: var(--card);
      border-radius: 14px;
      box-shadow: 0 12px 30px rgba(2,6,23,0.12);
      border: 1px solid var(--border);
    }
    .nav-btn {
      flex: 1;
      padding: 10px 12px;
      border-radius: 10px;
      border: none;
      cursor: pointer;
      background: transparent;
      color: var(--muted);
      font-weight: 700;
      transition: all 0.2s;
    }
    .nav-btn.active {
      background: linear-gradient(180deg, var(--accent), #0f8a4d);
      color: white;
    }

    .note {
      font-size: 13px;
      color: var(--muted);
      margin-top: 8px;
    }
    .center {
      text-align: center;
    }

    /* Notification */
    .notification {
      position: fixed;
      top: 20px;
      left: 50%;
      transform: translateX(-50%);
      background: var(--success);
      color: white;
      padding: 12px 20px;
      border-radius: 10px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.2);
      z-index: 2000;
      opacity: 0;
      transition: opacity 0.3s;
    }
    .notification.show {
      opacity: 1;
    }

    /* Dark mode toggle */
    .theme-toggle {
      position: absolute;
      top: 16px;
      left: 16px;
      background: rgba(255,255,255,0.2);
      border: none;
      width: 40px;
      height: 40px;
      border-radius: 50%;
      color: white;
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    @media (max-width: 420px) {
      .avatar { width: 64px; height: 64px; }
      .bottom { left: 8px; right: 8px; transform: none; width: auto; max-width: calc(100% - 16px); }
    }
  </style>
</head>
<body>
  <!-- Notification -->
  <div id="notification" class="notification">تم الحفظ بنجاح!</div>

  <div class="app">
    <!-- SPLASH -->
    <section id="splash" class="splash">
      <button class="theme-toggle" id="splashThemeToggle">
        <i class="fas fa-moon"></i>
      </button>
      <div class="logo">ح</div>
      <h1>الحريفية ترحب بكم</h1>
      <p>تطبيق الحرفيين — أسرع طريقة تلقى الحرفي المناسب</p>
      <button id="startBtn" class="btn-start">ابدأ التطبيق</button>
    </section>

    <!-- LOGIN -->
    <div id="loginPage" class="login-page" style="display:none;">
      <div class="login-card">
        <h2 class="login-title"><i class="fas fa-user-plus"></i> سجل دخولك</h2>
        <p class="login-subtitle">أو سجل حساب جديد باش تبدأ</p>

        <div class="form-group">
          <label>البريد الإلكتروني</label>
          <input type="email" id="loginEmail" placeholder="ex@example.com" required>
        </div>
        <div class="form-group">
          <label>كلمة المرور</label>
          <input type="password" id="loginPassword" placeholder="••••••••" required>
        </div>

        <button id="btnLogin" class="btn-login">تسجيل الدخول</button>
        <button id="btnRegister" class="btn-register">سجل حساب جديد</button>
      </div>
    </div>

    <!-- MAIN -->
    <div class="container" id="main" style="display:none;">
      <div class="topbar">
        <div>
          <div class="title"><i class="fas fa-tools"></i> الحريفية</div>
          <div class="sub">للقاء الحرفيين المحترفين</div>
        </div>
        <button class="theme-toggle" id="mainThemeToggle">
          <i class="fas fa-moon"></i>
        </button>
      </div>

      <div class="card" id="roleCard">
        <div style="display:flex;justify-content:space-between;align-items:center">
          <div>
            <div style="font-weight:800;font-size:16px">مرحباً بك!</div>
            <div class="sub">اختر دورك لبدء الاستخدام</div>
          </div>
        </div>
        <div class="roles">
          <button id="toArt" class="role-btn">أنا حريف</button>
          <button id="toCli" class="role-btn ghost">أنا زبون</button>
        </div>
      </div>

      <section id="pageArt" class="page">
        <div class="card">
          <h3>أضف حريف جديد</h3>
          <form id="artisanForm">
            <label>الاسم الكامل</label>
            <input type="text" id="name" required>
            <label>المهنة</label>
            <input type="text" id="craft" required>
            <label>الهاتف</label>
            <input type="tel" id="phone" required>
            <label>الصورة (اختياري)</label>
            <input type="file" id="photo" accept="image/*">
            <div class="actions">
              <button type="submit" class="btn">حفظ الحريف</button>
            </div>
          </form>
        </div>

        <div class="card">
          <h3>الحرفيين المسجلين</h3>
          <div class="artisan-list" id="artisanList"></div>
        </div>
      </section>

      <section id="pageCli" class="page">
        <div class="card">
          <h3>ابحث عن حريف</h3>
          <input type="text" id="searchInput" placeholder="ابحث بالاسم أو المهنة..." style="width:100%;padding:10px;border-radius:10px;border:1px solid var(--border);background:var(--soft);color:var(--text);">
          <div class="artisan-list" id="searchResults"></div>
        </div>
      </section>

      <section id="settings" class="page">
        <div class="card">
          <h3>الإعدادات</h3>
          <div class="actions" style="flex-direction:column;gap:10px">
            <button id="toggleVisibility" class="btn">إظهار ملفي للكليان</button>
            <button id="clearData" class="btn ghost">مسح كل البيانات</button>
            <div class="center note" id="statusVisible">مخفي عن الكليان</div>
          </div>
        </div>
      </section>
    </div>

    <div class="bottom" id="bottom_nav">
      <button class="nav-btn active" data-page="pageArt">حرفيين</button>
      <button class="nav-btn" data-page="pageCli">بحث</button>
      <button class="nav-btn" data-page="settings">الإعدادات</button>
    </div>
  </div>

  <script>
    // =============== UTILITIES ===============
    const STORE = 'artisans_v3';
    const VISIBILITY_KEY = 'artisan_visibility';
    const USER_STORE = 'user_v2';
    const THEME_KEY = 'theme';

    // Theme
    function setTheme(theme) {
      document.documentElement.setAttribute('data-theme', theme);
      localStorage.setItem(THEME_KEY, theme);
      updateThemeIcon();
    }
    function getTheme() {
      return localStorage.getItem(THEME_KEY) || 'light';
    }
    function toggleTheme() {
      const current = getTheme();
      setTheme(current === 'light' ? 'dark' : 'light');
    }
    function updateThemeIcon() {
      const isDark = getTheme() === 'dark';
      document.querySelectorAll('.theme-toggle i').forEach(el => {
        el.className = isDark ? 'fas fa-sun' : 'fas fa-moon';
      });
    }

    // Data
    function load() {
      try {
        return JSON.parse(localStorage.getItem(STORE)) || [];
      } catch (e) {
        return [];
      }
    }
    function saveAll(list) {
      localStorage.setItem(STORE, JSON.stringify(list));
    }
    function isVisible() {
      return localStorage.getItem(VISIBILITY_KEY) === 'true';
    }
    function setVisibility(visible) {
      localStorage.setItem(VISIBILITY_KEY, visible ? 'true' : 'false');
      updateVisibilityStatus();
    }
    function uid() {
      return Date.now().toString(36) + Math.random().toString(36).slice(2, 6);
    }
    function readImageFile(input, cb) {
      if (!input.files || !input.files[0]) return cb(null);
      const fr = new FileReader();
      fr.onload = e => cb(e.target.result);
      fr.readAsDataURL(input.files[0]);
    }
    function updateUser(user) {
      localStorage.setItem(USER_STORE, JSON.stringify(user));
    }
    function getCurrentUser() {
      try {
        return JSON.parse(localStorage.getItem(USER_STORE)) || null;
      } catch (e) {
        return null;
      }
    }
    function notify(msg, type = 'success') {
      const el = document.getElementById('notification');
      el.textContent = msg;
      el.style.background = type === 'error' ? 'var(--error)' : 'var(--success)';
      el.classList.add('show');
      setTimeout(() => el.classList.remove('show'), 3000);
    }
    function updateVisibilityStatus() {
      const el = document.getElementById('statusVisible');
      el.textContent = isVisible() ? 'ظاهر للكليان' : 'مخفي عن الكليان';
    }

    // =============== INIT ===============
    setTheme(getTheme());
    updateThemeIcon();

    // =============== SPLASH -> LOGIN ===============
    document.getElementById('startBtn').addEventListener('click', () => {
      document.getElementById('splash').classList.add('fade-out');
      setTimeout(() => {
        document.getElementById('splash').style.display = 'none';
        document.getElementById('loginPage').style.display = 'flex';
        const user = getCurrentUser();
        if (user) showMainApp();
      }, 600);
    });

    // =============== THEME TOGGLE ===============
    document.getElementById('splashThemeToggle').addEventListener('click', toggleTheme);
    document.getElementById('mainThemeToggle').addEventListener('click', toggleTheme);

    // =============== LOGIN ===============
    document.getElementById('btnLogin').addEventListener('click', () => {
      const email = document.getElementById('loginEmail').value.trim();
      const password = document.getElementById('loginPassword').value.trim();
      if (!email || !password) return notify('الرجاء إدخال البريد وكلمة المرور', 'error');
      const user = { email, password, name: email.split('@')[0], id: uid() };
      updateUser(user);
      showMainApp();
    });

    document.getElementById('btnRegister').addEventListener('click', () => {
      const email = prompt('أدخل بريدك الإلكتروني:');
      if (!email || !email.includes('@')) return;
      const password = prompt('أدخل كلمة المرور (6 أحرف على الأقل):');
      if (!password || password.length < 6) return;
      const name = prompt('أدخل اسمك:', email.split('@')[0]);
      if (!name) return;
      const user = { email, password, name, id: uid() };
      updateUser(user);
      showMainApp();
    });

    function showMainApp() {
      document.getElementById('loginPage').style.opacity = '0';
      setTimeout(() => {
        document.getElementById('loginPage').style.display = 'none';
        document.getElementById('main').style.display = 'block';
        document.getElementById('main').style.opacity = '1';
        loadArtisans();
        updateVisibilityStatus();
        showPage('pageArt'); // افتراضيًا نعرض صفحة الحرفيين
      }, 500);
    }

    // =============== NAVIGATION ===============
    function showPage(pageId) {
      document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
      document.getElementById(pageId).classList.add('active');

      document.querySelectorAll('.nav-btn').forEach(btn => btn.classList.remove('active'));
      document.querySelector(`.nav-btn[data-page="${pageId}"]`).classList.add('active');

      if (pageId === 'pageCli') {
        searchArtisans(document.getElementById('searchInput').value);
      }
    }

    document.querySelectorAll('.nav-btn').forEach(btn => {
      btn.addEventListener('click', () => {
        const page = btn.getAttribute('data-page');
        showPage(page);
      });
    });

    // =============== ROLE ===============
    document.getElementById('toArt').addEventListener('click', () => {
      document.getElementById('toArt').classList.remove('ghost');
      document.getElementById('toCli').classList.add('ghost');
      showPage('pageArt');
    });

    document.getElementById('toCli').addEventListener('click', () => {
      document.getElementById('toCli').classList.remove('ghost');
      document.getElementById('toArt').classList.add('ghost');
      showPage('pageCli');
      searchArtisans('');
    });

    // =============== ARTISAN CRUD ===============
    function renderArtisan(artisan, container) {
      if (!isVisible() && container === document.getElementById('searchResults')) return;

      const div = document.createElement('div');
      div.className = 'artisan';
      const imgSrc = artisan.photo || 'https://via.placeholder.com/72?text=ح';
      div.innerHTML = `
        <div class="avatar"><img src="${imgSrc}" alt="${artisan.name}"></div>
        <div class="meta">
          <h4>${artisan.name}</h4>
          <p>${artisan.phone}</p>
          <span class="tag">${artisan.craft}</span>
        </div>
      `;
      container.appendChild(div);
    }

    function loadArtisans() {
      const artisans = load();
      const list = document.getElementById('artisanList');
      list.innerHTML = '';
      artisans.forEach(a => renderArtisan(a, list));
    }

    document.getElementById('artisanForm').addEventListener('submit', function(e) {
      e.preventDefault();
      const name = document.getElementById('name').value.trim();
      const craft = document.getElementById('craft').value.trim();
      const phone = document.getElementById('phone').value.trim();

      if (!name || !craft || !phone) {
        return notify('الرجاء ملء جميع الحقول', 'error');
      }

      readImageFile(document.getElementById('photo'), (photo) => {
        const artisan = { id: uid(), name, craft, phone, photo };
        const list = load();
        list.push(artisan);
        saveAll(list);
        loadArtisans();
        this.reset();
        notify('تم حفظ الحريف بنجاح!');
      });
    });

    // =============== SEARCH ===============
    function searchArtisans(query) {
      const results = document.getElementById('searchResults');
      results.innerHTML = '';
      if (!isVisible()) {
        results.innerHTML = '<p class="center" style="color:var(--muted)">الحساب مخفي عن الزبائن</p>';
        return;
      }
      const artisans = load().filter(a =>
        a.name.toLowerCase().includes(query.toLowerCase()) ||
        a.craft.toLowerCase().includes(query.toLowerCase())
      );
      if (artisans.length === 0) {
        results.innerHTML = '<p class="center" style="color:var(--muted)">ما لقيتش شي حريف</p>';
      } else {
        artisans.forEach(a => renderArtisan(a, results));
      }
    }

    document.getElementById('searchInput').addEventListener('input', (e) => {
      searchArtisans(e.target.value);
    });

    // =============== SETTINGS ===============
    document.getElementById('toggleVisibility').addEventListener('click', () => {
      const wasVisible = isVisible();
      setVisibility(!wasVisible);
      const btn = document.getElementById('toggleVisibility');
      btn.textContent = wasVisible ? 'إظهار ملفي للكليان' : 'إخفاء ملفي عن الكليان';
      if (!wasVisible) {
        searchArtisans(document.getElementById('searchInput').value);
      }
    });

    document.getElementById('clearData').addEventListener('click', () => {
      if (confirm('هل أنت متأكد من مسح كل البيانات؟')) {
        localStorage.removeItem(STORE);
        loadArtisans();
        searchArtisans('');
        notify('تم مسح البيانات بنجاح');
      }
    });

    // Initialize visibility
    setVisibility(isVisible());
  </script>
</body>
</html>
