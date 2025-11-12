<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>دردشتي — الطراز المغربي</title>
  <meta name="theme-color" content="#c62828">
  <link rel="manifest" href="data:application/manifest+json,{
    %22name%22:%22دردشتي%22,
    %22short_name%22:%22دردشة%22,
    %22start_url%22:%22zellige-chat-full.html%22,
    %22display%22:%22standalone%22,
    %22background_color%22:%22%23fff8e1%22,
    %22theme_color%22:%22%23c62828%22,
    %22icons%22:[{
      %22src%22:%22data:image/svg+xml,%3Csvg%20xmlns='http://www.w3.org/2000/svg'%20viewBox='0%200%20100%20100'%3E%3Crect%20width='100'%20height='100'%20fill='%23c62828'/%3E%3Cpath%20d='M20,20%20L50,50%20L20,80%20Z'%20fill='%23ffd700'/%3E%3C/svg%3E%22,
      %22sizes%22:%22192x192%22,
      %22type%22:%22image/svg+xml%22
    }]
  }">

  <style>
    body::before {
      content: "";
      position: fixed;
      top: 0; left: 0;
      width: 100%; height: 100%;
      background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='100' height='100' viewBox='0 0 100 100'%3E%3Cpath d='M0,0 L50,50 L0,100 Z' fill='%23e8f5e9' opacity='0.08'/%3E%3Cpath d='M100,0 L50,50 L100,100 Z' fill='%23fff3e0' opacity='0.08'/%3E%3Ccircle cx='50' cy='50' r='12' fill='%23ffecb3' opacity='0.06'/%3E%3C/svg%3E");
      z-index: -1;
    }

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Tajawal', sans-serif;
    }

    body {
      background: #fff8e1;
      color: #333;
      height: 100vh;
      overflow: hidden;
    }

    @import url('https://fonts.googleapis.com/css2?family=Tajawal:wght@400;600;700&display=swap');

    /* =============== */
    /* الصفحات */
    .page {
      display: none;
      height: 100vh;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      padding: 20px;
    }
    .page.active { display: flex; }

    /* =============== */
    /* تسجيل الدخول */
    .login-box {
      background: white;
      padding: 30px;
      border-radius: 20px;
      box-shadow: 0 10px 30px rgba(0,0,0,0.15);
      width: 90%;
      max-width: 400px;
      text-align: center;
      border: 2px solid #ffecb3;
    }
    .login-box h2 {
      color: #c62828;
      margin-bottom: 20px;
    }
    input {
      width: 100%;
      padding: 12px;
      margin: 10px 0;
      border: 2px solid #ffb300;
      border-radius: 10px;
      font-size: 16px;
      text-align: center;
    }
    .btn {
      background: linear-gradient(to right, #c62828, #d32f2f);
      color: white;
      border: none;
      padding: 12px 24px;
      border-radius: 30px;
      cursor: pointer;
      font-weight: bold;
      margin-top: 10px;
      width: 100%;
    }

    /* =============== */
    /* الواجهة الرئيسية */
    .app {
      display: flex;
      height: 100%;
    }

    .sidebar {
      width: 220px;
      background: linear-gradient(135deg, #c62828, #b71c1c);
      color: white;
      display: flex;
      flex-direction: column;
      align-items: center;
      padding: 16px 8px;
      box-shadow: 3px 0 15px rgba(0,0,0,0.2);
    }
    .logo { font-size: 22px; margin: 12px 0; font-weight: 800; }
    .user-info { margin-top: auto; padding: 10px; font-size: 14px; }

    .servers {
      margin-top: 10px;
    }
    .server-item {
      width: 50px;
      height: 50px;
      border-radius: 50%;
      background: #ffd54f;
      color: #b71c1c;
      display: flex;
      align-items: center;
      justify-content: center;
      margin: 10px 0;
      cursor: pointer;
      font-weight: bold;
      box-shadow: 0 3px 6px rgba(0,0,0,0.2);
    }
    .server-item.add { background: #4caf50; color: white; font-size: 24px; }

    .channels {
      flex: 1;
      background: #fff8e1;
      padding: 14px;
      width: 180px;
      border-right: 2px solid #ffecb3;
    }
    .channel {
      padding: 10px 12px;
      margin: 8px 0;
      border-radius: 8px;
      cursor: pointer;
      color: #5d4037;
      font-weight: 600;
    }
    .channel:hover { background: #ffecb3; }
    .channel.add { color: #2e7d32; font-weight: bold; }

    .chat-area {
      flex: 1;
      display: flex;
      flex-direction: column;
    }
    .chat-header {
      padding: 14px 20px;
      background: linear-gradient(to right, #2e7d32, #4caf50);
      color: white;
      font-weight: bold;
    }
    .messages {
      flex: 1;
      padding: 20px;
      overflow-y: auto;
      background: rgba(255,255,255,0.8);
    }
    .message {
      margin-bottom: 12px;
      padding: 10px;
      background: white;
      border-radius: 10px;
      max-width: 80%;
    }
    .input-area {
      padding: 14px;
      background: #fff8e1;
      display: flex;
      gap: 10px;
    }

    /* =============== */
    /* نافذة المكالمة */
    #callModal {
      display: none;
      position: fixed;
      inset: 0;
      background: rgba(0,0,0,0.9);
      z-index: 1000;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      color: white;
    }
    #localVideo {
      width: 320px;
      height: 240px;
      background: black;
      border: 2px solid #ffd54f;
      border-radius: 10px;
      transform: rotateY(180deg);
    }
    #callControls {
      margin-top: 20px;
    }
    #callControls button {
      background: #c62828;
      color: white;
      border: none;
      padding: 10px 20px;
      border-radius: 30px;
      cursor: pointer;
      margin: 0 10px;
    }
  </style>
</head>
<body>

  <!-- صفحة تسجيل الدخول -->
  <div id="loginPage" class="page active">
    <div class="login-box">
      <h2>مرحباً بك في دردشتي</h2>
      <p style="margin-bottom:15px; color:#5d4037">ادخل اسمك لتبدأ المغامرة</p>
      <input type="text" id="usernameInput" placeholder="اسمك الكامل" maxlength="20" />
      <button class="btn" onclick="login()">دخول إلى التطبيق</button>
    </div>
  </div>

  <!-- الواجهة الرئيسية -->
  <div id="appPage" class="page">
    <div class="app">
      <div class="sidebar">
        <div class="logo">دردشتي</div>
        <div class="servers" id="serversList">
          <div class="server-item" onclick="joinServer('عام')">🏠</div>
        </div>
        <div class="server-item add" onclick="createServer()">+</div>
        <div class="user-info" id="userInfo"></div>
      </div>

      <div class="channels" id="channelsList">
        <div class="channel active"># عام</div>
        <div class="channel" onclick="startCall()">🎤 روم صوتي</div>
        <div class="channel add" onclick="createChannel()">+ إنشاء روم</div>
      </div>

      <div class="chat-area">
        <div class="chat-header" id="currentRoom"># عام</div>
        <div class="messages" id="messages">
          <div class="message"><strong>النظام:</strong> مرحبًا! أنت في الغرفة العامة.</div>
        </div>
        <div class="input-area">
          <input type="text" id="messageInput" placeholder="اكتب رسالتك..." />
          <button class="btn" style="width:auto;padding:10px 20px;" onclick="sendMessage()">إرسال</button>
        </div>
      </div>
    </div>
  </div>

  <!-- نافذة المكالمة -->
  <div id="callModal">
    <video id="localVideo" autoplay muted playsinline></video>
    <div id="callControls">
      <button onclick="endCall()">إنهاء المكالمة</button>
    </div>
  </div>

  <script>
    let currentUser = localStorage.getItem('username') || null;
    let currentServer = 'عام';
    let currentChannel = 'عام';

    function login() {
      const name = document.getElementById('usernameInput').value.trim();
      if (name) {
        currentUser = name;
        localStorage.setItem('username', name);
        document.getElementById('userInfo').innerText = name;
        showPage('appPage');
      } else {
        alert('الرجاء إدخال اسمك');
      }
    }

    function showPage(pageId) {
      document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
      document.getElementById(pageId).classList.add('active');
    }

    // إذا كان المستخدم مسجل دخوله مسبقًا
    if (currentUser) {
      document.getElementById('userInfo').innerText = currentUser;
      showPage('appPage');
    }

    function sendMessage() {
      const input = document.getElementById('messageInput');
      const text = input.value.trim();
      if (text && currentUser) {
        const msg = document.createElement('div');
        msg.className = 'message';
        msg.innerHTML = `<strong>${currentUser}:</strong> ${text}`;
        document.getElementById('messages').appendChild(msg);
        input.value = '';
        document.getElementById('messages').scrollTop = document.getElementById('messages').scrollHeight;
      }
    }

    document.getElementById('messageInput').addEventListener('keypress', (e) => {
      if (e.key === 'Enter') sendMessage();
    });

    function createServer() {
      const name = prompt('أدخل اسم السيرفر الجديد:');
      if (name) {
        const servers = document.getElementById('serversList');
        const div = document.createElement('div');
        div.className = 'server-item';
        div.innerText = name.charAt(0).toUpperCase();
        div.onclick = () => joinServer(name);
        servers.appendChild(div);
        alert(`تم إنشاء سيرفر: ${name}`);
      }
    }

    function joinServer(name) {
      currentServer = name;
      document.getElementById('currentRoom').innerText = `# ${name}`;
      document.getElementById('messages').innerHTML = `<div class="message"><strong>النظام:</strong> دخلت إلى سيرفر "${name}".</div>`;
    }

    function createChannel() {
      const name = prompt('اسم الروم الجديد:');
      if (name) {
        const channels = document.getElementById('channelsList');
        const div = document.createElement('div');
        div.className = 'channel';
        div.innerText = `# ${name}`;
        channels.insertBefore(div, channels.lastElementChild);
        alert(`تم إنشاء روم: ${name}`);
      }
    }

    async function startCall() {
      try {
        const stream = await navigator.mediaDevices.getUserMedia({ video: true, audio: true });
        const video = document.getElementById('localVideo');
        video.srcObject = stream;
        document.getElementById('callModal').style.display = 'flex';
      } catch (err) {
        alert('لم نتمكن من فتح الكاميرا أو الميكروفون. تأكد من منح الإذن.');
        console.error(err);
      }
    }

    function endCall() {
      const video = document.getElementById('localVideo');
      const stream = video.srcObject;
      if (stream) {
        stream.getTracks().forEach(track => track.stop());
      }
      document.getElementById('callModal').style.display = 'none';
    }
  </script>
</body>
</html>
