<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>MarkitPlays — متابعين حقيقيون على كل المنصات</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }
    body {
      background: linear-gradient(135deg, #f0f9ff, #eef2ff);
      color: #1e293b;
      line-height: 1.6;
    }
    .container {
      width: 90%;
      max-width: 1200px;
      margin: 0 auto;
    }
    header {
      background: white;
      box-shadow: 0 2px 10px rgba(0,0,0,0.08);
      position: sticky;
      top: 0;
      z-index: 100;
    }
    .navbar {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 18px 0;
    }
    .logo {
      font-size: 1.9rem;
      font-weight: 800;
      color: #4f46e5;
    }
    .hero {
      text-align: center;
      padding: 90px 0;
    }
    .hero h1 {
      font-size: 2.8rem;
      margin-bottom: 20px;
      color: #0f172a;
    }
    .hero p {
      font-size: 1.2rem;
      color: #475569;
      max-width: 700px;
      margin: 0 auto 30px;
    }
    .section {
      padding: 80px 0;
    }
    .section-title {
      text-align: center;
      font-size: 2.2rem;
      margin-bottom: 15px;
      color: #0f172a;
    }
    .section-subtitle {
      text-align: center;
      color: #64748b;
      max-width: 700px;
      margin: 0 auto 50px;
      font-size: 1.1rem;
    }
    .pricing-cards {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 30px;
    }
    .pricing-card {
      background: white;
      border-radius: 20px;
      padding: 40px 25px;
      text-align: center;
      box-shadow: 0 6px 20px rgba(0,0,0,0.06);
    }
    .pricing-card.popular {
      border: 2px solid #4f46e5;
      position: relative;
    }
    .popular-tag {
      position: absolute;
      top: -12px;
      right: 25px;
      background: #10b981;
      color: white;
      padding: 4px 14px;
      border-radius: 20px;
      font-size: 0.85rem;
      font-weight: bold;
    }
    .price {
      font-size: 2.2rem;
      font-weight: 800;
      margin: 20px 0;
      color: #0f172a;
    }
    .price span {
      font-size: 1rem;
      color: #64748b;
    }
    ul {
      list-style: none;
      margin: 25px 0;
    }
    ul li {
      padding: 8px 0;
      color: #64748b;
    }
    ul li::before {
      content: "✓";
      color: #10b981;
      font-weight: bold;
      margin-left: 10px;
    }
    .btn {
      display: inline-block;
      padding: 14px 32px;
      background: #4f46e5;
      color: white;
      text-decoration: none;
      border-radius: 10px;
      font-weight: 600;
      margin-top: 15px;
      transition: background 0.3s;
    }
    .btn:hover {
      background: #4338ca;
    }
    footer {
      background: #0f172a;
      color: #cbd5e1;
      text-align: center;
      padding: 30px 0;
      margin-top: 60px;
    }
    @media (max-width: 768px) {
      .hero h1 { font-size: 2.2rem; }
      .pricing-card { padding: 30px 15px; }
    }
  </style>
</head>
<body>

  <!-- Header -->
  <header>
    <div class="container navbar">
      <div class="logo">Markit<span style="color:#0f172a">Plays</span></div>
    </div>
  </header>

  <!-- Hero -->
  <section class="hero">
    <div class="container">
      <h1>متابعين حقيقيون — نتائج خلال 24 ساعة</h1>
      <p>نزوّدك بمتابعين نشطين وحقيقيين على إنستغرام، تيك توك، يوتيوب، تويتر، وفيسبوك — بدون خطر الحظر.</p>
    </div>
  </section>

  <!-- Pricing -->
  <section class="section">
    <div class="container">
      <h2 class="section-title">اختر خطتك</h2>
      <p class="section-subtitle">كل الخُطَط تشمل متابعين حقيقيين + دعم فني + ضمان استرداد</p>
      <div class="pricing-cards">

        <!-- Basic Plan -->
        <div class="pricing-card">
          <h3>الأساسية</h3>
          <div class="price">14.99<span> دولار</span></div>
          <p>1000 متابع</p>
          <ul>
            <li>تسليم خلال 48 ساعة</li>
            <li>دعم عبر الواتساب</li>
            <li>ضمان 30 يوم</li>
          </ul>
          <a href="https://wa.me/YOUR_PHONE_NUMBER?text=السلام%20عليكم%2C%20بغيت%20أشري%20خطة%20الأساسية%20(1000%20متابعين)%20على%20إنستغرام.%20رابط%20حسابي%3A%20%40yourname" class="btn">اطلب الآن</a>
        </div>

        <!-- Pro Plan -->
        <div class="pricing-card popular">
          <div class="popular-tag">الأكثر طلبًا</div>
          <h3>الاحترافية</h3>
          <div class="price">34.99<span> دولار</span></div>
          <p>3000 متابع</p>
          <ul>
            <li>تسليم خلال 24 ساعة</li>
            <li>دعم فني أولوي</li>
            <li>ضمان 60 يوم</li>
            <li>تقرير أداء</li>
          </ul>
          <a href="https://wa.me/YOUR_PHONE_NUMBER?text=السلام%20عليكم%2C%20بغيت%20أشري%20خطة%20الاحترافية%20(3000%20متابعين)%20على%20إنستغرام.%20رابط%20حسابي%3A%20%40yourname" class="btn">اطلب الآن</a>
        </div>

        <!-- Gold Plan -->
        <div class="pricing-card">
          <h3>الذهبية</h3>
          <div class="price">79.99<span> دولار</span></div>
          <p>10000 متابع</p>
          <ul>
            <li>تسليم خلال 12 ساعة</li>
            <li>مدير حساب شخصي</li>
            <li>ضمان 90 يوم</li>
            <li>استراتيجية محتوى</li>
          </ul>
          <a href="https://wa.me/YOUR_PHONE_NUMBER?text=السلام%20عليكم%2C%20بغيت%20أشري%20خطة%20الذهبية%20(10000%20متابعين)%20على%20إنستغرام.%20رابط%20حسابي%3A%20%40yourname" class="btn">اطلب الآن</a>
        </div>

      </div>
    </div>
  </section>

  <!-- Footer -->
  <footer>
    <div class="container">
      &copy; 2025 MarkitPlays. جميع الحقوق محفوظة.
    </div>
  </footer>

</body>
</html>
