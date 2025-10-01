<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>سوقنا — موقع البيع والشراء</title>
  <link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@400;700;800&display=swap" rel="stylesheet">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">
  <style>
    :root {
      --bg: #ffffff;
      --text: #0b0b0b;
      --muted: #6b7280;
      --accent: #16a34a;
      --accent-light: #dcf7e6;
      --soft: #f3f6f4;
      --card: #ffffff;
      --shadow: 0 4px 20px rgba(0,0,0,0.06);
      --shadow-strong: 0 10px 30px rgba(2,6,23,0.08);
      --blue-bg: #4F6FFF;
      --blue-light: #6A8BFF;
      --border: rgba(0,0,0,0.08);
    }

    [data-theme="dark"] {
      --bg: #111827;
      --text: #f9fafb;
      --muted: #9ca3af;
      --soft: #1f2937;
      --card: #1e293b;
      --border: rgba(255,255,255,0.1);
      --shadow: 0 4px 20px rgba(0,0,0,0.2);
      --shadow-strong: 0 10px 30px rgba(0,0,0,0.3);
    }

    * { box-sizing: border-box; font-family: "Tajawal", system-ui, Arial; }
    html, body { height: 100%; margin: 0; background: var(--bg); color: var(--text); -webkit-font-smoothing: antialiased; }
    .app { min-height: 100vh; display: flex; flex-direction: column; }

    /* Header */
    .header {
      background: white;
      padding: 12px 16px;
      box-shadow: var(--shadow);
      position: sticky;
      top: 0;
      z-index: 100;
    }
    [data-theme="dark"] .header { background: var(--card); }
    .header-content {
      max-width: 1200px;
      margin: 0 auto;
      display: flex;
      align-items: center;
      gap: 16px;
    }
    .logo {
      font-size: 24px;
      font-weight: 800;
      color: var(--accent);
      text-decoration: none;
    }
    .search-bar {
      flex: 1;
      display: flex;
      gap: 8px;
    }
    .search-bar input {
      flex: 1;
      padding: 12px 16px;
      border-radius: 12px;
      border: 1px solid var(--border);
      font-size: 16px;
      background: var(--soft);
    }
    .search-bar select {
      padding: 12px 16px;
      border-radius: 12px;
      border: 1px solid var(--border);
      background: var(--soft);
      font-size: 16px;
    }
    .header-actions {
      display: flex;
      gap: 12px;
    }
    .btn-header {
      padding: 10px 16px;
      border-radius: 12px;
      border: none;
      background: var(--accent);
      color: white;
      font-weight: 700;
      cursor: pointer;
      display: flex;
      align-items: center;
      gap: 8px;
    }
    .theme-toggle {
      width: 40px;
      height: 40px;
      border-radius: 50%;
      background: var(--soft);
      border: none;
      color: var(--text);
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    /* Main Content */
    .main {
      max-width: 1200px;
      margin: 0 auto;
      padding: 20px 16px;
      display: flex;
      gap: 24px;
    }
    .sidebar {
      width: 280px;
      flex-shrink: 0;
    }
    .main-content {
      flex: 1;
    }

    /* Sidebar */
    .sidebar-card {
      background: var(--card);
      border-radius: 16px;
      padding: 20px;
      margin-bottom: 20px;
      box-shadow: var(--shadow);
    }
    .sidebar-card h3 {
      margin: 0 0 16px 0;
      font-size: 18px;
      color: var(--text);
    }
    .category-list {
      list-style: none;
      padding: 0;
      margin: 0;
    }
    .category-list li {
      padding: 10px 0;
      border-bottom: 1px solid var(--border);
    }
    .category-list li:last-child {
      border-bottom: none;
    }
    .category-list a {
      color: var(--text);
      text-decoration: none;
      display: flex;
      align-items: center;
      gap: 12px;
    }
    .category-list a:hover {
      color: var(--accent);
    }
    .category-list i {
      width: 24px;
      text-align: center;
      color: var(--accent);
    }

    /* Ad Listings */
    .ads-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
      gap: 24px;
    }
    .ad-card {
      background: var(--card);
      border-radius: 16px;
      overflow: hidden;
      box-shadow: var(--shadow);
      transition: transform 0.2s ease, box-shadow 0.2s ease;
    }
    .ad-card:hover {
      transform: translateY(-4px);
      box-shadow: var(--shadow-strong);
    }
    .ad-image {
      height: 200px;
      overflow: hidden;
    }
    .ad-image img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      display: block;
    }
    .ad-content {
      padding: 16px;
    }
    .ad-title {
      font-size: 16px;
      font-weight: 700;
      margin: 0 0 8px 0;
      color: var(--text);
      display: -webkit-box;
      -webkit-line-clamp: 2;
      -webkit-box-orient: vertical;
      overflow: hidden;
    }
    .ad-price {
      font-size: 18px;
      font-weight: 800;
      color: var(--accent);
      margin: 0 0 8px 0;
    }
    .ad-location {
      font-size: 13px;
      color: var(--muted);
      display: flex;
      align-items: center;
      gap: 6px;
      margin: 0 0 12px 0;
    }
    .ad-meta {
      display: flex;
      justify-content: space-between;
      font-size: 12px;
      color: var(--muted);
    }
    .ad-actions {
      display: flex;
      gap: 8px;
      margin-top: 12px;
    }
    .ad-btn {
      flex: 1;
      padding: 8px;
      border-radius: 8px;
      border: 1px solid var(--border);
      background: transparent;
      color: var(--text);
      font-size: 13px;
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 6px;
    }
    .ad-btn.chat {
      border-color: var(--accent);
      color: var(--accent);
    }

    /* Add Ad Form */
    .add-ad-form {
      background: var(--card);
      border-radius: 16px;
      padding: 24px;
      box-shadow: var(--shadow);
      margin-bottom: 24px;
    }
    .form-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 20px;
      margin-bottom: 20px;
    }
    .form-group {
      margin-bottom: 16px;
    }
    .form-group label {
      display: block;
      font-size: 14px;
      color: var(--text);
      margin-bottom: 8px;
      font-weight: 600;
    }
    .form-group input,
    .form-group select,
    .form-group textarea {
      width: 100%;
      padding: 12px;
      border-radius: 12px;
      border: 1px solid var(--border);
      font-size: 15px;
      background: var(--soft);
      color: var(--text);
    }
    .form-group textarea {
      min-height: 120px;
      resize: vertical;
    }
    .photos-preview {
      display: flex;
      gap: 12px;
      margin-top: 12px;
      flex-wrap: wrap;
    }
    .photo-thumb {
      width: 80px;
      height: 80px;
      border-radius: 8px;
      overflow: hidden;
      border: 1px solid var(--border);
    }
    .photo-thumb img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    /* Chat */
    .chat-container {
      background: var(--card);
      border-radius: 16px;
      padding: 24px;
      box-shadow: var(--shadow);
      height: 500px;
      display: flex;
      flex-direction: column;
    }
    .chat-header {
      display: flex;
      align-items: center;
      gap: 12px;
      padding-bottom: 16px;
      border-bottom: 1px solid var(--border);
      margin-bottom: 16px;
    }
    .chat-avatar {
      width: 48px;
      height: 48px;
      border-radius: 50%;
      background: var(--accent-light);
      display: flex;
      align-items: center;
      justify-content: center;
      color: var(--accent);
      font-weight: 700;
      font-size: 20px;
    }
    .chat-messages {
      flex: 1;
      overflow-y: auto;
      display: flex;
      flex-direction: column;
      gap: 12px;
    }
    .message {
      max-width: 70%;
      padding: 12px;
      border-radius: 16px;
      background: var(--soft);
      word-wrap: break-word;
    }
    .message.self {
      background: var(--accent-light);
      color: var(--accent);
      align-self: flex-end;
    }
    .chat-input {
      display: flex;
      gap: 12px;
      margin-top: 16px;
    }
    .chat-input input {
      flex: 1;
      padding: 12px;
      border-radius: 12px;
      border: 1px solid var(--border);
      background: var(--soft);
    }
    .chat-input button {
      padding: 12px 24px;
      border-radius: 12px;
      border: none;
      background: var(--accent);
      color: white;
      font-weight: 700;
      cursor: pointer;
    }

    /* Auth Modals */
    .modal {
      position: fixed;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background: rgba(0,0,0,0.5);
      display: flex;
      align-items: center;
      justify-content: center;
      z-index: 1000;
      opacity: 0;
      visibility: hidden;
      transition: all 0.3s ease;
    }
    .modal.active {
      opacity: 1;
      visibility: visible;
    }
    .modal-content {
      background: var(--card);
      border-radius: 20px;
      padding: 30px;
      width: 100%;
      max-width: 420px;
      box-shadow: 0 20px 40px rgba(0,0,0,0.2);
      transform: translateY(20px);
      transition: transform 0.3s ease;
    }
    .modal.active .modal-content {
      transform: translateY(0);
    }
    .modal-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 20px;
    }
    .modal-header h2 {
      margin: 0;
      font-size: 22px;
      color: var(--text);
    }
    .close-modal {
      background: none;
      border: none;
      font-size: 24px;
      cursor: pointer;
      color: var(--muted);
    }
    .auth-form .form-group {
      margin-bottom: 16px;
    }
    .auth-form .form-group label {
      display: block;
      font-size: 14px;
      color: var(--text);
      margin-bottom: 8px;
      font-weight: 600;
    }
    .auth-form .form-group input {
      width: 100%;
      padding: 12px;
      border-radius: 12px;
      border: 1px solid var(--border);
      font-size: 15px;
      background: var(--soft);
      color: var(--text);
    }
    .auth-btn {
      width: 100%;
      padding: 14px;
      border-radius: 12px;
      border: none;
      background: var(--accent);
      color: white;
      font-weight: 700;
      font-size: 16px;
      cursor: pointer;
      margin-top: 10px;
    }
    .switch-form {
      text-align: center;
      margin-top: 16px;
      color: var(--muted);
    }
    .switch-form a {
      color: var(--accent);
      text-decoration: none;
      font-weight: 700;
    }

    /* Footer */
    .footer {
      background: var(--card);
      padding: 30px 0;
      margin-top: 40px;
      border-top: 1px solid var(--border);
    }
    .footer-content {
      max-width: 1200px;
      margin: 0 auto;
      padding: 0 16px;
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
      gap: 30px;
    }
    .footer-column h3 {
      font-size: 18px;
      margin: 0 0 20px 0;
      color: var(--text);
    }
    .footer-links {
      list-style: none;
      padding: 0;
      margin: 0;
    }
    .footer-links li {
      margin-bottom: 10px;
    }
    .footer-links a {
      color: var(--muted);
      text-decoration: none;
      font-size: 14px;
    }
    .footer-links a:hover {
      color: var(--accent);
    }
    .copyright {
      text-align: center;
      padding: 20px 0;
      color: var(--muted);
      font-size: 14px;
      border-top: 1px solid var(--border);
      margin-top: 30px;
    }

    /* Responsive */
    @media (max-width: 768px) {
      .main {
        flex-direction: column;
      }
      .sidebar {
        width: 100%;
      }
      .header-content {
        flex-wrap: wrap;
      }
      .search-bar {
        width: 100%;
        order: 3;
      }
      .header-actions {
        width: 100%;
        justify-content: space-between;
        order: 2;
      }
    }
  </style>
