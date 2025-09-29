<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>ابرامو - ألغاز مغربية</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <!-- الشريط العلوي -->
  <div class="header">
    <div class="header-left">مرحبا بكم في لعبة ألغاز مغربية سهلة</div>
    <div class="header-right">مرحبا عندي في إنستغرام: <strong>lhaj_abramou</strong></div>
  </div>

  <!-- الشاشة الرئيسية -->
  <div class="container" id="homeScreen">
    <h1>ابرامو</h1>
    <p>ألغاز مغربية تختبر معرفتك بتاريخ المغرب، تراثه، وأسراره!</p>
    
    <button class="btn" id="startBtn">بداية المغامرة</button>
  </div>

  <!-- شاشة اللعبة -->
  <div class="container game-screen" id="gameScreen">
    <div class="scoreboard">
      <div>النقاط: <span id="score">0</span></div>
      <div>المستوى: <span id="level">1</span></div>
    </div>
    <h1>العب الآن مع ابرامو وألغاز مغربية</h1>
    <div class="question" id="question"></div>
    <div class="options" id="options"></div>
  </div>

  <!-- رسالة النتيجة -->
  <div class="message" id="message">
    <div class="message-text" id="messageText"></div>
    <button class="btn" id="nextBtn">السؤال التالي</button>
  </div>

  <!-- الشريط السفلي -->
  <div class="footer">
    <button class="footer-btn" id="settingsBtn">الإعدادات</button>
    <button class="footer-btn" id="photoBtn">الصورة</button>
    <button class="footer-btn" id="shareBtn">مشاركة النتيجة</button>
    <button class="footer-btn" id="restartBtn">العودة من الأول</button>
    <button class="footer-btn" id="exitBtn">الخروج من اللعبة</button>
  </div>

  <!-- الصوتيات (مخفي) -->
  <audio id="winSound" preload="auto"></audio>
  <audio id="loseSound" preload="auto"></audio>

  <script src="script.js"></script>
</body>
</html>
