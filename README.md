<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>قطاع العزم الأمني</title>
    <style>
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        @keyframes pulseLogo {
            0% { transform: scale(1); box-shadow: 0 0 15px rgba(0,255,102,0.3); }
            50% { transform: scale(1.05); box-shadow: 0 0 30px rgba(0,255,102,0.7); }
            100% { transform: scale(1); box-shadow: 0 0 15px rgba(0,255,102,0.3); }
        }
        @keyframes floatItem {
            0% { transform: translateY(0px); }
            50% { transform: translateY(-5px); }
            100% { transform: translateY(0px); }
        }

        * { margin: 0; padding: 0; box-sizing: border-box; font-family: Tahoma, sans-serif; }
        
        body { 
            background-color: #03140A; 
            color: #FFFFFF; 
            min-height: 100vh; 
            display: flex; 
            flex-direction: column; 
            align-items: center; 
            justify-content: center; 
            padding: 20px; 
            animation: fadeIn 1s ease-out;
        }
        
        .menu-btn { 
            position: absolute; 
            top: 20px; 
            right: 20px; 
            background: rgba(0, 50, 20, 0.6); 
            border: 1px solid #00FF66; 
            color: #00FF66; 
            padding: 10px 18px; 
            border-radius: 10px; 
            cursor: pointer; 
            font-size: 20px;
            transition: all 0.3s ease; 
        }
        .menu-btn:hover { 
            background: #00FF66; 
            color: #03140A; 
            transform: rotate(90deg) scale(1.1); 
        }

        .container { 
            text-align: center; 
            max-width: 600px; 
            width: 100%; 
            display: flex; 
            flex-direction: column; 
            align-items: center; 
            animation: fadeIn 1.2s ease-out;
        }
        
        .logo-container { 
            width: 130px; 
            height: 130px; 
            border-radius: 50%; 
            border: 3px solid #00FF66; 
            overflow: hidden; 
            margin-bottom: 20px; 
            background: #010A05; 
            animation: pulseLogo 3s infinite ease-in-out;
        }
        .logo-container img { 
            width: 100%; 
            height: 100%; 
            object-fit: cover; 
            transition: transform 0.5s; 
        }
        .logo-container img:hover { transform: scale(1.15); }

        h1 { 
            font-size: 26px; 
            color: #00FF66; 
            margin-bottom: 10px; 
            text-shadow: 0 0 10px rgba(0,255,102,0.4); 
        }
        
        p.desc { 
            font-size: 14px; 
            color: #CCCCCC; 
            margin-bottom: 25px; 
            line-height: 1.6; 
        }

        /* النظام التوضيحي لحالة الأقسام */
        .status-badge {
            background: rgba(0, 255, 102, 0.1);
            border: 1px dashed #00FF66;
            color: #00FF66;
            padding: 8px 15px;
            border-radius: 8px;
            font-size: 12px;
            margin-bottom: 25px;
            display: inline-block;
            box-shadow: 0 0 10px rgba(0,255,102,0.1);
        }

        .social-buttons { 
            display: flex; 
            gap: 15px; 
            width: 100%; 
            justify-content: center; 
            margin-bottom: 35px; 
        }
        
        .btn { 
            flex: 1; 
            padding: 12px; 
            border-radius: 10px; 
            text-decoration: none; 
            font-weight: bold; 
            font-size: 14px; 
            text-align: center; 
            transition: all 0.3s ease; 
            border: 1px solid #00FF66; 
        }
        .btn-discord { 
            background: #00FF66; 
            color: #03140A; 
        }
        .btn-discord:hover { 
            background: #00cc52; 
            transform: translateY(-4px); 
            box-shadow: 0 5px 15px rgba(0,255,102,0.4); 
        }
        .btn-x { 
            background: transparent; 
            color: #00FF66; 
        }
        .btn-x:hover { 
            background: rgba(0,255,102,0.15); 
            transform: translateY(-4px); 
        }

        .founders-section { 
            width: 100%; 
            border-top: 1px solid rgba(0,255,102,0.3); 
            padding-top: 25px; 
            display: flex; 
            justify-content: space-around; 
            gap: 15px; 
        }
        
        .founder-card { 
            display: flex; 
            align-items: center; 
            gap: 12px; 
            background: rgba(0, 40, 15, 0.5); 
            border: 1px solid rgba(0,255,102,0.3); 
            padding: 12px 15px; 
            border-radius: 14px; 
            width: 48%; 
            text-align: right; 
            transition: all 0.4s ease;
            animation: floatItem 4s infinite ease-in-out;
        }
        .founder-card:hover {
            transform: translateY(-8px) scale(1.02);
            border-color: #00FF66;
            box-shadow: 0 8px 20px rgba(0,255,102,0.3);
            background: rgba(0, 60, 20, 0.7);
        }
        
        .founder-img { 
            width: 48px; 
            height: 48px; 
            border-radius: 50%; 
            border: 2px solid #00FF66; 
            object-fit: cover; 
            flex-shrink: 0; 
        }
        
        .founder-info h3 { 
            font-size: 13px; 
            color: #00FF66; 
            margin-bottom: 3px; 
        }
        .founder-info p { 
            font-size: 11px; 
            color: #EEEEEE; 
        }

        /* نافذة القائمة التفاعلية */
        .modal { 
            display: none; 
            position: fixed; 
            top: 0; 
            left: 0; 
            width: 100%; 
            height: 100%; 
            background: rgba(3, 20, 10, 0.95); 
            justify-content: center; 
            align-items: center; 
            z-index: 100; 
            animation: fadeIn 0.3s ease;
        }
        .modal-content { 
            background: #052210; 
            border: 2px solid #00FF66; 
            padding: 30px; 
            border-radius: 18px; 
            width: 85%; 
            max-width: 350px; 
            text-align: center; 
            position: relative; 
            box-shadow: 0 0 35px rgba(0,255,102,0.5); 
            animation: fadeIn 0.4s ease-out;
        }
        .close-btn { 
            position: absolute; 
            top: 12px; 
            left: 15px; 
            background: none; 
            border: none; 
            color: #00FF66; 
            font-size: 22px; 
            cursor: pointer; 
            transition: transform 0.3s;
        }
        .close-btn:hover { transform: rotate(90deg); }

        .modal-links { 
            display: flex; 
            flex-direction: column; 
            gap: 12px; 
            margin-top: 20px; 
        }
        .modal-link { 
            padding: 12px; 
            background: rgba(0,255,102,0.1); 
            border: 1px solid #00FF66; 
            color: #FFFFFF; 
            text-decoration: none; 
            border-radius: 10px; 
            font-size: 14px; 
            transition: all 0.3s ease; 
        }
        .modal-link:hover { 
            background: #00FF66; 
            color: #03140A; 
            font-weight: bold; 
            transform: scale(1.03); 
        }
    </style>
