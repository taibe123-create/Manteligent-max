<!DOCTYPE html>
<html>
<head>
  <title>MX - AI Learning Platform</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      background: linear-gradient(135deg, #0a1628 0%, #0f2540 100%);
      color: #e0f4ff;
      font-family: 'Segoe UI', Arial, sans-serif;
      min-height: 100vh;
    }

    /* ========== HEADER ========== */
    header {
      text-align: center;
      padding: 20px;
      background: radial-gradient(circle at center, rgba(0, 0, 0, 0.8), #0e0e0e);
      border-bottom: 2px solid rgba(255, 215, 0, 0.3);
      animation: glowPulse 3s infinite;
    }

    @keyframes glowPulse {
      0%, 100% {
        box-shadow: inset 0 0 20px rgba(255, 215, 0, 0.1);
      }
      50%, 60% {
        box-shadow: inset 0 0 40px rgba(0, 150, 255, 0.4),
                    0 0 50px rgba(255, 215, 0, 0.3);
      }
    }

    .logo-container {
      position: relative;
      display: inline-block;
      animation: lightningFlash 2s infinite;
      margin-bottom: 14px;
    }

    @keyframes lightningFlash {
      0% {
        filter: drop-shadow(0 0 5px rgba(255, 215, 0, 0.3));
      }
      45% {
        filter: drop-shadow(0 0 5px rgba(255, 215, 0, 0.3));
      }
      50% {
        filter: drop-shadow(0 0 30px rgba(255, 215, 0, 1)) 
                drop-shadow(0 0 60px rgba(0, 150, 255, 0.8))
                brightness(1.3);
      }
      55% {
        filter: drop-shadow(0 0 5px rgba(255, 215, 0, 0.3));
      }
      60% {
        filter: drop-shadow(0 0 30px rgba(255, 215, 0, 1)) 
                drop-shadow(0 0 60px rgba(0, 150, 255, 0.8))
                brightness(1.3);
      }
      65% {
        filter: drop-shadow(0 0 5px rgba(255, 215, 0, 0.3));
      }
      100% {
        filter: drop-shadow(0 0 5px rgba(255, 215, 0, 0.3));
      }
    }

    .logo {
      width: 80px;
      height: 80px;
      background: black-blue(135deg, #ffdd00, #ffa500);
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 2em;
      font-weight: bold;
      color: #000;
      box-shadow: 0 0 20px rgba(255, 215, 0, 0.5);
      cursor: pointer;
      transition: transform 1s;
    }

    .logo:hover {
      transform: scale(1.1);
    }

    header h1 {
      color: #ffdd00;
      text-shadow: 0 0 10px rgba(255, 215, 0, 0.5);
      margin: 10px 0 5px 0;
    }

    header p {
      color: #00d4ff;
    }

    /* ========== NAVIGATION ========== */
    nav {
      display: flex;
      justify-content: center;
      flex-wrap: wrap;
      gap: 10px;
      background: #111;
      padding: 15px;
      border-bottom: 1px solid rgba(255, 215, 0, 0.2);
    }

    nav button {
      padding: 12px 25px;
      background: linear-gradient(135deg, rgba(255, 215, 0, 0.1), rgba(0, 212, 255, 0.1));
      border: 2px solid #ffdd00;
      color: #ffdd00;
      border-radius: 25px;
      cursor: pointer;
      font-weight: bold;
      transition: all 0.3s;
      box-shadow: 0 0 10px rgba(255, 215, 0, 0.2);
    }

    nav button:hover {
      background: linear-gradient(135deg, #ffdd00, #00d4ff);
      color: #000;
      transform: translateY(-3px);
      box-shadow: 0 5px 20px rgba(255, 215, 0, 0.5);
    }

    /* ========== PAGES CONTAINER ========== */
    .page {
      display: none;
      animation: fadeIn 0.5s ease-in;
    }

    .page.active {
      display: block;
    }

    @keyframes fadeIn {
      from { opacity: 0; }
      to { opacity: 1; }
    }

    /* ========== HOME PAGE ========== */
    .home-content {
      max-width: 1000px;
      margin: 30px auto;
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 20px;
      padding: 20px;
    }

    .card {
      background: linear-gradient(135deg, rgba(26, 26, 26, 0.8), rgba(40, 40, 40, 0.8));
      padding: 30px;
      border-radius: 15px;
      border: 2px solid #ffdd00;
      cursor: pointer;
      transition: all 0.3s;
      box-shadow: 0 0 20px rgba(255, 215, 0, 0.1);
      text-align: center;
      position: relative;
      overflow: hidden;
    }

    .card::before {
      content: '';
      position: absolute;
      top: 0;
      left: -100%;
      width: 100%;
      height: 100%;
      background: linear-gradient(90deg, transparent, rgba(255, 215, 0, 0.3), transparent);
      transition: left 0.5s;
    }

    .card:hover::before {
      left: 100%;
    }

    .card:hover {
      background: linear-gradient(135deg, rgba(255, 215, 0, 0.1), rgba(0, 212, 255, 0.1));
      box-shadow: 0 0 30px rgba(255, 215, 0, 0.4), 0 0 50px rgba(0, 212, 255, 0.2);
      transform: translateY(-5px) scale(1.05);
      border-color: #00d4ff;
    }

    .card h2 {
      color: #ffdd00;
      margin-bottom: 10px;
      font-size: 1.5em;
      text-shadow: 0 0 10px rgba(255, 215, 0, 0.3);
    }

    .card p {
      color: #00d4ff;
      font-size: 1em;
    }

    .card-icon {
      font-size: 2em;
      margin-bottom: 10px;
    }

    /* ========== AI PAGE ========== */
    .ai-container {
      display: flex;
      max-width: 1200px;
      margin: 20px auto;
      gap: 20px;
      padding: 20px;
      height: 70vh;
    }

    .robot-section {
      flex: 1;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      background: linear-gradient(135deg, rgba(0, 212, 255, 0.1) 0%, rgba(135, 206, 235, 0.1) 100%);
      border: 2px solid #00d4ff;
      border-radius: 20px;
      padding: 30px;
      box-shadow: 0 0 30px rgba(0, 212, 255, 0.3);
      position: relative;
      overflow: hidden;
    }

    .robot {
      position: relative;
      text-align: center;
      animation: float 3s ease-in-out infinite;
      z-index: 1;
    }

    @keyframes float {
      0%, 100% { transform: translateY(0px); }
      50% { transform: translateY(-10px); }
    }

    .robot-head {
      width: 100px;
      height: 100px;
      background: linear-gradient(135deg, #00d4ff, #00a8cc);
      border-radius: 50%;
      margin: 0 auto 20px;
      position: relative;
      box-shadow: 0 0 20px rgba(0, 212, 255, 0.5);
      border: 3px solid #87ceeb;
    }

    .robot-eyes {
      display: flex;
      justify-content: center;
      gap: 20px;
      margin-top: 25px;
      position: absolute;
      width: 100%;
      top: 20px;
    }

    .eye {
      width: 15px;
      height: 15px;
      background: #001a33;
      border-radius: 50%;
      border: 2px solid #00ff88;
      animation: blink 3s infinite;
    }

    @keyframes blink {
      0%, 49%, 100% { height: 15px; }
      50%, 51% { height: 2px; }
    }

    .mouth {
      width: 40px;
      height: 20px;
      border: 2px solid #00ff88;
      border-top: none;
      border-radius: 0 0 40px 40px;
      margin: 45px auto 0;
      position: absolute;
      bottom: 10px;
      left: 50%;
      transform: translateX(-50%);
      animation: talk 0.5s infinite;
    }

    @keyframes talk {
      0%, 100% { height: 8px; }
      50% { height: 20px; }
    }

    .robot-body {
      width: 80px;
      height: 100px;
      background: linear-gradient(135deg, #00a8cc, #0088aa);
      border-radius: 10px;
      margin: 10px auto;
      box-shadow: 0 0 15px rgba(0, 212, 255, 0.4);
      border: 2px solid #87ceeb;
    }

    .robot-status {
      margin-top: 15px;
      color: #00ff88;
      font-size: 0.9em;
      text-shadow: 0 0 5px #00ff88;
    }

    .chat-section {
      flex: 1.5;
      display: flex;
      flex-direction: column;
      background: rgba(10, 22, 40, 0.6);
      border: 2px solid #00d4ff;
      border-radius: 20px;
      overflow: hidden;
      box-shadow: 0 0 30px rgba(0, 212, 255, 0.2);
    }

    .chat-header {
      background: linear-gradient(90deg, #00d4ff, #00a8cc);
      color: #001a33;
      padding: 15px;
      font-weight: bold;
      text-align: center;
      border-bottom: 2px solid #00a8cc;
    }

    .chat-messages {
      flex: 1;
      overflow-y: auto;
      padding: 15px;
      display: flex;
      flex-direction: column;
      gap: 10px;
    }

    .msg {
      padding: 12px 15px;
      border-radius: 15px;
      max-width: 80%;
      word-wrap: break-word;
      animation: slideIn 0.3s ease-out;
    }

    @keyframes slideIn {
      from { opacity: 0; transform: translateY(10px); }
      to { opacity: 1; transform: translateY(0); }
    }

    .user-msg {
      background: linear-gradient(135deg, #00d4ff, #00a8cc);
      color: #001a33;
      align-self: flex-end;
      border-bottom-right-radius: 5px;
    }

    .ai-msg {
      background: rgba(0, 212, 255, 0.2);
      color: #e0f4ff;
      border: 1px solid #00d4ff;
      border-bottom-left-radius: 5px;
      align-self: flex-start;
    }

    .chat-input-box {
      display: flex;
      gap: 10px;
      padding: 15px;
      background: rgba(0, 22, 40, 0.8);
      border-top: 2px solid #00d4ff;
    }

    #chatInput {
      flex: 1;
      padding: 10px 15px;
      background: rgba(0, 212, 255, 0.1);
      border: 1px solid #00d4ff;
      border-radius: 8px;
      color: #e0f4ff;
    }

    #chatInput::placeholder {
      color: #00a8cc;
    }

    #sendChatBtn {
      padding: 10px 25px;
      background: linear-gradient(135deg, #00d4ff, #00a8cc);
      color: #001a33;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      font-weight: bold;
      transition: all 0.3s;
    }

    #sendChatBtn:hover {
      transform: translateY(-2px);
      box-shadow: 0 0 20px rgba(0, 212, 255, 0.5);
    }

    /* ========== APK PAGE ========== */
    .apk-content {
      max-width: 1000px;
      margin: 30px auto;
      padding: 20px;
    }

    .apk-card {
      background: linear-gradient(135deg, rgba(26, 26, 26, 0.8), rgba(40, 40, 40, 0.8));
      padding: 20px;
      border-radius: 15px;
      border: 2px solid #ffdd00;
      margin: 15px 0;
      display: flex;
      justify-content: space-between;
      align-items: center;
      transition: all 0.3s;
    }

    .apk-card:hover {
      background: linear-gradient(135deg, rgba(255, 215, 0, 0.1), rgba(0, 212, 255, 0.1));
      box-shadow: 0 0 30px rgba(255, 215, 0, 0.4);
      transform: translateX(5px);
    }

    .apk-info h3 {
      color: #ffdd00;
      margin-bottom: 5px;
    }

    .apk-info p {
      color: #00d4ff;
      font-size: 0.9em;
    }

    .apk-btn {
      padding: 10px 20px;
      background: linear-gradient(135deg, #00d4ff, #00a8cc);
      color: #001a33;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      font-weight: bold;
      transition: all 0.3s;
    }

    .apk-btn:hover {
      transform: translateY(-2px);
      box-shadow: 0 0 15px rgba(0, 212, 255, 0.5);
    }

    /* ========== UPLOAD PAGE ========== */
    .upload-content {
      max-width: 600px;
      margin: 50px auto;
      background: linear-gradient(135deg, rgba(0, 212, 255, 0.1) 0%, rgba(135, 206, 235, 0.1) 100%);
      border: 2px solid #00d4ff;
      border-radius: 20px;
      padding: 40px;
      box-shadow: 0 0 30px rgba(0, 212, 255, 0.3);
    }

    .upload-content h2 {
      color: #ffdd00;
      text-shadow: 0 0 10px rgba(255, 215, 0, 0.5);
      margin-bottom: 20px;
    }

    .form-group {
      margin: 15px 0;
    }

    .form-group label {
      display: block;
      color: #00d4ff;
      margin-bottom: 8px;
      font-weight: bold;
    }

    .form-group input,
    .form-group textarea {
      width: 100%;
      padding: 12px;
      background: rgba(0, 212, 255, 0.1);
      border: 2px solid #00d4ff;
      border-radius: 8px;
      color: #e0f4ff;
      font-family: Arial;
    }

    .form-group textarea {
      resize: vertical;
      min-height: 100px;
    }

    .form-group input::placeholder,
    .form-group textarea::placeholder {
      color: #00a8cc;
    }

    .form-group input:focus,
    .form-group textarea:focus {
      outline: none;
      box-shadow: 0 0 10px rgba(0, 212, 255, 0.5);
    }

    .upload-btn {
      width: 100%;
      padding: 15px;
      background: linear-gradient(135deg, #00d4ff, #00a8cc);
      color: #001a33;
      border: none;
      border-radius: 8px;
      font-weight: bold;
      font-size: 1em;
      cursor: pointer;
      transition: all 0.3s;
      margin-top: 20px;
    }

    .upload-btn:hover {
      transform: translateY(-3px);
      box-shadow: 0 5px 20px rgba(0, 212, 255, 0.5);
    }

    /* ========== JOKE PAGE ========== */
    .joke-container {
      max-width: 600px;
      margin: 50px auto;
      background: linear-gradient(135deg, rgba(0, 212, 255, 0.1) 0%, rgba(135, 206, 235, 0.1) 100%);
      border: 2px solid #00d4ff;
      border-radius: 20px;
      padding: 40px;
      box-shadow: 0 0 30px rgba(0, 212, 255, 0.3);
      text-align: center;
    }

    .joke-container h2 {
      color: #ffdd00;
      text-shadow: 0 0 10px rgba(255, 215, 0, 0.5);
      margin-bottom: 20px;
    }

    .joke-box {
      background: rgba(0, 0, 0, 0.5);
      border: 2px solid #00d4ff;
      border-radius: 15px;
      padding: 30px;
      margin: 20px 0;
      min-height: 100px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.2em;
      color: #00d4ff;
      line-height: 1.6;
      animation: fadeIn 0.5s ease-in;
    }

    .joke-type {
      color: #ffdd00;
      font-size: 0.9em;
      margin-top: 10px;
    }

    .joke-buttons {
      display: flex;
      gap: 10px;
      margin-top: 20px;
      flex-wrap: wrap;
      justify-content: center;
    }

    .joke-btn {
      padding: 12px 25px;
      background: linear-gradient(135deg, #00d4ff, #00a8cc);
      color: #001a33;
      border: none;
      border-radius: 8px;
      cursor: pointer;
      font-weight: bold;
      transition: all 0.3s;
    }

    .joke-btn:hover {
      transform: translateY(-2px);
      box-shadow: 0 0 20px rgba(0, 212, 255, 0.5);
    }

    /* ========== FOOTER ========== */
    footer {
      text-align: center;
      background: linear-gradient(90deg, #000, #111, #000);
      padding: 15px;
      border-top: 2px solid rgba(255, 215, 0, 0.2);
      color: #888;
      margin-top: 30px;
      cursor: pointer;
      transition: all 0.3s;
    }

    footer:hover {
      background: linear-gradient(90deg, rgba(255, 215, 0, 0.1), rgba(0, 212, 255, 0.1), rgba(255, 215, 0, 0.1));
      color: #ffdd00;
    }

    /* ========== RESPONSIVE ========== */
    @media (max-width: 768px) {
      .ai-container {
        flex-direction: column;
        height: auto;
      }

      nav {
        flex-direction: column;
        align-items: center;
      }

      nav button {
        width: 90%;
      }

      .apk-card {
        flex-direction: column;
        text-align: center;
        gap: 15px;
      }

      .chat-messages::-webkit-scrollbar {
        width: 6px;
      }

      .chat-messages::-webkit-scrollbar-track {
        background: rgba(0, 212, 255, 0.1);
      }

      .chat-messages::-webkit-scrollbar-thumb {
        background: #00d4ff;
        border-radius: 3px;
      }
    }
  </style>
</head>
<body>

<!-- HEADER -->
<header>
  <div class="logo-container">
    <div class="logo">⚡MX</div>
  </div>
  <h1>MANTELIGENT MAX WEB</h1>
  <p>AI Learning Platform & APK Store</p>
</header>

<!-- NAVIGATION -->
<nav>
  <button onclick="showPage('home')">🏠 Home</button>
  <button onclick="showPage('ai')">🤖 AI Chat</button>
  <button onclick="showPage('apk')">📱 APK Store</button>
  <button onclick="showPage('upload')">📤 Upload</button>
  <button onclick="showPage('jokes')">😂 Jokes</button>
</nav>

<!-- ========== HOME PAGE ========== -->
<div id="home" class="page active">
  <div class="home-content">
    <div class="card" onclick="showPage('ai')">
      <div class="card-icon">🤖</div>
      <h2>AI Chat</h2>
      <p>Learn with intelligent AI assistant</p>
    </div>

    <div class="card" onclick="showPage('apk')">
      <div class="card-icon">📱</div>
      <h2>APK Store</h2>
      <p>Download apps from our store</p>
    </div>

    <div class="card" onclick="showPage('upload')">
      <div class="card-icon">📤</div>
      <h2>Upload APK</h2>
      <p>Share your APK with us</p>
    </div>

    <div class="card" onclick="showPage('jokes')">
      <div class="card-icon">😂</div>
      <h2>Joke Generator</h2>
      <p>Get random funny jokes</p>
    </div>
  </div>
</div>

<!-- ========== AI PAGE ========== -->
<div id="ai" class="page">
  <div class="ai-container">
    <div class="robot-section">
      <div class="robot">
        <div class="robot-head">
          <div class="robot-eyes">
            <div class="eye"></div>
            <div class="eye"></div>
          </div>
          <div class="mouth"></div>
        </div>
        <div class="robot-body"></div>
      </div>
      <div class="robot-status" id="aiStatus">🟢 READY</div>
    </div>

    <div class="chat-section">
      <div class="chat-header">MX AI Chat</div>
      <div class="chat-messages" id="chatBox"></div>
      <div class="chat-input-box">
        <input id="chatInput" placeholder="Ask me anything...">
        <button id="sendChatBtn" onclick="sendChat()">Send</button>
      </div>
    </div>
  </div>
</div>

<!-- ========== APK PAGE ========== -->
<div id="apk" class="page">
  <div class="apk-content">
    <h1 style="color: #ffdd00; text-align: center; text-shadow: 0 0 10px rgba(255, 215, 0, 0.5); margin-bottom: 30px;">📱 MX APK Store</h1>

    <div class="apk-card">
      <div class="apk-info">
        <h3>Demo App</h3>
        <p>Example application for testing</p>
      </div>
      <button class="apk-btn" onclick="alert('Download started!')">Download</button>
    </div>

    <div class="apk-card">
      <div class="apk-info">
        <h3>Learning Tool</h3>
        <p>Learn coding on the go</p>
      </div>
      <button class="apk-btn" onclick="alert('Download started!')">Download</button>
    </div>

    <div class="apk-card">
      <div class="apk-info">
        <h3>Quiz Master</h3>
        <p>Test your programming knowledge</p>
      </div>
      <button class="apk-btn" onclick="alert('Download started!')">Download</button>
    </div>
  </div>
</div>

<!-- ========== UPLOAD PAGE ========== -->
<div id="upload" class="page">
  <div class="upload-content">
    <h2>📤 Upload Your APK</h2>

    <div class="form-group">
      <label>App Name</label>
      <input type="text" placeholder="Enter app name" id="appName">
    </div>

    <div class="form-group">
      <label>Description</label>
      <textarea placeholder="Describe your app..." id="appDesc"></textarea>
    </div>

    <div class="form-group">
      <label>Google Drive Link</label>
      <input type="text" placeholder="Paste Google Drive link" id="appLink">
    </div>

    <button class="upload-btn" onclick="submitUpload()">✓ Submit</button>
  </div>
</div>

<!-- ========== JOKE PAGE ========== -->
<div id="jokes" class="page">
  <div class="joke-container">
    <h2>😂 Random Joke Generator</h2>

    <div class="joke-box" id="jokeBox">
      Click "Get Joke" to start! 🚀
    </div>

    <div class="joke-type" id="jokeType"></div>

    <div class="joke-buttons">
      <button class="joke-btn" onclick="getJoke()">📢 Get Joke</button>
      <button class="joke-btn" onclick="shareJoke()">📤 Share</button>
      <button class="joke-btn" onclick="copyJoke()">📋 Copy</button>
    </div>
  </div>
</div>

<!-- FOOTER -->
<footer onclick="showPage('home')">
  © 2026 MX Web - All Rights Reserved | Click to go home
</footer>

<script>
  // PAGE NAVIGATION
  function showPage(pageName) {
    const pages = document.querySelectorAll('.page');
    pages.forEach(page => page.classList.remove('active'));
    document.getElementById(pageName).classList.add('active');
  }

  // ========== AI CHAT ========== 
  let chatCount = 0;
  const chatBox = document.getElementById('chatBox');
  const aiStatus = document.getElementById('aiStatus');
  const mouth = document.querySelector('.mouth');

  async function sendChat() {
    const msg = document.getElementById('chatInput').value.trim();
    if (!msg) return;

    // User message
    let userMsg = document.createElement('div');
    userMsg.className = 'msg user-msg';
    userMsg.innerText = msg;
    chatBox.appendChild(userMsg);
    document.getElementById('chatInput').value = '';

    // AI thinking
    aiStatus.innerText = '🟡 THINKING...';
    mouth.style.animation = 'talk 0.3s infinite';

    let aiMsg = document.createElement('div');
    aiMsg.className = 'msg ai-msg';
    aiMsg.innerText = '⏳ Processing...';
    chatBox.appendChild(aiMsg);
    chatBox.scrollTop = chatBox.scrollHeight;

    try {
      const res = await fetch('https://official-joke-api.appspot.com/random_joke');
      const data = await res.json();
      aiMsg.innerText = data.setup + '\n\n' + data.punchline;
    } catch (e) {
      aiMsg.innerText = '❌ Connection error. Please try again.';
    }

    aiStatus.innerText = '🟢 READY';
    mouth.style.animation = 'talk 4s infinite';
    chatBox.scrollTop = chatBox.scrollHeight;
  }

  document.getElementById('chatInput').addEventListener('keypress', (e) => {
    if (e.key === 'Enter') sendChat();
  });

  // ========== UPLOAD FORM ==========
  function submitUpload() {
    const appName = document.getElementById('appName').value.trim();
    const appDesc = document.getElementById('appDesc').value.trim();
    const appLink = document.getElementById('appLink').value.trim();

    if (!appName || !appDesc || !appLink) {
      alert('❌ Please fill all fields!');
      return;
    }

    alert(`✅ Upload submitted!\n\nApp: ${appName}\nLink: ${appLink}`);
    
    // Reset form
    document.getElementById('appName').value = '';
    document.getElementById('appDesc').value = '';
    document.getElementById('appLink').value = '';
  }

  // ========== JOKE GENERATOR ==========
  let currentJoke = '';
  const jokeBox = document.getElementById('jokeBox');
  const jokeType = document.getElementById('jokeType');

  async function getJoke() {
    jokeBox.innerText = '⏳ Getting joke...';
    jokeType.innerText = '';

    try {
      const res = await fetch('https://official-joke-api.appspot.com/random_joke');
      const data = await res.json();

      currentJoke = `${data.setup}\n\n${data.punchline}`;
      jokeBox.innerText = currentJoke;
      jokeType.innerText = '📝 Setup & Punchline';
    } catch (e) {
      jokeBox.innerText = '❌ Failed to load joke';
    }
  }

  function copyJoke() {
    if (!currentJoke) {
      alert('Get a joke first!');
      return;
    }
    navigator.clipboard.writeText(currentJoke);
    alert('✅ Joke copied!');
  }

  function shareJoke() {
    if (!currentJoke) {
      alert('Get a joke first!');
      return;
    }
    navigator.clipboard.writeText(currentJoke);
    alert('✅ Joke copied! Share it manually.');
  }

  // Load joke on page load
  window.onload = () => {
    getJoke();
  };
</script>

</body>
</html>
