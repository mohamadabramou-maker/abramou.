<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>الحريف تشايت – دردشة فيديو عشوائية 🇲🇦</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Tajawal', 'Segoe UI', Tahoma, sans-serif;
    }

    body {
      background: linear-gradient(135deg, #1a237e, #283593);
      color: white;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      padding: 2rem 1rem;
      text-align: center;
    }

    .logo {
      font-size: 2.8rem;
      font-weight: bold;
      margin-bottom: 1rem;
      color: #ffcc00;
    }

    .tagline {
      font-size: 1.3rem;
      margin-bottom: 2.5rem;
      max-width: 600px;
      line-height: 1.6;
    }

    .btn {
      background: #ffcc00;
      color: #1a237e;
      border: none;
      padding: 1rem 2.5rem;
      font-size: 1.2rem;
      font-weight: bold;
      border-radius: 50px;
      cursor: pointer;
      transition: transform 0.2s, box-shadow 0.3s;
      margin: 1rem;
    }

    .btn:hover {
      transform: scale(1.05);
      box-shadow: 0 6px 15px rgba(255, 204, 0, 0.4);
    }

    .features {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 1.5rem;
      margin-top: 3rem;
      max-width: 900px;
    }

    .feature {
      background: rgba(255, 255, 255, 0.1);
      backdrop-filter: blur(10px);
      padding: 1.5rem;
      border-radius: 15px;
      width: 220px;
    }

    .feature h3 {
      margin: 1rem 0 0.8rem;
      color: #ffcc00;
    }

    footer {
      margin-top: 3rem;
      opacity: 0.8;
      font-size: 0.9rem;
    }

    @media (max-width: 600px) {
      .logo { font-size: 2.2rem; }
      .tagline { font-size: 1.1rem; }
    }
  </style>
</head>
<body>

  <div class="logo">الحريف تشايت</div>
  <p class="tagline">دردشة فيديو عشوائية مع ناس من المغرب والعالم العربي! تقابل شي واحد جديد كل مرة... بلا تسجيل، بلا تعقيد!</p>

  <!-- زر وهمي (لأن الفيديو الحقيقي يحتاج خادم) -->
  <button class="btn" onclick="alert('التطبيق قيد التطوير! سيتم الإطلاق قريباً 🇲🇦')">ابدأ الدردشة الآن</button>

  <div class="features">
    <div class="feature">
      <h3>🎥 فيديو مباشر</h3>
      <p>اتصل بناس جداد عبر الكاميرا في ثوانٍ</p>
    </div>
    <div class="feature">
      <h3>🔒 خصوصية</h3>
      <p>ماشي محتاج تحط إيميل ولا رقم. اسم مستعار بس!</p>
    </div>
    <div class="feature">
      <h3>🇲🇦 دارجة مغربية</h3>
      <p>فلترة حسب المنطقة: الدار البيضاء، مراكش، فاس...</p>
    </div>
    <div class="feature">
      <h3>🚫 تخطي بضغطة</h3>
      <p>ما عجبك؟ اضغط "تخطي" ولقيت شي واحد خرا!</p>
    </div>
  </div>

  <footer>
    <p>© 2025 الحريف تشايت – مشروع مغربي 100%</p>
    <p>دردش، تعرف، واسمع قصص من دابرك!</p>
  </footer>

</body>
</html>
