<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>الحريفية المغربية</title>
  <link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@400;500;700&display=swap" rel="stylesheet">
  <link rel="stylesheet" href=" https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css " />
  <style>
    :root {
      --bg: #e8f5e9;
      --primary: #2e7d32;
      --secondary: #1b5e20;
      --accent: #d4af37;
      --text: #263238;
      --text-light: #546e7a;
      --card-bg: white;
      --shadow: 0 4px 20px rgba(0, 0, 0, 0.12);
    }

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Tajawal', sans-serif;
      background-color: var(--bg);
      background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='100' height='100' viewBox='0 0 100 100'%3E%3Crect width='100' height='100' fill='%23e8f5e9'/%3E%3Cpath d='M0 0L20 0L0 20Z' fill='%23c8e6c9' opacity='0.05'/%3E%3Cpath d='M100 100L80 100L100 80Z' fill='%23c8e6c9' opacity='0.05'/%3E%3C/svg%3E");
      color: var(--text);
      line-height: 1.6;
    }

    .header {
      background: linear-gradient(135deg, var(--primary), #0d4d1a);
      color: white;
      text-align: center;
      padding: 2rem 1rem;
      box-shadow: var(--shadow);
    }

    .header h1 {
      font-size: 2.4rem;
      margin-bottom: 0.5rem;
      text-shadow: 0 2px 4px rgba(0,0,0,0.2);
    }

    .header p {
      font-size: 1.15rem;
      opacity: 0.95;
    }

    .tabs {
      display: flex;
      justify-content: center;
      gap: 1rem;
      padding: 1.2rem;
      background-color: white;
      box-shadow: 0 2px 10px rgba(0,0,0,0.08);
      flex-wrap: wrap;
    }

    .tab {
      padding: 0.8rem 2rem;
      font-size: 1.1rem;
      font-weight: 600;
      border: none;
      border-radius: 30px;
      background-color: #f1f8e9;
      color: var(--primary);
      cursor: pointer;
      transition: all 0.3s ease;
    }

    .tab.active {
      background: linear-gradient(to right, var(--primary), #0d4d1a);
      color: white;
      transform: translateY(-2px);
      box-shadow: 0 4px 12px rgba(0,0,0,0.2);
    }

    .tab:hover:not(.active) {
      background-color: #dcedc8;
      transform: translateY(-1px);
    }

    .container {
      max-width: 900px;
      margin: 2rem auto;
      padding: 0 1.5rem;
    }

    .tab-content {
      display: none;
      animation: fadeIn 0.5s ease;
    }

    .tab-content.active {
      display: block;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(10px); }
      to { opacity: 1; transform: translateY(0); }
    }

    h2 {
      color: var(--secondary);
      margin-bottom: 1rem;
    }

    p {
      margin-bottom: 1.5rem;
      color: var(--text-light);
    }

    .form-group {
      margin-bottom: 1.4rem;
    }

    .form-group label {
      display: block;
      margin-bottom: 0.6rem;
      font-weight: 600;
      color: var(--text);
    }

    .form-group input,
    .form-group textarea,
    #cityFilter {
      width: 100%;
      padding: 0.9rem;
      border: 2px solid #c8e6c9;
      border-radius: 10px;
      font-family: 'Tajawal', sans-serif;
      font-size: 1rem;
      background-color: white;
      color: var(--text);
    }

    .form-group input::placeholder,
    .form-group textarea::placeholder {
      color: #81c784;
    }

    .form-group input:focus,
    .form-group textarea:focus,
    #cityFilter:focus {
      border-color: var(--accent);
      outline: none;
      box-shadow: 0 0 0 3px rgba(212, 175, 55, 0.3);
    }

    .btn-primary,
    .btn-secondary {
      padding: 1rem 2rem;
      font-size: 1.1rem;
      font-weight: bold;
      border: none;
      border-radius: 10px;
      cursor: pointer;
      transition: all 0.3s ease;
      box-shadow: 0 4px 10px rgba(0,0,0,0.15);
      font-family: 'Tajawal', sans-serif;
      width: 100%;
    }

    .btn-primary {
      background: linear-gradient(to right, var(--primary), #0d4d1a);
      color: white;
    }

    .btn-secondary {
      background: linear-gradient(to right, var(--accent), #b8860b);
      color: white;
    }

    .btn-primary:hover,
    .btn-secondary:hover {
      transform: translateY(-2px);
      box-shadow: 0 6px 15px rgba(0,0,0,0.2);
    }

    .settings-section {
      background-color: #f9fbe7;
      padding: 1.4rem;
      border-radius: 14px;
      border: 1px solid #dcedc8;
      margin-top: 1rem;
    }

    .settings-section h3 {
      margin-bottom: 1rem;
      color: var(--primary);
      font-size: 1.3rem;
    }

    .settings-row {
      margin-bottom: 0.9rem;
    }

    .settings-row label {
      display: flex;
      align-items: center;
      gap: 0.8rem;
      font-weight: 500;
      color: var(--text);
    }

    .controls {
      display: flex;
      gap: 1rem;
      margin-bottom: 1.8rem;
      flex-wrap: wrap;
    }

    #searchInput,
    #cityFilter {
      flex: 1;
      min-width: 180px;
    }

    .artisans-list {
      display: flex;
      flex-direction: column;
      gap: 1.4rem;
    }

    .artisan-card {
      background: var(--card-bg);
      border-radius: 14px;
      padding: 1.6rem;
      box-shadow: var(--shadow);
      border-right: 5px solid var(--accent);
      transition: transform 0.2s;
    }

    .artisan-card:hover {
      transform: translateY(-3px);
      box-shadow: 0 8px 20px rgba(0,0,0,0.18);
    }

    .artisan-card h3 {
      color: var(--secondary);
      margin-bottom: 0.6rem;
      display: flex;
      align-items: center;
      gap: 0.6rem;
    }

    .artisan-icon {
      color: var(--accent);
      font-size: 1.4rem;
    }

    .artisan-photo {
      width: 80px;
      height: 80px;
      border-radius: 50%;
      object-fit: cover;
      border: 3px solid var(--accent);
      margin-bottom: 1rem;
      box-shadow: 0 3px 8px rgba(0,0,0,0.1);
    }

    .contact-buttons {
      display: flex;
      gap: 0.8rem;
      margin: 1rem 0;
      flex-wrap: wrap;
    }

    .btn-contact {
      display: inline-block;
      padding: 0.65rem 1.2rem;
      border-radius: 8px;
      font-weight: bold;
      text-decoration: none;
      text-align: center;
      font-size: 0.95rem;
      color: white;
      transition: transform 0.2s, box-shadow 0.2s;
      flex: 1;
      min-width: 120px;
    }

    .btn-contact.call {
      background-color: #4caf50;
    }

    .btn-contact.whatsapp {
      background-color: #25d366;
    }

    .btn-contact:hover {
      transform: translateY(-2px);
      box-shadow: 0 4px 10px rgba(0,0,0,0.2);
    }

    .rating {
      color: var(--accent);
      margin: 0.6rem 0;
      font-size: 1.25rem;
    }

    .notification {
      position: fixed;
      top: 20px;
      right: 20px;
      padding: 1rem 1.5rem;
      border-radius: 10px;
      color: white;
      font-weight: bold;
      font-family: 'Tajawal', sans-serif;
      box-shadow: 0 4px 15px rgba(0,0,0,0.3);
      transform: translateX(200%);
      transition: transform 0.3s ease;
      z-index: 1000;
    }

    .notification.show {
      transform: translateX(0);
    }

    .notification.success {
      background: linear-gradient(to right, var(--primary), #0d4d1a);
    }

    .notification.error {
      background: linear-gradient(to right, #d32f2f, #b71c1c);
    }

    @media (max-width: 600px) {
      .header h1 {
        font-size: 1.9rem;
      }
      .controls {
        flex-direction: column;
      }
      .contact-buttons {
        flex-direction: column;
      }
      .btn-contact {
        width: 100%;
      }
    }
  </style>
</head>
<body>
  <!-- Header -->
  <header class="header">
    <h1>الحريفية المغربية</h1>
    <p>منصّة تجمع الحرفيين المغاربة والزبناء في مكان واحد</p>
  </header>

  <!-- Tabs -->
  <div class="tabs">
    <button id="tab1" class="tab active" onclick="showTab(1)">أنا حرفي</button>
    <button id="tab2" class="tab" onclick="showTab(2)">أبحث عن حرفي</button>
  </div>

  <!-- Main Content -->
  <main class="container">
    <!-- Tab 1: تسجيل الحرفي -->
    <section id="artisan-form" class="tab-content active">
      <h2>مرحباً بك يا حرفي! 🛠️</h2>
      <p>سجّل معلوماتك بدقة علشان يلقاك الزبناء اللي كيقلّبوا عليك.</p>
      
      <form id="registerForm">
        <div class="form-group">
          <label for="name">الاسم الكامل *</label>
          <input type="text" id="name" placeholder="مثال: أحمد التلمساني" required />
        </div>

        <div class="form-group">
          <label for="profession">المهنة *</label>
          <input type="text" id="profession" placeholder="مثال: سباك، نجّار، كهربائي..." required />
        </div>

        <div class="form-group">
          <label for="serviceArea">مكان تقديم الخدمة *</label>
          <input type="text" id="serviceArea" placeholder="مثال: الدار البيضاء، أو 'أتنقل لجميع المدن'" required />
        </div>

        <div class="form-group">
          <label for="repairs">الأعطال أو الخدمات اللي كتقدمها *</label>
          <textarea id="repairs" placeholder="مثال: تسريب الماء، انسداد الأنابيب، تركيب الحنفيات..." rows="3" required></textarea>
        </div>

        <div class="form-group">
          <label for="description">وصف عنك (اختياري)</label>
          <textarea id="description" placeholder="مثال: خبرة 10 سنوات، أسعار مناسبة، ضمان على الشغل..." rows="3"></textarea>
        </div>

        <!-- الإعدادات -->
        <div class="form-group settings-section">
          <h3>⚙️ الإعدادات</h3>
          <div class="settings-row">
            <label for="phone">رقم الهاتف (اختياري لكن موصى به)</label>
            <input type="tel" id="phone" placeholder="06XXXXXXXX" />
          </div>
          <div class="settings-row">
            <label for="photoUrl">صورة (رابط أو اختر ملف)</label>
            <input type="text" id="photoUrl" placeholder="لصق رابط الصورة (اختياري)" />
            <input type="file" id="photoFile" accept="image/*" style="margin-top: 0.5rem;" />
            <small style="display: block; margin-top: 0.3rem; color: #666;">أو اختر صورة من جهازك</small>
          </div>
          <div class="settings-row">
            <label>
              <input type="checkbox" id="available" checked />
              الخدمة متاحة حالياً
            </label>
          </div>
        </div>

        <div class="form-group">
          <label for="rating">التقييم الابتدائي (من 1 إلى 5)</label>
          <input type="number" id="rating" min="1" max="5" step="0.5" placeholder="مثال: 4.5" />
        </div>

        <button type="submit" class="btn-primary">أضف حرفتك</button>
      </form>
    </section>

    <!-- Tab 2: البحث عن الحرفيين -->
    <section id="search-artisans" class="tab-content">
      <h2>مرحباً بك! نتمنى تلقى الحرفي اللي بغيتي 💼</h2>
      <p>هنا تلقى لائحة الحرفيين المسجلين مع تقييماتهم وأماكنهم.</p>
      
      <div class="controls">
        <input type="text" id="searchInput" placeholder="ابحث بالاسم، المهنة، أو نوع العطل..." />
        <select id="cityFilter">
          <option value="">جميع المدن</option>
          <option value="الدار البيضاء">الدار البيضاء</option>
          <option value="الرباط">الرباط</option>
          <option value="فاس">فاس</option>
          <option value="مراكش">مراكش</option>
          <option value="أكادير">أكادير</option>
          <option value="طنجة">طنجة</option>
          <option value="وجدة">وجدة</option>
          <option value="أغادير">أغادير</option>
          <option value="أتنقل لجميع المدن">أتنقل لجميع المدن</option>
        </select>
        <button id="exportBtn" class="btn-secondary">تصدير البيانات (JSON)</button>
      </div>

      <div id="artisansList" class="artisans-list"></div>
    </section>
  </main>

  <!-- نظام الإشعارات -->
  <div id="notification" class="notification"></div>

  <script>
    let artisans = JSON.parse(localStorage.getItem('artisans')) || [];

    function showTab(tabNumber) {
      document.querySelectorAll('.tab-content').forEach(el => el.classList.remove('active'));
      document.querySelectorAll('.tab').forEach(el => el.classList.remove('active'));

      document.getElementById('artisan-form').classList.toggle('active', tabNumber === 1);
      document.getElementById('search-artisans').classList.toggle('active', tabNumber === 2);
      document.getElementById(`tab${tabNumber}`).classList.add('active');

      if (tabNumber === 2) {
        renderArtisans();
      }
    }

    function showNotification(message, type = 'success') {
      const notif = document.getElementById('notification');
      notif.textContent = message;
      notif.className = `notification ${type} show`;
      setTimeout(() => {
        notif.classList.remove('show');
      }, 3000);
    }

    function toWhatsAppNumber(phone) {
      let clean = phone.replace(/\D/g, '');
      if (clean.startsWith('0')) {
        clean = '212' + clean.substring(1);
      } else if (!clean.startsWith('212')) {
        clean = '212' + clean;
      }
      return clean;
    }

    function getIconForProfession(profession) {
      const lower = profession.toLowerCase();
      if (lower.includes('نجار')) return 'fas fa-hammer';
      if (lower.includes('سباك') || lower.includes('سباك')) return 'fas fa-wrench';
      if (lower.includes('كهرب') || lower.includes('إلكترو')) return 'fas fa-bolt';
      if (lower.includes('حداد')) return 'fas fa-fire';
      if (lower.includes('خياط')) return 'fas fa-scissors';
      if (lower.includes('دهان') || lower.includes('بوي')) return 'fas fa-paint-roller';
      if (lower.includes('بناء') || lower.includes('بنّاء')) return 'fas fa-hard-hat';
      if (lower.includes('ميكانيك')) return 'fas fa-car';
      if (lower.includes('تكييف') || lower.includes('تكيف')) return 'fas fa-wind';
      if (lower.includes('حلاقة') || lower.includes('حلاق')) return 'fas fa-cut';
      return 'fas fa-tools';
    }

    document.getElementById('photoFile').addEventListener('change', function(e) {
      const file = e.target.files[0];
      if (file) {
        const reader = new FileReader();
        reader.onload = function(event) {
          document.getElementById('photoUrl').value = event.target.result;
        };
        reader.readAsDataURL(file);
      }
    });

    document.getElementById('registerForm').addEventListener('submit', function(e) {
      e.preventDefault();

      const name = document.getElementById('name').value.trim();
      const profession = document.getElementById('profession').value.trim();
      const serviceArea = document.getElementById('serviceArea').value.trim();
      const repairs = document.getElementById('repairs').value.trim();
      const description = document.getElementById('description').value.trim();
      const phone = document.getElementById('phone').value.trim();
      const photoUrl = document.getElementById('photoUrl').value.trim();
      const available = document.getElementById('available').checked;
      const ratingInput = document.getElementById('rating').value;
      const rating = ratingInput ? parseFloat(ratingInput) : 0;

      let finalPhoto = photoUrl;
      if (!finalPhoto) {
        finalPhoto = 'https://via.placeholder.com/150/d4af37/ffffff?text=حرفي';
      }

      const newArtisan = {
        id: Date.now(),
        name,
        profession,
        serviceArea,
        repairs,
        description,
        phone,
        photo: finalPhoto,
        available,
        rating: Math.min(5, Math.max(0, rating))
      };

      artisans.push(newArtisan);
      localStorage.setItem('artisans', JSON.stringify(artisans));

      document.getElementById('registerForm').reset();
      document.getElementById('available').checked = true;
      document.getElementById('photoUrl').value = '';

      showNotification('تم تسجيل حرفتك بنجاح! 🎉', 'success');

      if (document.getElementById('search-artisans').classList.contains('active')) {
        renderArtisans();
      }
    });

    function renderStars(rating) {
      if (rating <= 0) return '<i class="far fa-star"></i>'.repeat(5);
      const full = Math.floor(rating);
      const hasHalf = rating % 1 >= 0.5;
      const empty = 5 - full - (hasHalf ? 1 : 0);
      let stars = '<i class="fas fa-star"></i>'.repeat(full);
      if (hasHalf) stars += '<i class="fas fa-star-half-alt"></i>';
      stars += '<i class="far fa-star"></i>'.repeat(empty);
      return `<span style="color:#d4af37;">${stars}</span>`;
    }

    function renderArtisans() {
      const list = document.getElementById('artisansList');
      const searchTerm = document.getElementById('searchInput').value.toLowerCase();
      const cityFilter = document.getElementById('cityFilter').value;

      const filtered = artisans.filter(a => {
        const matchesSearch = 
          a.name.toLowerCase().includes(searchTerm) ||
          a.profession.toLowerCase().includes(searchTerm) ||
          a.repairs.toLowerCase().includes(searchTerm) ||
          a.serviceArea.toLowerCase().includes(searchTerm);
        
        const matchesCity = !cityFilter || a.serviceArea.includes(cityFilter);
        
        return matchesSearch && matchesCity;
      });

      if (filtered.length === 0) {
        list.innerHTML = '<p style="text-align:center; color:#777; padding:1.5rem;">ما كاينش شي حرفي مسجل حالياً.</p>';
        return;
      }

      list.innerHTML = filtered.map(artisan => {
        const stars = renderStars(artisan.rating);
        const availability = artisan.available 
          ? '<span>✅ متاح</span>' 
          : '<span>❌ غير متاح</span>';
        const icon = getIconForProfession(artisan.profession);
        const contactButtons = artisan.phone ? `
          <div class="contact-buttons">
            <a href="tel:${artisan.phone}" class="btn-contact call">📞 اتصل</a>
            <a href=" https://wa.me/ ${toWhatsAppNumber(artisan.phone)}" target="_blank" class="btn-contact whatsapp">💬 واتساب</a>
          </div>
        ` : '';

        return `
          <div class="artisan-card">
            <img src="${artisan.photo}" alt="صورة ${artisan.name}" class="artisan-photo" onerror="this.src='https://via.placeholder.com/150/d4af37/ffffff?text=حرفي'">
            <h3><i class="${icon} artisan-icon"></i> ${artisan.name}</h3>
            <p><strong>المهنة:</strong> ${artisan.profession}</p>
            <p><strong>مكان الخدمة:</strong> ${artisan.serviceArea}</p>
            <p><strong>الأعطال/الخدمات:</strong> ${artisan.repairs}</p>
            ${contactButtons}
            <div class="rating">${stars} ${artisan.rating > 0 ? `(${artisan.rating.toFixed(1)})` : ''}</div>
            <p>${availability}</p>
            ${artisan.description ? `<p style="margin-top:0.8rem; font-style:italic; color:#555;">${artisan.description}</p>` : ''}
          </div>
        `;
      }).join('');
    }

    document.getElementById('searchInput').addEventListener('input', renderArtisans);
    document.getElementById('cityFilter').addEventListener('change', renderArtisans);

    document.getElementById('exportBtn').addEventListener('click', () => {
      if (artisans.length === 0) {
        showNotification('ما كاينش شي بيانات باش تصدرها!', 'error');
        return;
      }
      const dataStr = JSON.stringify(artisans, null, 2);
      const a = document.createElement('a');
      a.href = URL.createObjectURL(new Blob([dataStr], { type: 'application/json' }));
      a.download = 'al7arafia_artisans.json';
      a.click();
    });

    renderArtisans();
  </script>
</body>
</html> 