</head>
<body data-theme="light">
  <div class="app">
    <!-- Header -->
    <header class="header">
      <div class="header-content">
        <a href="#" class="logo">سوقنا</a>
        <div class="search-bar">
          <input type="text" id="searchInput" placeholder="ابحث عن منتجات، سيارات، عقارات...">
          <select id="categoryFilter">
            <option value="">جميع التصنيفات</option>
            <option value="cars">سيارات</option>
            <option value="real_estate">عقارات</option>
            <option value="electronics">إلكترونيات</option>
            <option value="furniture">أثاث</option>
            <option value="jobs">وظائف</option>
            <option value="other">أخرى</option>
          </select>
          <button id="searchBtn" class="btn-header">
            <i class="fas fa-search"></i>
          </button>
        </div>
        <div class="header-actions">
          <button id="loginBtn" class="btn-header">
            <i class="fas fa-user"></i> دخول
          </button>
          <button id="addAdBtn" class="btn-header">
            <i class="fas fa-plus"></i> إضافة إعلان
          </button>
          <button class="theme-toggle" id="themeToggle">
            <i class="fas fa-moon"></i>
          </button>
        </div>
      </div>
    </header>

    <!-- Main Content -->
    <main class="main">
      <!-- Sidebar -->
      <aside class="sidebar">
        <div class="sidebar-card">
          <h3>التصنيفات</h3>
          <ul class="category-list">
            <li><a href="#" data-category="cars"><i class="fas fa-car"></i> سيارات</a></li>
            <li><a href="#" data-category="real_estate"><i class="fas fa-home"></i> عقارات</a></li>
            <li><a href="#" data-category="electronics"><i class="fas fa-mobile-alt"></i> إلكترونيات</a></li>
            <li><a href="#" data-category="furniture"><i class="fas fa-couch"></i> أثاث</a></li>
            <li><a href="#" data-category="jobs"><i class="fas fa-briefcase"></i> وظائف</a></li>
            <li><a href="#" data-category="other"><i class="fas fa-tags"></i> أخرى</a></li>
          </ul>
        </div>

        <div class="sidebar-card">
          <h3>الفلاتر</h3>
          <div class="form-group">
            <label>السعر من</label>
            <input type="number" id="priceFrom" placeholder="0">
          </div>
          <div class="form-group">
            <label>السعر إلى</label>
            <input type="number" id="priceTo" placeholder="1000000">
          </div>
          <div class="form-group">
            <label>المدينة</label>
            <select id="cityFilter">
              <option value="">جميع المدن</option>
              <option value="casablanca">الدار البيضاء</option>
              <option value="rabat">الرباط</option>
              <option value="marrakech">مراكش</option>
              <option value="fez">فاس</option>
              <option value="tangier">طنجة</option>
            </select>
          </div>
          <button id="applyFilters" class="btn-header" style="width:100%;margin-top:10px;">
            تطبيق الفلاتر
          </button>
        </div>
      </aside>

      <!-- Main Content -->
      <div class="main-content">
        <!-- Add Ad Form (Hidden by default) -->
        <div id="addAdForm" class="add-ad-form" style="display:none;">
          <h2>إضافة إعلان جديد</h2>
          <div class="form-grid">
            <div class="form-group">
              <label>العنوان</label>
              <input type="text" id="adTitle" placeholder="مثال: سيارة رينو موديل 2020" required>
            </div>
            <div class="form-group">
              <label>التصنيف</label>
              <select id="adCategory" required>
                <option value="">اختر التصنيف</option>
                <option value="cars">سيارات</option>
                <option value="real_estate">عقارات</option>
                <option value="electronics">إلكترونيات</option>
                <option value="furniture">أثاث</option>
                <option value="jobs">وظائف</option>
                <option value="other">أخرى</option>
              </select>
            </div>
            <div class="form-group">
              <label>السعر (درهم)</label>
              <input type="number" id="adPrice" placeholder="0" required>
            </div>
            <div class="form-group">
              <label>المدينة</label>
              <select id="adCity" required>
                <option value="">اختر المدينة</option>
                <option value="casablanca">الدار البيضاء</option>
                <option value="rabat">الرباط</option>
                <option value="marrakech">مراكش</option>
                <option value="fez">فاس</option>
                <option value="tangier">طنجة</option>
              </select>
            </div>
          </div>
          <div class="form-group">
            <label>الوصف</label>
            <textarea id="adDescription" placeholder="وصف مفصل للمنتج..." required></textarea>
          </div>
          <div class="form-group">
            <label>صور المنتج (اختر عدة صور)</label>
            <input type="file" id="adPhotos" accept="image/*" multiple>
            <div class="photos-preview" id="photosPreview"></div>
          </div>
          <button id="submitAd" class="btn-header" style="width:100%;">
            <i class="fas fa-plus"></i> نشر الإعلان
          </button>
        </div>

        <!-- Ads Listings -->
        <div id="adsContainer" class="ads-grid">
          <!-- سيتم ملؤه ديناميكيًا -->
        </div>

        <!-- Chat Section (Hidden by default) -->
        <div id="chatSection" class="chat-container" style="display:none;">
          <div class="chat-header">
            <div class="chat-avatar">ع</div>
            <div>
              <div class="chat-name" id="chatName">عمر</div>
              <div class="chat-status">متصل الآن</div>
            </div>
          </div>
          <div class="chat-messages" id="chatMessages">
            <!-- سيتم ملؤه ديناميكيًا -->
          </div>
          <div class="chat-input">
            <input type="text" id="chatInput" placeholder="اكتب رسالتك...">
            <button id="sendChat"><i class="fas fa-paper-plane"></i></button>
          </div>
        </div>
      </div>
    </main>

    <!-- Footer -->
    <footer class="footer">
      <div class="footer-content">
        <div class="footer-column">
          <h3>سوقنا</h3>
          <ul class="footer-links">
            <li><a href="#">من نحن</a></li>
            <li><a href="#">شروط الاستخدام</a></li>
            <li><a href="#">سياسة الخصوصية</a></li>
            <li><a href="#">اتصل بنا</a></li>
          </ul>
        </div>
        <div class="footer-column">
          <h3>التصنيفات</h3>
          <ul class="footer-links">
            <li><a href="#">سيارات</a></li>
            <li><a href="#">عقارات</a></li>
            <li><a href="#">إلكترونيات</a></li>
            <li><a href="#">أثاث</a></li>
          </ul>
        </div>
        <div class="footer-column">
          <h3>الدعم</h3>
          <ul class="footer-links">
            <li><a href="#">الأسئلة الشائعة</a></li>
            <li><a href="#">مركز المساعدة</a></li>
            <li><a href="#">إبلاغ عن إعلان</a></li>
            <li><a href="#">نصائح الأمان</a></li>
          </ul>
        </div>
      </div>
      <div class="copyright">
        &copy; 2024 سوقنا. جميع الحقوق محفوظة.
      </div>
    </footer>

    <!-- Login Modal -->
    <div id="loginModal" class="modal">
      <div class="modal-content">
        <div class="modal-header">
          <h2>تسجيل الدخول</h2>
          <button class="close-modal">&times;</button>
        </div>
        <form class="auth-form" id="loginForm">
          <div class="form-group">
            <label>البريد الإلكتروني</label>
            <input type="email" id="loginEmail" placeholder="ex@example.com" required>
          </div>
          <div class="form-group">
            <label>كلمة المرور</label>
            <input type="password" id="loginPassword" placeholder="••••••••" required>
          </div>
          <button type="submit" class="auth-btn">تسجيل الدخول</button>
          <div class="switch-form">
            ليس لديك حساب؟ <a href="#" id="showRegister">سجل الآن</a>
          </div>
        </form>
      </div>
    </div>

    <!-- Register Modal -->
    <div id="registerModal" class="modal">
      <div class="modal-content">
        <div class="modal-header">
          <h2>إنشاء حساب</h2>
          <button class="close-modal">&times;</button>
        </div>
        <form class="auth-form" id="registerForm">
          <div class="form-group">
            <label>الاسم الكامل</label>
            <input type="text" id="registerName" placeholder="أدخل اسمك الكامل" required>
          </div>
          <div class="form-group">
            <label>البريد الإلكتروني</label>
            <input type="email" id="registerEmail" placeholder="ex@example.com" required>
          </div>
          <div class="form-group">
            <label>كلمة المرور</label>
            <input type="password" id="registerPassword" placeholder="••••••••" required>
          </div>
          <div class="form-group">
            <label>تأكيد كلمة المرور</label>
            <input type="password" id="registerConfirmPassword" placeholder="••••••••" required>
          </div>
          <button type="submit" class="auth-btn">إنشاء حساب</button>
          <div class="switch-form">
            لديك حساب؟ <a href="#" id="showLogin">سجل الدخول</a>
          </div>
        </form>
      </div>
    </div>
  </div>

  <script>
    // =============== Theme Management ===============
    const THEME_KEY = 'marketplace_theme';
    
    function setTheme(theme) {
      document.documentElement.setAttribute('data-theme', theme);
      localStorage.setItem(THEME_KEY, theme);
      updateThemeIcon();
    }
    
    function getTheme() {
      return localStorage.getItem(THEME_KEY) || 'light';
    }
    
    function updateThemeIcon() {
      const isDark = getTheme() === 'dark';
      document.querySelector('#themeToggle i').className = isDark ? 'fas fa-sun' : 'fas fa-moon';
    }
    
    document.getElementById('themeToggle').addEventListener('click', () => {
      const current = getTheme();
      setTheme(current === 'light' ? 'dark' : 'light');
    });
    
    // =============== Modal Management ===============
    function openModal(modalId) {
      document.getElementById(modalId).classList.add('active');
    }
    
    function closeModal(modalId) {
      document.getElementById(modalId).classList.remove('active');
    }
    
    // Close modals when clicking outside
    document.querySelectorAll('.modal').forEach(modal => {
      modal.addEventListener('click', (e) => {
        if (e.target === modal) {
          closeModal(modal.id);
        }
      });
    });
    
    // Close buttons
    document.querySelectorAll('.close-modal').forEach(btn => {
      btn.addEventListener('click', () => {
        const modal = btn.closest('.modal');
        closeModal(modal.id);
      });
    });
    
    // Switch between login and register
    document.getElementById('showRegister').addEventListener('click', (e) => {
      e.preventDefault();
      closeModal('loginModal');
      openModal('registerModal');
    });
    
    document.getElementById('showLogin').addEventListener('click', (e) => {
      e.preventDefault();
      closeModal('registerModal');
      openModal('loginModal');
    });
    
    // =============== Authentication ===============
    const USER_KEY = 'marketplace_user';
    
    function saveUser(user) {
      localStorage.setItem(USER_KEY, JSON.stringify(user));
    }
    
    function getCurrentUser() {
      try {
        return JSON.parse(localStorage.getItem(USER_KEY)) || null;
      } catch (e) {
        return null;
      }
    }
    
    function updateAuthUI() {
      const user = getCurrentUser();
      const loginBtn = document.getElementById('loginBtn');
      if (user) {
        loginBtn.innerHTML = `<i class="fas fa-user"></i> ${user.name}`;
        loginBtn.onclick = null; // Remove login click handler
      } else {
        loginBtn.innerHTML = '<i class="fas fa-user"></i> دخول';
        loginBtn.onclick = () => openModal('loginModal');
      }
    }
    
    // Login form
    document.getElementById('loginForm').addEventListener('submit', (e) => {
      e.preventDefault();
      const email = document.getElementById('loginEmail').value.trim();
      const password = document.getElementById('loginPassword').value.trim();
      
      if (!email || !password) {
        alert('الرجاء ملء جميع الحقول');
        return;
      }
      
      // In a real app, you would verify credentials with a server
      // Here we simulate a successful login
      const user = { id: Date.now(), name: email.split('@')[0], email };
      saveUser(user);
      updateAuthUI();
      closeModal('loginModal');
      alert('تم تسجيل الدخول بنجاح!');
    });
    
    // Register form
    document.getElementById('registerForm').addEventListener('submit', (e) => {
      e.preventDefault();
      const name = document.getElementById('registerName').value.trim();
      const email = document.getElementById('registerEmail').value.trim();
      const password = document.getElementById('registerPassword').value.trim();
      const confirmPassword = document.getElementById('registerConfirmPassword').value.trim();
      
      if (!name || !email || !password || !confirmPassword) {
        alert('الرجاء ملء جميع الحقول');
        return;
      }
      
      if (password !== confirmPassword) {
        alert('كلمات المرور غير متطابقة');
        return;
      }
      
      const user = { id: Date.now(), name, email };
      saveUser(user);
      updateAuthUI();
      closeModal('registerModal');
      alert('تم إنشاء الحساب بنجاح!');
    });
    
    // =============== Ad Management ===============
    const ADS_KEY = 'marketplace_ads';
    const CHATS_KEY = 'marketplace_chats';
    
    function saveAds(ads) {
      localStorage.setItem(ADS_KEY, JSON.stringify(ads));
    }
    
    function loadAds() {
      try {
        return JSON.parse(localStorage.getItem(ADS_KEY)) || [];
      } catch (e) {
        return [];
      }
    }
    
    function saveChats(chats) {
      localStorage.setItem(CHATS_KEY, JSON.stringify(chats));
    }
    
    function loadChats() {
      try {
        return JSON.parse(localStorage.getItem(CHATS_KEY)) || {};
      } catch (e) {
        return {};
      }
    }
    
    function uid() {
      return Date.now().toString(36) + Math.random().toString(36).slice(2, 6);
    }
    
    // Photo preview
    document.getElementById('adPhotos').addEventListener('change', (e) => {
      const preview = document.getElementById('photosPreview');
      preview.innerHTML = '';
      const files = Array.from(e.target.files);
      files.forEach(file => {
        const reader = new FileReader();
        reader.onload = (event) => {
          const div = document.createElement('div');
          div.className = 'photo-thumb';
          div.innerHTML = `<img src="${event.target.result}" alt="صورة">`;
          preview.appendChild(div);
        };
        reader.readAsDataURL(file);
      });
    });
    
    // Submit ad
    document.getElementById('submitAd').addEventListener('submit', (e) => {
      e.preventDefault();
    });
    
    document.getElementById('submitAd').addEventListener('click', () => {
      const title = document.getElementById('adTitle').value.trim();
      const category = document.getElementById('adCategory').value;
      const price = document.getElementById('adPrice').value;
      const city = document.getElementById('adCity').value;
      const description = document.getElementById('adDescription').value.trim();
      
      if (!title || !category || !price || !city || !description) {
        alert('الرجاء ملء جميع الحقول');
        return;
      }
      
      const user = getCurrentUser();
      if (!user) {
        alert('يجب تسجيل الدخول لإضافة إعلان');
        openModal('loginModal');
        return;
      }
      
      const ad = {
        id: uid(),
        title,
        category,
        price: parseFloat(price),
        city,
        description,
        userId: user.id,
        userName: user.name,
        timestamp: new Date().toISOString(),
        photos: [] // In a real app, you would upload photos
      };
      
      const ads = loadAds();
      ads.push(ad);
      saveAds(ads);
      
      // Reset form
      document.getElementById('adTitle').value = '';
      document.getElementById('adCategory').value = '';
      document.getElementById('adPrice').value = '';
      document.getElementById('adCity').value = '';
      document.getElementById('adDescription').value = '';
      document.getElementById('adPhotos').value = '';
      document.getElementById('photosPreview').innerHTML = '';
      
      document.getElementById('addAdForm').style.display = 'none';
      loadAdsList();
      alert('تم نشر الإعلان بنجاح!');
    });
    
    // =============== Ad Display ===============
    const CATEGORIES = {
      cars: 'سيارات',
      real_estate: 'عقارات',
      electronics: 'إلكترونيات',
      furniture: 'أثاث',
      jobs: 'وظائف',
      other: 'أخرى'
    };
    
    const CITIES = {
      casablanca: 'الدار البيضاء',
      rabat: 'الرباط',
      marrakech: 'مراكش',
      fez: 'فاس',
      tangier: 'طنجة'
    };
    
    function renderAd(ad) {
      const div = document.createElement('div');
      div.className = 'ad-card';
      const categoryText = CATEGORIES[ad.category] || ad.category;
      const cityText = CITIES[ad.city] || ad.city;
      
      div.innerHTML = `
        <div class="ad-image">
          <img src="https://via.placeholder.com/300x200?text=${encodeURIComponent(ad.title)}" alt="${ad.title}">
        </div>
        <div class="ad-content">
          <h3 class="ad-title">${ad.title}</h3>
          <div class="ad-price">${ad.price.toLocaleString()} درهم</div>
          <div class="ad-location">
            <i class="fas fa-map-marker-alt"></i> ${cityText}
          </div>
          <div class="ad-meta">
            <span>${categoryText}</span>
            <span>${new Date(ad.timestamp).toLocaleDateString('ar-MA')}</span>
          </div>
          <div class="ad-actions">
            <button class="ad-btn chat" onclick="openChat('${ad.userId}', '${ad.userName}')">
              <i class="fas fa-comments"></i> دردشة
            </button>
            <button class="ad-btn">
              <i class="fas fa-phone"></i> اتصال
            </button>
          </div>
        </div>
      `;
      return div;
    }
    
    function loadAdsList(category = '', city = '', priceFrom = '', priceTo = '') {
      const ads = loadAds();
      const container = document.getElementById('adsContainer');
      container.innerHTML = '';
      
      let filteredAds = ads;
      
      if (category) {
        filteredAds = filteredAds.filter(ad => ad.category === category);
      }
      
      if (city) {
        filteredAds = filteredAds.filter(ad => ad.city === city);
      }
      
      if (priceFrom) {
        filteredAds = filteredAds.filter(ad => ad.price >= parseFloat(priceFrom));
      }
      
      if (priceTo) {
        filteredAds = filteredAds.filter(ad => ad.price <= parseFloat(priceTo));
      }
      
      if (filteredAds.length === 0) {
        container.innerHTML = '<p style="text-align:center;color:var(--muted);grid-column:1/-1;">لا توجد إعلانات تطابق معايير البحث</p>';
        return;
      }
      
      filteredAds.forEach(ad => {
        container.appendChild(renderAd(ad));
      });
    }
    
    // =============== Search and Filters ===============
    document.getElementById('searchBtn').addEventListener('click', () => {
      const query = document.getElementById('searchInput').value.toLowerCase();
      const category = document.getElementById('categoryFilter').value;
      const city = document.getElementById('cityFilter').value;
      const priceFrom = document.getElementById('priceFrom').value;
      const priceTo = document.getElementById('priceTo').value;
      
      const ads = loadAds();
      const container = document.getElementById('adsContainer');
      container.innerHTML = '';
      
      const filteredAds = ads.filter(ad => {
        const matchesQuery = ad.title.toLowerCase().includes(query) || 
                             ad.description.toLowerCase().includes(query);
        const matchesCategory = !category || ad.category === category;
        const matchesCity = !city || ad.city === city;
        const matchesPriceFrom = !priceFrom || ad.price >= parseFloat(priceFrom);
        const matchesPriceTo = !priceTo || ad.price <= parseFloat(priceTo);
        
        return matchesQuery && matchesCategory && matchesCity && matchesPriceFrom && matchesPriceTo;
      });
      
      if (filteredAds.length === 0) {
        container.innerHTML = '<p style="text-align:center;color:var(--muted);grid-column:1/-1;">لا توجد إعلانات تطابق معايير البحث</p>';
        return;
      }
      
      filteredAds.forEach(ad => {
        container.appendChild(renderAd(ad));
      });
    });
    
    document.getElementById('applyFilters').addEventListener('click', () => {
      const category = document.getElementById('categoryFilter').value;
      const city = document.getElementById('cityFilter').value;
      const priceFrom = document.getElementById('priceFrom').value;
      const priceTo = document.getElementById('priceTo').value;
      loadAdsList(category, city, priceFrom, priceTo);
    });
    
    // Category links
    document.querySelectorAll('[data-category]').forEach(link => {
      link.addEventListener('click', (e) => {
        e.preventDefault();
        const category = link.getAttribute('data-category');
        loadAdsList(category);
      });
    });
    
    // =============== Chat ===============
    let currentChatId = null;
    
    function openChat(userId, userName) {
      const user = getCurrentUser();
      if (!user) {
        alert('يجب تسجيل الدخول للدردشة');
        openModal('loginModal');
        return;
      }
      
      currentChatId = userId;
      document.getElementById('chatName').textContent = userName;
      document.getElementById('chatSection').style.display = 'flex';
      document.getElementById('adsContainer').style.display = 'none';
      document.getElementById('addAdForm').style.display = 'none';
      
      loadChatMessages();
    }
    
    function loadChatMessages() {
      const chats = loadChats();
      const messages = chats[currentChatId] || [];
      const container = document.getElementById('chatMessages');
      container.innerHTML = '';
      
      messages.forEach(msg => {
        const div = document.createElement('div');
        div.className = 'message' + (msg.self ? ' self' : '');
        div.textContent = msg.text;
        container.appendChild(div);
      });
      
      container.scrollTop = container.scrollHeight;
    }
    
    document.getElementById('sendChat').addEventListener('click', () => {
      const input = document.getElementById('chatInput');
      const text = input.value.trim();
      if (!text || !currentChatId) return;
      
      const chats = loadChats();
      if (!chats[currentChatId]) chats[currentChatId] = [];
      
      const user = getCurrentUser();
      chats[currentChatId].push({
        self: true,
        text,
        timestamp: new Date().toISOString()
      });
      
      saveChats(chats);
      loadChatMessages();
      input.value = '';
    });
    
    // =============== Navigation ===============
    document.getElementById('loginBtn').addEventListener('click', () => {
      const user = getCurrentUser();
      if (!user) {
        openModal('loginModal');
      }
    });
    
    document.getElementById('addAdBtn').addEventListener('click', () => {
      const user = getCurrentUser();
      if (!user) {
        alert('يجب تسجيل الدخول لإضافة إعلان');
        openModal('loginModal');
        return;
      }
      
      document.getElementById('chatSection').style.display = 'none';
      document.getElementById('adsContainer').style.display = 'grid';
      document.getElementById('addAdForm').style.display = 'block';
    });
    
    // =============== Initialize ===============
    setTheme(getTheme());
    updateAuthUI();
    loadAdsList();
    
    // Handle Enter key in search
    document.getElementById('searchInput').addEventListener('keypress', (e) => {
      if (e.key === 'Enter') {
        document.getElementById('searchBtn').click();
      }
    });
  </script>
</body>
</html>
