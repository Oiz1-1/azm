<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>قطاع العزم الأمني | BRQ STUDIO</title>
    <style>
        * { box-sizing: border-box; margin: 0; padding: 0; font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; }
        body { background-color: #030805; color: #f1f1f1; overflow-x: hidden; }
        a { text-decoration: none; color: inherit; }
        button { background: none; border: none; cursor: pointer; }

        /* --- Header & Navbar --- */
        header {
            position: fixed; top: 0; left: 0; width: 100%; height: 75px;
            background: rgba(3,8,5,0.95); border-bottom: 1px solid #0f3d1e;
            display: flex; justify-content: space-between; align-items: center;
            padding: 0 25px; z-index: 1000; backdrop-filter: blur(6px);
        }
        .logo-azm { font-size: 1.8em; font-weight: bold; letter-spacing: 2px; color: #00ff66; text-shadow: 0 0 10px rgba(0,255,102,0.5); }
        .hamburger-btn { font-size: 2.2em; color: #00ff66; border: 1px solid #0f3d1e; padding: 2px 10px; border-radius: 6px; }

        /* --- Fullscreen Menu Modal --- */
        #menu-modal {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(2,5,3,0.98); z-index: 2000;
            display: none; flex-direction: column; justify-content: center; align-items: center;
            opacity: 0; transition: opacity 0.4s ease;
        }
        #menu-modal.active { display: flex; opacity: 1; }
        .close-menu-btn { position: absolute; top: 25px; right: 35px; font-size: 3em; color: #ff3333; }
        .menu-links-container { display: flex; flex-direction: column; gap: 15px; text-align: center; width: 85%; max-width: 400px; }
        .menu-links-container a {
            font-size: 1.2em; letter-spacing: 1px; padding: 14px; border: 1px solid #0f3d1e;
            background: #08140c; color: #00ff66; transition: 0.3s; border-radius: 6px;
            box-shadow: 0 0 8px rgba(0,255,102,0.1);
        }
        .menu-links-container a:hover { background: #0f3d1e; color: #fff; }
        .menu-socials { margin-top: 25px; display: flex; gap: 15px; }
        .menu-socials a { font-size: 1em; padding: 8px 15px; background: #08140c; border: 1px solid #0f3d1e; color: #00ff66; border-radius: 6px; }

        /* --- Main Layout --- */
        main { padding: 100px 20px 40px 20px; max-width: 900px; margin: 0 auto; }
        .section-pane { display: none; animation: fadeInPane 0.4s ease; }
        .section-pane.active { display: block; }
        @keyframes fadeInPane { from { opacity: 0; transform: translateY(8px); } to { opacity: 1; transform: translateY(0); } }

        /* --- Home View (As in screenshot) --- */
        #home-view { text-align: center; }
        .hero-emblem {
            width: 130px; height: 130px; border: 2px solid #00ff66; border-radius: 50%;
            margin: 0 auto 20px auto; display: flex; align-items: center; justify-content: center;
            box-shadow: 0 0 25px rgba(0,255,102,0.4); background: #08140c; font-size: 2.5em; color: #00ff66;
        }
        .hero-title { font-size: 2.2em; color: #00ff66; margin-bottom: 12px; text-shadow: 0 0 10px rgba(0,255,102,0.3); }
        .hero-desc { color: #aaa; font-size: 0.95em; line-height: 1.6; max-width: 600px; margin: 0 auto 25px auto; }
        
        .hero-actions { display: flex; justify-content: center; gap: 15px; margin-bottom: 35px; flex-wrap: wrap; }
        .btn-discord {
            background: #00ff66; color: #030805; font-weight: bold; padding: 12px 25px;
            border-radius: 8px; font-size: 1.05em; box-shadow: 0 0 15px rgba(0,255,102,0.4); transition: 0.3s;
        }
        .btn-discord:hover { background: #fff; box-shadow: 0 0 20px #fff; }
        .btn-tiktok {
            background: #08140c; color: #00ff66; font-weight: bold; padding: 12px 25px;
            border: 1px solid #00ff66; border-radius: 8px; font-size: 1.05em; transition: 0.3s;
        }
        .btn-tiktok:hover { background: #0f3d1e; color: #fff; }

        .leaders-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(260px, 1fr)); gap: 20px; margin-top: 20px; }
        .leader-card {
            background: #08140c; border: 1px solid #0f3d1e; border-radius: 12px; padding: 20px;
            display: flex; align-items: center; gap: 15px; text-align: right; box-shadow: 0 4px 15px rgba(0,0,0,0.5);
        }
        .leader-avatar { width: 65px; height: 65px; border-radius: 50%; border: 2px solid #00ff66; object-fit: cover; background: #111; }
        .leader-info .l-role { font-size: 0.85em; color: #00ff66; margin-bottom: 4px; font-weight: bold; }
        .leader-info .l-name { font-size: 1.15em; font-weight: bold; color: #fff; }

        /* --- Sections Shared Styles --- */
        h2.section-title {
            text-align: center; margin-bottom: 30px; font-size: 1.6em; text-transform: uppercase;
            letter-spacing: 2px; color: #00ff66; border-bottom: 2px solid #0f3d1e; display: table; margin-left: auto; margin-right: auto; padding-bottom: 8px;
        }

        /* Admin & Fleet & Laws & Reports Cards */
        .admin-grid, .fleet-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(240px, 1fr)); gap: 15px; }
        .card-box { background: #08140c; border: 1px solid #0f3d1e; padding: 20px; text-align: center; border-radius: 8px; }
        .card-box .sub { color: #888; font-size: 0.85em; margin-bottom: 5px; }
        .card-box .main-txt { font-size: 1.15em; font-weight: bold; color: #00ff66; }

        /* Ranks Accordion */
        .ranks-box { display: flex; flex-direction: column; gap: 10px; }
        .rank-bar { background: #08140c; border: 1px solid #0f3d1e; padding: 15px; border-radius: 6px; cursor: pointer; display: flex; justify-content: space-between; color: #00ff66; font-weight: bold; }
        .rank-bar::after { content: '+'; }
        .rank-bar.open::after { content: '-'; }
        .rank-drop { max-height: 0; overflow: hidden; background: #050d08; border-radius: 0 0 6px 6px; padding: 0 15px; transition: max-height 0.3s; }
        .rank-drop ul { list-style: none; padding: 12px 0; }
        .rank-drop li { padding: 6px 0; border-bottom: 1px solid #0a1f12; color: #ccc; }

        /* Laws */
        .laws-content { background: #08140c; border: 1px solid #0f3d1e; padding: 25px; border-radius: 8px; }
        .laws-content ol { padding-right: 20px; }
        .laws-content li { margin-bottom: 12px; line-height: 1.6; color: #ddd; }

        /* Reports Layout */
        .reports-layout { display: grid; grid-template-columns: 1fr 1fr; gap: 20px; }
        @media(max-width: 768px) { .reports-layout { grid-template-columns: 1fr; } }
        .rep-form-wrap, .rep-feed-wrap { background: #08140c; border: 1px solid #0f3d1e; padding: 20px; border-radius: 8px; }
        .form-group { margin-bottom: 15px; }
        .form-group label { display: block; margin-bottom: 6px; color: #00ff66; font-weight: bold; font-size: 0.95em; }
        .form-group select, .form-group input { width: 100%; padding: 10px; background: #030805; border: 1px solid #0f3d1e; color: #fff; border-radius: 6px; }
        .submit-btn { width: 100%; padding: 12px; background: #00ff66; color: #030805; font-weight: bold; border-radius: 6px; cursor: pointer; transition: 0.3s; font-size: 1em; }
        .submit-btn:hover { background: #fff; }
        
        .feed-item { background: #030805; border: 1px solid #0f3d1e; padding: 12px; border-radius: 6px; margin-bottom: 12px; }
        .feed-top { display: flex; justify-content: space-between; font-size: 0.8em; color: #888; margin-bottom: 4px; }
        .feed-heading { font-weight: bold; color: #00ff66; font-size: 0.95em; }
        .feed-img-show { width: 100%; height: 120px; object-fit: cover; border-radius: 4px; margin-top: 8px; }

        /* Fleet Cards */
        .fleet-card { background: #08140c; border: 1px solid #0f3d1e; border-radius: 8px; overflow: hidden; text-align: center; }
        .fleet-img { width: 100%; height: 140px; object-fit: cover; background: #030805; }
        .fleet-txt { padding: 12px; }
        .fleet-txt .car-name { font-weight: bold; color: #fff; margin-bottom: 4px; }
        .fleet-txt .car-rank { color: #00ff66; font-size: 0.9em; }

        .back-home-bar { text-align: center; margin-bottom: 25px; }
        .back-home-btn { color: #00ff66; border: 1px solid #0f3d1e; padding: 6px 15px; border-radius: 6px; font-size: 0.9em; background: #08140c; }
    </style>
</head>
<body>

    <!-- Top Header -->
    <header>
        <div class="logo-azm">azm</div>
        <button class="hamburger-btn" onclick="toggleMenu()">&#9776;</button>
    </header>

    <!-- Fullscreen Menu Overlay -->
    <div id="menu-modal">
        <button class="close-menu-btn" onclick="toggleMenu()">&times;</button>
        <div class="menu-links-container">
            <a href="#" onclick="navigateSection('home')">الرئيسية</a>
            <a href="#" onclick="navigateSection('admin')">الإدارة العليا</a>
            <a href="#" onclick="navigateSection('ranks')">السلك العسكري والضباط</a>
            <a href="#" onclick="navigateSection('laws')">قوانين القطاع</a>
            <a href="#" onclick="navigateSection('reports')">التقارير والميدان</a>
            <a href="#" onclick="navigateSection('fleet')">أسطول الآليات</a>
        </div>
        <div class="menu-socials">
            <a href="https://discord.gg/CFvpJp2GR" target="_blank">ديسكورد</a>
            <a href="https://www.tiktok.com/@ssoh022" target="_blank">تيك توك</a>
        </div>
    </div>

    <!-- Main Content Container -->
    <main>
        
        <!-- HOME SECTION -->
        <section id="home" class="section-pane active">
            <div id="home-view">
                <div class="hero-emblem">🛡️</div>
                <h1 class="hero-title">قطاع العزم الأمنـي</h1>
                <p class="hero-desc">القطاع الأمنـي الرسمي والمجتمعي المتميز. انضم إلينا لبيئة احترافية، تنظيم عالٍ، وفعاليات حصرية.</p>
                
                <div class="hero-actions">
                    <a href="https://discord.gg/CFvpJp2GR" target="_blank" class="btn-discord">سيرفر الديسكورد</a>
                    <a href="https://www.tiktok.com/@ssoh022" target="_blank" class="btn-tiktok">حسابنا في تيك توك</a>
                </div>

                <div class="leaders-grid">
                    <div class="leader-card">
                        <img src="https://images.unsplash.com/photo-1535713875002-d1d0cf377fde?auto=format&fit=crop&w=150&q=80" alt="قائد القطاع" class="leader-avatar">
                        <div class="leader-info">
                            <div class="l-role">قائد القطاع</div>
                            <div class="l-name">اللواء سعد العتيبي</div>
                        </div>
                    </div>
                    <div class="leader-card">
                        <img src="https://images.unsplash.com/photo-1570295999919-56ceb5ecca61?auto=format&fit=crop&w=150&q=80" alt="المؤسس" class="leader-avatar">
                        <div class="leader-info">
                            <div class="l-role">ملازم أول ومؤسس</div>
                            <div class="l-name">أحمد المعشني</div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- ADMIN SECTION -->
        <section id="admin" class="section-pane">
            <div class="back-home-bar"><button class="back-home-btn" onclick="navigateSection('home')">← العودة للرئيسية</button></div>
            <h2 class="section-title">إدارة القطاع</h2>
            <div class="admin-grid">
                <div class="card-box"><div class="sub">اللواء</div><div class="main-txt">سعد العتيبي</div></div>
                <div class="card-box"><div class="sub">العميد</div><div class="main-txt">خالد القحطاني</div></div>
                <div class="card-box"><div class="sub">العقيد</div><div class="main-txt">بسام</div></div>
                <div class="card-box"><div class="sub">إداري</div><div class="main-txt">خالد</div></div>
                <div class="card-box"><div class="sub">إداري</div><div class="main-txt">عبد العزيز العتيبي</div></div>
            </div>
        </section>

        <!-- RANKS SECTION -->
        <section id="ranks" class="section-pane">
            <div class="back-home-bar"><button class="back-home-btn" onclick="navigateSection('home')">← العودة للرئيسية</button></div>
            <h2 class="section-title">السلك العسكري</h2>
            <div class="ranks-box">
                <div class="rank-bar" onclick="toggleAcc(this)">الضباط</div>
                <div class="rank-drop">
                    <ul>
                        <li>ملازم أول - أحمد المعشني (المؤسس)</li>
                        <li>ملازم - عبد العزيز العتيبي</li>
                    </ul>
                </div>
                <div class="rank-bar" onclick="toggleAcc(this)">الأفراد والرتب العسكرية</div>
                <div class="rank-drop">
                    <ul>
                        <li>رئيس رقباء</li>
                        <li>رقيب أول</li>
                        <li>عريف</li>
                        <li>جندي أول / جندي</li>
                    </ul>
                </div>
            </div>
        </section>

        <!-- LAWS SECTION -->
        <section id="laws" class="section-pane">
            <div class="back-home-bar"><button class="back-home-btn" onclick="navigateSection('home')">← العودة للرئيسية</button></div>
            <h2 class="section-title">قوانين القطاع</h2>
            <div class="laws-content">
                <ol>
                    <li><strong>شرط العمر:</strong> الحد الأدنى للقبول والانضمام للقطاع هو 14 سنة فما فوق.</li>
                    <li><strong>الآليات الرسمية:</strong> الالتزام التام بقيادة الآلية المخصصة لكل رتبة وعدم تجاوزها.</li>
                    <li><strong>الاحترام والولاء:</strong> طاعة الأوامر العسكرية واحترام القيادة العليا والأعضاء كافة.</li>
                    <li><strong>دقة البلاغات الميدانية:</strong> توثيق الحالات بحيادية وشفافية عبر النظام المعتمد.</li>
                </ol>
            </div>
        </section>

        <!-- REPORTS SECTION -->
        <section id="reports" class="section-pane">
            <div class="back-home-bar"><button class="back-home-btn" onclick="navigateSection('home')">← العودة للرئيسية</button></div>
            <h2 class="section-title">التقارير والميدان</h2>
            <div class="reports-layout">
                <div class="rep-form-wrap">
                    <form id="fieldForm" onsubmit="submitFieldReport(event)">
                        <div class="form-group">
                            <label>اسم العسكري والرتبة:</label>
                            <input type="text" id="rName" placeholder="مثال: جندي أول / فلان" required>
                        </div>
                        <div class="form-group">
                            <label>الرتبة:</label>
                            <select id="rRank">
                                <option value="جندي / جندي أول">جندي / جندي أول</option>
                                <option value="عريف">عريف</option>
                                <option value="رقيب أول">رقيب أول</option>
                                <option value="رئيس رقباء">رئيس رقباء</option>
                                <option value="ملازم / ملازم أول">ملازم / ملازم أول</option>
                            </select>
                        </div>
                        <div class="form-group">
                            <label>نوع الحالة / البلاغ:</label>
                            <select id="rType">
                                <option value="استيقاف مروري (10 نقاط)" data-pts="10">استيقاف مروري (+10 نقاط)</option>
                                <option value="مخالفة وحبس (15 نقطة)" data-pts="15">مخالفة وحبس (+15 نقطة)</option>
                                <option value="تفتيش ميداني (25 نقطة)" data-pts="25">تفتيش ميداني (+25 نقطة)</option>
                                <option value="مطاردة أمنية (50 نقطة)" data-pts="50">مطاردة أمنية (+50 نقطة)</option>
                                <option value="بلاغ تهريب كبرى (100 نقطة)" data-pts="100">بلاغ تهريب كبرى (+100 نقطة)</option>
                            </select>
                        </div>
                        <div class="form-group">
                            <label>إرفاق صورة الحدث:</label>
                            <input type="file" id="rImg" accept="image/*">
                        </div>
                        <button type="submit" class="submit-btn">تسجيل البلاغ والنشر للعلن</button>
                    </form>
                </div>
                <div class="rep-feed-wrap" id="publicFeedBox">
                    <h3 style="color:#00ff66; margin-bottom:12px; font-size:1em; border-bottom:1px solid #0f3d1e; padding-bottom:5px;">سجل البلاغات الميدانية الحية</h3>
                </div>
            </div>
        </section>

        <!-- FLEET SECTION -->
        <section id="fleet" class="section-pane">
            <div class="back-home-bar"><button class="back-home-btn" onclick="navigateSection('home')">← العودة للرئيسية</button></div>
            <h2 class="section-title">أسطول الآليات العسكرية</h2>
            <div class="fleet-grid">
                <div class="fleet-card">
                    <img src="image_7.png" class="fleet-img" alt="التاهو">
                    <div class="fleet-txt"><div class="car-name">دورية تاهو</div><div class="car-rank">مخصص للضباط</div></div>
                </div>
                <div class="fleet-card">
                    <img src="image_10.png" class="fleet-img" alt="التوريس">
                    <div class="fleet-txt"><div class="car-name">سيارة التوريس</div><div class="car-rank">رئيس رقباء</div></div>
                </div>
                <div class="fleet-card">
                    <img src="image_11.png" class="fleet-img" alt="الفورد">
                    <div class="fleet-txt"><div class="car-name">دورية الفورد</div><div class="car-rank">رقيب أول</div></div>
                </div>
                <div class="fleet-card">
                    <img src="image_3.png" class="fleet-img" alt="الربع">
                    <div class="fleet-txt"><div class="car-name">دورية الربع</div><div class="car-rank">جندي أول / جندي</div></div>
                </div>
            </div>
        </section>

    </main>

    <script>
        function toggleMenu() {
            document.getElementById('menu-modal').classList.toggle('active');
        }

        function navigateSection(id) {
            document.querySelectorAll('.section-pane').forEach(p => p.classList.remove('active'));
            document.getElementById(id).classList.add('active');
            const menu = document.getElementById('menu-modal');
            if(menu.classList.contains('active')) menu.classList.remove('active');
            window.scrollTo(0, 0);
        }

        function toggleAcc(bar) {
            bar.classList.toggle('open');
            const drop = bar.nextElementSibling;
            drop.style.maxHeight = drop.style.maxHeight ? null : drop.scrollHeight + "px";
        }

        function submitFieldReport(e) {
            e.preventDefault();
            const name = document.getElementById('rName').value;
            const rank = document.getElementById('rRank').value;
            const type = document.getElementById('rType').value;
            const fileInput = document.getElementById('rImg').files[0];

            const reader = new FileReader();
            reader.onload = function(evt) {
                const imgResult = evt.target ? evt.target.result : '';
                const feedBox = document.getElementById('publicFeedBox');
                
                const item = document.createElement('div');
                item.className = 'feed-item';
                item.innerHTML = `
                    <div class="feed-top">
                        <span>${name} (${rank})</span>
                    </div>
                    <div class="feed-heading">الحالة: ${type}</div>
                    ${imgResult ? `<img src="${imgResult}" class="feed-img-show">` : ''}
                `;
                feedBox.prepend(item);
                alert('تم تسجيل البلاغ الميداني ونشره بنجاح!');
                document.getElementById('fieldForm').reset();
                navigateSection('reports');
            };

            if(fileInput) {
                reader.readAsDataURL(fileInput);
            } else {
                reader.onload({ target: { result: '' } });
            }
        }
    </script>
</body>
</html>
