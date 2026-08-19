<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>قطاع العزم الأمني</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: Tahoma, sans-serif;
        }
        body {
            background-color: #03140A; /* أخضر داكن جداً طاغي */
            color: #FFFFFF;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 20px;
        }
        /* زر القائمة العلوية */
        .menu-btn {
            position: absolute;
            top: 20px;
            right: 20px;
            background: rgba(0, 40, 15, 0.8);
            border: 1px solid #0B6623;
            color: #FFFFFF;
            padding: 10px 15px;
            border-radius: 12px;
            cursor: pointer;
            font-size: 20px;
        }
        /* الشعار والاسم */
        .profile-container {
            text-align: center;
            margin-bottom: 30px;
        }
        .logo {
            width: 100px;
            height: 100px;
            border-radius: 50%;
            border: 2px solid #0B6623;
            object-fit: cover;
            margin-bottom: 15px;
        }
        h1 {
            font-size: 24px;
            color: #FFFFFF;
            margin-bottom: 10px;
        }
        p {
            font-size: 14px;
            color: #CCCCCC;
            max-width: 300px;
            line-height: 1.5;
        }
        /* الأزرار الرئيسية */
        .main-buttons {
            display: flex;
            flex-direction: column;
            gap: 15px;
            width: 100%;
            max-width: 320px;
        }
        .btn {
            background-color: #052610;
            color: #FFFFFF;
            border: 1px solid #0B6623;
            padding: 14px;
            text-align: center;
            border-radius: 30px;
            text-decoration: none;
            font-weight: bold;
            font-size: 16px;
            transition: 0.3s;
        }
        .btn:hover {
            background-color: #0B6623;
        }
        .btn-discord {
            background-color: #0B6623;
            color: #FFFFFF;
        }
        /* نافذة القائمة المنسدلة (المينيو) */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.85);
            flex-direction: column;
            align-items: center;
            justify-content: center;
            z-index: 1000;
        }
        .modal-content {
            background: #041C0E;
            border: 1px solid #0B6623;
            width: 85%;
            max-width: 350px;
            padding: 30px 20px;
            border-radius: 20px;
            text-align: center;
            display: flex;
            flex-direction: column;
            gap: 12px;
            position: relative;
        }
        .close-btn {
            position: absolute;
            top: 15px;
            left: 15px;
            background: none;
            border: none;
            color: #FFFFFF;
            font-size: 22px;
            cursor: pointer;
        }
        .modal-link {
            background: rgba(255, 255, 255, 0.05);
            color: #FFFFFF;
            padding: 12px;
            border-radius: 10px;
            text-decoration: none;
            font-size: 15px;
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        .modal-link:hover {
            background: #0B6623;
        }
    </style>
</head>
<body>

    <!-- زر القائمة (المينيو) -->
    <button class="menu-btn" onclick="toggleMenu()">☰</button>

    <!-- واجهة الصفحة الأساسية -->
    <div class="profile-container">
        <div style="width:100px; height:100px; background:#0B6623; border-radius:50%; margin: 0 auto 15px; display:flex; align-items:center; justify-content:center; font-size:24px; font-weight:bold;">عزم</div>
        <h1>قطاع العزم الأمني</h1>
        <p>سيرفر عزم الأمني هو مجتمع متكامل يهدف لتقديم تجربة حياة واقعية فريدة من نوعها.</p>
    </div>

    <div class="main-buttons">
        <!-- استبدل # برابط سيرفر الديسكورد حقكم -->
        <a href="#" class="btn btn-discord">سيرفر الديسكورد</a>
    </div>

    <!-- نافذة القائمة المنسدلة -->
    <div class="modal" id="menuModal">
        <div class="modal-content">
            <button class="close-btn" onclick="toggleMenu()">✕</button>
            <h3 style="margin-bottom: 10px; color: #FFFFFF;">الأقسام</h3>
            <a href="#" class="modal-link">الرئيسية</a>
            <a href="#" class="modal-link">القوانين</a>
            <a href="#" class="modal-link">الشروط</a>
            <a href="#" class="modal-link">الرتب</a>
            <a href="#" class="modal-link">تقديم الوظائف</a>
        </div>
    </div>

    <script>
        function toggleMenu() {
            const modal = document.getElementById('menuModal');
            if (modal.style.display === 'flex') {
                modal.style.display = 'none';
            } else {
                modal.style.display = 'flex';
            }
        }
    </script>
</body>
</html>
