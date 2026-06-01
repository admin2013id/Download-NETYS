<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>NETYS - Secure Gateway</title>
    <!-- Font Google -->
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&family=Segoe+UI&display=swap" rel="stylesheet">
    <!-- Icon FontAwesome -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    
    <style>
        /* --- GLOBAL STYLES --- */
        * { margin: 0; padding: 0; box-sizing: border-box; }
        
        body {
            font-family: 'Poppins', sans-serif;
            background: linear-gradient(135deg, #0f172a, #1e2937);
            color: #e2e8f0;
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
        }

        .main-container {
            position: relative;
            width: 90%;
            max-width: 420px;
            min-height: 500px;
            background: rgba(15, 23, 42, 0.95);
            border-radius: 20px;
            box-shadow: 0 20px 50px rgba(0, 0, 0, 0.5);
            border: 1px solid #334155;
            padding: 30px;
            text-align: center;
            transition: all 0.5s ease;
        }

        /* Utility Classes */
        .hidden { display: none !important; }
        .fade-in { animation: fadeIn 0.6s ease forwards; }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* --- STEP 1: SLIDER VERIFICATION STYLES --- */
        .slider-wrapper h1 { font-size: 24px; color: #f1f5f9; margin-bottom: 10px; }
        .divider { width: 60px; height: 3px; background: #3b82f6; margin: 10px auto 20px; border-radius: 2px; }
        .slider-desc { font-size: 14px; color: #cbd5e1; margin-bottom: 40px; }

        .slider-container {
            position: relative;
            width: 100%;
            height: 55px;
            background: #1e2937;
            border-radius: 50px;
            overflow: hidden;
            border: 2px solid #334155;
            cursor: grab;
            user-select: none;
        }

        .slider-track {
            position: absolute;
            height: 100%;
            background: linear-gradient(to right, #3b82f6, #22c55e);
            width: 0%;
            transition: width 0.1s;
        }

        .slider-thumb {
            position: absolute;
            width: 48px;
            height: 48px;
            background: white;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 20px;
            color: #334155;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.3);
            left: 2px;
            top: 1.5px;
            transition: left 0.1s;
            z-index: 2;
        }

        /* --- STEP 2: LOGIN FORM STYLES --- */
        .login-wrapper .app-icon {
            width: 70px; height: 70px;
            background: linear-gradient(135deg, #3b82f6, #2563eb);
            border-radius: 18px;
            display: inline-flex; align-items: center; justify-content: center;
            font-size: 30px; color: white;
            margin-bottom: 15px;
            box-shadow: 0 10px 20px rgba(59, 130, 246, 0.3);
        }
        
        .input-group { text-align: left; margin: 25px 0; }
        .input-group label { display: block; font-size: 12px; color: #94a3b8; margin-bottom: 8px; font-weight: 600; }
        .input-field {
            width: 100%; padding: 14px; border-radius: 12px;
            border: 2px solid #334155; background: #0f172a;
            color: white; font-size: 16px; text-align: center; letter-spacing: 2px;
            outline: none; transition: 0.3s;
        }
        .input-field:focus { border-color: #3b82f6; }

        .btn-login {
            width: 100%; padding: 14px; border: none; border-radius: 12px;
            background: linear-gradient(to right, #3b82f6, #2563eb);
            color: white; font-weight: 600; font-size: 16px; cursor: pointer;
            transition: 0.3s;
        }
        .btn-login:hover { transform: translateY(-2px); box-shadow: 0 5px 15px rgba(37, 99, 235, 0.4); }
        
        .error-msg { color: #ef4444; font-size: 13px; margin-top: 10px; display: none; }

        /* --- STEP 3: DASHBOARD MENU STYLES --- */
        .menu-wrapper h2 { color: #f8fafc; margin-bottom: 5px; }
        .status-badge {
            display: inline-block; padding: 5px 12px; background: rgba(34, 197, 94, 0.2);
            color: #4ade80; border-radius: 20px; font-size: 12px; margin-bottom: 25px;
            border: 1px solid rgba(34, 197, 94, 0.3);
        }

        .btn-action {
            width: 100%; padding: 16px; border-radius: 14px; border: none;
            font-size: 15px; font-weight: 600; cursor: pointer;
            display: flex; align-items: center; justify-content: center; gap: 10px;
            margin-bottom: 12px; transition: 0.3s; text-decoration: none;
        }

        .btn-download { background: linear-gradient(135deg, #0ea5e9, #0284c7); color: white; }
        .btn-download:hover { filter: brightness(1.1); transform: translateY(-2px); }

        .btn-keygen { background: #1e2937; color: #e2e8f0; border: 1px solid #475569; }
        .btn-keygen:hover { background: #334155; transform: translateY(-2px); }

        .btn-back { background: none; border: none; color: #64748b; font-size: 13px; cursor: pointer; margin-top: 10px; text-decoration: underline; }

    </style>
</head>
<body>

    <div class="main-container">
        
        <!-- === VIEW 1: SLIDER VERIFICATION === -->
        <div id="view-slider" class="slider-wrapper fade-in">
            <h1>Verifikasi Keamanan</h1>
            <div class="divider"></div>
            <p class="slider-desc">Geser tombol ke kanan untuk melanjutkan</p>
            
            <div class="slider-container" id="slider">
                <div class="slider-track" id="track"></div>
                <div class="slider-thumb" id="thumb">→</div>
            </div>
            
            <div style="margin-top: 30px; font-size: 12px; color: #64748b;">
                Powered by NETYS Security
            </div>
        </div>

        <!-- === VIEW 2: LOGIN PAGE === -->
        <div id="view-login" class="login-wrapper hidden">
            <div class="app-icon"><i class="fas fa-shield-alt"></i></div>
            <h2>NETYS ACCESS</h2>
            <p style="color:#94a3b8; font-size:14px;">Masukkan kode untuk masuk</p>

            <div class="input-group">
                <label>KODE AKSES</label>
                <input type="password" id="access-code" class="input-field" placeholder="••••••••">
            </div>
            
            <button onclick="verifyLogin()" class="btn-login">
                <i class="fas fa-sign-in-alt"></i> Masuk Sekarang
            </button>
            
            <p class="error-msg" id="login-error">Kode salah! Coba lagi.</p>
        </div>

        <!-- === VIEW 3: DASHBOARD MENU === -->
        <div id="view-dashboard" class="menu-wrapper hidden">
            <div class="app-icon" style="background:none; box-shadow:none; font-size:40px; color:#4ade80;">
                <i class="fas fa-check-circle"></i>
            </div>
            <h2>Akses Diterima</h2>
            <div class="status-badge">Verified User</div>

            <p style="color:#cbd5e1; font-size:14px; margin-bottom:20px;">
                Pilih tindakan di bawah ini:
            </p>

            <!-- Tombol Download Langsung (Link NETYSV4.apk) -->
            <a href="https://www.mediafire.com/file/lbam44ggem4ztr6/NETYSV4.apk/file" target="_blank" class="btn-action btn-download">
                <i class="fas fa-cloud-download-alt"></i> Download Aplikasi
            </a>

            <!-- Tombol Ambil Kode Akses (Link Eksternal) -->
            <a href="https://yx.yoonso.shop/fakelagyoonso/getkey.php?s=df9f77c9dfaffe502c73" target="_blank" class="btn-action btn-keygen">
                <i class="fas fa-key"></i> Ambil Kode Aksesnya
            </a>

            <button onclick="location.reload()" class="btn-back">Keluar / Logout</button>
        </div>

    </div>

    <script>
        // --- NAVIGATION LOGIC ---
        function switchView(viewId) {
            document.querySelectorAll('.main-container > div').forEach(div => {
                div.classList.add('hidden');
                div.classList.remove('fade-in');
            });
            const target = document.getElementById(viewId);
            target.classList.remove('hidden');
            target.classList.add('fade-in');
        }

        // --- STEP 1: SLIDER LOGIC ---
        const slider = document.getElementById('slider');
        const thumb = document.getElementById('thumb');
        const track = document.getElementById('track');
        
        let isDragging = false;
        let startX = 0;
        let currentX = 0;
        const maxWidth = slider.offsetWidth - thumb.offsetWidth - 4; 

        function updateSlider() {
            const percentage = Math.min(Math.max(0, currentX / maxWidth), 1);
            thumb.style.left = `${currentX + 2}px`;
            track.style.width = `${percentage * 100}%`;
        }

        function completeVerification() {
            thumb.innerHTML = '<i class="fas fa-check"></i>';
            thumb.style.background = '#22c55e';
            thumb.style.color = 'white';
            
            setTimeout(() => {
                switchView('view-login');
            }, 800);
        }

        const startDrag = (x) => { isDragging = true; startX = x - currentX; };
        const moveDrag = (x) => {
            if (!isDragging) return;
            currentX = Math.min(Math.max(0, x - startX), maxWidth);
            updateSlider();
        };
        const endDrag = () => {
            if (!isDragging) return;
            isDragging = false;
            if (currentX > maxWidth * 0.9) {
                completeVerification();
            } else {
                currentX = 0;
                updateSlider();
            }
        };

        thumb.addEventListener('mousedown', e => startDrag(e.clientX));
        document.addEventListener('mousemove', e => moveDrag(e.clientX));
        document.addEventListener('mouseup', endDrag);

        thumb.addEventListener('touchstart', e => startDrag(e.touches[0].clientX));
        document.addEventListener('touchmove', e => moveDrag(e.touches[0].clientX));
        document.addEventListener('touchend', endDrag);


        // --- STEP 2: LOGIN LOGIC ---
        const VALID_CODE = "AZFER.ID";

        function verifyLogin() {
            const input = document.getElementById('access-code').value;
            const errorMsg = document.getElementById('login-error');
            
            if(input === VALID_CODE) {
                switchView('view-dashboard');
            } else {
                errorMsg.style.display = 'block';
                const field = document.getElementById('access-code');
                field.style.borderColor = '#ef4444';
                setTimeout(() => field.style.borderColor = '#334155', 500);
            }
        }
        
        document.getElementById('access-code').addEventListener('keypress', function (e) {
            if (e.key === 'Enter') verifyLogin();
        });
    </script>
</body>
</html>
