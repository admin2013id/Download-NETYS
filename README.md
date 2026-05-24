<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>NETYS - Premium Access</title>
    <!-- Font Google: Poppins -->
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600;700&display=swap" rel="stylesheet">
    <!-- Icon FontAwesome -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    
    <style>
        :root {
            --primary-color: #6a11cb;
            --secondary-color: #2575fc;
            --text-dark: #1f2937;
            --glass-bg: rgba(255, 255, 255, 0.95);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Poppins', sans-serif;
        }

        body {
            background: linear-gradient(135deg, var(--primary-color) 0%, var(--secondary-color) 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow: hidden;
            position: relative;
        }

        /* Background Shapes */
        .shape {
            position: absolute;
            filter: blur(50px);
            z-index: 0;
            animation: float 6s infinite ease-in-out;
        }
        .shape-1 { top: -50px; left: -50px; width: 200px; height: 200px; background: rgba(255, 215, 0, 0.4); border-radius: 50%; }
        .shape-2 { bottom: -50px; right: -50px; width: 250px; height: 250px; background: rgba(255, 255, 255, 0.3); border-radius: 50%; animation-delay: 3s; }

        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-20px); }
        }

        /* Main Card Container */
        .container {
            position: relative;
            z-index: 10;
            background: var(--glass-bg);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            border: 1px solid rgba(255, 255, 255, 0.5);
            padding: 40px 30px;
            border-radius: 24px;
            box-shadow: 0 20px 50px rgba(0,0,0,0.2);
            width: 90%;
            max-width: 420px;
            text-align: center;
            transition: all 0.5s ease;
            min-height: 500px; /* Menjaga tinggi agar tidak kaget saat ganti tampilan */
            display: flex;
            flex-direction: column;
            justify-content: center;
        }

        /* --- STYLES FOR LOGIN & DOWNLOAD SECTION --- */
        .logo-area { margin-bottom: 25px; }
        .app-icon {
            width: 80px; height: 80px;
            background: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%);
            border-radius: 20px;
            display: inline-flex; align-items: center; justify-content: center;
            color: white; font-size: 32px;
            box-shadow: 0 10px 20px rgba(30, 60, 114, 0.3);
            margin-bottom: 15px;
        }
        
        h1 { color: var(--text-dark); font-weight: 700; font-size: 26px; letter-spacing: -0.5px; }
        p.subtitle { color: #6b7280; font-size: 14px; margin-bottom: 30px; }

        .input-group { position: relative; margin-bottom: 20px; text-align: left; }
        .input-group label { display: block; font-size: 12px; color: #6b7280; margin-bottom: 8px; font-weight: 600; margin-left: 5px; }
        .input-field {
            width: 100%; padding: 15px 20px; border-radius: 12px;
            border: 2px solid #e5e7eb; background: #f9fafb; font-size: 16px;
            transition: all 0.3s; outline: none; text-align: center; letter-spacing: 2px; font-weight: 600; color: var(--text-dark);
        }
        .input-field:focus { border-color: var(--secondary-color); background: white; box-shadow: 0 0 0 4px rgba(37, 117, 252, 0.1); }

        .btn {
            width: 100%; padding: 16px; border: none; border-radius: 14px;
            font-size: 16px; font-weight: 600; cursor: pointer; transition: all 0.3s ease;
            display: flex; align-items: center; justify-content: center; gap: 10px; text-decoration: none;
        }
        .btn-primary { background: linear-gradient(to right, var(--primary-color), var(--secondary-color)); color: white; box-shadow: 0 10px 20px rgba(37, 117, 252, 0.3); }
        .btn-primary:hover { transform: translateY(-2px); box-shadow: 0 15px 25px rgba(37, 117, 252, 0.4); }
        
        .btn-download-link { background: linear-gradient(to right, #0070ff, #00c6ff); color: white; margin-bottom: 12px; box-shadow: 0 5px 15px rgba(0, 112, 255, 0.3); }
        .btn-download-link:hover { transform: translateY(-2px); filter: brightness(1.1); }

        .btn-generator { background: #2d2d2d; color: #fff; margin-bottom: 12px; border: 1px solid #444; }
        .btn-generator:hover { background: #444; transform: translateY(-2px); }

        .btn-outline { background: transparent; border: 2px solid #e5e7eb; color: #6b7280; }
        .btn-outline:hover { border-color: var(--text-dark); color: var(--text-dark); background: white; }

        .error-msg { color: #ef4444; font-size: 13px; margin-top: 10px; display: none; animation: shake 0.5s; }
        @keyframes shake { 0%, 100% { transform: translateX(0); } 25% { transform: translateX(-5px); } 75% { transform: translateX(5px); } }

        .spinner { display: none; width: 20px; height: 20px; border: 3px solid rgba(255,255,255,0.3); border-radius: 50%; border-top-color: white; animation: spin 1s ease-in-out infinite; }
        @keyframes spin { to { transform: rotate(360deg); } }

        /* --- STYLES FOR GENERATOR SECTION (Dark Mode Style) --- */
        .generator-container {
            background-color: #2d2d2d;
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 10px 25px rgba(0,0,0,0.5);
            text-align: center;
            width: 100%;
            border: 1px solid #444;
            color: #ffffff;
            display: none; /* Hidden by default */
        }
        
        .gen-title { margin-top: 0; color: #00d2ff; font-size: 24px; margin-bottom: 20px; }
        
        .status-box { margin: 20px 0; min-height: 60px; display: flex; flex-direction: column; justify-content: center; align-items: center; }
        .timer { font-size: 2em; font-weight: bold; color: #ffcc00; margin: 10px 0; }
        
        .gen-btn {
            background-color: #007bff; color: white; border: none; padding: 12px 24px;
            font-size: 16px; border-radius: 5px; cursor: pointer; transition: background 0.3s;
            width: 100%; font-weight: bold;
        }
        .gen-btn:hover { background-color: #0056b3; }
        .gen-btn:disabled { background-color: #555; cursor: not-allowed; color: #aaa; }
        .btn-create-now { background-color: #28a745 !important; }
        .btn-create-now:hover { background-color: #218838 !important; }

        .key-display {
            background-color: #000; color: #0f0; font-family: 'Courier New', Courier, monospace;
            padding: 15px; border-radius: 5px; font-size: 1.2em; letter-spacing: 2px;
            margin-top: 10px; border: 1px dashed #0f0; display: none; word-break: break-all;
        }

        /* Utility Classes */
        .hidden { display: none !important; }
        .fade-in { animation: fadeIn 0.5s forwards; }
        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }

    </style>
</head>
<body>

    <!-- Background Decoration -->
    <div class="shape shape-1"></div>
    <div class="shape shape-2"></div>

    <div class="container">
        
        <!-- === VIEW 1: LOGIN SECTION === -->
        <div id="login-section">
            <div class="logo-area">
                <div class="app-icon"><i class="fas fa-network-wired"></i></div>
                <h1>NETYS</h1>
                <p class="subtitle">Secure Application Gateway</p>
            </div>

            <div class="input-group">
                <label for="access-code">MASUKKAN KODE AKSES</label>
                <input type="password" id="access-code" class="input-field" placeholder="••••••••" autocomplete="off">
            </div>
            
            <button onclick="verifyCode()" class="btn btn-primary" id="login-btn">
                <span id="btn-text">Verifikasi & Masuk</span>
                <div class="spinner" id="btn-spinner"></div>
            </button>
            
            <p class="error-msg" id="error-message">
                <i class="fas fa-exclamation-circle"></i> Kode akses salah! Silakan coba lagi.
            </p>
            
            <div style="margin-top: 20px;">
                <a href="#" onclick="alert('Hubungi Admin via WhatsApp jika lupa.')" class="btn btn-outline" style="font-size: 14px; padding: 12px;">
                    Lupa Kode Akses?
                </a>
            </div>
        </div>

        <!-- === VIEW 2: DOWNLOAD MENU (Hidden) === -->
        <div id="download-section" class="hidden">
            <div class="logo-area">
                <div class="app-icon"><i class="fas fa-check-circle" style="color: #25D366;"></i></div>
                <h1>Akses Diterima</h1>
                <p class="subtitle">Silakan pilih opsi di bawah ini</p>
            </div>

            <!-- Tombol 1: Download Langsung (MediaFire) -->
            <a href="https://www.mediafire.com/file/j1a1o1xa95yzgok/NETYSV4%252BBY_AZFER.apk/file" class="btn btn-download-link" target="_blank">
                <i class="fas fa-cloud-download-alt"></i> Download Sekarang
            </a>

            <!-- Tombol 2: Buka Generator Key -->
            <button onclick="showGenerator()" class="btn btn-generator">
                <i class="fas fa-key"></i> Ambil Kode Aksesnya
            </button>
            
            <button onclick="logout()" style="margin-top: 15px; background: none; border: none; color: #9ca3af; font-size: 12px; cursor: pointer; text-decoration: underline;">
                Kembali ke Login
            </button>
        </div>

        <!-- === VIEW 3: KEY GENERATOR (Hidden) === -->
        <div id="generator-view" class="generator-container">
            <h2 class="gen-title">KEY GENERATOR</h2>
            
            <!-- Area Status dan Timer -->
            <div class="status-box" id="statusArea">
                <p id="messageText" style="color:#ccc;">Klik tombol di bawah untuk memulai.</p>
                <div id="timerDisplay" class="timer hidden">00</div>
            </div>

            <!-- Tombol Aksi -->
            <button id="mainBtn" class="gen-btn" onclick="startProcess()">Create Generator</button>

            <!-- Area Hasil Key -->
            <div id="resultArea" class="key-display">
                NETYSYOONSOXIT
            </div>

            <button onclick="backToDownload()" style="margin-top: 20px; background: transparent; border: 1px solid #555; color: #888; padding: 8px; width: 100%; border-radius: 5px; cursor: pointer;">
                <i class="fas fa-arrow-left"></i> Kembali ke Menu Download
            </button>
        </div>

    </div>

    <script>
        // --- LOGIC LOGIN ---
        const VALID_CODE = "AZFER.ID";

        function verifyCode() {
            const inputCode = document.getElementById('access-code').value;
            const errorMsg = document.getElementById('error-message');
            const loginBtn = document.getElementById('login-btn');
            const btnText = document.getElementById('btn-text');
            const spinner = document.getElementById('btn-spinner');
            const loginSection = document.getElementById('login-section');
            const downloadSection = document.getElementById('download-section');

            errorMsg.style.display = 'none';
            btnText.style.display = 'none';
            spinner.style.display = 'block';
            loginBtn.disabled = true;
            loginBtn.style.opacity = '0.7';

            setTimeout(() => {
                if (inputCode === VALID_CODE) {
                    loginSection.classList.add('hidden');
                    downloadSection.classList.remove('hidden');
                    downloadSection.classList.add('fade-in');
                } else {
                    errorMsg.style.display = 'block';
                    document.getElementById('access-code').value = '';
                    document.getElementById('access-code').focus();
                    btnText.style.display = 'block';
                    spinner.style.display = 'none';
                    loginBtn.disabled = false;
                    loginBtn.style.opacity = '1';
                }
            }, 1200);
        }

        document.getElementById('access-code').addEventListener("keypress", function(event) {
            if (event.key === "Enter") verifyCode();
        });

        function logout() {
            location.reload();
        }

        // --- NAVIGASI ANTAR HALAMAN ---
        function showGenerator() {
            document.getElementById('download-section').classList.add('hidden');
            const genView = document.getElementById('generator-view');
            genView.style.display = 'block';
            genView.classList.add('fade-in');
        }

        function backToDownload() {
            document.getElementById('generator-view').style.display = 'none';
            const dlSection = document.getElementById('download-section');
            dlSection.classList.remove('hidden');
            dlSection.classList.add('fade-in');
        }

        // --- LOGIC KEY GENERATOR ---
        const mainBtn = document.getElementById('mainBtn');
        const messageText = document.getElementById('messageText');
        const timerDisplay = document.getElementById('timerDisplay');
        const resultArea = document.getElementById('resultArea');
        const SECRET_KEY = "NETYSYOONSOXIT";

        function startProcess() {
            mainBtn.disabled = true;
            mainBtn.innerText = "Processing...";
            messageText.innerText = "Sedang mempersiapkan verifikasi...";
            messageText.style.color = "#fff";
            
            startTimer(60, () => {
                enableCreateNowButton();
            });
        }

        function enableCreateNowButton() {
            mainBtn.disabled = false;
            mainBtn.innerText = "Create Now";
            mainBtn.classList.add('btn-create-now');
            messageText.innerText = "Verifikasi tahap 1 selesai. Silakan lanjutkan.";
            mainBtn.onclick = startFinalGeneration;
        }

        function startFinalGeneration() {
            mainBtn.disabled = true;
            mainBtn.innerText = "Generating Key...";
            messageText.innerText = "Sedang menghasilkan key unik...";
            
            startTimer(30, () => {
                showKey();
            });
        }

        function showKey() {
            messageText.innerText = "Key berhasil dibuat!";
            timerDisplay.classList.add('hidden');
            mainBtn.style.display = 'none';
            resultArea.style.display = 'block';
            resultArea.innerText = SECRET_KEY;
        }

        function startTimer(seconds, callback) {
            let timeLeft = seconds;
            timerDisplay.classList.remove('hidden');
            timerDisplay.innerText = timeLeft;

            const countdown = setInterval(() => {
                timeLeft--;
                timerDisplay.innerText = timeLeft;

                if (timeLeft <= 0) {
                    clearInterval(countdown);
                    timerDisplay.classList.add('hidden');
                    if (callback) callback();
                }
            }, 1000);
        }
    </script>
</body>
</html>
