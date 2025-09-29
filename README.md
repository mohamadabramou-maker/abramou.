<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1,viewport-fit=cover" />
<meta name="description" content="الحريفية — أفضل تطبيق للحرفيين في منطقتك" />
<title>الحريفية — Abramou</title>

<!-- Leaflet -->
<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" integrity="sha256-p4NxAoJBhIIN+hmNHrzRCf9tD/miZyoHS5obTRR9BMY=" crossorigin=""/>
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js" integrity="sha256-20nQCchB9co0qIjJZRGuk2/Z9VM+kNiyxNV1lvTlZBo=" crossorigin=""></script>

<!-- Fonts -->
<link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">

<style>
  :root {
    --primary: #0f9d58;
    --primary-dark: #0a7a44;
    --primary-light: #23b475;
    --secondary: #6b7280;
    --success: #10b981;
    --warning: #f59e0b;
    --danger: #ef4444;
    --info: #3b82f6;
    --light: #f8fafc;
    --dark: #0f172a;
    --white: #ffffff;
    --gray-100: #f1f5f9;
    --gray-200: #e2e8f0;
    --gray-300: #cbd5e1;
    --gray-400: #94a3b8;
    --gray-500: #64748b;
    --gray-600: #475569;
    --gray-700: #334155;
    --gray-800: #1e293b;
    --gray-900: #0f172a;
    --shadow-sm: 0 1px 2px 0 rgba(0, 0, 0, 0.05);
    --shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
    --shadow-md: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
    --shadow-lg: 0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04);
    --shadow-xl: 0 25px 50px -12px rgba(0, 0, 0, 0.25);
    --radius-xs: 4px;
    --radius-sm: 6px;
    --radius: 8px;
    --radius-md: 12px;
    --radius-lg: 16px;
    --radius-xl: 20px;
    --radius-2xl: 24px;
    --radius-full: 9999px;
    --transition: all 0.2s cubic-bezier(0.4, 0, 0.2, 1);
    --ease-in: cubic-bezier(0.4, 0, 1, 1);
    --ease-out: cubic-bezier(0, 0, 0.2, 1);
    --ease-in-out: cubic-bezier(0.4, 0, 0.2, 1);
  }

  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  html {
    scroll-behavior: smooth;
  }

  body {
    font-family: 'Tajawal', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    background-color: var(--gray-100);
    color: var(--gray-800);
    line-height: 1.5;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    min-height: 100vh;
  }

  /* Loading Overlay */
  .loading-overlay {
    position: fixed;
    inset: 0;
    background: rgba(255, 255, 255, 0.9);
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 10000;
    opacity: 1;
    transition: opacity 0.3s ease;
  }

  .loading-overlay.hidden {
    opacity: 0;
    pointer-events: none;
  }

  .spinner {
    width: 48px;
    height: 48px;
    border: 4px solid rgba(15, 157, 88, 0.1);
    border-top-color: var(--primary);
    border-radius: 50%;
    animation: spin 1s linear infinite;
  }

  @keyframes spin {
    to { transform: rotate(360deg); }
  }

  /* Header */
  header {
    background: linear-gradient(135deg, rgba(255,255,255,0.95) 0%, rgba(255,255,255,0.85) 100%);
    backdrop-filter: blur(12px);
    -webkit-backdrop-filter: blur(12px);
    padding: 16px 20px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 16px;
    border-bottom: 1px solid rgba(15, 157, 88, 0.1);
    position: sticky;
    top: 0;
    z-index: 100;
    box-shadow: var(--shadow-sm);
  }

  .brand {
    display: flex;
    align-items: center;
    gap: 12px;
    min-width: 0;
  }

  .logo {
    width: 44px;
    height: 44px;
    border-radius: var(--radius-lg);
    background: linear-gradient(135deg, var(--primary) 0%, var(--primary-dark) 100%);
    display: flex;
    align-items: center;
    justify-content: center;
    color: var(--white);
    font-weight: 800;
    font-size: 18px;
    box-shadow: var(--shadow-md);
  }

  .app-info {
    min-width: 0;
  }

  .app-title {
    font-weight: 700;
    font-size: 18px;
    color: var(--gray-900);
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }

  .app-subtitle {
    font-size: 13px;
    color: var(--gray-600);
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }

  .header-actions {
    display: flex;
    align-items: center;
    gap: 12px;
  }

  .notification-btn {
    position: relative;
    background: transparent;
    border: none;
    cursor: pointer;
    padding: 8px;
    border-radius: var(--radius-full);
    transition: var(--transition);
  }

  .notification-btn:hover {
    background: var(--gray-200);
  }

  .notification-badge {
    position: absolute;
    top: -4px;
    right: -4px;
    background: var(--danger);
    color: var(--white);
    font-size: 10px;
    font-weight: 600;
    width: 18px;
    height: 18px;
    border-radius: var(--radius-full);
    display: flex;
    align-items: center;
    justify-content: center;
    display: none;
  }

  .notification-badge.show {
    display: flex;
  }

  /* Main Layout */
  .main-container {
    display: grid;
    grid-template-columns: 320px 1fr;
    gap: 20px;
    max-width: 1400px;
    margin: 20px auto;
    padding: 0 20px;
    min-height: calc(100vh - 120px);
  }

  @media (max-width: 992px) {
    .main-container {
      grid-template-columns: 1fr;
      padding: 0 16px;
    }
  }

  /* Sidebar */
  .sidebar {
    background: var(--white);
    border-radius: var(--radius-xl);
    padding: 20px;
    box-shadow: var(--shadow);
    height: fit-content;
    position: sticky;
    top: 80px;
    align-self: flex-start;
  }

  .user-card {
    display: flex;
    align-items: center;
    gap: 16px;
    padding: 16px;
    background: linear-gradient(135deg, rgba(241, 245, 249, 0.8) 0%, rgba(255, 255, 255, 0.9) 100%);
    border-radius: var(--radius-lg);
    border: 1px solid var(--gray-200);
    margin-bottom: 20px;
  }

  .user-avatar {
    width: 56px;
    height: 56px;
    border-radius: var(--radius-xl);
    background: linear-gradient(135deg, var(--primary-light) 0%, var(--primary) 100%);
    display: flex;
    align-items: center;
    justify-content: center;
    color: var(--white);
    font-weight: 700;
    font-size: 20px;
    box-shadow: var(--shadow-sm);
  }

  .user-details {
    flex: 1;
    min-width: 0;
  }

  .user-name {
    font-weight: 700;
    font-size: 16px;
    color: var(--gray-900);
    margin-bottom: 4px;
  }

  .user-email {
    font-size: 13px;
    color: var(--gray-600);
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }

  .search-section {
    margin-bottom: 20px;
  }

  .search-input {
    width: 100%;
    padding: 12px 16px;
    border: 2px solid var(--gray-200);
    border-radius: var(--radius-lg);
    font-size: 14px;
    transition: var(--transition);
  }

  .search-input:focus {
    outline: none;
    border-color: var(--primary);
    box-shadow: 0 0 0 3px rgba(15, 157, 88, 0.1);
  }

  .add-btn {
    width: 100%;
    padding: 12px;
    background: linear-gradient(135deg, var(--primary) 0%, var(--primary-dark) 100%);
    color: var(--white);
    border: none;
    border-radius: var(--radius-lg);
    font-weight: 600;
    font-size: 14px;
    cursor: pointer;
    transition: var(--transition);
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
    box-shadow: var(--shadow-sm);
  }

  .add-btn:hover {
    transform: translateY(-2px);
    box-shadow: var(--shadow);
  }

  .filters-section {
    margin-bottom: 20px;
  }

  .filter-label {
    display: block;
    font-size: 13px;
    font-weight: 600;
    color: var(--gray-700);
    margin-bottom: 8px;
  }

  .filter-input, .filter-select {
    width: 100%;
    padding: 12px 16px;
    border: 2px solid var(--gray-200);
    border-radius: var(--radius-lg);
    font-size: 14px;
    background: var(--white);
    transition: var(--transition);
  }

  .filter-input:focus, .filter-select:focus {
    outline: none;
    border-color: var(--primary);
    box-shadow: 0 0 0 3px rgba(15, 157, 88, 0.1);
  }

  .filter-actions {
    display: flex;
    gap: 12px;
    margin-top: 16px;
  }

  .btn {
    padding: 10px 16px;
    border-radius: var(--radius-lg);
    font-weight: 600;
    font-size: 14px;
    cursor: pointer;
    transition: var(--transition);
    border: none;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
  }

  .btn-primary {
    background: linear-gradient(135deg, var(--primary) 0%, var(--primary-dark) 100%);
    color: var(--white);
    box-shadow: var(--shadow-sm);
  }

  .btn-primary:hover {
    transform: translateY(-2px);
    box-shadow: var(--shadow);
  }

  .btn-outline {
    background: transparent;
    border: 2px solid var(--gray-300);
    color: var(--gray-700);
  }

  .btn-outline:hover {
    border-color: var(--primary);
    color: var(--primary);
  }

  .btn-danger {
    background: linear-gradient(135deg, var(--danger) 0%, #dc2626 100%);
    color: var(--white);
    box-shadow: var(--shadow-sm);
  }

  .btn-danger:hover {
    transform: translateY(-2px);
    box-shadow: var(--shadow);
  }

  .artisans-section {
    margin-top: 20px;
  }

  .section-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 16px;
  }

  .section-title {
    font-weight: 700;
    font-size: 18px;
    color: var(--gray-900);
  }

  .section-count {
    font-size: 14px;
    color: var(--gray-600);
    font-weight: 600;
  }

  .artisans-list {
    max-height: 50vh;
    overflow-y: auto;
    padding-right: 4px;
  }

  .artisans-list::-webkit-scrollbar {
    width: 6px;
  }

  .artisans-list::-webkit-scrollbar-track {
    background: var(--gray-100);
    border-radius: var(--radius-full);
  }

  .artisans-list::-webkit-scrollbar-thumb {
    background: var(--gray-300);
    border-radius: var(--radius-full);
  }

  .artisans-list::-webkit-scrollbar-thumb:hover {
    background: var(--gray-400);
  }

  .artisan-card {
    background: var(--white);
    border: 2px solid var(--gray-200);
    border-radius: var(--radius-lg);
    padding: 16px;
    margin-bottom: 16px;
    cursor: pointer;
    transition: var(--transition);
    position: relative;
    overflow: hidden;
  }

  .artisan-card:hover {
    transform: translateY(-4px);
    border-color: var(--primary);
    box-shadow: var(--shadow-md);
  }

  .artisan-card::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    height: 3px;
    background: linear-gradient(90deg, var(--primary) 0%, var(--primary-light) 100%);
    opacity: 0;
    transition: var(--transition);
  }

  .artisan-card:hover::before {
    opacity: 1;
  }

  .artisan-header {
    display: flex;
    gap: 16px;
    margin-bottom: 12px;
  }

  .artisan-avatar {
    width: 60px;
    height: 60px;
    border-radius: var(--radius-lg);
    background: linear-gradient(135deg, var(--gray-200) 0%, var(--gray-300) 100%);
    display: flex;
    align-items: center;
    justify-content: center;
    font-weight: 700;
    color: var(--primary);
    font-size: 20px;
    flex-shrink: 0;
  }

  .artisan-info {
    flex: 1;
    min-width: 0;
  }

  .artisan-name {
    font-weight: 700;
    font-size: 16px;
    color: var(--gray-900);
    margin-bottom: 4px;
  }

  .artisan-job {
    font-size: 14px;
    color: var(--gray-600);
    margin-bottom: 4px;
  }

  .artisan-price {
    font-size: 14px;
    font-weight: 600;
    color: var(--primary);
  }

  .artisan-meta {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-top: 8px;
    padding-top: 8px;
    border-top: 1px solid var(--gray-200);
  }

  .artisan-rating {
    display: flex;
    align-items: center;
    gap: 4px;
    font-weight: 600;
    color: var(--warning);
    font-size: 14px;
  }

  .artisan-distance {
    font-size: 13px;
    color: var(--gray-600);
  }

  .artisan-description {
    font-size: 14px;
    color: var(--gray-700);
    line-height: 1.4;
    margin-top: 8px;
    display: -webkit-box;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
    overflow: hidden;
  }

  /* Main Content */
  .main-content {
    display: flex;
    flex-direction: column;
    gap: 20px;
  }

  .map-section {
    background: var(--white);
    border-radius: var(--radius-xl);
    padding: 20px;
    box-shadow: var(--shadow);
  }

  .section-header-main {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 16px;
  }

  .map-title {
    font-weight: 800;
    font-size: 20px;
    color: var(--gray-900);
  }

  .map-subtitle {
    font-size: 14px;
    color: var(--gray-600);
  }

  .map-actions {
    display: flex;
    gap: 12px;
  }

  .map-container {
    height: 400px;
    border-radius: var(--radius-lg);
    overflow: hidden;
    border: 2px solid var(--gray-200);
  }

  #map {
    height: 100%;
    width: 100%;
  }

  .content-area {
    background: var(--white);
    border-radius: var(--radius-xl);
    padding: 20px;
    box-shadow: var(--shadow);
    min-height: 300px;
  }

  .welcome-content {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
    padding: 40px 20px;
    min-height: 300px;
  }

  .welcome-icon {
    width: 80px;
    height: 80px;
    background: linear-gradient(135deg, rgba(15, 157, 88, 0.1) 0%, rgba(35, 180, 117, 0.1) 100%);
    border-radius: var(--radius-2xl);
    display: flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 24px;
  }

  .welcome-icon svg {
    width: 40px;
    height: 40px;
    color: var(--primary);
  }

  .welcome-title {
    font-weight: 800;
    font-size: 28px;
    color: var(--gray-900);
    margin-bottom: 12px;
  }

  .welcome-subtitle {
    font-size: 16px;
    color: var(--gray-600);
    max-width: 600px;
    margin-bottom: 24px;
    line-height: 1.6;
  }

  .quick-actions {
    display: flex;
    gap: 16px;
    margin-top: 24px;
    width: 100%;
    max-width: 500px;
  }

  .quick-search {
    flex: 1;
  }

  .quick-search-input {
    width: 100%;
    padding: 14px 20px;
    border: 2px solid var(--gray-300);
    border-radius: var(--radius-lg);
    font-size: 16px;
    transition: var(--transition);
  }

  .quick-search-input:focus {
    outline: none;
    border-color: var(--primary);
    box-shadow: 0 0 0 3px rgba(15, 157, 88, 0.1);
  }

  /* Modals */
  .modal-overlay {
    position: fixed;
    inset: 0;
    background: rgba(0, 0, 0, 0.5);
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 2000;
    opacity: 0;
    visibility: hidden;
    transition: var(--transition);
  }

  .modal-overlay.active {
    opacity: 1;
    visibility: visible;
  }

  .modal {
    background: var(--white);
    border-radius: var(--radius-2xl);
    width: 100%;
    max-width: 600px;
    max-height: 90vh;
    overflow: auto;
    box-shadow: var(--shadow-xl);
    transform: scale(0.95);
    transition: transform 0.3s var(--ease-out);
  }

  .modal-overlay.active .modal {
    transform: scale(1);
  }

  .modal-header {
    padding: 24px 24px 16px;
    border-bottom: 1px solid var(--gray-200);
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .modal-title {
    font-weight: 700;
    font-size: 20px;
    color: var(--gray-900);
  }

  .modal-close {
    background: transparent;
    border: none;
    font-size: 24px;
    cursor: pointer;
    color: var(--gray-500);
    width: 36px;
    height: 36px;
    border-radius: var(--radius-full);
    display: flex;
    align-items: center;
    justify-content: center;
    transition: var(--transition);
  }

  .modal-close:hover {
    background: var(--gray-100);
    color: var(--gray-700);
  }

  .modal-body {
    padding: 24px;
  }

  .form-group {
    margin-bottom: 20px;
  }

  .form-label {
    display: block;
    font-weight: 600;
    font-size: 14px;
    color: var(--gray-700);
    margin-bottom: 8px;
  }

  .form-control {
    width: 100%;
    padding: 14px 16px;
    border: 2px solid var(--gray-300);
    border-radius: var(--radius-lg);
    font-size: 16px;
    transition: var(--transition);
  }

  .form-control:focus {
    outline: none;
    border-color: var(--primary);
    box-shadow: 0 0 0 3px rgba(15, 157, 88, 0.1);
  }

  .form-row {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 16px;
  }

  .form-actions {
    display: flex;
    justify-content: flex-end;
    gap: 12px;
    margin-top: 24px;
  }

  /* Toast */
  .toast {
    position: fixed;
    bottom: 20px;
    left: 50%;
    transform: translateX(-50%) translateY(100px);
    background: var(--gray-900);
    color: var(--white);
    padding: 16px 24px;
    border-radius: var(--radius-lg);
    box-shadow: var(--shadow-lg);
    z-index: 3000;
    opacity: 0;
    transition: transform 0.3s var(--ease-out), opacity 0.3s var(--ease-out);
  }

  .toast.show {
    transform: translateX(-50%) translateY(0);
    opacity: 1;
  }

  /* Footer */
  footer {
    text-align: center;
    padding: 32px 20px;
    color: var(--gray-600);
    font-size: 14px;
    margin-top: 40px;
  }

  /* Responsive */
  @media (max-width: 768px) {
    .main-container {
      margin: 16px auto;
    }
    
    .quick-actions {
      flex-direction: column;
    }
    
    .map-container {
      height: 300px;
    }
    
    .artisan-header {
      flex-direction: column;
      align-items: flex-start;
    }
    
    .artisan-avatar {
      width: 50px;
      height: 50px;
    }
  }

  @media (max-width: 480px) {
    .header-actions {
      gap: 8px;
    }
    
    .logo {
      width: 40px;
      height: 40px;
      font-size: 16px;
    }
    
    .app-title {
      font-size: 16px;
    }
    
    .modal {
      margin: 16px;
      border-radius: var(--radius-xl);
    }
  }

  /* Input fixes for RTL */
  input, textarea, select {
    direction: ltr;
    text-align: left;
    font-family: inherit;
  }

  input::placeholder, textarea::placeholder {
    direction: ltr;
    text-align: left;
    color: var(--gray-400);
  }

  /* Animation classes */
  .fade-in {
    animation: fadeIn 0.3s ease-out forwards;
  }

  @keyframes fadeIn {
    from { opacity: 0; transform: translateY(10px); }
    to { opacity: 1; transform: translateY(0); }
  }

  .slide-up {
    animation: slideUp 0.4s ease-out forwards;
  }

  @keyframes slideUp {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
  }
</style>
</head>
<body>

<!-- Loading Overlay -->
<div id="loadingOverlay" class="loading-overlay">
  <div class="spinner"></div>
</div>

<!-- Header -->
<header>
  <div class="brand">
    <div class="logo">ح</div>
    <div class="app-info">
      <div class="app-title">الحريفية</div>
      <div class="app-subtitle">Abramou — أفضل الحرفيين في منطقتك</div>
    </div>
  </div>
  
  <div class="header-actions">
    <button id="notificationBtn" class="notification-btn">
      <svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
        <path d="M18 8A6 6 0 0 0 6 8c0 7-3 9-3 9h18s-3-2-3-9"></path>
        <path d="M13.73 21a2 2 0 0 1-3.46 0"></path>
      </svg>
      <div id="notificationBadge" class="notification-badge">0</div>
    </button>
    
    <div id="authSection">
      <button id="loginBtn" class="btn btn-outline">تسجيل الدخول</button>
    </div>
    
    <div id="userSection" style="display: none;">
      <div class="user-avatar" id="headerUserAvatar">أ</div>
    </div>
  </div>
</header>

<!-- Main Content -->
<div class="main-container">
  <!-- Sidebar -->
  <div class="sidebar">
    <div class="user-card">
      <div class="user-avatar" id="sidebarUserAvatar">أ</div>
      <div class="user-details">
        <div class="user-name" id="sidebarUserName">مرحباً بك</div>
        <div class="user-email" id="sidebarUserEmail">استكشف الحرفيين</div>
      </div>
    </div>
    
    <div class="search-section">
      <input type="text" id="searchInput" class="search-input" placeholder="ابحث باسم الحرفي أو المهنة...">
      <button id="addArtisanBtn" class="add-btn">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <line x1="12" y1="5" x2="12" y2="19"></line>
          <line x1="5" y1="12" x2="19" y2="12"></line>
        </svg>
        إضافة حرفي
      </button>
    </div>
    
    <div class="filters-section">
      <label class="filter-label">المهنة</label>
      <input type="text" id="jobFilter" class="filter-input" placeholder="مثال: حداد، سباك، نجار">
      
      <label class="filter-label" style="margin-top: 16px;">المسافة (كم)</label>
      <select id="distanceFilter" class="filter-select">
        <option value="0">جميع المسافات</option>
        <option value="5">حتى 5 كم</option>
        <option value="15">حتى 15 كم</option>
        <option value="50">حتى 50 كم</option>
      </select>
      
      <div class="filter-actions">
        <button id="applyFiltersBtn" class="btn btn-primary">تطبيق الفلاتر</button>
        <button id="clearFiltersBtn" class="btn btn-outline">مسح الكل</button>
      </div>
    </div>
    
    <div class="artisans-section">
      <div class="section-header">
        <h2 class="section-title">الحرفيون</h2>
        <span class="section-count" id="artisansCount">0</span>
      </div>
      <div class="artisans-list" id="artisansList"></div>
    </div>
  </div>
  
  <!-- Main Content Area -->
  <div class="main-content">
    <div class="map-section">
      <div class="section-header-main">
        <div>
          <h2 class="map-title">خريطة الحرفيين</h2>
          <p class="map-subtitle">انقر على العلامة لعرض تفاصيل الحرفي</p>
        </div>
        <div class="map-actions">
          <button id="locateMeBtn" class="btn btn-outline">
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0 1 18 0z"></path>
              <circle cx="12" cy="10" r="3"></circle>
            </svg>
            موقعي
          </button>
          <button id="refreshMapBtn" class="btn btn-outline">
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <polyline points="23 4 23 10 17 10"></polyline>
              <polyline points="1 20 1 14 7 14"></polyline>
              <path d="M3.51 9a9 9 0 0 1 14.85-3.36L23 10M1 14l4.64 4.36A9 9 0 0 0 20.49 15"></path>
            </svg>
            تحديث
          </button>
        </div>
      </div>
      <div class="map-container">
        <div id="map"></div>
      </div>
    </div>
    
    <div class="content-area" id="contentArea">
      <div class="welcome-content fade-in">
        <div class="welcome-icon">
          <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <path d="M20.24 12.24a6 6 0 0 0-8.49-8.49L5 10.5V19h8.5z"></path>
            <line x1="16" y1="16" x2="2" y2="2"></line>
            <line x1="12" y1="1" x2="12" y2="5"></line>
            <line x1="1" y1="12" x2="5" y2="12"></line>
          </svg>
        </div>
        <h1 class="welcome-title">مرحباً بك في الحريفية!</h1>
        <p class="welcome-subtitle">ابحث عن أفضل الحرفيين في منطقتك، احجز مواعيد، وتواصل معهم مباشرة. كل شيء في مكان واحد!</p>
        <div class="quick-actions">
          <div class="quick-search">
            <input type="text" id="quickSearch" class="quick-search-input" placeholder="ابحث عن حرفي (حداد، سباك، نجار...)">
          </div>
          <button id="viewBookingsBtn" class="btn btn-outline">حجوزاتي</button>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- Toast Notification -->
<div id="toast" class="toast"></div>

<!-- Footer -->
<footer>
  <p>© 2025 Abramou — الحريفية. جميع الحقوق محفوظة.</p>
</footer>

<!-- Modals will be added dynamically via JavaScript -->

<script>
// ======================
// Professional App Architecture
// ======================

class ArtisanApp {
  constructor() {
    this.state = {
      user: null,
      artisans: [],
      bookings: [],
      notifications: [],
      map: null,
      markers: new Map(),
      currentLocation: null,
      filters: {
        search: '',
        job: '',
        distance: 0
      }
    };
    
    this.storageKeys = {
      USER: 'artisan_app_user',
      ARTISANS: 'artisan_app_artisans',
      BOOKINGS: 'artisan_app_bookings',
      NOTIFICATIONS: 'artisan_app_notifications'
    };
    
    this.init();
  }
  
  // Initialize the application
  async init() {
    this.showLoading();
    await this.loadState();
    this.bindEvents();
    this.initMap();
    this.renderUI();
    this.hideLoading();
  }
  
  // Show loading overlay
  showLoading() {
    document.getElementById('loadingOverlay').classList.remove('hidden');
  }
  
  // Hide loading overlay
  hideLoading() {
    setTimeout(() => {
      document.getElementById('loadingOverlay').classList.add('hidden');
    }, 300);
  }
  
  // Load state from localStorage
  loadState() {
    return new Promise((resolve) => {
      try {
        const user = localStorage.getItem(this.storageKeys.USER);
        const artisans = localStorage.getItem(this.storageKeys.ARTISANS);
        const bookings = localStorage.getItem(this.storageKeys.BOOKINGS);
        const notifications = localStorage.getItem(this.storageKeys.NOTIFICATIONS);
        
        this.state.user = user ? JSON.parse(user) : null;
        this.state.artisans = artisans ? JSON.parse(artisans) : this.getDefaultArtisans();
        this.state.bookings = bookings ? JSON.parse(bookings) : [];
        this.state.notifications = notifications ? JSON.parse(notifications) : [];
        
        // Save default data if empty
        if (!artisans) {
          localStorage.setItem(this.storageKeys.ARTISANS, JSON.stringify(this.state.artisans));
        }
      } catch (error) {
        console.error('Error loading state:', error);
        this.showToast('حدث خطأ أثناء تحميل البيانات');
      }
      resolve();
    });
  }
  
  // Get default artisans data
  getDefaultArtisans() {
    return [
      {
        id: this.generateId(),
        name: 'أحمد الحداد',
        job: 'حداد',
        phone: '0612345678',
        price: 'من 300 درهم',
        description: 'حداد متمرس في صناعة الأبواب والدرابزين والأسوار المعدنية. خدمة محترفة مع ضمان الجودة.',
        photos: [],
        lat: 33.5900,
        lng: -7.6000,
        ratings: [
          { user: 'user1@example.com', stars: 5, text: 'عمل ممتاز ودقيق', date: new Date().toISOString() }
        ],
        messages: []
      },
      {
        id: this.generateId(),
        name: 'فاطمة النجارة',
        job: 'نجارة',
        phone: '0622345678',
        price: 'من 500 درهم',
        description: 'تفصيل أثاث خشبي حسب الطلب مع أعلى جودة في المواد والتصنيع.',
        photos: [],
        lat: 33.5820,
        lng: -7.6250,
        ratings: [],
        messages: []
      },
      {
        id: this.generateId(),
        name: 'خالد السباك',
        job: 'سباك',
        phone: '0631122334',
        price: 'يبدأ من 150 درهم',
        description: 'أعمال السباكة والصيانة المنزلية بسرعة واحترافية.',
        photos: [],
        lat: 33.5730,
        lng: -7.6100,
        ratings: [],
        messages: []
      }
    ];
  }
  
  // Save state to localStorage
  saveState() {
    try {
      localStorage.setItem(this.storageKeys.USER, JSON.stringify(this.state.user));
      localStorage.setItem(this.storageKeys.ARTISANS, JSON.stringify(this.state.artisans));
      localStorage.setItem(this.storageKeys.BOOKINGS, JSON.stringify(this.state.bookings));
      localStorage.setItem(this.storageKeys.NOTIFICATIONS, JSON.stringify(this.state.notifications));
      this.updateNotificationBadge();
    } catch (error) {
      console.error('Error saving state:', error);
      this.showToast('حدث خطأ أثناء حفظ البيانات');
    }
  }
  
  // Bind all event listeners
  bindEvents() {
    // Authentication
    document.getElementById('loginBtn').addEventListener('click', () => this.showAuthModal());
    document.getElementById('authSection').addEventListener('click', (e) => {
      if (e.target.id === 'loginBtn') this.showAuthModal();
    });
    
    // Search
    document.getElementById('searchInput').addEventListener('input', () => this.applyFilters());
    document.getElementById('quickSearch').addEventListener('keypress', (e) => {
      if (e.key === 'Enter') {
        document.getElementById('searchInput').value = e.target.value;
        this.applyFilters();
      }
    });
    
    // Filters
    document.getElementById('jobFilter').addEventListener('input', () => this.applyFilters());
    document.getElementById('distanceFilter').addEventListener('change', () => this.applyFilters());
    document.getElementById('applyFiltersBtn').addEventListener('click', () => this.applyFilters());
    document.getElementById('clearFiltersBtn').addEventListener('click', () => this.clearFilters());
    
    // Map actions
    document.getElementById('locateMeBtn').addEventListener('click', () => this.locateUser());
    document.getElementById('refreshMapBtn').addEventListener('click', () => this.refreshMap());
    
    // Artisan actions
    document.getElementById('addArtisanBtn').addEventListener('click', () => this.showAddArtisanModal());
    document.getElementById('viewBookingsBtn').addEventListener('click', () => this.showBookingsModal());
    
    // Notifications
    document.getElementById('notificationBtn').addEventListener('click', () => this.showNotificationsModal());
    
    // Close modals on escape key
    document.addEventListener('keydown', (e) => {
      if (e.key === 'Escape') {
        this.closeAllModals();
      }
    });
  }
  
  // Initialize map
  initMap() {
    try {
      this.state.map = L.map('map', {
        zoomControl: true,
        attributionControl: false
      }).setView([33.5883, -7.6114], 12);
      
      L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
        maxZoom: 19,
        attribution: '© OpenStreetMap contributors'
      }).addTo(this.state.map);
      
      this.renderMapMarkers();
    } catch (error) {
      console.error('Error initializing map:', error);
      this.showToast('حدث خطأ أثناء تحميل الخريطة');
    }
  }
  
  // Render UI based on current state
  renderUI() {
    this.updateAuthUI();
    this.renderArtisansList();
    this.updateNotificationBadge();
  }
  
  // Update authentication UI
  updateAuthUI() {
    const authSection = document.getElementById('authSection');
    const userSection = document.getElementById('userSection');
    const sidebarUserName = document.getElementById('sidebarUserName');
    const sidebarUserEmail = document.getElementById('sidebarUserEmail');
    const sidebarUserAvatar = document.getElementById('sidebarUserAvatar');
    const headerUserAvatar = document.getElementById('headerUserAvatar');
    
    if (this.state.user) {
      authSection.style.display = 'none';
      userSection.style.display = 'block';
      sidebarUserName.textContent = this.state.user.name;
      sidebarUserEmail.textContent = this.state.user.email;
      const initials = this.getUserInitials(this.state.user.name);
      sidebarUserAvatar.textContent = initials;
      headerUserAvatar.textContent = initials;
    } else {
      authSection.style.display = 'block';
      userSection.style.display = 'none';
      sidebarUserName.textContent = 'مرحباً بك';
      sidebarUserEmail.textContent = 'استكشف الحرفيين';
      sidebarUserAvatar.textContent = 'أ';
      headerUserAvatar.textContent = 'أ';
    }
  }
  
  // Render artisans list
  renderArtisansList() {
    const listContainer = document.getElementById('artisansList');
    const countElement = document.getElementById('artisansCount');
    
    // Apply filters
    let filteredArtisans = this.state.artisans;
    
    if (this.state.filters.search) {
      const searchTerm = this.state.filters.search.toLowerCase();
      filteredArtisans = filteredArtisans.filter(artisan => 
        artisan.name.toLowerCase().includes(searchTerm) ||
        artisan.job.toLowerCase().includes(searchTerm) ||
        (artisan.description && artisan.description.toLowerCase().includes(searchTerm))
      );
    }
    
    if (this.state.filters.job) {
      const jobTerm = this.state.filters.job.toLowerCase();
      filteredArtisans = filteredArtisans.filter(artisan => 
        artisan.job.toLowerCase().includes(jobTerm)
      );
    }
    
    if (this.state.filters.distance > 0 && this.state.currentLocation) {
      filteredArtisans = filteredArtisans.filter(artisan => 
        artisan.lat && artisan.lng && 
        this.calculateDistance(
          this.state.currentLocation.lat,
          this.state.currentLocation.lng,
          artisan.lat,
          artisan.lng
        ) <= this.state.filters.distance
      );
    }
    
    // Render list
    listContainer.innerHTML = '';
    countElement.textContent = filteredArtisans.length;
    
    if (filteredArtisans.length === 0) {
      listContainer.innerHTML = `
        <div style="text-align: center; padding: 40px 20px; color: var(--gray-500);">
          <svg width="48" height="48" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" style="margin: 0 auto 16px;">
            <circle cx="12" cy="12" r="10"></circle>
            <line x1="12" y1="8" x2="12" y2="12"></line>
            <line x1="12" y1="16" x2="12.01" y2="16"></line>
          </svg>
          <p>لا يوجد حرفيون يطابقون البحث</p>
        </div>
      `;
      return;
    }
    
    filteredArtisans.forEach(artisan => {
      const distance = this.state.currentLocation && artisan.lat && artisan.lng
        ? this.calculateDistance(
            this.state.currentLocation.lat,
            this.state.currentLocation.lng,
            artisan.lat,
            artisan.lng
          ).toFixed(1)
        : null;
      
      const avgRating = artisan.ratings.length > 0
        ? (artisan.ratings.reduce((sum, r) => sum + r.stars, 0) / artisan.ratings.length).toFixed(1)
        : 0;
      
      const card = document.createElement('div');
      card.className = 'artisan-card slide-up';
      card.innerHTML = `
        <div class="artisan-header">
          <div class="artisan-avatar">${this.getUserInitials(artisan.name)}</div>
          <div class="artisan-info">
            <div class="artisan-name">${this.escapeHtml(artisan.name)}</div>
            <div class="artisan-job">${this.escapeHtml(artisan.job)}</div>
            <div class="artisan-price">${artisan.price || 'غير محدد'}</div>
          </div>
        </div>
        <div class="artisan-description">${this.escapeHtml(artisan.description || 'لا يوجد وصف')}</div>
        <div class="artisan-meta">
          <div class="artisan-rating">
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <polygon points="12 2 15.09 8.26 22 9.27 17 14.14 18.18 21.02 12 17.77 5.82 21.02 7 14.14 2 9.27 8.91 8.26 12 2"></polygon>
            </svg>
            ${avgRating} (${artisan.ratings.length})
          </div>
          ${distance ? `<div class="artisan-distance">${distance} كم</div>` : ''}
        </div>
      `;
      
      card.addEventListener('click', () => this.showArtisanProfile(artisan.id));
      listContainer.appendChild(card);
    });
    
    // Update map markers
    this.renderMapMarkers();
  }
  
  // Render map markers
  renderMapMarkers() {
    if (!this.state.map) return;
    
    // Clear existing markers
    this.state.markers.forEach(marker => {
      this.state.map.removeLayer(marker);
    });
    this.state.markers.clear();
    
    // Add filtered markers
    let filteredArtisans = this.state.artisans;
    
    if (this.state.filters.search) {
      const searchTerm = this.state.filters.search.toLowerCase();
      filteredArtisans = filteredArtisans.filter(artisan => 
        artisan.name.toLowerCase().includes(searchTerm) ||
        artisan.job.toLowerCase().includes(searchTerm)
      );
    }
    
    if (this.state.filters.job) {
      const jobTerm = this.state.filters.job.toLowerCase();
      filteredArtisans = filteredArtisans.filter(artisan => 
        artisan.job.toLowerCase().includes(jobTerm)
      );
    }
    
    if (this.state.filters.distance > 0 && this.state.currentLocation) {
      filteredArtisans = filteredArtisans.filter(artisan => 
        artisan.lat && artisan.lng && 
        this.calculateDistance(
          this.state.currentLocation.lat,
          this.state.currentLocation.lng,
          artisan.lat,
          artisan.lng
        ) <= this.state.filters.distance
      );
    }
    
    filteredArtisans.forEach(artisan => {
      if (artisan.lat && artisan.lng) {
        const marker = L.marker([artisan.lat, artisan.lng]).addTo(this.state.map);
        marker.bindPopup(`
          <div style="min-width: 200px;">
            <h3 style="font-weight: 700; margin: 0 0 8px 0;">${this.escapeHtml(artisan.name)}</h3>
            <p style="margin: 0 0 12px 0; color: #64748b;">${this.escapeHtml(artisan.job)}</p>
            <button onclick="app.showArtisanProfile('${artisan.id}')" 
                    style="background: #0f9d58; color: white; border: none; padding: 8px 16px; border-radius: 6px; cursor: pointer; width: 100%;">
              عرض التفاصيل
            </button>
          </div>
        `);
        this.state.markers.set(artisan.id, marker);
      }
    });
  }
  
  // Apply filters
  applyFilters() {
    this.state.filters.search = document.getElementById('searchInput').value.trim();
    this.state.filters.job = document.getElementById('jobFilter').value.trim();
    this.state.filters.distance = parseInt(document.getElementById('distanceFilter').value) || 0;
    this.renderArtisansList();
  }
  
  // Clear filters
  clearFilters() {
    document.getElementById('searchInput').value = '';
    document.getElementById('jobFilter').value = '';
    document.getElementById('distanceFilter').value = '0';
    this.state.filters = { search: '', job: '', distance: 0 };
    this.renderArtisansList();
  }
  
  // Locate user
  locateUser() {
    if (!navigator.geolocation) {
      this.showToast('المتصفح لا يدعم تحديد الموقع');
      return;
    }
    
    this.showLoading();
    
    navigator.geolocation.getCurrentPosition(
      (position) => {
        this.state.currentLocation = {
          lat: position.coords.latitude,
          lng: position.coords.longitude
        };
        
        // Remove existing location marker if any
        if (this.state.locationMarker) {
          this.state.map.removeLayer(this.state.locationMarker);
        }
        
        // Add location marker
        this.state.locationMarker = L.circleMarker(
          [this.state.currentLocation.lat, this.state.currentLocation.lng],
          {
            radius: 12,
            fillColor: '#0f9d58',
            color: '#0a7a44',
            weight: 2,
            opacity: 1,
            fillOpacity: 0.8
          }
        ).addTo(this.state.map);
        
        this.state.map.setView([this.state.currentLocation.lat, this.state.currentLocation.lng], 14);
        this.renderArtisansList();
        this.hideLoading();
        this.showToast('تم تحديد موقعك بنجاح');
      },
      (error) => {
        this.hideLoading();
        let message = 'تعذر تحديد موقعك';
        if (error.code === 1) {
          message = 'يرجى السماح بالوصول إلى موقعك';
        }
        this.showToast(message);
      }
    );
  }
  
  // Refresh map
  refreshMap() {
    this.renderMapMarkers();
    this.showToast('تم تحديث الخريطة');
  }
  
  // Show artisan profile
  showArtisanProfile(artisanId) {
    const artisan = this.state.artisans.find(a => a.id === artisanId);
    if (!artisan) {
      this.showToast('الحرفي غير موجود');
      return;
    }
    
    const modalHTML = `
      <div class="modal-overlay" id="profileModal">
        <div class="modal">
          <div class="modal-header">
            <h3 class="modal-title">${this.escapeHtml(artisan.name)}</h3>
            <button class="modal-close" onclick="app.closeModal('profileModal')">&times;</button>
          </div>
          <div class="modal-body">
            <div style="display: grid; grid-template-columns: 1fr 300px; gap: 24px;">
              <div>
                <div style="display: flex; justify-content: space-between; align-items-start; margin-bottom: 20px;">
                  <div>
                    <p style="color: var(--gray-600); margin: 4px 0;">${this.escapeHtml(artisan.job)}</p>
                    <p style="font-weight: 600; color: var(--primary); margin: 4px 0;">${artisan.price || 'غير محدد'}</p>
                    ${this.state.currentLocation && artisan.lat && artisan.lng ? 
                      `<p style="color: var(--gray-600); margin: 4px 0;">
                        ${this.calculateDistance(this.state.currentLocation.lat, this.state.currentLocation.lng, artisan.lat, artisan.lng).toFixed(1)} كم من موقعك
                      </p>` : ''
                    }
                  </div>
                  <div style="text-align: left;">
                    <p style="font-weight: 600; color: var(--gray-700); margin: 0;">
                      ${artisan.phone || 'غير متوفر'}
                    </p>
                  </div>
                </div>
                
                <p style="line-height: 1.6; margin-bottom: 24px;">${this.escapeHtml(artisan.description || 'لا يوجد وصف')}</p>
                
                <div style="display: flex; gap: 12px; flex-wrap: wrap;">
                  <button class="btn btn-primary" onclick="app.bookArtisan('${artisan.id}')">
                    <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                      <rect x="3" y="4" width="18" height="18" rx="2" ry="2"></rect>
                      <line x1="16" y1="2" x2="16" y2="6"></line>
                      <line x1="8" y1="2" x2="8" y2="6"></line>
                      <line x1="3" y1="10" x2="21" y2="10"></line>
                    </svg>
                    حجز موعد
                  </button>
                  <button class="btn btn-outline" onclick="app.chatWithArtisan('${artisan.id}')">
                    <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                      <path d="M21 15a2 2 0 0 1-2 2H7l-4 4V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2z"></path>
                    </svg>
                    دردشة
                  </button>
                  <button class="btn btn-outline" onclick="app.rateArtisan('${artisan.id}')">
                    <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                      <polygon points="12 2 15.09 8.26 22 9.27 17 14.14 18.18 21.02 12 17.77 5.82 21.02 7 14.14 2 9.27 8.91 8.26 12 2"></polygon>
                    </svg>
                    تقييم
                  </button>
                  ${this.state.user ? `
                    <button class="btn btn-outline" onclick="app.editArtisan('${artisan.id}')">
                      <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                        <path d="M11 4H4a2 2 0 0 0-2 2v14a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2v-7"></path>
                        <path d="M18.5 2.5a2.121 2.121 0 0 1 3 3L12 15l-4 1 1-4 9.5-9.5z"></path>
                      </svg>
                      تعديل
                    </button>
                    <button class="btn btn-danger" onclick="app.deleteArtisan('${artisan.id}')">
                      <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                        <polyline points="3 6 5 6 21 6"></polyline>
                        <path d="M19 6v14a2 2 0 0 1-2 2H7a2 2 0 0 1-2-2V6m3 0V4a2 2 0 0 1 2-2h4a2 2 0 0 1 2 2v2"></path>
                      </svg>
                      حذف
                    </button>
                  ` : ''}
                </div>
              </div>
              
              <div>
                <h4 style="font-weight: 700; margin-bottom: 16px;">التقييمات (${artisan.ratings.length})</h4>
                ${artisan.ratings.length > 0 ? 
                  artisan.ratings.map(rating => `
                    <div style="padding: 12px; border-bottom: 1px solid var(--gray-200); margin-bottom: 12px;">
                      <div style="display: flex; justify-content: space-between; margin-bottom: 8px;">
                        <strong>${this.escapeHtml(rating.user)}</strong>
                        <div style="color: var(--warning); font-weight: 600;">
                          ${'★'.repeat(rating.stars)}${'☆'.repeat(5 - rating.stars)}
                        </div>
                      </div>
                      <p style="color: var(--gray-700); font-size: 14px;">${this.escapeHtml(rating.text)}</p>
                      <p style="color: var(--gray-500); font-size: 12px; margin-top: 8px;">
                        ${new Date(rating.date).toLocaleDateString('ar-MA')}
                      </p>
                    </div>
                  `).join('') : 
                  '<p style="color: var(--gray-500);">لا توجد تقييمات بعد</p>'
                }
              </div>
            </div>
          </div>
        </div>
      </div>
    `;
    
    document.body.insertAdjacentHTML('beforeend', modalHTML);
    document.getElementById('profileModal').classList.add('active');
  }
  
  // Show authentication modal
  showAuthModal() {
    const modalHTML = `
      <div class="modal-overlay" id="authModal">
        <div class="modal">
          <div class="modal-header">
            <h3 class="modal-title">تسجيل الدخول</h3>
            <button class="modal-close" onclick="app.closeModal('authModal')">&times;</button>
          </div>
          <div class="modal-body">
            <div style="display: flex; gap: 20px; margin-bottom: 24px;">
              <button class="btn btn-outline" style="flex: 1;" onclick="app.switchAuthTab('login')">
                تسجيل الدخول
              </button>
              <button class="btn btn-outline" style="flex: 1;" onclick="app.switchAuthTab('register')">
                إنشاء حساب
              </button>
            </div>
            
            <div id="loginTab">
              <div class="form-group">
                <label class="form-label">البريد الإلكتروني</label>
                <input type="email" id="loginEmail" class="form-control" placeholder="example@email.com">
              </div>
              <div class="form-group">
                <label class="form-label">كلمة المرور</label>
                <input type="password" id="loginPassword" class="form-control" placeholder="••••••••">
              </div>
              <div class="form-actions">
                <button class="btn btn-primary" onclick="app.handleLogin()">تسجيل الدخول</button>
              </div>
            </div>
            
            <div id="registerTab" style="display: none;">
              <div class="form-group">
                <label class="form-label">الاسم الكامل</label>
                <input type="text" id="registerName" class="form-control" placeholder="أحمد محمد">
              </div>
              <div class="form-group">
                <label class="form-label">البريد الإلكتروني</label>
                <input type="email" id="registerEmail" class="form-control" placeholder="example@email.com">
              </div>
              <div class="form-group">
                <label class="form-label">كلمة المرور</label>
                <input type="password" id="registerPassword" class="form-control" placeholder="••••••••">
              </div>
              <div class="form-actions">
                <button class="btn btn-primary" onclick="app.handleRegister()">إنشاء حساب</button>
              </div>
            </div>
          </div>
        </div>
      </div>
    `;
    
    document.body.insertAdjacentHTML('beforeend', modalHTML);
    document.getElementById('authModal').classList.add('active');
  }
  
  // Switch authentication tab
  switchAuthTab(tab) {
    document.getElementById('loginTab').style.display = tab === 'login' ? 'block' : 'none';
    document.getElementById('registerTab').style.display = tab === 'register' ? 'block' : 'none';
    document.querySelector('.modal-title').textContent = tab === 'login' ? 'تسجيل الدخول' : 'إنشاء حساب';
  }
  
  // Handle login
  handleLogin() {
    const email = document.getElementById('loginEmail').value.trim();
    const password = document.getElementById('loginPassword').value;
    
    if (!email || !password) {
      this.showToast('يرجى ملء جميع الحقول');
      return;
    }
    
    // In a real app, this would be an API call
    const savedUser = JSON.parse(localStorage.getItem(this.storageKeys.USER));
    if (savedUser && savedUser.email === email && savedUser.password === password) {
      this.state.user = savedUser;
      this.saveState();
      this.updateAuthUI();
      this.closeModal('authModal');
      this.showToast('تم تسجيل الدخول بنجاح');
    } else {
      this.showToast('البريد الإلكتروني أو كلمة المرور غير صحيحة');
    }
  }
  
  // Handle register
  handleRegister() {
    const name = document.getElementById('registerName').value.trim();
    const email = document.getElementById('registerEmail').value.trim();
    const password = document.getElementById('registerPassword').value;
    
    if (!name || !email || !password) {
      this.showToast('يرجى ملء جميع الحقول');
      return;
    }
    
    if (password.length < 6) {
      this.showToast('كلمة المرور يجب أن تكون 6 أحرف على الأقل');
      return;
    }
    
    // Check if email already exists
    const existingUser = JSON.parse(localStorage.getItem(this.storageKeys.USER));
    if (existingUser && existingUser.email === email) {
      this.showToast('هذا البريد الإلكتروني مستخدم بالفعل');
      return;
    }
    
    this.state.user = { name, email, password };
    this.saveState();
    this.updateAuthUI();
    this.closeModal('authModal');
    this.showToast('تم إنشاء الحساب بنجاح');
  }
  
  // Show add artisan modal
  showAddArtisanModal() {
    if (!this.state.user) {
      this.showToast('يرجى تسجيل الدخول أولاً');
      this.showAuthModal();
      return;
    }
    
    const modalHTML = `
      <div class="modal-overlay" id="addArtisanModal">
        <div class="modal">
          <div class="modal-header">
            <h3 class="modal-title">إضافة حرفي جديد</h3>
            <button class="modal-close" onclick="app.closeModal('addArtisanModal')">&times;</button>
          </div>
          <div class="modal-body">
            <div class="form-row">
              <div class="form-group">
                <label class="form-label">الاسم الكامل</label>
                <input type="text" id="artisanName" class="form-control" placeholder="أحمد الحداد" required>
              </div>
              <div class="form-group">
                <label class="form-label">المهنة</label>
                <input type="text" id="artisanJob" class="form-control" placeholder="حداد" required>
              </div>
            </div>
            <div class="form-row">
              <div class="form-group">
                <label class="form-label">رقم الهاتف</label>
                <input type="tel" id="artisanPhone" class="form-control" placeholder="0612345678">
              </div>
              <div class="form-group">
                <label class="form-label">التسعير</label>
                <input type="text" id="artisanPrice" class="form-control" placeholder="من 300 درهم">
              </div>
            </div>
            <div class="form-group">
              <label class="form-label">الوصف</label>
              <textarea id="artisanDescription" class="form-control" rows="3" placeholder="وصف مفصل عن الخدمات المقدمة"></textarea>
            </div>
            <div class="form-row">
              <div class="form-group">
                <label class="form-label">خط العرض</label>
                <input type="number" id="artisanLat" class="form-control" placeholder="33.5883" step="0.0001">
              </div>
              <div class="form-group">
                <label class="form-label">خط الطول</label>
                <input type="number" id="artisanLng" class="form-control" placeholder="-7.6114" step="0.0001">
              </div>
            </div>
            <div class="form-actions">
              <button class="btn btn-outline" onclick="app.closeModal('addArtisanModal')">إلغاء</button>
              <button class="btn btn-primary" onclick="app.handleAddArtisan()">إضافة</button>
            </div>
          </div>
        </div>
      </div>
    `;
    
    document.body.insertAdjacentHTML('beforeend', modalHTML);
    document.getElementById('addArtisanModal').classList.add('active');
  }
  
  // Handle add artisan
  handleAddArtisan() {
    const name = document.getElementById('artisanName').value.trim();
    const job = document.getElementById('artisanJob').value.trim();
    const phone = document.getElementById('artisanPhone').value.trim();
    const price = document.getElementById('artisanPrice').value.trim();
    const description = document.getElementById('artisanDescription').value.trim();
    const lat = parseFloat(document.getElementById('artisanLat').value) || null;
    const lng = parseFloat(document.getElementById('artisanLng').value) || null;
    
    if (!name || !job) {
      this.showToast('يرجى ملء الحقول المطلوبة');
      return;
    }
    
    const newArtisan = {
      id: this.generateId(),
      name,
      job,
      phone,
      price,
      description,
      photos: [],
      lat,
      lng,
      ratings: [],
      messages: []
    };
    
    this.state.artisans.unshift(newArtisan);
    this.saveState();
    this.renderArtisansList();
    this.closeModal('addArtisanModal');
    this.showToast('تمت إضافة الحرفي بنجاح');
  }
  
  // Book artisan
  bookArtisan(artisanId) {
    if (!this.state.user) {
      this.showToast('يرجى تسجيل الدخول أولاً');
      this.showAuthModal();
      return;
    }
    
    const artisan = this.state.artisans.find(a => a.id === artisanId);
    if (!artisan) return;
    
    const modalHTML = `
      <div class="modal-overlay" id="bookingModal">
        <div class="modal">
          <div class="modal-header">
            <h3 class="modal-title">حجز موعد مع ${this.escapeHtml(artisan.name)}</h3>
            <button class="modal-close" onclick="app.closeModal('bookingModal')">&times;</button>
          </div>
          <div class="modal-body">
            <div class="form-group">
              <label class="form-label">التاريخ والوقت</label>
              <input type="datetime-local" id="bookingDateTime" class="form-control">
            </div>
            <div class="form-group">
              <label class="form-label">ملاحظات إضافية</label>
              <textarea id="bookingNotes" class="form-control" rows="3" placeholder="أي ملاحظات تريد إضافتها..."></textarea>
            </div>
            <div class="form-actions">
              <button class="btn btn-outline" onclick="app.closeModal('bookingModal')">إلغاء</button>
              <button class="btn btn-primary" onclick="app.handleBooking('${artisanId}')">تأكيد الحجز</button>
            </div>
          </div>
        </div>
      </div>
    `;
    
    document.body.insertAdjacentHTML('beforeend', modalHTML);
    document.getElementById('bookingModal').classList.add('active');
    
    // Set min date to today
    const now = new Date();
    const year = now.getFullYear();
    const month = String(now.getMonth() + 1).padStart(2, '0');
    const day = String(now.getDate()).padStart(2, '0');
    const hours = String(now.getHours()).padStart(2, '0');
    const minutes = String(now.getMinutes()).padStart(2, '0');
    document.getElementById('bookingDateTime').min = `${year}-${month}-${day}T${hours}:${minutes}`;
  }
  
  // Handle booking
  handleBooking(artisanId) {
    const dateTime = document.getElementById('bookingDateTime').value;
    const notes = document.getElementById('bookingNotes').value.trim();
    
    if (!dateTime) {
      this.showToast('يرجى اختيار تاريخ ووقت الحجز');
      return;
    }
    
    const newBooking = {
      id: this.generateId(),
      artisanId,
      userEmail: this.state.user.email,
      dateTime,
      notes,
      status: 'pending',
      createdAt: new Date().toISOString()
    };
    
    this.state.bookings.push(newBooking);
    this.saveState();
    this.closeModal('bookingModal');
    this.addNotification(`تم حجز موعد مع ${this.state.artisans.find(a => a.id === artisanId)?.name} في ${new Date(dateTime).toLocaleDateString('ar-MA')}`);
    this.showToast('تم تأكيد الحجز بنجاح');
  }
  
  // Show bookings modal
  showBookingsModal() {
    if (!this.state.user) {
      this.showToast('يرجى تسجيل الدخول أولاً');
      this.showAuthModal();
      return;
    }
    
    const userBookings = this.state.bookings
      .filter(b => b.userEmail === this.state.user.email)
      .sort((a, b) => new Date(b.dateTime) - new Date(a.dateTime));
    
    const modalHTML = `
      <div class="modal-overlay" id="bookingsModal">
        <div class="modal">
          <div class="modal-header">
            <h3 class="modal-title">حجوزاتي (${userBookings.length})</h3>
            <button class="modal-close" onclick="app.closeModal('bookingsModal')">&times;</button>
          </div>
          <div class="modal-body">
            ${userBookings.length > 0 ? 
              userBookings.map(booking => {
                const artisan = this.state.artisans.find(a => a.id === booking.artisanId);
                return `
                  <div style="padding: 16px; border: 1px solid var(--gray-200); border-radius: var(--radius-lg); margin-bottom: 16px;">
                    <div style="display: flex; justify-content: space-between; align-items-start; margin-bottom: 12px;">
                      <div>
                        <h4 style="font-weight: 700; margin: 0;">${artisan ? this.escapeHtml(artisan.name) : 'حرفي غير معروف'}</h4>
                        <p style="color: var(--gray-600); margin: 4px 0;">${artisan ? this.escapeHtml(artisan.job) : ''}</p>
                      </div>
                      <div style="text-align: left;">
                        <p style="font-weight: 600; color: var(--primary); margin: 0;">
                          ${new Date(booking.dateTime).toLocaleDateString('ar-MA')}
                        </p>
                        <p style="color: var(--gray-600); margin: 4px 0;">
                          ${new Date(booking.dateTime).toLocaleTimeString('ar-MA', { hour: '2-digit', minute: '2-digit' })}
                        </p>
                      </div>
                    </div>
                    ${booking.notes ? `
                      <div style="margin-top: 12px; padding-top: 12px; border-top: 1px solid var(--gray-200);">
                        <p style="color: var(--gray-700);"><strong>ملاحظات:</strong> ${this.escapeHtml(booking.notes)}</p>
                      </div>
                    ` : ''}
                    <div style="display: flex; justify-content: flex-end; margin-top: 16px;">
                      <button class="btn btn-outline" onclick="app.cancelBooking('${booking.id}')">
                        إلغاء الحجز
                      </button>
                    </div>
                  </div>
                `;
              }).join('') : 
              `
                <div style="text-align: center; padding: 40px 20px; color: var(--gray-500);">
                  <svg width="48" height="48" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" style="margin: 0 auto 16px;">
                    <rect x="3" y="4" width="18" height="18" rx="2" ry="2"></rect>
                    <line x1="16" y1="2" x2="16" y2="6"></line>
                    <line x1="8" y1="2" x2="8" y2="6"></line>
                    <line x1="3" y1="10" x2="21" y2="10"></line>
                  </svg>
                  <p>لا توجد حجوزات حالياً</p>
                </div>
              `
            }
          </div>
        </div>
      </div>
    `;
    
    document.body.insertAdjacentHTML('beforeend', modalHTML);
    document.getElementById('bookingsModal').classList.add('active');
  }
  
  // Cancel booking
  cancelBooking(bookingId) {
    if (!confirm('هل أنت متأكد من إلغاء هذا الحجز؟')) return;
    
    this.state.bookings = this.state.bookings.filter(b => b.id !== bookingId);
    this.saveState();
    this.closeModal('bookingsModal');
    this.addNotification('تم إلغاء الحجز بنجاح');
    this.showToast('تم إلغاء الحجز');
    this.showBookingsModal(); // Refresh
  }
  
  // Chat with artisan
  chatWithArtisan(artisanId) {
    if (!this.state.user) {
      this.showToast('يرجى تسجيل الدخول أولاً');
      this.showAuthModal();
      return;
    }
    
    const artisan = this.state.artisans.find(a => a.id === artisanId);
    if (!artisan) return;
    
    const modalHTML = `
      <div class="modal-overlay" id="chatModal">
        <div class="modal">
          <div class="modal-header">
            <h3 class="modal-title">الدردشة مع ${this.escapeHtml(artisan.name)}</h3>
            <button class="modal-close" onclick="app.closeModal('chatModal')">&times;</button>
          </div>
          <div class="modal-body">
            <div style="height: 400px; display: flex; flex-direction: column;">
              <div id="chatMessages" style="flex: 1; overflow-y: auto; padding: 16px; background: var(--gray-100); border-radius: var(--radius-lg); margin-bottom: 16px;">
                ${artisan.messages && artisan.messages.length > 0 ? 
                  artisan.messages.map(msg => `
                    <div style="display: flex; ${msg.from === 'me' ? 'justify-content: flex-end;' : 'justify-content: flex-start;'} margin-bottom: 12px;">
                      <div style="max-width: 70%; padding: 12px 16px; border-radius: 18px; ${msg.from === 'me' ? 'background: var(--primary); color: white;' : 'background: white; border: 1px solid var(--gray-200);'}">
                        ${this.escapeHtml(msg.text)}
                      </div>
                    </div>
                  `).join('') : 
                  '<div style="text-align: center; color: var(--gray-500); padding: 20px;">ابدأ المحادثة الأولى!</div>'
                }
              </div>
              <div style="display: flex; gap: 12px;">
                <input type="text" id="chatMessage" class="form-control" placeholder="اكتب رسالتك..." style="flex: 1;">
                <button class="btn btn-primary" onclick="app.sendMessage('${artisanId}')">إرسال</button>
              </div>
            </div>
          </div>
        </div>
      </div>
    `;
    
    document.body.insertAdjacentHTML('beforeend', modalHTML);
    document.getElementById('chatModal').classList.add('active');
    
    // Focus on message input
    setTimeout(() => {
      const input = document.getElementById('chatMessage');
      if (input) input.focus();
    }, 300);
    
    // Scroll to bottom
    const messagesDiv = document.getElementById('chatMessages');
    if (messagesDiv) messagesDiv.scrollTop = messagesDiv.scrollHeight;
  }
  
  // Send message
  sendMessage(artisanId) {
    const messageInput = document.getElementById('chatMessage');
    const message = messageInput.value.trim();
    
    if (!message) return;
    
    const artisan = this.state.artisans.find(a => a.id === artisanId);
    if (!artisan) return;
    
    artisan.messages = artisan.messages || [];
    artisan.messages.push({
      from: 'me',
      text: message,
      timestamp: new Date().toISOString()
    });
    
    this.saveState();
    messageInput.value = '';
    
    // Simulate reply after 1 second
    setTimeout(() => {
      artisan.messages.push({
        from: 'artisan',
        text: 'شكراً على رسالتك! سأرد عليك في أقرب وقت ممكن.',
        timestamp: new Date().toISOString()
      });
      this.saveState();
      
      // Update chat if still open
      const messagesDiv = document.getElementById('chatMessages');
      if (messagesDiv) {
        messagesDiv.innerHTML = artisan.messages.map(msg => `
          <div style="display: flex; ${msg.from === 'me' ? 'justify-content: flex-end;' : 'justify-content: flex-start;'} margin-bottom: 12px;">
            <div style="max-width: 70%; padding: 12px 16px; border-radius: 18px; ${msg.from === 'me' ? 'background: var(--primary); color: white;' : 'background: white; border: 1px solid var(--gray-200);'}">
              ${this.escapeHtml(msg.text)}
            </div>
          </div>
        `).join('');
        messagesDiv.scrollTop = messagesDiv.scrollHeight;
      }
    }, 1000);
    
    // Update chat display
    const messagesDiv = document.getElementById('chatMessages');
    if (messagesDiv) {
      messagesDiv.innerHTML = artisan.messages.map(msg => `
        <div style="display: flex; ${msg.from === 'me' ? 'justify-content: flex-end;' : 'justify-content: flex-start;'} margin-bottom: 12px;">
          <div style="max-width: 70%; padding: 12px 16px; border-radius: 18px; ${msg.from === 'me' ? 'background: var(--primary); color: white;' : 'background: white; border: 1px solid var(--gray-200);'}">
            ${this.escapeHtml(msg.text)}
          </div>
        </div>
      `).join('');
      messagesDiv.scrollTop = messagesDiv.scrollHeight;
    }
  }
  
  // Rate artisan
  rateArtisan(artisanId) {
    if (!this.state.user) {
      this.showToast('يرجى تسجيل الدخول أولاً');
      this.showAuthModal();
      return;
    }
    
    const modalHTML = `
      <div class="modal-overlay" id="ratingModal">
        <div class="modal">
          <div class="modal-header">
            <h3 class="modal-title">تقييم الحرفي</h3>
            <button class="modal-close" onclick="app.closeModal('ratingModal')">&times;</button>
          </div>
          <div class="modal-body">
            <div class="form-group">
              <label class="form-label">عدد النجوم</label>
              <select id="ratingStars" class="form-control">
                <option value="5">★★★★★ (5)</option>
                <option value="4">★★★★☆ (4)</option>
                <option value="3">★★★☆☆ (3)</option>
                <option value="2">★★☆☆☆ (2)</option>
                <option value="1">★☆☆☆☆ (1)</option>
              </select>
            </div>
            <div class="form-group">
              <label class="form-label">التعليق</label>
              <textarea id="ratingComment" class="form-control" rows="3" placeholder="شارك تجربتك مع هذا الحرفي..."></textarea>
            </div>
            <div class="form-actions">
              <button class="btn btn-outline" onclick="app.closeModal('ratingModal')">إلغاء</button>
              <button class="btn btn-primary" onclick="app.handleRating('${artisanId}')">إرسال التقييم</button>
            </div>
          </div>
        </div>
      </div>
    `;
    
    document.body.insertAdjacentHTML('beforeend', modalHTML);
    document.getElementById('ratingModal').classList.add('active');
  }
  
  // Handle rating
  handleRating(artisanId) {
    const stars = parseInt(document.getElementById('ratingStars').value);
    const comment = document.getElementById('ratingComment').value.trim();
    
    const artisan = this.state.artisans.find(a => a.id === artisanId);
    if (!artisan) return;
    
    artisan.ratings = artisan.ratings || [];
    artisan.ratings.push({
      user: this.state.user.email,
      stars,
      text: comment || 'لا يوجد تعليق',
      date: new Date().toISOString()
    });
    
    this.saveState();
    this.closeModal('ratingModal');
    this.showToast('شكراً على تقييمك!');
    this.showArtisanProfile(artisanId); // Refresh profile
  }
  
  // Edit artisan
  editArtisan(artisanId) {
    const artisan = this.state.artisans.find(a => a.id === artisanId);
    if (!artisan) return;
    
    const modalHTML = `
      <div class="modal-overlay" id="editArtisanModal">
        <div class="modal">
          <div class="modal-header">
            <h3 class="modal-title">تعديل الحرفي</h3>
            <button class="modal-close" onclick="app.closeModal('editArtisanModal')">&times;</button>
          </div>
          <div class="modal-body">
            <div class="form-row">
              <div class="form-group">
                <label class="form-label">الاسم الكامل</label>
                <input type="text" id="editArtisanName" class="form-control" value="${this.escapeHtml(artisan.name)}" required>
              </div>
              <div class="form-group">
                <label class="form-label">المهنة</label>
                <input type="text" id="editArtisanJob" class="form-control" value="${this.escapeHtml(artisan.job)}" required>
              </div>
            </div>
            <div class="form-row">
              <div class="form-group">
                <label class="form-label">رقم الهاتف</label>
                <input type="tel" id="editArtisanPhone" class="form-control" value="${this.escapeHtml(artisan.phone || '')}">
              </div>
              <div class="form-group">
                <label class="form-label">التسعير</label>
                <input type="text" id="editArtisanPrice" class="form-control" value="${this.escapeHtml(artisan.price || '')}">
              </div>
            </div>
            <div class="form-group">
              <label class="form-label">الوصف</label>
              <textarea id="editArtisanDescription" class="form-control" rows="3">${this.escapeHtml(artisan.description || '')}</textarea>
            </div>
            <div class="form-row">
              <div class="form-group">
                <label class="form-label">خط العرض</label>
                <input type="number" id="editArtisanLat" class="form-control" value="${artisan.lat || ''}" step="0.0001">
              </div>
              <div class="form-group">
                <label class="form-label">خط الطول</label>
                <input type="number" id="editArtisanLng" class="form-control" value="${artisan.lng || ''}" step="0.0001">
              </div>
            </div>
            <div class="form-actions">
              <button class="btn btn-outline" onclick="app.closeModal('editArtisanModal')">إلغاء</button>
              <button class="btn btn-primary" onclick="app.handleEditArtisan('${artisanId}')">حفظ التغييرات</button>
            </div>
          </div>
        </div>
      </div>
    `;
    
    document.body.insertAdjacentHTML('beforeend', modalHTML);
    document.getElementById('editArtisanModal').classList.add('active');
  }
  
  // Handle edit artisan
  handleEditArtisan(artisanId) {
    const name = document.getElementById('editArtisanName').value.trim();
    const job = document.getElementById('editArtisanJob').value.trim();
    const phone = document.getElementById('editArtisanPhone').value.trim();
    const price = document.getElementById('editArtisanPrice').value.trim();
    const description = document.getElementById('editArtisanDescription').value.trim();
    const lat = parseFloat(document.getElementById('editArtisanLat').value) || null;
    const lng = parseFloat(document.getElementById('editArtisanLng').value) || null;
    
    if (!name || !job) {
      this.showToast('يرجى ملء الحقول المطلوبة');
      return;
    }
    
    const artisanIndex = this.state.artisans.findIndex(a => a.id === artisanId);
    if (artisanIndex === -1) return;
    
    this.state.artisans[artisanIndex] = {
      ...this.state.artisans[artisanIndex],
      name,
      job,
      phone,
      price,
      description,
      lat,
      lng
    };
    
    this.saveState();
    this.renderArtisansList();
    this.closeModal('editArtisanModal');
    this.showToast('تم تحديث معلومات الحرفي بنجاح');
  }
  
  // Delete artisan
  deleteArtisan(artisanId) {
    if (!confirm('هل أنت متأكد من حذف هذا الحرفي؟ لن تتمكن من استعادته.')) return;
    
    this.state.artisans = this.state.artisans.filter(a => a.id !== artisanId);
    this.saveState();
    this.renderArtisansList();
    this.closeModal('profileModal');
    this.showToast('تم حذف الحرفي بنجاح');
  }
  
  // Show notifications modal
  showNotificationsModal() {
    const modalHTML = `
      <div class="modal-overlay" id="notificationsModal">
        <div class="modal">
          <div class="modal-header">
            <h3 class="modal-title">الإشعارات (${this.state.notifications.length})</h3>
            <button class="modal-close" onclick="app.closeModal('notificationsModal')">&times;</button>
          </div>
          <div class="modal-body">
            ${this.state.notifications.length > 0 ? 
              this.state.notifications.map(notification => `
                <div style="padding: 16px; border-bottom: 1px solid var(--gray-200); margin-bottom: 16px;">
                  <p style="margin: 0 0 8px 0;">${this.escapeHtml(notification.text)}</p>
                  <p style="color: var(--gray-500); font-size: 13px;">
                    ${new Date(notification.timestamp).toLocaleDateString('ar-MA')} 
                    ${new Date(notification.timestamp).toLocaleTimeString('ar-MA', { hour: '2-digit', minute: '2-digit' })}
                  </p>
                </div>
              `).join('') : 
              `
                <div style="text-align: center; padding: 40px 20px; color: var(--gray-500);">
                  <svg width="48" height="48" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" style="margin: 0 auto 16px;">
                    <path d="M18 8A6 6 0 0 0 6 8c0 7-3 9-3 9h18s-3-2-3-9"></path>
                    <path d="M13.73 21a2 2 0 0 1-3.46 0"></path>
                  </svg>
                  <p>لا توجد إشعارات حالياً</p>
                </div>
              `
            }
          </div>
        </div>
      </div>
    `;
    
    document.body.insertAdjacentHTML('beforeend', modalHTML);
    document.getElementById('notificationsModal').classList.add('active');
    
    // Mark all as read
    this.state.notifications.forEach(n => n.read = true);
    this.saveState();
    this.updateNotificationBadge();
  }
  
  // Add notification
  addNotification(text) {
    this.state.notifications.unshift({
      id: this.generateId(),
      text,
      timestamp: new Date().toISOString(),
      read: false
    });
    this.saveState();
    this.updateNotificationBadge();
  }
  
  // Update notification badge
  updateNotificationBadge() {
    const unreadCount = this.state.notifications.filter(n => !n.read).length;
    const badge = document.getElementById('notificationBadge');
    
    if (unreadCount > 0) {
      badge.textContent = unreadCount > 99 ? '99+' : unreadCount;
      badge.classList.add('show');
    } else {
      badge.classList.remove('show');
    }
  }
  
  // Close modal
  closeModal(modalId) {
    const modal = document.getElementById(modalId);
    if (modal) {
      modal.classList.remove('active');
      setTimeout(() => {
        if (modal.parentNode) {
          modal.parentNode.removeChild(modal);
        }
      }, 300);
    }
  }
  
  // Close all modals
  closeAllModals() {
    const modals = document.querySelectorAll('.modal-overlay');
    modals.forEach(modal => {
      modal.classList.remove('active');
      setTimeout(() => {
        if (modal.parentNode) {
          modal.parentNode.removeChild(modal);
        }
      }, 300);
    });
  }
  
  // Show toast notification
  showToast(message, duration = 3000) {
    const toast = document.getElementById('toast');
    toast.textContent = message;
    toast.classList.add('show');
    
    setTimeout(() => {
      toast.classList.remove('show');
    }, duration);
  }
  
  // Utility functions
  generateId() {
    return 'id_' + Math.random().toString(36).substr(2, 9);
  }
  
  getUserInitials(name) {
    return name.split(' ').slice(0, 2).map(n => n[0] || '').join('').toUpperCase() || 'أ';
  }
  
  escapeHtml(text) {
    if (!text) return '';
    const map = {
      '&': '&amp;',
      '<': '<',
      '>': '>',
      '"': '&quot;',
      "'": '&#039;'
    };
    return text.replace(/[&<>"']/g, m => map[m]);
  }
  
  calculateDistance(lat1, lon1, lat2, lon2) {
    const R = 6371; // Radius of the earth in km
    const dLat = this.deg2rad(lat2 - lat1);
    const dLon = this.deg2rad(lon2 - lon1);
    const a = 
      Math.sin(dLat / 2) * Math.sin(dLat / 2) +
      Math.cos(this.deg2rad(lat1)) * Math.cos(this.deg2rad(lat2)) * 
      Math.sin(dLon / 2) * Math.sin(dLon / 2);
    const c = 2 * Math.atan2(Math.sqrt(a), Math.sqrt(1 - a));
    return R * c;
  }
  
  deg2rad(deg) {
    return deg * (Math.PI / 180);
  }
}

// Initialize the app when the DOM is loaded
document.addEventListener('DOMContentLoaded', () => {
  window.app = new ArtisanApp();
});

// Handle window resize for map
window.addEventListener('resize', () => {
  if (window.app && window.app.state.map) {
    window.app.state.map.invalidateSize();
  }
});
</script>

</body>
</html>
