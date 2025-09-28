<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>الحريفية — تطبيق الحرفيين</title>
<link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@400;700;800&display=swap" rel="stylesheet">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">
<style>
  :root {
    --bg-gradient: linear-gradient(135deg, #f3f6f4, #e0f2f1);
    --card: #ffffff;
    --text: #111827;
    --muted: #6b7280;
    --accent: #16a34a;
    --accent-light: #dcf7e6;
    --soft: #f3f6f4;
    --border: rgba(0,0,0,0.08);
    --shadow: 0 4px 20px rgba(0,0,0,0.06);
    --shadow-strong: 0 10px 30px rgba(2,6,23,0.08);
    --blue-bg: #4F6FFF;
    --blue-light: #6A8BFF;
  }

  [data-theme="dark"] {
    --bg-gradient: linear-gradient(135deg, #111827, #1f2937);
    --card: #1e293b;
    --text: #f9fafb;
    --muted: #9ca3af;
    --accent: #4ade80;
    --accent-light: rgba(74, 222, 128, 0.1);
    --soft: #1f2937;
    --border: rgba(255,255,255,0.1);
    --shadow: 0 4px 20px rgba(0,0,0,0.2);
    --shadow-strong: 0 10px 30px rgba(0,0,0,0.3);
    --blue-bg: #4338ca;
    --blue-light: #4f46e5;
  }

  *{box-sizing:border-box;font-family: "Tajawal", system-ui, Arial; }
  html,body{height:100%;margin:0;background:var(--bg-gradient);color:var(--text);-webkit-font-smoothing:antialiased;transition: background 0.5s ease, color 0.5s ease;}
  .app {
    min-height:100vh;
    display:flex;
    flex-direction:column;
    align-items:center;
    justify-content:flex-start;
    padding-bottom:80px;
  }

  /* Splash */
  .splash {
    width:100%;
    max-width:420px;
    height:100vh;
    display:flex;
    align-items:center;
    justify-content:center;
    flex-direction:column;
    gap:24px;
    padding:28px;
    text-align:center;
    background:linear-gradient(180deg,#16a34a 0%, #0ea06b 60%);
    color:white;
    position:relative;
  }
  .logo {
    width:96px;height:96px;border-radius:24px;background:rgba(255,255,255,0.15);
    display:flex;align-items:center;justify-content:center;font-weight:800;font-size:32px;box-shadow:0 8px 28px rgba(0,0,0,0.22)
  }
  .splash h1{margin:0;font-size:24px;font-weight:800}
  .splash p{margin:0;color:rgba(255,255,255,0.92);font-size:15px;line-height:1.5}
  .btn-start{
    margin-top:8px;padding:14px 24px;border-radius:14px;border:none;background:white;color:var(--accent);
    font-weight:800;cursor:pointer;box-shadow:0 10px 24px rgba(0,0,0,0.18);
    transition: all 0.3s ease;
  }
  .btn-start:hover{ transform:scale(1.03); box-shadow:0 12px 28px rgba(0,0,0,0.22); }
  .fade-out { animation: splashHide .6s forwards; }
  @keyframes splashHide { 
    to { opacity:0; transform:translateY(-30px); } 
  }

  /* Login Page */
  .login-page {
    width:100%;
    max-width:420px;
    height:100vh;
    display:flex;
    align-items:center;
    justify-content:center;
    background:var(--bg-gradient);
    padding:20px;
    position:fixed;
    top:0;
    left:0;
    z-index:1000;
    opacity:1;
    transition: opacity 0.5s ease;
  }
  .login-container {
    width: 100%;
    max-width: 380px;
    background: var(--card);
    border-radius: 20px;
    padding: 30px 20px;
    box-shadow: var(--shadow);
    text-align: center;
  }
  .login-container h1 {
    font-size: 22px;
    font-weight: 800;
    margin-bottom: 10px;
  }
  .login-container p {
    font-size: 14px;
    color: var(--muted);
    margin-bottom: 20px;
  }
  .form-group {
    margin-bottom: 16px;
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
  .btn-login {
    width: 100%;
    padding: 14px;
    border-radius: 12px;
    border: none;
    cursor: pointer;
    font-weight: 800;
    background: var(--accent);
    color: white;
    font-size: 15px;
    transition: all 0.3s ease;
    margin-top: 20px;
  }
  .btn-login:hover { transform: scale(1.02); }
  .btn-register {
    width: 100%;
    padding: 12px;
    border-radius: 12px;
    border: none;
    cursor: pointer;
    font-weight: 700;
    background: transparent;
    color: var(--accent);
    margin-top: 10px;
    border: 1px solid var(--accent);
    transition: all 0.3s ease;
  }
  .btn-register:hover {
    background: rgba(22,163,74,0.06);
  }
  .login-footer {
    margin-top: 20px;
    font-size: 12px;
    color: var(--muted);
  }
  .note {
    font-size: 13px;
    color: var(--muted);
    margin-top: 12px;
  }

  /* Main UI */
  .container {
    width:100%;
    max-width:420px;
    background:transparent;
    padding:16px;
    opacity:0;
    transition: opacity 0.4s ease;
  }

  .topbar {
    display:flex;align-items:center;justify-content:space-between;padding:10px 8px;
    gap:10px; margin-bottom:8px;
  }
  .title { font-size:20px;font-weight:800;color:var(--text); display:flex;align-items:center;gap:8px; }
  .title i{ color:var(--accent); }
  .sub { font-size:13px;color:var(--muted); }

  .card {
    background:var(--card);
    border-radius:16px;
    padding:16px;
    box-shadow:var(--shadow-strong);
    border:1px solid var(--border);
    margin-bottom:16px;
    transition: transform 0.2s ease;
  }
  .card:hover { transform: translateY(-2px); }

  .roles { display:flex; gap:12px; justify-content:center; margin-top:16px }
  .role-btn {
    flex:1;padding:14px;border-radius:14px;border:none;cursor:pointer;font-weight:800;
    background:linear-gradient(180deg,var(--accent), #0f8a4d); color:white; 
    box-shadow:0 8px 24px rgba(16,163,122,0.2);
    transition: all 0.2s ease;
  }
  .role-btn:hover { transform: scale(1.02); }
  .role-btn.ghost { 
    background:transparent;color:var(--accent);border:2px solid var(--accent); 
    box-shadow: none; font-weight:700;
  }
  .role-btn.ghost:hover { background: rgba(22,163,74,0.06); }

  .page { display:none; padding:8px 0; }
  .page.active { display:block; }

  form .row { display:flex; gap:10px; }
  label{display:block;font-size:13px;color:var(--muted);margin-top:12px;margin-bottom:6px;font-weight:600}
  input[type="text"], input[type="tel"], select, textarea {
    width:100%;padding:12px;border-radius:12px;border:1px solid var(--border);
    font-size:15px;background:var(--soft);color:var(--text);outline:none;transition: border 0.3s, background 0.3s;
  }
  input[type="text"]:focus, input[type="tel"]:focus {
    border-color: var(--accent);
    background: var(--card);
  }
  input[type="file"] { padding:8px; }

  .actions { display:flex; gap:10px; margin-top:16px }
  .btn { 
    padding:14px;border-radius:12px;border:none;cursor:pointer;font-weight:800;
    background:var(--accent);color:white;flex:1;transition:all 0.3s ease;
  }
  .btn:hover { background:#0f8a4d; transform:scale(1.02); }
  .btn.ghost{ 
    background:transparent;color:var(--text);border:1px solid var(--border); 
    box-shadow:none; 
  }
  .btn.small{ padding:8px 10px; font-size:14px }

  .artisan-list { display:flex; flex-direction:column; gap:12px; margin-top:8px }
  .artisan {
    display:flex; gap:12px; align-items:center; padding:12px; background:var(--card); border-radius:12px;
    box-shadow:0 8px 24px rgba(0,0,0,0.06); border:1px solid var(--border);
    transition: transform 0.2s;
  }
  .artisan:hover { transform: translateX(4px); }
  .avatar {
    width:72px;height:72px;border-radius:14px;background:#eee;overflow:hidden;flex-shrink:0;border:2px solid var(--accent);
  }
  .avatar img{ width:100%;height:100%;object-fit:cover;display:block; }
  .meta{ flex:1; text-align:right }
  .meta h4{ margin:0;font-size:16px; color:var(--text); }
  .meta p{ margin:4px 0;color:var(--muted); font-size:13px }
  .meta .tag { display:inline-block;margin-top:6px;padding:6px 8px;border-radius:8px;background:var(--accent-light); color:var(--accent); font-weight:700; font-size:12px }

  .artisan .controls { display:flex; flex-direction:column; gap:6px; margin-left:8px }
  .stat { font-size:12px;color:var(--muted) }

  /* Call Page */
  .call-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 20px;
    padding: 20px;
  }
  .video-container {
    display: flex;
    gap: 20px;
    justify-content: center;
    flex-wrap: wrap;
  }
  .video-wrapper {
    text-align: center;
  }
  .video-wrapper video {
    width: 200px;
    height: 150px;
    border-radius: 12px;
    border: 1px solid var(--border);
    background: #000;
  }
  .video-label {
    margin-top: 8px;
    font-size: 14px;
    color: var(--muted);
  }
  .call-controls {
    display: flex;
    gap: 15px;
    margin-top: 20px;
  }
  .call-btn {
    padding: 14px 24px;
    border-radius: 14px;
    border: none;
    cursor: pointer;
    font-weight: 800;
    font-size: 16px;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .call-btn.end {
    background: #ef4444;
    color: white;
  }
  .call-btn.end:hover {
    background: #dc2626;
  }

  /* Chat Styles */
  .chat-header {
    padding: 12px;
    background: var(--card);
    border-radius: 12px;
    margin-bottom: 16px;
    box-shadow: var(--shadow);
    text-align: center;
    font-weight: 700;
    color: var(--text);
  }
  .messages {
    flex: 1;
    display: flex;
    flex-direction: column;
    gap: 12px;
    padding: 12px 0;
    overflow-y: auto;
    max-height: 400px;
  }
  .message {
    max-width: 70%;
    padding: 12px;
    border-radius: 16px;
    background: var(--soft);
    word-wrap: break-word;
    align-self: flex-start;
    color: var(--text);
  }
  .message.self {
    background: var(--accent-light);
    color: var(--accent);
    align-self: flex-end;
  }
  .chat-input {
    display: flex;
    gap: 10px;
    margin-top: 16px;
  }
  .chat-input input {
    flex: 1;
    padding: 12px;
    border-radius: 12px;
    border: 1px solid var(--border);
    background: var(--soft);
    color: var(--text);
  }
  .chat-input button {
    padding: 12px 16px;
    border: none;
    border-radius: 12px;
    background: var(--accent);
    color: white;
    cursor: pointer;
  }
  .chat-input button:hover {
    background: #0f8a4d;
  }

  /* Settings Page */
  .settings-card {
    background: var(--card);
    border-radius: 16px;
    padding: 20px;
    margin-bottom: 20px;
    box-shadow: var(--shadow);
    transition: transform 0.2s ease;
  }
  .settings-card:hover { transform: translateY(-2px); }

  .setting-item {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 12px 0;
    border-bottom: 1px solid var(--border);
  }
  .setting-item:last-child { border-bottom: none; }

  .setting-item i {
    margin-left: 10px;
    color: var(--accent);
    font-size: 18px;
  }

  .toggle-btn {
    width: 50px;
    height: 25px;
    background: #ccc;
    border-radius: 50px;
    position: relative;
    cursor: pointer;
    transition: background 0.3s;
  }
  .toggle-btn::after {
    content: "";
    width: 21px;
    height: 21px;
    background: white;
    border-radius: 50%;
    position: absolute;
    top: 2px;
    left: 2px;
    transition: all 0.3s ease;
  }
  .toggle-btn.active {
    background: var(--accent);
  }
  .toggle-btn.active::after {
    transform: translateX(25px);
  }

  .profile-section {
    display: flex;
    align-items: center;
    gap: 16px;
    padding: 10px 0;
  }
  .profile-pic {
    width: 64px;
    height: 64px;
    border-radius: 50%;
    border: 2px solid var(--accent);
    overflow: hidden;
    cursor: pointer;
  }
  .profile-pic img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  .bottom {
    position:fixed; bottom:12px; left:50%; transform:translateX(-50%); width:calc(100% - 40px); max-width:420px;
    display:flex; justify-content:space-between; gap:10px; padding:8px; background:var(--card);
    border-radius:14px; box-shadow:0 12px 30px rgba(2,6,23,0.12); border:1px solid var(--border);
  }
  .nav-btn { flex:1; padding:10px 12px; border-radius:10px; border:none; cursor:pointer; background:transparent; color:var(--muted); font-weight:700 }
  .nav-btn.active { background:linear-gradient(180deg,var(--accent), #0f8a4d); color:white }

  .note{ font-size:13px;color:var(--muted); margin-top:8px }
  .center{ text-align:center }

  /* Theme Toggle Button */
  .theme-toggle {
    position: absolute;
    top: 16px;
    right: 16px;
    width: 40px;
    height: 40px;
    border-radius: 50%;
    border: none;
    background: rgba(255,255,255,0.2);
    color: white;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: all 0.3s ease;
  }
  [data-theme="dark"] .theme-toggle {
    background: rgba(0,0,0,0.2);
    color: white;
  }
  .theme-toggle:hover {
    transform: scale(1.1);
  }

  /* Loading Indicator */
  .loading {
    display: none;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,0.5);
    z-index: 2000;
    justify-content: center;
    align-items: center;
    color: white;
    font-size: 18px;
  }

  .spinner {
    border: 4px solid rgba(255, 255, 255, 0.3);
    border-radius: 50%;
    border-top: 4px solid var(--accent);
    width: 40px;
    height: 40px;
    animation: spin 1s linear infinite;
    margin-right: 10px;
  }

  @keyframes spin {
    0% { transform: rotate(0deg); }
    100% { transform: rotate(360deg); }
  }

  /* Alert Messages */
  .alert {
    position: fixed;
    top: 20px;
    right: 20px;
    padding: 12px 20px;
    border-radius: 8px;
    color: white;
    font-weight: bold;
    z-index: 3000;
    box-shadow: 0 4px 12px rgba(0,0,0,0.15);
    transform: translateX(100%);
    transition: transform 0.3s ease;
  }
  .alert.success {
    background: var(--accent);
  }
  .alert.error {
    background: #ef4444;
  }
  .alert.show {
    transform: translateX(0);
  }

  @media(max-width:420px){
    .avatar{ width:64px; height:64px }
    .id-photo{ width:88px; height:88px }
    .bottom{ left:8px; right:8px; transform:none; width:auto; max-width:calc(100% - 16px) }
    .video-wrapper video {
      width: 150px;
      height: 112px;
    }
  }
</style>
</head>
<body data-theme="light">
<div class="app">

  <!-- SPLASH -->
  <section id="splash" class="splash">
    <button class="theme-toggle" id="splashThemeToggle">
      <i class="fas fa-moon"></i>
    </button>
    <div class="logo">AB</div>
    <h1>abramou يرحب بكم</h1>
    <p>تطبيق الحرفيين — أسرع طريقة تلقى الحرفي المناسب</p>
    <button id="startBtn" class="btn-start">ابدأ التطبيق</button>
  </section>

  <!-- LOGIN PAGE -->
  <div id="loginPage" class="login-page" style="display:none;">
    <div class="login-container">
      <h1>مرحباً بكم في تطبيق <span style="color:var(--accent)">Abramou</span></h1>
      <p>شكراً على حسن اختياركم! سجل دخولك أو أنشئ حساب جديد.</p>

      <div class="form-group">
        <label>البريد الإلكتروني</label>
        <input type="email" id="loginEmail" placeholder="ex@example.com">
      </div>

      <div class="form-group">
        <label>كلمة المرور</label>
        <input type="password" id="loginPassword" placeholder="••••••••">
      </div>

      <button class="btn-login" id="btnLogin">تسجيل الدخول</button>
      <button class="btn-register" id="btnRegister">أنشئ حساب جديد</button>

      <div class="login-footer">
        <small>بتسجيلك، توافق على <a href="#" style="color:var(--accent)">شروط الخدمة</a></small>
      </div>
    </div>
  </div>

  <!-- REGISTER PAGE -->
  <div id="registerPage" class="login-page" style="display:none;">
    <div class="login-container">
      <h1>إنشاء حساب جديد</h1>
      <p>أدخل معلوماتك لإنشاء حساب جديد</p>

      <div class="form-group">
        <label>الاسم الكامل</label>
        <input type="text" id="registerName" placeholder="أدخل اسمك الكامل">
      </div>

      <div class="form-group">
        <label>البريد الإلكتروني</label>
        <input type="email" id="registerEmail" placeholder="ex@example.com">
      </div>

      <div class="form-group">
        <label>كلمة المرور</label>
        <input type="password" id="registerPassword" placeholder="••••••••">
      </div>

      <button class="btn-login" id="btnSubmitRegister">إنشاء الحساب</button>
      <button class="btn-register" id="btnBackToLogin">العودة لتسجيل الدخول</button>
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

    <!-- role select -->
    <div class="card" id="roleCard">
      <div style="display:flex;justify-content:space-between;align-items:center">
        <div>
          <div style="font-weight:800;font-size:16px">مرحبا <span id="userNameDisplay">المستخدم</span></div>
          <div class="sub">اختار دورك باش تبدأ</div>
        </div>
      </div>
      <div class="roles" style="margin-top:12px">
        <button id="toArt" class="role-btn">جهة الحريف</button>
        <button id="toCli" class="role-btn ghost">جهة الكليان</button>
      </div>
    </div>

    <!-- Pages -->
    <section id="pageArt" class="page">
      <div class="card">
        <h3>أضف حريف جديد</h3>
        <form id="artisanForm">
          <label>الاسم الكامل</label>
          <input type="text" id="artisanName" required>
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
        <div class="artisan-list" id="artisanList">
          <!-- سيتم ملؤه ديناميكيًا -->
        </div>
      </div>
    </section>

    <section id="pageCli" class="page">
      <div class="card">
        <h3>ابحث عن حريف</h3>
        <input type="text" id="searchInput" placeholder="ابحث بالاسم أو المهنة..." style="width:100%;padding:10px;border-radius:10px;border:1px solid var(--border);background:var(--soft);color:var(--text);">
        <div class="artisan-list" id="searchResults">
          <!-- سيتم ملؤه عند البحث -->
        </div>
      </div>
    </section>

    <section id="chatPage" class="page">
      <div class="card">
        <div class="chat-header" id="chatHeader">اختر حريفًا للدردشة</div>
        <div class="messages" id="messages"></div>
        <div class="chat-input">
          <input type="text" id="msgInput" placeholder="اكتب رسالة..." disabled>
          <button id="sendMsg" disabled><i class="fas fa-paper-plane"></i></button>
        </div>
      </div>
    </section>

    <!-- صفحة المكالمات -->
    <section id="callPage" class="page">
      <div class="card">
        <h3>المكالمة الصوتية/الفيديوية</h3>
        <div class="call-container">
          <div class="video-container">
            <div class="video-wrapper">
              <video id="localVideo" autoplay muted playsinline></video>
              <div class="video-label">أنت</div>
            </div>
            <div class="video-wrapper">
              <video id="remoteVideo" autoplay playsinline></video>
              <div class="video-label" id="remoteName">الطرف الآخر</div>
            </div>
          </div>
          <div class="call-controls">
            <button id="startCall" class="call-btn">
              <i class="fas fa-video"></i> بدء المكالمة
            </button>
            <button id="endCall" class="call-btn end">
              <i class="fas fa-phone-slash"></i> إنهاء
            </button>
          </div>
          <div class="center" id="callStatus" style="color:var(--muted); margin-top: 10px;"></div>
        </div>
      </div>
    </section>

    <section id="settings" class="page">
      <div class="settings-card">
        <div class="profile-section">
          <div class="profile-pic" id="profilePic">
            <img src="https://via.placeholder.com/64?text=ص" alt="Profile">
          </div>
          <div>
            <div style="font-weight:800;" id="settingsUserNameDisplay">اسم المستخدم</div>
            <div style="color: var(--muted); font-size: 14px;">تغيير الصورة الشخصية</div>
          </div>
          <input type="file" id="picInput" style="display:none;" accept="image/*">
        </div>
      </div>

      <div class="settings-card">
        <div class="setting-item">
          <span>الوضع الليلي/النهاري</span>
          <div class="toggle-btn" id="themeToggle"></div>
        </div>
        <div class="setting-item">
          <span>الإشعارات</span>
          <div class="toggle-btn" id="notifToggle"></div>
        </div>
        <div class="setting-item">
          <span>تشغيل الأصوات</span>
          <div class="toggle-btn" id="soundToggle"></div>
        </div>
        <div class="setting-item">
          <span>إظهار ملفي للكليان</span>
          <div class="toggle-btn" id="visibilityToggle"></div>
        </div>
      </div>

      <div class="settings-card">
        <button id="clearData" class="btn ghost" style="width:100%;">مسح كل البيانات</button>
        <button id="logoutBtn" class="btn ghost" style="width:100%; margin-top: 10px;">تسجيل الخروج</button>
      </div>
    </section>

  </div>

  <!-- bottom nav -->
  <div class="bottom" id="bottom_nav">
    <button class="nav-btn active" data-page="pageArt">حرفيين</button>
    <button class="nav-btn" data-page="pageCli">بحث</button>
    <button class="nav-btn" data-page="chatPage">الدردشة</button>
    <button class="nav-btn" data-page="callPage">المكالمات</button>
    <button class="nav-btn" data-page="settings">الإعدادات</button>
  </div>

  <!-- Loading Indicator -->
  <div class="loading" id="loadingIndicator">
    <div class="spinner"></div>
    <span>جاري المعالجة...</span>
  </div>
</div>

<script>
/* ---------- Theme Management ---------- */
const THEME_KEY = 'theme';

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
  const newTheme = current === 'light' ? 'dark' : 'light';
  setTheme(newTheme);
}

function updateThemeIcon() {
  const isDark = getTheme() === 'dark';
  const icons = document.querySelectorAll('.theme-toggle i');
  icons.forEach(icon => {
    icon.className = isDark ? 'fas fa-sun' : 'fas fa-moon';
  });
}

/* ---------- Toggle Buttons ---------- */
function setupToggle(id, callback) {
  const el = document.getElementById(id);
  let state = localStorage.getItem(id) === 'true';
  el.classList.toggle('active', state);
  el.addEventListener('click', () => {
    state = !state;
    el.classList.toggle('active', state);
    localStorage.setItem(id, state);
    if (callback) callback(state);
  });
}

/* ---------- Utilities ---------- */
function showLoading(show = true) {
  document.getElementById('loadingIndicator').style.display = show ? 'flex' : 'none';
}

function showAlert(message, isError = false) {
  // إزالة التنبيهات السابقة
  const existingAlert = document.querySelector('.alert');
  if (existingAlert) {
    existingAlert.remove();
  }
  
  const alertDiv = document.createElement('div');
  alertDiv.className = `alert ${isError ? 'error' : 'success'} show`;
  alertDiv.textContent = message;
  document.body.appendChild(alertDiv);
  
  // إخفاء الرسالة بعد 3 ثوانٍ
  setTimeout(() => {
    alertDiv.style.transform = 'translateX(100%)';
    setTimeout(() => {
      if (alertDiv.parentNode) {
        alertDiv.parentNode.removeChild(alertDiv);
      }
    }, 300);
  }, 3000);
}

/* ---------- Navigation ---------- */
function showPage(pageId) {
  document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
  document.getElementById(pageId).classList.add('active');
  
  document.querySelectorAll('.nav-btn').forEach(btn => btn.classList.remove('active'));
  document.querySelector(`.nav-btn[data-page="${pageId}"]`).classList.add('active');
}

/* ---------- Role Selection ---------- */
document.getElementById('toArt').addEventListener('click', () => {
  document.getElementById('toArt').classList.add('role-btn');
  document.getElementById('toArt').classList.remove('ghost');
  document.getElementById('toCli').classList.add('ghost');
  document.getElementById('toCli').classList.remove('role-btn');
  showPage('pageArt');
});

document.getElementById('toCli').addEventListener('click', () => {
  document.getElementById('toCli').classList.add('role-btn');
  document.getElementById('toCli').classList.remove('ghost');
  document.getElementById('toArt').classList.add('ghost');
  document.getElementById('toArt').classList.remove('role-btn');
  showPage('pageCli');
});

/* ---------- Navigation ---------- */
document.querySelectorAll('.nav-btn').forEach(btn => {
  btn.addEventListener('click', () => {
    const page = btn.getAttribute('data-page');
    showPage(page);
  });
});

/* ---------- Profile Picture ---------- */
const profilePic = document.getElementById('profilePic');
const picInput = document.getElementById('picInput');

profilePic.addEventListener('click', () => picInput.click());

picInput.addEventListener('change', (e) => {
  const file = e.target.files[0];
  if (!file) return;
  const reader = new FileReader();
  reader.onload = () => {
    profilePic.querySelector('img').src = reader.result;
  };
  reader.readAsDataURL(file);
});

/* ---------- Theme Toggle Events ---------- */
document.getElementById('splashThemeToggle').addEventListener('click', toggleTheme);
document.getElementById('mainThemeToggle').addEventListener('click', toggleTheme);

/* ---------- Settings ---------- */
document.getElementById('clearData').addEventListener('click', () => {
  if (confirm('واش بغيتي تمسح كل البيانات؟')) {
    showAlert('تم مسح البيانات المحلية');
  }
});

// Initialize theme and toggles
setTheme(getTheme());
setupToggle('themeToggle', (state) => {
  setTheme(state ? 'dark' : 'light');
});
setupToggle('notifToggle');
setupToggle('soundToggle');
setupToggle('visibilityToggle');

// دوال الدردشة والمكالمات (للاستخدام المستقبلي)
window.openChat = function(artisanId, artisanName) {
  showAlert(`فتح الدردشة مع ${artisanName}`);
};

window.initiateCall = function(artisanId, artisanName) {
  showAlert(`بدء مكالمة مع ${artisanName}`);
};

// بدء التطبيق
document.getElementById('startBtn').addEventListener('click', () => {
  document.getElementById('splash').classList.add('fade-out');
  setTimeout(() => {
    document.getElementById('splash').style.display = 'none';
    document.getElementById('loginPage').style.display = 'flex';
  }, 600);
});

// التنقل بين صفحات تسجيل الدخول والتسجيل
document.getElementById('btnRegister').addEventListener('click', () => {
  document.getElementById('loginPage').style.display = 'none';
  document.getElementById('registerPage').style.display = 'flex';
});

document.getElementById('btnBackToLogin').addEventListener('click', () => {
  document.getElementById('registerPage').style.display = 'none';
  document.getElementById('loginPage').style.display = 'flex';
});

// معالجة التسجيل
document.getElementById('btnSubmitRegister').addEventListener('click', () => {
  const name = document.getElementById('registerName').value.trim();
  const email = document.getElementById('registerEmail').value.trim();
  const password = document.getElementById('registerPassword').value.trim();

  if (!name || !email || !password) {
    showAlert('الرجاء ملء جميع الحقول!', true);
    return;
  }

  if (password.length < 6) {
    showAlert('كلمة المرور يجب أن تكون 6 أحرف على الأقل!', true);
    return;
  }

  // هنا سيتم تنفيذ التسجيل الفعلي مع Firebase
  showAlert('تم إنشاء الحساب بنجاح! يمكنك الآن تسجيل الدخول.', false);
  
  // ملء حقول تسجيل الدخول تلقائيًا
  document.getElementById('loginEmail').value = email;
  document.getElementById('loginPassword').value = password;
  
  // العودة لصفحة تسجيل الدخول
  setTimeout(() => {
    document.getElementById('registerPage').style.display = 'none';
    document.getElementById('loginPage').style.display = 'flex';
  }, 1500);
});

// معالجة تسجيل الدخول
document.getElementById('btnLogin').addEventListener('click', () => {
  const email = document.getElementById('loginEmail').value.trim();
  const password = document.getElementById('loginPassword').value.trim();

  if (!email || !password) {
    showAlert('الرجاء إدخال البريد الإلكتروني وكلمة المرور!', true);
    return;
  }

  // هنا سيتم تنفيذ تسجيل الدخول الفعلي مع Firebase
  const mockUser = { name: "جميل", email: email };
  
  // عرض اسم المستخدم في الواجهة
  document.getElementById('userNameDisplay').textContent = mockUser.name;
  document.getElementById('settingsUserNameDisplay').textContent = mockUser.name;
  
  // عرض الواجهة الرئيسية
  document.getElementById('loginPage').style.opacity = '0';
  setTimeout(() => {
    document.getElementById('loginPage').style.display = 'none';
    document.getElementById('main').style.display = 'block';
    document.getElementById('main').style.opacity = '1';
    
    // عرض رسالة ترحيب
    showAlert(`مرحباً بك، ${mockUser.name}!`);
  }, 500);
});

// تسجيل الخروج
document.getElementById('logoutBtn').addEventListener('click', () => {
  showAlert('تم تسجيل الخروج بنجاح!');
  document.getElementById('main').style.display = 'none';
  document.getElementById('loginPage').style.display = 'flex';
});

// معالجة نموذج إضافة حريف
document.getElementById('artisanForm').addEventListener('submit', function(e) {
  e.preventDefault();
  const name = document.getElementById('artisanName').value.trim();
  const craft = document.getElementById('craft').value.trim();
  const phone = document.getElementById('phone').value.trim();
  
  if (!name || !craft || !phone) {
    showAlert('الرجاء ملء جميع الحقول!', true);
    return;
  }
  
  showAlert('تم حفظ الحريف بنجاح!');
  this.reset();
});

// البحث عن حرفيين
document.getElementById('searchInput').addEventListener('input', (e) => {
  const query = e.target.value.trim();
  const results = document.getElementById('searchResults');
  results.innerHTML = '';
  
  if (query.length < 2) {
    results.innerHTML = '<p class="center" style="color:var(--muted); padding: 20px;">اكتب لبدء البحث...</p>';
    return;
  }
  
  // مثال على نتائج البحث
  results.innerHTML = `
    <div class="artisan">
      <div class="avatar"><img src="https://via.placeholder.com/72?text=ح" alt="حريف"></div>
      <div class="meta">
        <h4>أحمد التمسماني</h4>
        <p>0612345678</p>
        <span class="tag">نجار</span>
      </div>
      <div class="controls">
        <button class="btn small">دردشة</button>
        <button class="btn small ghost"><i class="fas fa-phone"></i> اتصال</button>
      </div>
    </div>
    <div class="artisan">
      <div class="avatar"><img src="https://via.placeholder.com/72?text=ح" alt="حريف"></div>
      <div class="meta">
        <h4>محمد الزعيمي</h4>
        <p>0687654321</p>
        <span class="tag">سباك</span>
      </div>
      <div class="controls">
        <button class="btn small">دردشة</button>
        <button class="btn small ghost"><i class="fas fa-phone"></i> اتصال</button>
      </div>
    </div>
  `;
});
</script>

</body>
</html>