</head>
<body>

    <!-- زر القائمة المتحرك -->
    <button class="menu-btn" onclick="toggleMenu()">☰</button>

    <div class="container">
        <!-- شعار القطاع بنبض مستمر -->
        <div class="logo-container">
            <img src="IMG_0347.jpeg" alt="شعار قطاع العزم الأمني">
        </div>

        <h1>قطاع العزم الأمني</h1>
        <p class="desc">القطاع الأمني الرسمي والمجتمعي المتميز. انضم إلينا لبيئة احترافية، تنظيم عالٍ، وفعاليات حصرية.</p>

        <!-- النظام التوضيحي لحالة الأقسام -->
        <div class="status-badge">
            ⚠️ تنبيه: بعض الأقسام والخدمات تحت التحديث والتطوير المستمر
        </div>

        <!-- أزرار التواصل -->
        <div class="social-buttons">
            <a href="https://discord.gg/azm" target="_blank" class="btn btn-discord">سيرفر الديسكورد</a>
            <a href="https://x.com" target="_blank" class="btn btn-x">حسابنا في X</a>
        </div>

        <!-- قسم القيادة والمؤسسين -->
        <div class="founders-section">
            <div class="founder-card">
                <img src="IMG_0349.jpeg" alt="قائد القطاع" class="founder-img">
                <div class="founder-info">
                    <h3>قائد القطاع</h3>
                    <p>قائد قطاع عزم الأمني</p>
                </div>
            </div>
            <div class="founder-card">
                <img src="IMG_8050.jpeg" alt="المؤسس" class="founder-img">
                <div class="founder-info">
                    <h3>أحمد المعشني</h3>
                    <p>ملازم أول ومؤسس</p>
                </div>
            </div>
        </div>
    </div>

    <!-- نافذة القائمة التفاعلية -->
    <div id="menuModal" class="modal">
        <div class="modal-content">
            <button class="close-btn" onclick="toggleMenu()">✕</button>
            <h2 style="color: #00FF66; font-size: 18px; margin-bottom: 5px;">قائمة القطاع</h2>
            <div class="modal-links">
                <a href="#" class="modal-link">الرئيسية</a>
                <a href="#" class="modal-link">قوانين القطاع (قريباً)</a>
                <a href="#" class="modal-link">متجر القطاع (قريباً)</a>
                <a href="#" class="modal-link">تقديم الوظائف (مفتوح)</a>
                <a href="#" class="modal-link">فريق الإدارة</a>
            </div>
        </div>
    </div>

    <script>
        function toggleMenu() {
            const modal = document.getElementById('menuModal');
            modal.style.display = modal.style.display === 'flex' ? 'none' : 'flex';
        }
    </script>
</body>
</html>
