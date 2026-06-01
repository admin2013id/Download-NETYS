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

        /* --- STEP 4: GENERATOR STYLES --- */
        .gen-wrapper { text-align: center; color: white; }
        .gen-title { color: #38bdf8; font-size: 22px; margin-bottom: 20px; }
        .timer { font-size: 2.5em; font-weight: bold; color: #facc15; margin: 15px 0; font-family: monospace; }
        
        .btn-gen-action {
            width: 100%; padding: 12px; border: none; border-radius: 8px;
            font-size: 16px; font-weight: bold; cursor: pointer; color: white;
            background: #3b82f6; transition: 0.3s;
        }
        .btn-gen-action:disabled { background: #475569; cursor: not-allowed; }
        .btn-create-now { background: #22c55e !important; }

        .key-result {
            background: black; color: #22c55e; font-family: monospace;
            padding: 15px; border: 1px dashed #22c55e; border-radius: 8px;
            font-size: 18px; letter-spacing: 2px; margin-top: 20px;
            display: none; word-break: break-all;
        }
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

            <!-- Tombol Download Langsung (Link Diperbarui) -->
            <a href="https://www.mediafire.com/file/lbam44ggem4ztr6/NETYSV4.apk/file" target="_blank" class="btn-action btn-download">
                <i class="fas fa-cloud-download-alt"></i> Download Aplikasi
            </a>

            <!-- Tombol Buka Generator -->
            <button onclick="switchView('view-generator')" class="btn-action btn-keygen">
                <i class="fas fa-key"></i> Ambil Kode Aksesnya
            </button>

            <button onclick="location.reload()" class="btn-back">Keluar / Logout</button>
        </div>

        <!-- === VIEW 4: KEY GENERATOR === -->
        <div id="view-generator" class="gen-wrapper hidden">
            <h2 class="gen-title">KEY GENERATOR</h2>
            
            <div id="gen-status-area">
                <p id="gen-msg" style="font-size:14px; color:#cbd5e1;">Siap membuat key baru.</p>
                <div id="gen-timer" class="timer hidden">00</div>
            </div>

            <button id="gen-btn" class="btn-gen-action" onclick="startGenProcess()">Create Generator</button>

            <div id="gen-result" class="key-result">NETYSYOONSOXIT</div>

            <button onclick="switchView('view-dashboard')" class="btn-back" style="margin-top:25px;">
                <i class="fas fa-arrow-left"></i> Kembali ke Menu
            </button>
        </div>

    </div>

    <script>
        // --- NAVIGATION LOGIC ---
        function switchView(viewId) {
            // Sembunyikan semua view
            document.querySelectorAll('.main-container > div').forEach(div => {
                div.classList.add('hidden');
                div.classList.remove('fade-in');
            });
            
            // Tampilkan view tujuan
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
        // Hitung lebar maksimal (lebar container - lebar thumb - padding)
        const maxWidth = slider.offsetWidth - thumb.offsetWidth - 4; 

        function updateSlider() {
            const percentage = Math.min(Math.max(0, currentX / maxWidth), 1);
            thumb.style.left = `${currentX + 2}px`; // +2 for border offset
            track.style.width = `${percentage * 100}%`;
        }

        function completeVerification() {
            thumb.innerHTML = '<i class="fas fa-check"></i>';
            thumb.style.background = '#22c55e';
            thumb.style.color = 'white';
            
            // Delay sedikit lalu pindah ke Login
            setTimeout(() => {
                switchView('view-login');
            }, 800);
        }

        // Event Listeners untuk Slider (Mouse & Touch)
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
                // Animasi getar sederhana
                const field = document.getElementById('access-code');
                field.style.borderColor = '#ef4444';
                setTimeout(() => field.style.borderColor = '#334155', 500);
            }
        }
        
        // Enter key untuk login
        document.getElementById('access-code').addEventListener('keypress', function (e) {
            if (e.key === 'Enter') verifyLogin();
        });


        // --- STEP 4: GENERATOR LOGIC ---
        const genBtn = document.getElementById('gen-btn');
        const genMsg = document.getElementById('gen-msg');
        const genTimer = document.getElementById('gen-timer');
        const genResult = document.getElementById('gen-result');
        const SECRET_KEY = "NETYSYOONSOXIT";

        function startGenProcess() {
            // Tahap 1: 60 Detik
            genBtn.disabled = true;
            genBtn.innerText = "Processing...";
            genMsg.innerText = "Menghubungkan ke server...";
            
            runTimer(60, () => {
                // Selesai Tahap 1
                genBtn.disabled = false;
                genBtn.innerText = "Create Now";
                genBtn.classList.add('btn-create-now');
                genMsg.innerText = "Server siap. Klik untuk generate.";
                genBtn.onclick = startFinalGen;
            });
        }

        function startFinalGen() {
            // Tahap 2: 30 Detik
            genBtn.disabled = true;
            genBtn.innerText = "Generating Key...";
            genMsg.innerText = "Sedang membuat kunci unik...";
            
            runTimer(30, () => {
                // Selesai Tahap 2
                genMsg.innerText = "Key Berhasil Dibuat!";
                genBtn.style.display = 'none';
                genResult.style.display = 'block';
                genResult.innerText = SECRET_KEY;
            });
        }

        function runTimer(seconds, callback) {
            let timeLeft = seconds;
            genTimer.classList.remove('hidden');
            genTimer.innerText = timeLeft;
            
            const interval = setInterval(() => {
                timeLeft--;
                genTimer.innerText = timeLeft;
                if(timeLeft <= 0) {
                    clearInterval(interval);
                    genTimer.classList.add('hidden');
                    callback();
                }
            }, 1000);
        }
    </script>
</body>
</html>
