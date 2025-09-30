<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no"/>
  <title>لُغْز – ألغاز مغربية</title>
  <link rel="icon" href="data:image/svg+xml,<svg xmlns=%22http://www.w3.org/2000/svg%22 viewBox=%220 0 100 100%22><text y=%22.9em%22 font-size=%2290%22 fill=%22gold%22>🧩</text></svg>">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      -webkit-tap-highlight-color: transparent;
      font-family: 'Tajawal', 'Segoe UI', sans-serif;
    }
    body {
      background: linear-gradient(135deg, #0c1427, #1a2332);
      color: #f8f9fa;
      min-height: 100vh;
      overflow: hidden;
      position: relative;
    }
    body::before {
      content: "";
      position: absolute;
      top: 0; left: 0; right: 0; bottom: 0;
      background-image: 
        radial-gradient(circle at 10% 20%, rgba(139, 0, 0, 0.03) 0%, transparent 20%),
        radial-gradient(circle at 90% 80%, rgba(76, 175, 80, 0.03) 0%, transparent 20%);
      pointer-events: none;
    }

    .screen {
      display: none;
      padding: 20px;
      max-width: 500px;
      margin: 0 auto;
      height: 100vh;
      overflow-y: auto;
      position: relative;
    }
    .screen.active {
      display: block;
      animation: fadeIn 0.4s ease;
    }
    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(12px); }
      to { opacity: 1; transform: translateY(0); }
    }

    /* الشاشة الرئيسية */
    .home {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      height: 100%;
      text-align: center;
    }
    .home h1 {
      font-size: 2.6em;
      margin: 20px 0;
      color: #FFD700;
      text-shadow: 0 0 12px rgba(255, 215, 0, 0.6);
      font-weight: 800;
      letter-spacing: -0.5px;
    }
    .home p {
      margin: 15px 0;
      line-height: 1.6;
      color: #d1d5db;
      max-width: 90%;
    }
    .btn {
      display: block;
      width: 85%;
      margin: 16px auto;
      padding: 16px;
      font-size: 1.25em;
      background: linear-gradient(to right, #b21f1f, #d32f2f);
      color: white;
      border: none;
      border-radius: 14px;
      cursor: pointer;
      font-weight: bold;
      box-shadow: 0 4px 14px rgba(0,0,0,0.35);
      transition: all 0.2s;
      position: relative;
      overflow: hidden;
    }
    .btn::after {
      content: '';
      position: absolute;
      top: 0; left: 0;
      width: 100%; height: 100%;
      background: rgba(255,255,255,0.1);
      opacity: 0;
      transition: opacity 0.2s;
    }
    .btn:active::after {
      opacity: 1;
    }
    .music-btn {
      background: linear-gradient(to right, #1b5e20, #388e3c);
    }
    .high-score {
      text-align: center;
      margin: 25px 0;
      font-size: 1.2em;
      color: #4CAF50;
      font-weight: bold;
      background: rgba(0,0,0,0.2);
      padding: 10px 20px;
      border-radius: 12px;
      width: 85%;
    }
    .instagram {
      margin-top: 20px;
      color: #FFD700;
      font-size: 1.1em;
    }
    .instagram a {
      color: #FFD700;
      text-decoration: underline;
    }

    /* شاشة اللعب */
    .game-header {
      display: flex;
      justify-content: space-between;
      background: rgba(0,0,0,0.35);
      padding: 14px;
      border-radius: 14px;
      margin-bottom: 22px;
      font-weight: bold;
      box-shadow: 0 2px 8px rgba(0,0,0,0.2);
    }
    .progress-bar {
      height: 8px;
      background: rgba(255,255,255,0.1);
      border-radius: 4px;
      margin: 15px 0;
      overflow: hidden;
    }
    .progress-fill {
      height: 100%;
      background: linear-gradient(to right, #FFD700, #FF8C00);
      width: 0%;
      transition: width 0.4s ease;
    }
    .city-title {
      font-size: 1.5em;
      color: #FFD700;
      text-align: center;
      margin: 15px 0;
      font-weight: 700;
    }
    .riddle-box {
      background: rgba(15, 23, 42, 0.75);
      padding: 22px;
      border-radius: 16px;
      margin: 20px 0;
      line-height: 1.7;
      font-size: 1.25em;
      border: 1px solid rgba(255, 215, 0, 0.25);
      box-shadow: 0 4px 12px rgba(0,0,0,0.2);
    }

    /* === تعديل رئيسي: شبكة الخيارات 2x2 === */
    #options-grid {
      display: grid;
      grid-template-columns: repeat(2, 1fr);
      gap: 12px;
      margin: 20px 0;
    }
    .option {
      padding: 14px;
      background: rgba(20, 28, 50, 0.85);
      color: white;
      border: 1px solid rgba(255, 215, 0, 0.3);
      border-radius: 12px;
      text-align: center;
      cursor: pointer;
      transition: all 0.25s;
      font-size: 1.1em;
      box-shadow: 0 2px 6px rgba(0,0,0,0.15);
    }
    .option:hover {
      transform: scale(1.03);
      border-color: #FFD700;
      background: rgba(30, 40, 70, 0.95);
    }
    .option.correct {
      background: rgba(76, 175, 80, 0.3);
      border-color: #4CAF50;
      color: #E8F5E9;
    }
    .option.wrong {
      background: rgba(244, 67, 54, 0.25);
      border-color: #f44336;
      color: #FFEBEE;
    }

    #hintBtn {
      display: block;
      width: 70%;
      margin: 20px auto 10px;
      padding: 12px;
      background: linear-gradient(to right, #1b5e20, #388e3c);
      color: white;
      border: none;
      border-radius: 12px;
      cursor: pointer;
      font-weight: bold;
      box-shadow: 0 3px 8px rgba(0,0,0,0.25);
    }
    #hintText {
      margin: 15px 0;
      padding: 14px;
      background: rgba(0,0,0,0.4);
      border-radius: 12px;
      color: #FFD700;
      display: none;
      font-style: italic;
      line-height: 1.6;
    }

    /* شاشة النهاية */
    .win-screen {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      height: 100%;
      text-align: center;
      padding: 20px;
    }
    .win-screen h2 {
      color: #4CAF50;
      font-size: 2.2em;
      margin: 20px 0;
      text-shadow: 0 0 10px rgba(76, 175, 80, 0.4);
    }
    .final-score {
      font-size: 1.8em;
      margin: 20px 0;
      color: #FFD700;
      font-weight: bold;
    }
    .stats-detail {
      background: rgba(0,0,0,0.3);
      padding: 15px;
      border-radius: 14px;
      margin: 20px 0;
      width: 90%;
      line-height: 1.6;
    }
    .small-btn {
      background: rgba(255,255,255,0.12);
      color: white;
      border: 1px solid #FFD700;
      padding: 10px 20px;
      border-radius: 12px;
      font-size: 1em;
      margin-top: 15px;
      cursor: pointer;
      transition: all 0.2s;
    }

    .darja-message {
      font-size: 1.3em;
      font-weight: bold;
      margin: 15px 0;
      padding: 12px;
      border-radius: 10px;
      text-align: center;
      animation: bounce 0.6s;
    }
    @keyframes bounce {
      0%, 20%, 50%, 80%, 100% {transform: translateY(0);}
      40% {transform: translateY(-10px);}
      60% {transform: translateY(-5px);}
    }
  </style>
</head>
<body>

  <!-- الشاشة الرئيسية -->
  <div id="home" class="screen active">
    <div class="home">
      <h1>لُغْز</h1>
      <p>100 لغز مغربي – من التراث، بالدارجة، وواعر بزاف!</p>
      <div class="high-score" id="highScoreDisplay">أعلى نتيجة: 0</div>
      
      <button class="btn music-btn" onclick="startMusic()">🎵 شغّل الموسيقى التقليدية</button>
      
      <button class="btn" onclick="startGame()">ابدأ التحدي</button>
      <button class="btn" style="background:linear-gradient(to right, #5c6bc0, #3949ab);" onclick="showInstructions()">كيف تلعب؟</button>
      
      <div class="instagram">
        مطور اللعبة: <a href="https://www.instagram.com/lhaj_abramou" target="_blank">@lhaj_abramou</a>
      </div>
    </div>
  </div>

  <!-- التعليمات -->
  <div id="instructions" class="screen">
    <h2 style="text-align:center; color:#FFD700; margin:25px 0; font-size:1.8em;">كيف تلعب؟</h2>
    <div style="background:rgba(0,0,0,0.3); padding:20px; border-radius:16px; margin:20px;">
      <p style="margin:15px 0; line-height:1.8; font-size:1.1em;">
        📍 كل سؤال مرتبط بمدينة أو تراث مغربي.<br>
        ✅ اختر الجواب الصحيح من 4 خيارات.<br>
        💡 زر "تلميح؟" يعطيك تلميح (-100 نقطة).<br>
        🏆 جواب صحيح بدون تلميح = <strong>200 نقطة</strong>.<br>
        🥈 جواب صحيح مع تلميح = <strong>100 نقطة</strong>.<br>
        🎵 الموسيقى غادي تشتغل من بعد ما تضغط على زر التشغيل!
      </p>
    </div>
    <button class="btn" onclick="goHome()">العودة</button>
  </div>

  <!-- شاشة اللعب -->
  <div id="game" class="screen">
    <div class="game-header">
      <div>النقاط: <span id="score">0</span></div>
      <div><span id="questionNum">1</span>/100</div>
    </div>
    <div class="progress-bar">
      <div class="progress-fill" id="progressFill"></div>
    </div>
    <div class="city-title" id="cityTitle">📍 فاس</div>
    <div class="riddle-box" id="riddleBox">
      شي واحد كيطلع من الدار، ما كيهدرش، ولكن كيخليك تهدر... شكونا؟
    </div>
    
    <!-- الخيارات في شبكة 2x2 -->
    <div id="options-grid"></div>
    
    <button id="hintBtn" onclick="showHint()">تلميح؟ (-100 نقطة)</button>
    <div id="hintText"></div>
    <div id="darjaFeedback"></div>
  </div>

  <!-- شاشة النهاية -->
  <div id="win" class="screen">
    <div class="win-screen">
      <h2>🎉 مبروك!</h2>
      <div class="final-score">مجموع نقاطك: <span id="finalScore">0</span></div>
      <div class="stats-detail">
        <div>عدد الأسئلة: 100</div>
        <div>أعلى نتيجة: <span id="recordScore">0</span></div>
        <div id="recordMsg" style="color:#4CAF50; margin-top:8px;"></div>
      </div>
      <div style="margin:15px; color:#FFD700;">
        اللعبة من تطوير: <a href="https://www.instagram.com/lhaj_abramou" target="_blank">@lhaj_abramou</a>
      </div>
      <button class="btn" onclick="restartGame()">لعب من جديد</button>
      <button class="small-btn" onclick="goHome()">الشاشة الرئيسية</button>
    </div>
  </div>

  <script>
    // =============== تشغيل الموسيقى ===============
    let bgMusic = null;
    function startMusic() {
      if (!bgMusic) {
        bgMusic = new Audio("audio/mpeg;base64,SUQzBAAAAAABEVRYWFgAAAAtAAADY29tbWVudABCaWdTb3VuZEJhbmsuY29tIC8gTGFTb25vdGhlcXVlLm9yZwBURU5DAAAAHQAAA1N3aXRjaCBQbHVzIMKpIE5DSCBTb2Z0d2FyZQBUSVQyAAAABgAAAzIyMzUAVFNTRQAAAA8AAANMYXZmNTcuODMuMTAwAAAAAAAAAAAAAAD/80DEAAAAA0gAAAAATEFNRTMuMTAwVVVVVVVVVVVVVUxBTUUzLjEwMFVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVf/zQsRbAAADSAAAAABVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVf/zQMSkAAADSAAAAABVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV");
        bgMusic.loop = true;
        bgMusic.volume = 0.3;
      }
      bgMusic.play().then(() => {
        alert("✅ الموسيقى شغالة! استمتع باللعبة 🎶");
      }).catch(e => {
        alert("❌ ماقدرش نشغل الموسيقى. جرب تضغط مرة أخرى.");
      });
    }

    // =============== دالة خلط المصفوفة ===============
    function shuffleArray(array) {
      const newArray = [...array];
      for (let i = newArray.length - 1; i > 0; i--) {
        const j = Math.floor(Math.random() * (i + 1));
        [newArray[i], newArray[j]] = [newArray[j], newArray[i]];
      }
      return newArray;
    }

    // =============== 100 سؤال مغربي ===============
const puzzles = [
  { city: "فاس", q: "شي واحد كيطلع من الدار، ما كيهدرش، ولكن كيخليك تهدر... شكونا؟", options: ["الباب", "الحائط", "النافذة", "السقف"], answer: 0, hint: "شي حاجة كتكون فـ\"الحوش\" وكيقرع عليها الناس." },
  { city: "مراكش", q: "عندك 9 قطع نقود، وحدة مزيفة وأخف من الباقية. وعندك ميزان ذو كفتين، وحقك زْنْتين فقط. كيفاش غادي تعرف القطعة المزيفة؟", options: ["تقسمهم لـ 3 مجموعات", "تزْن كل واحد لواحده", "تضربهم فبعض", "تلقاهم فالميزان"], answer: 0, hint: "الحل فـالرياضيات: 3 مجموعات متساوية." },
  { city: "شفشاون", q: "كيما تمشي فـ\"الحومة\"، تشوف شي واحد كيضرب راسو على الحيط... وكيقول: \"واخا! نسيت شي واحد!\" شكون اللي نسي؟", options: ["راسو", "دارو", "فلوسو", "حذاءو"], answer: 0, hint: "الشي اللي كيضرب بيه الحيط هو نفسه اللي نسيه!" },
  { city: "الصويرة", q: "شي حاجة كتلقاها فـ\"الدابا\"، ولكن ما كتشريهاش... وإذا بغيتي تخدم بيها، خاصك تدفع... شكونا؟", options: ["المية", "الخبز", "الحليب", "الشاي"], answer: 0, hint: "شي حاجة ضرورية فـالدابا، ولكن ماشي للبيع." },
  { city: "طنجة", q: "شي واحد كيقول: \"أنا ماشي شي واحد، ولكن أنا كتجمع بزاف!\" شكونا؟", options: ["السوق", "المسجد", "الدار", "الحومة"], answer: 0, hint: "مكان كيجمع ناس بزاف فـوقت واحد." },
  { city: "الرباط", q: "شي حاجة كتكون فـ\"الدار\" و\"الحومة\" و\"المسجد\"... وكل واحد كيستخدمها، ولكن ما كيهدرش... شكونا؟", options: ["الباب", "السقف", "الحائط", "الدرج"], answer: 0, hint: "شي حاجة كتفتح وتقفل." },
  { city: "أكادير", q: "شي واحد كيطلع من الرمال، ويقدر يخليك تطير... شكونا؟", options: ["الريح", "النخيل", "السمك", "الحصان"], answer: 0, hint: "شي حاجة ما كتشافش، ولكن كتحس بيها." },
  { city: "وجدة", q: "شي حاجة كتكون فـالدار، ولكن كتلقاها فـالسوق... شكونا؟", options: ["الخبز", "الباب", "السقف", "الحائط"], answer: 0, hint: "شي حاجة كتاكلها كل يوم." },
  { city: "الدار البيضاء", q: "شي واحد كيقول: \"أنا كخدم للجميع، ولكن ما كيهدرش\"... شكونا؟", options: ["الباب", "الهاتف", "الراديو", "التلفاز"], answer: 0, hint: "شي حاجة كتفتح وتقفل." },
  { city: "مكناس", q: "شي حاجة كتلقاها فـالمسجد، ولكن ما كتشريهاش... شكونا؟", options: ["السجادة", "الحذاء", "الكتاب", "الساعة"], answer: 0, hint: "شي حاجة كتصلي عليها." },
  { city: "تطوان", q: "شي واحد كيكون فـالدار، ولكن كيخرج برا... شكونا؟", options: ["الدخان", "الباب", "النافذة", "الضوء"], answer: 0, hint: "شي حاجة كيطلع من المطبخ." },
  { city: "تارودانت", q: "شي حاجة كتكون فـالسوق، ولكن ما كتشريهاش... شكونا؟", options: ["الوقت", "الخبز", "الحليب", "الشاي"], answer: 0, hint: "شي ما كيتباعش، ولكن كيضيع." },
  { city: "العيون", q: "شي واحد كيقول: \"أنا كمشي، ولكن ما كتنقلش\"... شكونا؟", options: ["الساعة", "الحصان", "السيارة", "الطائرة"], answer: 0, hint: "شي حاجة كتلقاها فـالحائط." },
  { city: "الخميسات", q: "شي حاجة كتكون فـالدار، ولكن كتلقاها فـالحقل... شكونا؟", options: ["النملة", "الباب", "السقف", "الحائط"], answer: 0, hint: "حيوان صغير كيدوز فـالدار." },
  { city: "بني ملال", q: "شي واحد كيطلع من الأرض، ويقدر يخليك تهدر... شكونا؟", options: ["الهاتف", "النخيل", "السمك", "الحصان"], answer: 0, hint: "شي حاجة كتصل بيها الناس." },
  { city: "آسفي", q: "شي حاجة كتكون فـالبحر، ولكن كتاكلها فـالدار... شكونا؟", options: ["السمك", "المية", "الرمال", "الحصان"], answer: 0, hint: "أكلة تقليدية مغربية." },
  { city: "الحسيمة", q: "شي واحد كيقول: \"أنا كخدم، ولكن ما كيهدرش\"... شكونا؟", options: ["الراديو", "الهاتف", "الباب", "التلفاز"], answer: 0, hint: "شي حاجة كتفتح وتقفل." },
  { city: "تازة", q: "شي حاجة كتكون فـالمسجد، ولكن كتلقاها فـالدار... شكونا؟", options: ["السجادة", "الحذاء", "الكتاب", "الساعة"], answer: 0, hint: "شي حاجة كتصلي عليها." },
  { city: "خريبكة", q: "شي واحد كيطلع من الجبل، ويقدر يخليك تطير... شكونا؟", options: ["الريح", "النخيل", "السمك", "الحصان"], answer: 0, hint: "شي حاجة ما كتشافش، ولكن كتحس بيها." },
  { city: "سطات", q: "شي حاجة كتكون فـالدار، ولكن كتلقاها فـالسوق... شكونا؟", options: ["الخبز", "الباب", "السقف", "الحائط"], answer: 0, hint: "شي حاجة كتاكلها كل يوم." },
  { city: "فاس", q: "شي واحد كيقول: \"أنا ماشي شي واحد، ولكن أنا كتجمع بزاف!\" شكونا؟", options: ["السوق", "المسجد", "الدار", "الحومة"], answer: 0, hint: "مكان كيجمع ناس بزاف فـوقت واحد." },
  { city: "مراكش", q: "شي حاجة كتكون فـالدار، ولكن كتلقاها فـالحومة... شكونا؟", options: ["الضحك", "الباب", "السقف", "الحائط"], answer: 0, hint: "شي حاجة كتسمعها من الجيران." },
  { city: "شفشاون", q: "شي واحد كيطلع من الدار، ما كيهدرش، ولكن كيخليك تهدر... شكونا؟", options: ["الباب", "الحائط", "النافذة", "السقف"], answer: 0, hint: "شي حاجة كتكون فـ\"الحوش\" وكيقرع عليها الناس." },
  { city: "الصويرة", q: "شي حاجة كتلقاها فـ\"الدابا\"، ولكن ما كتشريهاش... شكونا؟", options: ["المية", "الخبز", "الحليب", "الشاي"], answer: 0, hint: "شي حاجة ضرورية فـالدابا، ولكن ماشي للبيع." },
  { city: "طنجة", q: "شي واحد كيقول: \"أنا كخدم للجميع، ولكن ما كيهدرش\"... شكونا؟", options: ["الباب", "الهاتف", "الراديو", "التلفاز"], answer: 0, hint: "شي حاجة كتفتح وتقفل." },
  { city: "الرباط", q: "شي حاجة كتكون فـ\"الدار\" و\"الحومة\" و\"المسجد\"... وكل واحد كيستخدمها، ولكن ما كيهدرش... شكونا؟", options: ["الباب", "السقف", "الحائط", "الدرج"], answer: 0, hint: "شي حاجة كتفتح وتقفل." },
  { city: "أكادير", q: "شي واحد كيطلع من الرمال، ويقدر يخليك تطير... شكونا؟", options: ["الريح", "النخيل", "السمك", "الحصان"], answer: 0, hint: "شي حاجة ما كتشافش، ولكن كتحس بيها." },
  { city: "وجدة", q: "شي حاجة كتكون فـالدار، ولكن كتلقاها فـالسوق... شكونا؟", options: ["الخبز", "الباب", "السقف", "الحائط"], answer: 0, hint: "شي حاجة كتاكلها كل يوم." },
  { city: "الدار البيضاء", q: "شي واحد كيقول: \"أنا ماشي شي واحد، ولكن أنا كتجمع بزاف!\" شكونا؟", options: ["السوق", "المسجد", "الدار", "الحومة"], answer: 0, hint: "مكان كيجمع ناس بزاف فـوقت واحد." },
  { city: "مكناس", q: "شي حاجة كتلقاها فـالمسجد، ولكن ما كتشريهاش... شكونا؟", options: ["السجادة", "الحذاء", "الكتاب", "الساعة"], answer: 0, hint: "شي حاجة كتصلي عليها." },
  { city: "تطوان", q: "شي واحد كيكون فـالدار، ولكن كيخرج برا... شكونا؟", options: ["الدخان", "الباب", "النافذة", "الضوء"], answer: 0, hint: "شي حاجة كيطلع من المطبخ." },
  { city: "تارودانت", q: "شي حاجة كتكون فـالسوق، ولكن ما كتشريهاش... شكونا؟", options: ["الوقت", "الخبز", "الحليب", "الشاي"], answer: 0, hint: "شي ما كيتباعش، ولكن كيضيع." },
  { city: "العيون", q: "شي واحد كيقول: \"أنا كمشي، ولكن ما كتنقلش\"... شكونا؟", options: ["الساعة", "الحصان", "السيارة", "الطائرة"], answer: 0, hint: "شي حاجة كتلقاها فـالحائط." },
  { city: "الخميسات", q: "شي حاجة كتكون فـالدار، ولكن كتلقاها فـالحقل... شكونا؟", options: ["النملة", "الباب", "السقف", "الحائط"], answer: 0, hint: "حيوان صغير كيدوز فـالدار." },
  { city: "بني ملال", q: "شي واحد كيطلع من الأرض، ويقدر يخليك تهدر... شكونا؟", options: ["الهاتف", "النخيل", "السمك", "الحصان"], answer: 0, hint: "شي حاجة كتصل بيها الناس." },
  { city: "آسفي", q: "شي حاجة كتكون فـالبحر، ولكن كتاكلها فـالدار... شكونا؟", options: ["السمك", "المية", "الرمال", "الحصان"], answer: 0, hint: "أكلة تقليدية مغربية." },
  { city: "الحسيمة", q: "شي واحد كيقول: \"أنا كخدم، ولكن ما كيهدرش\"... شكونا؟", options: ["الراديو", "الهاتف", "الباب", "التلفاز"], answer: 0, hint: "شي حاجة كتفتح وتقفل." },
  { city: "تازة", q: "شي حاجة كتكون فـالمسجد، ولكن كتلقاها فـالدار... شكونا؟", options: ["السجادة", "الحذاء", "الكتاب", "الساعة"], answer: 0, hint: "شي حاجة كتصلي عليها." },
  { city: "خريبكة", q: "شي واحد كيطلع من الجبل، ويقدر يخليك تطير... شكونا؟", options: ["الريح", "النخيل", "السمك", "الحصان"], answer: 0, hint: "شي حاجة ما كتشافش، ولكن كتحس بيها." },
  { city: "سطات", q: "شي حاجة كتكون فـالدار، ولكن كتلقاها فـالسوق... شكونا؟", options: ["الخبز", "الباب", "السقف", "الحائط"], answer: 0, hint: "شي حاجة كتاكلها كل يوم." },
  { city: "فاس", q: "شي واحد كيقول: \"أنا كخدم للجميع، ولكن ما كيهدرش\"... شكونا؟", options: ["الباب", "الهاتف", "الراديو", "التلفاز"], answer: 0, hint: "شي حاجة كتفتح وتقفل." },
  { city: "مراكش", q: "شي حاجة كتكون فـالدار، ولكن كتلقاها فـالحومة... شكونا؟", options: ["الضحك", "الباب", "السقف", "الحائط"], answer: 0, hint: "شي حاجة كتسمعها من الجيران." },
  { city: "شفشاون", q: "شي واحد كيطلع من الدار، ما كيهدرش، ولكن كيخليك تهدر... شكونا؟", options: ["الباب", "الحائط", "النافذة", "السقف"], answer: 0, hint: "شي حاجة كتكون فـ\"الحوش\" وكيقرع عليها الناس." },
  { city: "الصويرة", q: "شي حاجة كتلقاها فـ\"الدابا\"، ولكن ما كتشريهاش... شكونا؟", options: ["المية", "الخبز", "الحليب", "الشاي"], answer: 0, hint: "شي حاجة ضرورية فـالدابا، ولكن ماشي للبيع." },
  { city: "طنجة", q: "شي واحد كيقول: \"أنا ماشي شي واحد، ولكن أنا كتجمع بزاف!\" شكونا؟", options: ["السوق", "المسجد", "الدار", "الحومة"], answer: 0, hint: "مكان كيجمع ناس بزاف فـوقت واحد." },
  { city: "الرباط", q: "شي حاجة كتكون فـ\"الدار\" و\"الحومة\" و\"المسجد\"... وكل واحد كيستخدمها، ولكن ما كيهدرش... شكونا؟", options: ["الباب", "السقف", "الحائط", "الدرج"], answer: 0, hint: "شي حاجة كتفتح وتقفل." },
  { city: "أكادير", q: "شي واحد كيطلع من الرمال، ويقدر يخليك تطير... شكونا؟", options: ["الريح", "النخيل", "السمك", "الحصان"], answer: 0, hint: "شي حاجة ما كتشافش، ولكن كتحس بيها." },
  { city: "وجدة", q: "شي حاجة كتكون فـالدار، ولكن كتلقاها فـالسوق... شكونا؟", options: ["الخبز", "الباب", "السقف", "الحائط"], answer: 0, hint: "شي حاجة كتاكلها كل يوم." },
  { city: "الدار البيضاء", q: "شي واحد كيقول: \"أنا كخدم للجميع، ولكن ما كيهدرش\"... شكونا؟", options: ["الباب", "الهاتف", "الراديو", "التلفاز"], answer: 0, hint: "شي حاجة كتفتح وتقفل." },
  { city: "مكناس", q: "شي حاجة كتلقاها فـالمسجد، ولكن ما كتشريهاش... شكونا؟", options: ["السجادة", "الحذاء", "الكتاب", "الساعة"], answer: 0, hint: "شي حاجة كتصلي عليها." },
  { city: "تطوان", q: "شي واحد كيكون فـالدار، ولكن كيخرج برا... شكونا؟", options: ["الدخان", "الباب", "النافذة", "الضوء"], answer: 0, hint: "شي حاجة كيطلع من المطبخ." },
  { city: "تارودانت", q: "شي حاجة كتكون فـالسوق، ولكن ما كتشريهاش... شكونا؟", options: ["الوقت", "الخبز", "الحليب", "الشاي"], answer: 0, hint: "شي ما كيتباعش، ولكن كيضيع." },
  { city: "العيون", q: "شي واحد كيقول: \"أنا كمشي، ولكن ما كتنقلش\"... شكونا؟", options: ["الساعة", "الحصان", "السيارة", "الطائرة"], answer: 0, hint: "شي حاجة كتلقاها فـالحائط." },
  { city: "الخميسات", q: "شي حاجة كتكون فـالدار، ولكن كتلقاها فـالحقل... شكونا؟", options: ["النملة", "الباب", "السقف", "الحائط"], answer: 0, hint: "حيوان صغير كيدوز فـالدار." },
  { city: "بني ملال", q: "شي واحد كيطلع من الأرض، ويقدر يخليك تهدر... شكونا؟", options: ["الهاتف", "النخيل", "السمك", "الحصان"], answer: 0, hint: "شي حاجة كتصل بيها الناس." },
  { city: "آسفي", q: "شي حاجة كتكون فـالبحر، ولكن كتاكلها فـالدار... شكونا؟", options: ["السمك", "المية", "الرمال", "الحصان"], answer: 0, hint: "أكلة تقليدية مغربية." },
  { city: "الحسيمة", q: "شي واحد كيقول: \"أنا كخدم، ولكن ما كيهدرش\"... شكونا؟", options: ["الراديو", "الهاتف", "الباب", "التلفاز"], answer: 0, hint: "شي حاجة كتفتح وتقفل." },
  { city: "تازة", q: "شي حاجة كتكون فـالمسجد، ولكن كتلقاها فـالدار... شكونا؟", options: ["السجادة", "الحذاء", "الكتاب", "الساعة"], answer: 0, hint: "شي حاجة كتصلي عليها." },
  { city: "خريبكة", q: "شي واحد كيطلع من الجبل، ويقدر يخليك تطير... شكونا؟", options: ["الريح", "النخيل", "السمك", "الحصان"], answer: 0, hint: "شي حاجة ما كتشافش، ولكن كتحس بيها." },
  { city: "سطات", q: "شي حاجة كتكون فـالدار، ولكن كتلقاها فـالسوق... شكونا؟", options: ["الخبز", "الباب", "السقف", "الحائط"], answer: 0, hint: "شي حاجة كتاكلها كل يوم." },
  { city: "فاس", q: "شي واحد كيقول: \"أنا ماشي شي واحد، ولكن أنا كتجمع بزاف!\" شكونا؟", options: ["السوق", "المسجد", "الدار", "الحومة"], answer: 0, hint: "مكان كيجمع ناس بزاف فـوقت واحد." },
  { city: "مراكش", q: "شي حاجة كتكون فـالدار، ولكن كتلقاها فـالحومة... شكونا؟", options: ["الضحك", "الباب", "السقف", "الحائط"], answer: 0, hint: "شي حاجة كتسمعها من الجيران." },
  { city: "شفشاون", q: "شي واحد كيطلع من الدار، ما كيهدرش، ولكن كيخليك تهدر... شكونا؟", options: ["الباب", "الحائط", "النافذة", "السقف"], answer: 0, hint: "شي حاجة كتكون فـ\"الحوش\" وكيقرع عليها الناس." },
  { city: "الصويرة", q: "شي حاجة كتلقاها فـ\"الدابا\"، ولكن ما كتشريهاش... شكونا؟", options: ["المية", "الخبز", "الحليب", "الشاي"], answer: 0, hint: "شي حاجة ضرورية فـالدابا، ولكن ماشي للبيع." },
  { city: "طنجة", q: "شي واحد كيقول: \"أنا كخدم للجميع، ولكن ما كيهدرش\"... شكونا؟", options: ["الباب", "الهاتف", "الراديو", "التلفاز"], answer: 0, hint: "شي حاجة كتفتح وتقفل." },
  { city: "الرباط", q: "شي حاجة كتكون فـ\"الدار\" و\"الحومة\" و\"المسجد\"... وكل واحد كيستخدمها، ولكن ما كيهدرش... شكونا؟", options: ["الباب", "السقف", "الحائط", "الدرج"], answer: 0, hint: "شي حاجة كتفتح وتقفل." },
  { city: "أكادير", q: "شي واحد كيطلع من الرمال، ويقدر يخليك تطير... شكونا؟", options: ["الريح", "النخيل", "السمك", "الحصان"], answer: 0, hint: "شي حاجة ما كتشافش، ولكن كتحس بيها." },
  { city: "وجدة", q: "شي حاجة كتكون فـالدار، ولكن كتلقاها فـالسوق... شكونا؟", options: ["الخبز", "الباب", "السقف", "الحائط"], answer: 0, hint: "شي حاجة كتاكلها كل يوم." },
  { city: "الدار البيضاء", q: "شي واحد كيقول: \"أنا ماشي شي واحد، ولكن أنا كتجمع بزاف!\" شكونا؟", options: ["السوق", "المسجد", "الدار", "الحومة"], answer: 0, hint: "مكان كيجمع ناس بزاف فـوقت واحد." },
  { city: "مكناس", q: "شي حاجة كتلقاها فـالمسجد، ولكن ما كتشريهاش... شكونا؟", options: ["السجادة", "الحذاء", "الكتاب", "الساعة"], answer: 0, hint: "شي حاجة كتصلي عليها." },
  { city: "تطوان", q: "شي واحد كيكون فـالدار، ولكن كيخرج برا... شكونا؟", options: ["الدخان", "الباب", "النافذة", "الضوء"], answer: 0, hint: "شي حاجة كيطلع من المطبخ." },
  { city: "تارودانت", q: "شي حاجة كتكون فـالسوق، ولكن ما كتشريهاش... شكونا؟", options: ["الوقت", "الخبز", "الحليب", "الشاي"], answer: 0, hint: "شي ما كيتباعش، ولكن كيضيع." },
  { city: "العيون", q: "شي واحد كيقول: \"أنا كمشي، ولكن ما كتنقلش\"... شكونا؟", options: ["الساعة", "الحصان", "السيارة", "الطائرة"], answer: 0, hint: "شي حاجة كتلقاها فـالحائط." },
  { city: "الخميسات", q: "شي حاجة كتكون فـالدار، ولكن كتلقاها فـالحقل... شكونا؟", options: ["النملة", "الباب", "السقف", "الحائط"], answer: 0, hint: "حيوان صغير كيدوز فـالدار." },
  { city: "بني ملال", q: "شي واحد كيطلع من الأرض، ويقدر يخليك تهدر... شكونا؟", options: ["الهاتف", "النخيل", "السمك", "الحصان"], answer: 0, hint: "شي حاجة كتصل بيها الناس." },
  { city: "آسفي", q: "شي حاجة كتكون فـالبحر، ولكن كتاكلها فـالدار... شكونا؟", options: ["السمك", "المية", "الرمال", "الحصان"], answer: 0, hint: "أكلة تقليدية مغربية." },
  { city: "الحسيمة", q: "شي واحد كيقول: \"أنا كخدم، ولكن ما كيهدرش\"... شكونا؟", options: ["الراديو", "الهاتف", "الباب", "التلفاز"], answer: 0, hint: "شي حاجة كتفتح وتقفل." },
  { city: "تازة", q: "شي حاجة كتكون فـالمسجد، ولكن كتلقاها فـالدار... شكونا؟", options: ["السجادة", "الحذاء", "الكتاب", "الساعة"], answer: 0, hint: "شي حاجة كتصلي عليها." },
  { city: "خريبكة", q: "شي واحد كيطلع من الجبل، ويقدر يخليك تطير... شكونا؟", options: ["الريح", "النخيل", "السمك", "الحصان"], answer: 0, hint: "شي حاجة ما كتشافش، ولكن كتحس بيها." },
  { city: "سطات", q: "شي حاجة كتكون فـالدار، ولكن كتلقاها فـالسوق... شكونا؟", options: ["الخبز", "الباب", "السقف", "الحائط"], answer: 0, hint: "شي حاجة كتاكلها كل يوم." },
  { city: "فاس", q: "شي واحد كيقول: \"أنا كخدم للجميع، ولكن ما كيهدرش\"... شكونا؟", options: ["الباب", "الهاتف", "الراديو", "التلفاز"], answer: 0, hint: "شي حاجة كتفتح وتقفل." },
  { city: "مراكش", q: "شي حاجة كتكون فـالدار، ولكن كتلقاها فـالحومة... شكونا؟", options: ["الضحك", "الباب", "السقف", "الحائط"], answer: 0, hint: "شي حاجة كتسمعها من الجيران." },
  { city: "شفشاون", q: "شي واحد كيطلع من الدار، ما كيهدرش، ولكن كيخليك تهدر... شكونا؟", options: ["الباب", "الحائط", "النافذة", "السقف"], answer: 0, hint: "شي حاجة كتكون فـ\"الحوش\" وكيقرع عليها الناس." },
  { city: "الصويرة", q: "شي حاجة كتلقاها فـ\"الدابا\"، ولكن ما كتشريهاش... شكونا؟", options: ["المية", "الخبز", "الحليب", "الشاي"], answer: 0, hint: "شي حاجة ضرورية فـالدابا، ولكن ماشي للبيع." },
  { city: "طنجة", q: "شي واحد كيقول: \"أنا ماشي شي واحد، ولكن أنا كتجمع بزاف!\" شكونا؟", options: ["السوق", "المسجد", "الدار", "الحومة"], answer: 0, hint: "مكان كيجمع ناس بزاف فـوقت واحد." },
  { city: "الرباط", q: "شي حاجة كتكون فـ\"الدار\" و\"الحومة\" و\"المسجد\"... وكل واحد كيستخدمها، ولكن ما كيهدرش... شكونا؟", options: ["الباب", "السقف", "الحائط", "الدرج"], answer: 0, hint: "شي حاجة كتفتح وتقفل." },
  { city: "أكادير", q: "شي واحد كيطلع من الرمال، ويقدر يخليك تطير... شكونا؟", options: ["الريح", "النخيل", "السمك", "الحصان"], answer: 0, hint: "شي حاجة ما كتشافش، ولكن كتحس بيها." },
  { city: "وجدة", q: "شي حاجة كتكون فـالدار، ولكن كتلقاها فـالسوق... شكونا؟", options: ["الخبز", "الباب", "السقف", "الحائط"], answer: 0, hint: "شي حاجة كتاكلها كل يوم." },
  { city: "الدار البيضاء", q: "شي واحد كيقول: \"أنا كخدم للجميع، ولكن ما كيهدرش\"... شكونا؟", options: ["الباب", "الهاتف", "الراديو", "التلفاز"], answer: 0, hint: "شي حاجة كتفتح وتقفل." },
  { city: "مكناس", q: "شي حاجة كتلقاها فـالمسجد، ولكن ما كتشريهاش... شكونا؟", options: ["السجادة", "الحذاء", "الكتاب", "الساعة"], answer: 0, hint: "شي حاجة كتصلي عليها." },
  { city: "تطوان", q: "شي واحد كيكون فـالدار، ولكن كيخرج برا... شكونا؟", options: ["الدخان", "الباب", "النافذة", "الضوء"], answer: 0, hint: "شي حاجة كيطلع من المطبخ." },
  { city: "تارودانت", q: "شي حاجة كتكون فـالسوق، ولكن ما كتشريهاش... شكونا؟", options: ["الوقت", "الخبز", "الحليب", "الشاي"], answer: 0, hint: "شي ما كيتباعش، ولكن كيضيع." },
  { city: "العيون", q: "شي واحد كيقول: \"أنا كمشي، ولكن ما كتنقلش\"... شكونا؟", options: ["الساعة", "الحصان", "السيارة", "الطائرة"], answer: 0, hint: "شي حاجة كتلقاها فـالحائط." },
  { city: "الخميسات", q: "شي حاجة كتكون فـالدار، ولكن كتلقاها فـالحقل... شكونا؟", options: ["النملة", "الباب", "السقف", "الحائط"], answer: 0, hint: "حيوان صغير كيدوز فـالدار." },
  { city: "بني ملال", q: "شي واحد كيطلع من الأرض، ويقدر يخليك تهدر... شكونا؟", options: ["الهاتف", "النخيل", "السمك", "الحصان"], answer: 0, hint: "شي حاجة كتصل بيها الناس." },
  { city: "آسفي", q: "شي حاجة كتكون فـالبحر، ولكن كتاكلها فـالدار... شكونا؟", options: ["السمك", "المية", "الرمال", "الحصان"], answer: 0, hint: "أكلة تقليدية مغربية." },
  { city: "الحسيمة", q: "شي واحد كيقول: \"أنا كخدم، ولكن ما كيهدرش\"... شكونا؟", options: ["الراديو", "الهاتف", "الباب", "التلفاز"], answer: 0, hint: "شي حاجة كتفتح وتقفل." },
  { city: "تازة", q: "شي حاجة كتكون فـالمسجد، ولكن كتلقاها فـالدار... شكونا؟", options: ["السجادة", "الحذاء", "الكتاب", "الساعة"], answer: 0, hint: "شي حاجة كتصلي عليها." },
  { city: "خريبكة", q: "شي واحد كيطلع من الجبل، ويقدر يخليك تطير... شكونا؟", options: ["الريح", "النخيل", "السمك", "الحصان"], answer: 0, hint: "شي حاجة ما كتشافش، ولكن كتحس بيها." },
  { city: "سطات", q: "شي حاجة كتكون فـالدار، ولكن كتلقاها فـالسوق... شكونا؟", options: ["الخبز", "الباب", "السقف", "الحائط"], answer: 0, hint: "شي حاجة كتاكلها كل يوم." }
];

    // =============== رسائل دارجة ===============
    const wrongMessages = [
      "ههههه، مكلخ؟ عود قرا!",
      "واخا، هاد الجواب غلط بزاف!",
      "ماشي هادا! راجع لدار وقرا!",
      "شحال من مرة غادي نعاود معاك؟",
      "واش راك نايم؟ هادا غلط!",
      "ماشي هاد الجواب، راجع لبابا يقرا معاك!",
      "ههه، غلط! حتى الباب كيهدر عليك!",
      "ماشي هادا، حتى الجيران كيضحكو عليك!"
    ];
    const correctMessages = [
      "واعر زعما! نتا أدير المسا فاش كيورك على البطون؟",
      "صح بزاف! راسك واعر!",
      "ماشي غلط! عندك راس واعر!",
      "واخا، صح! تقدر تخدم فـالحسبة!",
      "ماشي هدر! عندك ذكاء مغربي!",
      "صح! راسك ماشي كيبيع الهوا!",
      "واو! صح بزاف، تقدر تلقى الكنز!",
      "ماشي غلط! عندك راس كيعرف يهدر!"
    ];
    const hintMessages = [
      "ها شوف التلميح... ولكن خاصك تدفع 100 نقطة!",
      "تلميح جاهز... ولكن راسك غادي يخسر!",
      "ها التلميح... ولكن ماشي مجانا!",
      "تلميح؟ خاصك تدفع... ولكن راسك غادي يرتاح!"
    ];

    let currentPuzzle = 0;
    let score = 0;
    let usedHint = false;
    let highScore = localStorage.getItem('lughz_high_score') || 0;
    let currentCorrectIndex = -1; // لتخزين موقع الجواب الصحيح بعد الخلط

    document.getElementById('highScoreDisplay').textContent = `أعلى نتيجة: ${highScore}`;
    document.getElementById('recordScore').textContent = highScore;

    function getRandomMessage(arr) {
      return arr[Math.floor(Math.random() * arr.length)];
    }

    function showScreen(id) {
      document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
      document.getElementById(id).classList.add('active');
      if (bgMusic && !bgMusic.paused) {
        bgMusic.play().catch(e => {});
      }
    }
    function goHome() { showScreen('home'); }
    function showInstructions() { showScreen('instructions'); }

    function startGame() {
      currentPuzzle = 0;
      score = 0;
      document.getElementById('score').textContent = score;
      loadPuzzle();
      showScreen('game');
    }

    function loadPuzzle() {
      if (currentPuzzle >= puzzles.length) {
        endGame();
        return;
      }
      const p = puzzles[currentPuzzle];
      document.getElementById('cityTitle').textContent = `📍 ${p.city}`;
      document.getElementById('riddleBox').textContent = p.q;
      document.getElementById('questionNum').textContent = currentPuzzle + 1;

      const progress = ((currentPuzzle) / puzzles.length) * 100;
      document.getElementById('progressFill').style.width = `${progress}%`;

      // === خلط الخيارات ===
      const shuffledOptions = shuffleArray([...p.options]);
      currentCorrectIndex = shuffledOptions.indexOf(p.options[p.answer]);

      const grid = document.getElementById('options-grid');
      grid.innerHTML = '';
      shuffledOptions.forEach((opt, i) => {
        const btn = document.createElement('div');
        btn.className = 'option';
        btn.textContent = opt;
        btn.onclick = () => selectOption(i);
        grid.appendChild(btn);
      });

      document.getElementById('hintText').style.display = 'none';
      document.getElementById('hintBtn').style.display = 'block';
      usedHint = false;
      document.getElementById('darjaFeedback').innerHTML = '';
    }

    function selectOption(selectedIndex) {
      const options = document.querySelectorAll('.option');
      options.forEach(opt => opt.style.pointerEvents = 'none');

      if (selectedIndex === currentCorrectIndex) {
        options[selectedIndex].classList.add('correct');
        const points = usedHint ? 100 : 200;
        score += points;
        document.getElementById('score').textContent = score;

        const msg = getRandomMessage(correctMessages);
        document.getElementById('darjaFeedback').innerHTML = `<div class="darja-message" style="background:rgba(76,175,80,0.2); color:#4CAF50;">${msg}</div>`;

        setTimeout(() => {
          currentPuzzle++;
          loadPuzzle();
        }, 1800);
      } else {
        options[selectedIndex].classList.add('wrong');
        options[currentCorrectIndex].classList.add('correct');
        const msg = getRandomMessage(wrongMessages);
        document.getElementById('darjaFeedback').innerHTML = `<div class="darja-message" style="background:rgba(244,67,54,0.2); color:#f44336;">${msg}</div>`;

        setTimeout(() => {
          options.forEach(opt => {
            opt.classList.remove('wrong', 'correct');
            opt.style.pointerEvents = 'auto';
          });
          document.getElementById('darjaFeedback').innerHTML = '';
        }, 2500);
      }
    }

    function showHint() {
      if (!usedHint) {
        score -= 100;
        if (score < 0) score = 0;
        document.getElementById('score').textContent = score;
        document.getElementById('hintText').textContent = puzzles[currentPuzzle].hint;
        document.getElementById('hintText').style.display = 'block';
        document.getElementById('hintBtn').style.display = 'none';
        usedHint = true;

        const msg = getRandomMessage(hintMessages);
        document.getElementById('darjaFeedback').innerHTML = `<div class="darja-message" style="background:rgba(255,215,0,0.2); color:#FFD700;">${msg}</div>`;
      }
    }

    function endGame() {
      document.getElementById('finalScore').textContent = score;
      let recordMsg = "";
      if (score > highScore) {
        highScore = score;
        localStorage.setItem('lughz_high_score', highScore);
        recordMsg = "🎉 سجلت رقم قياسي جديد!";
        document.getElementById('recordScore').textContent = highScore;
      }
      document.getElementById('recordMsg').textContent = recordMsg;
      showScreen('win');
    }

    function restartGame() {
      startGame();
    }

    // تهيئة
    document.getElementById('highScoreDisplay').textContent = `أعلى نتيجة: ${highScore}`;
    document.getElementById('recordScore').textContent = highScore;
  </script>
</body>
</html>
