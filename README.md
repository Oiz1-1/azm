<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>BRQ STUDIO - النظام العسكري المتطور</title>
    <style>
        * { box-sizing: border-box; margin: 0; padding: 0; }
        body { background-color: #000; color: #00ff66; font-family: monospace; min-height: 100vh; display: flex; justify-content: center; align-items: center; padding: 20px; }
        .container { width: 100%; max-width: 500px; background: #050a05; border: 2px solid #00ff66; border-radius: 12px; padding: 25px; box-shadow: 0 0 20px rgba(0, 255, 102, 0.2); }
        
        /* شاشة البوابة */
        #gateway-screen { text-align: center; }
        #gateway-screen h1 { font-size: 24px; margin-bottom: 15px; text-shadow: 0 0 10px rgba(0,255,102,0.5); }
        .btn-entry { background: #00ff66; color: #000; border: none; padding: 12px 25px; font-size: 16px; font-weight: bold; border-radius: 6px; cursor: pointer; margin-top: 15px; width: 100%; transition: 0.3s; }
        .btn-entry:hover { background: #00cc52; box-shadow: 0 0 15px #00ff66; }

        /* الواجهة الرئيسية */
        #main-system { display: none; }
        .header { border-bottom: 1px solid #00ff66; padding-bottom: 10px; margin-bottom: 15px; display: flex; justify-content: space-between; align-items: center; }
        .rank-info { font-size: 13px; color: #fff; line-height: 1.6; background: rgba(0,255,102,0.05); padding: 10px; border-radius: 6px; margin-bottom: 15px; border-right: 3px solid #00ff66; }
        
        /* قسم الروبوت */
        .bot-section { border: 1px solid #00ff66; border-radius: 8px; padding: 12px; background: #020502; }
        .bot-title { font-weight: bold; font-size: 13px; margin-bottom: 8px; border-bottom: 1px dashed #00ff66; padding-bottom: 5px; }
        #bot-output { font-size: 13px; color: #fff; margin-bottom: 10px; min-height: 40px; }
        .bot-controls { display: flex; gap: 8px; }
        input[type="text"] { flex: 1; background: #000; border: 1px solid #00ff66; color: #00ff66; padding: 8px; border-radius: 4px; outline: none; font-family: monospace; }
        .btn-exec { background: #00ff66; color: #000; border: none; padding: 8px 15px; font-weight: bold; border-radius: 4px; cursor: pointer; }
    </style>
</head>
<body>

    <div class="container">
        <!-- 1. بوابة الدخول -->
        <div id="gateway-screen">
            <h1>⚡ BRQ STUDIO ⚡</h1>
            <p style="color: #888; margin-bottom: 20px;">منطقة آمنة - يمنع الدخول غير المصرح به</p>
            <div style="font-size: 13px; color: #fff; margin-bottom: 15px; text-align: right; background: rgba(255,255,255,0.03); padding: 10px; border-radius: 5px;">
                > المؤسس: أحمد المعشني (ملازم أول)<br>
                > القائد: سعد العتيبي (لواء)
            </div>
            <button class="btn-entry" onclick="enterSystem()">فتح البوابة الأمنية</button>
        </div>

        <!-- 2. النظام الرئيسي والتحكم -->
        <div id="main-system">
            <div class="header">
                <h2>⚡ BRQ STUDIO</h2>
                <span style="font-size: 11px; color: #00ff66; border: 1px solid #00ff66; padding: 2px 6px; border-radius: 4px;">متصل</span>
            </div>

            <div class="rank-info">
                <strong>[ بيانات القيادة العليا ]</strong><br>
                • المؤسس: أحمد المعشني (ملازم أول)<br>
                • القائد العام: سعد العتيبي (لواء)<br>
                • حالة الرادار: نشط ومؤمن بالكامل.
            </div>

            <!-- وحدة الروبوت الذكي -->
            <div class="bot-section">
                <div class="bot-title">🤖 [ BRQ_AI_UNIT ] : المساعد العسكري</div>
                <div id="bot-output">> النظام جاهز لتلقي الأوامر يا قائد...</div>
                <div class="bot-controls">
                    <input type="text" id="bot-input" placeholder="اكتب أمرك هنا...">
                    <button class="btn-exec" onclick="sendBotCommand()">تنفيذ</button>
                </div>
            </div>
        </div>
    </div>

    <script>
        function enterSystem() {
            document.getElementById('gateway-screen').style.display = 'none';
            document.getElementById('main-system').style.display = 'block';
        }

        function sendBotCommand() {
            const inputField = document.getElementById('bot-input');
            const outputField = document.getElementById('bot-output');
            const cmd = inputField.value.trim();

            if (cmd === "") return;

            outputField.innerHTML = `> جارٍ تنفيذ الأمر: "${cmd}"...`;
            setTimeout(() => {
                outputField.innerHTML = `> [تم بنجاح]: تم تنفيذ الأمر العسكري بواسطة الملازم أول أحمد المعشني تحت إشراف اللواء سعد العتيبي.`;
                inputField.value = "";
            }, 800);
        }
    </script>
</body>
</html>
