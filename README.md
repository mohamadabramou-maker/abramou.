<!doctype html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <title>صفحة جذب النقرات — Abramo</title>
  <meta name="description" content="صفحة انترهيد جذابة مصممة لتحويل الزوار إلى نقرات (CTA)."> 
  <style>
    :root{
      --bg:#0f1724;
      --card:#0b1220;
      --accent1:#7c3aed; /* purple */
      --accent2:#06b6d4; /* teal */
      --glass: rgba(255,255,255,0.06);
      --text:#e6eef8;
      --muted: rgba(230,238,248,0.6);
    }
    *{box-sizing:border-box}
    body{
      margin:0;min-height:100vh;background:linear-gradient(180deg,var(--bg) 0%, #071022 100%);font-family:Inter, 'Segoe UI', Tahoma, sans-serif;color:var(--text);display:flex;align-items:center;justify-content:center;padding:32px;
    }
    .wrap{width:100%;max-width:1100px;display:grid;grid-template-columns:1fr 420px;gap:28px;align-items:center}
    @media (max-width:900px){.wrap{grid-template-columns:1fr;max-width:900px}}

    /* Left - Hero */
    .hero{padding:36px;border-radius:20px;background:linear-gradient(180deg, rgba(255,255,255,0.02), transparent);backdrop-filter: blur(6px);box-shadow: 0 6px 30px rgba(2,6,23,0.6);position:relative;overflow:hidden}
    .badge{display:inline-block;padding:8px 12px;border-radius:999px;background:linear-gradient(90deg,var(--accent2),var(--accent1));font-weight:600;color:#061017;margin-bottom:12px}
    h1{font-size:38px;line-height:1.02;margin:6px 0 12px}
    p.lead{color:var(--muted);margin:0 0 22px}

    /* Animated blob */
    .blob-wrap{position:absolute;right:-80px;top:-60px;z-index:0;filter:blur(28px);opacity:0.9}
    svg.blob{width:520px;height:520px}

    /* CTA area */
    .cta{display:flex;gap:12px;align-items:center;z-index:2;position:relative}
    .btn-primary{appearance:none;border:0;padding:14px 20px;border-radius:14px;font-weight:700;cursor:pointer;background:linear-gradient(90deg,var(--accent1),var(--accent2));color:#021019;box-shadow:0 8px 30px rgba(124,58,237,0.18);transform:translateY(0);transition:transform .14s ease, box-shadow .14s ease}
    .btn-primary:active{transform:translateY(2px)}
    .btn-ghost{background:transparent;border:1px solid rgba(255,255,255,0.06);padding:12px 14px;border-radius:12px;color:var(--muted)}

    /* Right - Preview Card */
    .card{padding:20px;border-radius:16px;background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));border:1px solid rgba(255,255,255,0.03);box-shadow:0 8px 30px rgba(2,6,23,0.5)}
    .profile{display:flex;gap:12px;align-items:center}
    .avatar{width:64px;height:64px;border-radius:14px;flex:0 0 64px;background:linear-gradient(180deg,var(--accent1),var(--accent2));display:flex;align-items:center;justify-content:center;font-weight:800;color:#021019;font-size:20px}
    .meta h3{margin:0;font-size:18px}
    .meta p{margin:4px 0 0;color:var(--muted);font-size:13px}

    .stats{display:flex;gap:8px;margin-top:16px}
    .stat{flex:1;background:var(--glass);padding:10px;border-radius:10px;text-align:center}
    .stat strong{display:block;font-size:18px}
    .stat span{font-size:12px;color:var(--muted)}

    /* micro interactions */
    .btn-primary:hover{box-shadow:0 18px 40px rgba(6,182,212,0.12);transform:translateY(-4px)}

    /* small footer */
    .foot{font-size:12px;color:var(--muted);margin-top:18px}

    /* sparkle pointer */
    .pointer{display:inline-flex;align-items:center;gap:8px;background:linear-gradient(90deg, rgba(255,255,255,0.03), transparent);padding:8px 10px;border-radius:999px}

    /* Subtle entrance animation */
    .hero, .card{transform:translateY(12px);opacity:0;animation:enter .6s forwards ease-out}
    .card{animation-delay:.08s}
    @keyframes enter{to{transform:none;opacity:1}}

    /* tiny input */
    .email{display:flex;gap:8px;margin-top:14px}
    .email input{flex:1;padding:12px;border-radius:12px;border:1px solid rgba(255,255,255,0.04);background:transparent;color:var(--text)}

  </style>
</head>
<body>
  <div class="wrap">
    <section class="hero">
      <div class="badge">حصري • سريع</div>
      <h1>خلي الزوار ينقرو — صفحة تصميم جذاب بتحويل عالي</h1>
      <p class="lead">هاذ الصفحة معمولة باش تجذب الانتباه و تحفز النقر على زرّ الدعوة للعمل (CTA). فيها شكل متحرك، نص واضح، وزر كبير بارز.</p>

      <div class="cta">
        <button class="btn-primary" id="mainCta">شاهد الآن — مجاناً</button>
        <button class="btn-ghost" id="secondary">اكتشف المزايا</button>
      </div>

      <div class="email">
        <input type="email" id="emailInput" placeholder="دخل الإيميل ديالك باش نتاصلو بيك" aria-label="email">
        <button class="btn-primary" id="signup">سجل</button>
      </div>

      <div class="foot">نصيحة: بدّل النصوص و الألوان باش يتناسق مع الهوية ديال القناة أو المنتج ديالك.</div>

      <div class="blob-wrap">
        <svg class="blob" viewBox="0 0 600 600" xmlns="http://www.w3.org/2000/svg">
          <defs>
            <linearGradient id="g1" x1="0%" x2="100%" y1="0%" y2="100%">
              <stop offset="0%" stop-color="#7c3aed" stop-opacity="0.95"/>
              <stop offset="100%" stop-color="#06b6d4" stop-opacity="0.95"/>
            </linearGradient>
            <filter id="f1" x="-50%" y="-50%" width="200%" height="200%">
              <feGaussianBlur stdDeviation="12" />
            </filter>
          </defs>
          <g filter="url(#f1)">
            <path fill="url(#g1)">
              <animate attributeName="d" dur="8s" repeatCount="indefinite"
                values="M442,318Q414,386,349,385Q284,384,257,339Q230,294,180,264Q130,234,138,174Q146,114,200,84Q254,54,310,70Q366,86,401,129Q436,172,442,236Q448,300,442,318Z;
                        M468,332Q439,404,365,404Q291,404,255,360Q219,316,168,288Q117,260,120,198Q123,136,179,101Q235,66,303,74Q371,82,408,129Q445,176,469,231Q493,286,468,332Z;
                        M438,316Q407,382,348,379Q289,376,258,329Q227,282,179,254Q131,226,122,170Q113,114,162,83Q211,52,272,50Q333,48,376,92Q419,136,441,188Q463,240,438,316Z"/>
            </path>
          </g>
        </svg>
      </div>
    </section>

    <aside class="card">
      <div class="profile">
        <div class="avatar">A</div>
        <div class="meta">
          <h3>أبرامو لايف</h3>
          <p>قناة العاب و محتوى إبداعي — كنزيدو نكبروا كل نهار</p>
        </div>
      </div>

      <div class="stats">
        <div class="stat"><strong>48</strong><span>مشترك</span></div>
        <div class="stat"><strong>12</strong><span>فيديو</span></div>
        <div class="stat"><strong>1.2k</strong><span>مشاهدات إجمالية</span></div>
      </div>

      <div style="margin-top:14px">
        <div class="pointer">↗️ <span style="font-weight:700;margin-right:6px">إبدا الآن</span> جرب الـ CTA و شوف النتيجة</div>
      </div>

    </aside>

    <!-- Testimonials Section -->
    <section class="hero" style="margin-top:32px;grid-column:1/-1">
      <div class="badge">آراء الناس</div>
      <h1 style="font-size:30px;margin-bottom:18px">آشنو قالو على التصميم</h1>

      <div style="display:grid;grid-template-columns:1fr 320px;gap:18px;margin-top:18px;align-items:start">
        <div style="display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:18px">
          <div class="card" style="padding:18px">
            <p style="color:var(--muted);font-size:14px">🔥 "أحسن صفحة هبطتها باش نطلع الكليكات — ديزاين نقي بزاف!"</p>
            <strong style="font-size:15px">— مستخدم 1</strong>
          </div>
          <div class="card" style="padding:18px">
            <p style="color:var(--muted);font-size:14px">"الصفحة بدات تجيب لي تفاعل كثر من قبل، شكراً بزاف."</p>
            <strong style="font-size:15px">— مستخدم 2</strong>
          </div>
          <div class="card" style="padding:18px">
            <p style="color:var(--muted);font-size:14px">"الستايل مزيان وكاين ديك اللمسة العصرية ديال 2025."</p>
            <strong style="font-size:15px">— مستخدم 3</strong>
          </div>
        </div>

        <!-- Social 3D Panel -->
        <div class="card" style="padding:18px;display:flex;flex-direction:column;gap:12px;align-items:center">
          <div id="badge3d" style="width:160px;height:160px;border-radius:18px;overflow:hidden;perspective:900px;display:flex;align-items:center;justify-content:center;background:linear-gradient(180deg,var(--accent1),var(--accent2));">
            <!-- Replace the inner img src with a real portrait URL. If you want a 3D-looking effect, use a square PNG. -->
            <div id="inner3d" style="width:140px;height:140px;border-radius:14px;background:url('https://i.imgur.com/7kQzGQG.png') center/cover no-repeat;transform-style:preserve-3d;transition:transform .12s linear;box-shadow:0 10px 30px rgba(2,6,23,0.6)"></div>
          </div>

          <div style="text-align:center">
            <strong>أبرامو لايف</strong>
            <div style="font-size:13px;color:var(--muted)">ربط مباشر بالبروفايلات:</div>
          </div>

          <div style="display:flex;gap:10px;margin-top:8px">
            <!-- Instagram -->
            <a class="social-link" href="https://www.instagram.com/lhaj_abramou?igsh=MWZhcXhqcDh3Y2I0Ng==" target="_blank" rel="noopener" title="Instagram">
              <svg width="44" height="44" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg" aria-hidden>
                <rect x="2" y="2" width="20" height="20" rx="5" stroke="currentColor" stroke-width="1.2" fill="url(#ig)" />
                <defs>
                  <linearGradient id="ig" x1="0" x2="1"><stop offset="0" stop-color="#f58529"/><stop offset="0.5" stop-color="#dd2a7b"/><stop offset="1" stop-color="#8134af"/></linearGradient>
                </defs>
              </svg>
            </a>

            <!-- YouTube -->
            <a class="social-link" href="https://www.youtube.com/@abramou_live" target="_blank" rel="noopener" title="YouTube">
              <svg width="44" height="44" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg" aria-hidden>
                <rect x="2" y="5" width="20" height="14" rx="3" stroke="currentColor" stroke-width="1.2" fill="#FF0000" />
                <path d="M10 9l5 3-5 3V9z" fill="#fff" />
              </svg>
            </a>

            <!-- Discord -->
            <a class="social-link" href="https://discord.gg/FwUvY3hsE8" target="_blank" rel="noopener" title="Discord">
              <svg width="44" height="44" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg" aria-hidden>
                <rect x="2" y="2" width="20" height="20" rx="6" stroke="currentColor" stroke-width="1.2" fill="#5865F2" />
                <path d="M7.5 10.5c.8 0 1.4.7 1.4 1.6s-.6 1.6-1.4 1.6S6.1 12.8 6.1 12s.7-1.5 1.4-1.5zM16.5 10.5c.8 0 1.4.7 1.4 1.6s-.6 1.6-1.4 1.6S15.1 12.8 15.1 12s.7-1.5 1.4-1.5z" fill="#fff" />
              </svg>
            </a>
          </div>

          <div style="font-size:12px;color:var(--muted);margin-top:6px">تقدر تبدّل الصورة من داخل الكود في العنصر <code>#inner3d</code></div>
        </div>
      </div>
    </section>
  </div>

  <script>
    // بسيط: تأثير تتبع النقر و تحكم فالـCTA
    document.getElementById('mainCta').addEventListener('click', function(){
      // تأثير بصري قصير
      const btn = this;
      btn.innerText = 'جيّد — تحوّل!';
      btn.style.transform = 'scale(0.98)';
      setTimeout(()=>{btn.style.transform=''; btn.innerText = 'شاهد الآن — مجاناً'},1200);

      // سجل حدث (مثال) — هنا تقدر تربط مع Analytics
      console.log('CTA clicked', new Date().toISOString());
    });

    document.getElementById('signup').addEventListener('click', function(){
      const email = document.getElementById('emailInput').value.trim();
      if(!email){
        alert('دخل الإيميل ديالك باش نسجلوك');
        return;
      }
      this.disabled = true; this.innerText = 'تم التسجيل';
      console.log('signup:', email);
      setTimeout(()=>{this.disabled=false; this.innerText='سجل'},1200);
    });

    // Optional: make avatar initial dynamic from channel name
    const name = 'أبرامو لايف';
    document.querySelector('.avatar').innerText = name.trim().charAt(0) || 'A';
  // Animated counters
const counters = document.querySelectorAll('.stat strong');
const animateCounters = ()=>{
  counters.forEach(c=>{
    const target = +c.innerText.replace(/[^0-9]/g,'');
    let current = 0;
    const step = target / 80;
    const update = ()=>{
      current += step;
      if(current < target){
        c.innerText = Math.floor(current);
        requestAnimationFrame(update);
      } else {
        c.innerText = target;
      }
    };
    update();
  });
};
setTimeout(animateCounters,800);

// 3D avatar tilt interaction
const inner3d = document.getElementById('inner3d');
const badge3d = document.getElementById('badge3d');
if(inner3d && badge3d){
  badge3d.addEventListener('mousemove', (e)=>{
    const r = badge3d.getBoundingClientRect();
    const cx = r.left + r.width/2;
    const cy = r.top + r.height/2;
    const dx = e.clientX - cx;
    const dy = e.clientY - cy;
    const rx = (dy / r.height) * -18; // rotateX
    const ry = (dx / r.width) * 18; // rotateY
    inner3d.style.transform = `rotateX(${rx}deg) rotateY(${ry}deg) scale(1.02)`;
  });
  badge3d.addEventListener('mouseleave', ()=>{ inner3d.style.transform = 'rotateX(0deg) rotateY(0deg) scale(1)'; });
}

// small social link pulse on hover
const socials = document.querySelectorAll('.social-link');
socials.forEach(s=>{
  s.style.display='inline-flex'; s.style.alignItems='center'; s.style.justifyContent='center'; s.style.width='44px'; s.style.height='44px'; s.style.borderRadius='10px'; s.style.boxShadow='0 6px 18px rgba(2,6,23,0.4)'; s.style.transition='transform .12s ease, box-shadow .12s ease';
  s.addEventListener('mouseenter', ()=>{ s.style.transform='translateY(-6px)'; s.style.boxShadow='0 18px 40px rgba(0,0,0,0.18)'; });
  s.addEventListener('mouseleave', ()=>{ s.style.transform=''; s.style.boxShadow='0 6px 18px rgba(2,6,23,0.4)'; });
});

</script>
  <button id="themeToggle" style="position:fixed;bottom:20px;left:20px;padding:10px 16px;border-radius:12px;border:0;cursor:pointer;background:var(--glass);color:var(--text);backdrop-filter:blur(6px)">تغيير الثيم</button>

<script>
  const root = document.documentElement;
  let dark = true;
  document.getElementById('themeToggle').onclick = ()=>{
    dark = !dark;
    if(dark){
      root.style.setProperty('--bg','#0f1724');
      root.style.setProperty('--card','#0b1220');
      root.style.setProperty('--text','#e6eef8');
      root.style.setProperty('--muted','rgba(230,238,248,0.6)');
    } else {
      root.style.setProperty('--bg','#fafafa');
      root.style.setProperty('--card','#ffffff');
      root.style.setProperty('--text','#0c1320');
      root.style.setProperty('--muted','rgba(0,0,0,0.55)');
    }
  };
</script>
</body>
</html>
