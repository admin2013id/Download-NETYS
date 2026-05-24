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
            --accent-color: #ffd700; /* Warna Emas untuk kesan premium */
            --text-dark: #1f2937;
            --text-light: #ffffff;
            --glass-bg: rgba(255, 255, 255, 0.95);
            --glass-border: rgba(255, 255, 255, 0.5);
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

        /* Background Shapes for Aesthetics */
        .shape {
            position: absolute;
            filter: blur(50px);
            z-index: 0;
            animation: float 6s infinite ease-in-out;
        }
        .shape-1 {
            top: -50px; left: -50px; width: 200px; height: 200px;
            background: rgba(255, 215, 0, 0.4);
            border-radius: 50%;
        }
        .shape-2 {
            bottom: -50px; right: -50px; width: 250px; height: 250px;
            background: rgba(255, 255, 255, 0.3);
            border-radius: 50%;
            animation-delay: 3s;
        }

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
            border: 1px solid var(--glass-border);
            padding: 40px 30px;
            border-radius: 24px;
            box-shadow: 0 20px 50px rgba(0,0,0,0.2);
            width: 90%;
            max-width: 420px;
            text-align: center;
            transition: all 0.5s ease;
        }

        /* Logo Area */
        .logo-area {
            margin-bottom: 25px;
        }
        .app-icon {
            width: 80px;
            height: 80px;
            background: linear-gradient(135deg, #1e3c72 0%, #2a5298 100%);
            border-radius: 20px;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 32px;
            box-shadow: 0 10px 20px rgba(30, 60, 114, 0.3);
            margin-bottom: 15px;
        }
        
        h1 {
            color: var(--text-dark);
            font-weight: 700;
            font-size: 26px;
            letter-spacing: -0.5px;
        }
        
        p.subtitle {
            color: #6b7280;
            font-size: 14px;
            margin-bottom: 30px;
        }

        /* Input Styles */
        .input-group {
            position: relative;
            margin-bottom: 20px;
            text-align: left;
        }
        
        .input-group label {
            display: block;
            font-size: 12px;
            color: #6b7280;
            margin-bottom: 8px;
            font-weight: 600;
            margin-left: 5px;
        }

        .input-field {
            width: 100%;
            padding: 15px 20px;
            border-radius: 12px;
            border: 2px solid #e5e7eb;
            background: #f9fafb;
            font-size: 16px;
            transition: all 0.3s;
            outline: none;
            text-align: center;
            letter-spacing: 2px;
            font-weight: 600;
            color: var(--text-dark);
        }

        .input-field:focus {
            border-color: var(--secondary-color);
            background: white;
            box-shadow: 0 0 0 4px rgba(37, 117, 252, 0.1);
        }

        /* Buttons */
        .btn {
            width: 100%;
            padding: 16px;
            border: none;
            border-radius: 14px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            text-decoration: none;
        }

        .btn-primary {
            background: linear-gradient(to right, var(--primary-color), var(--secondary-color));
            color: white;
            box-shadow: 0 10px 20px rgba(37, 117, 252, 0.3);
        }

        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 15px 25px rgba(37, 117, 252, 0.4);
        }

        .btn-whatsapp {
            background: #25D366;
            color: white;
            margin-bottom: 12px;
            box-shadow: 0 5px 15px rgba(37, 211, 102, 0.3);
        }
        
        .btn-whatsapp:hover {
            background: #20bd5a;
            transform: translateY(-2px);
        }

        .btn-outline {
            background: transparent;
            border: 2px solid #e5e7eb;
            color: #6b7280;
        }
        
        .btn-outline:hover {
            border-color: var(--text-dark);
            color: var(--text-dark);
            background: white;
        }

        /* Error Message */
        .error-msg {
            color: #ef4444;
            font-size: 13px;
            margin-top: 10px;
            display: none;
            animation: shake 0.5s;
        }

        @keyframes shake {
            0%, 100% { transform: translateX(0); }
            25% { transform: translateX(-5px); }
            75% { transform: translateX(5px); }
        }

        /* Sections Logic */
        #download-section {
            display: none;
            opacity: 0;
            transition: opacity 0.5s ease;
        }
        
        .fade-in {
            opacity: 1 !important;
        }

        /* Loading Spinner */
        .spinner {
            display: none;
            width: 20px;
            height: 20px;
            border: 3px solid rgba(255,255,255,0.3);
            border-radius: 50%;
            border-top-color: white;
            animation: spin 1s ease-in-out infinite;
        }

        @keyframes spin {
            to { transform: rotate(360deg); }
        }

    </style>
</head>
<body>

    <!-- Background Decoration -->
    <div class="shape shape-1"></div>
    <div class="shape shape-2"></div>

    <div class="container">
        
        <!-- HEADER / LOGO -->
        <div class="logo-area">
            <div class="app-icon">
                <i class="fas fa-network-wired"></i>
            </div>
            <h1>NETYS</h1>
            <p class="subtitle">Secure Application Gateway</p>
        </div>

        <!-- LOGIN SECTION -->
        <div id="login-section">
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
                <a href="https://wa.me/6285882382854?text=Halo%20admin,%20saya%20lupa%20kode%20akses%20NETYS.%20Bisa%20mintak%20bantuan?" class="btn btn-outline" style="font-size: 14px; padding: 12px;">
                    Lupa Kode Akses?
                </a>
            </div>
        </div>

        <!-- DOWNLOAD SECTION (Hidden by default) -->
        <div id="download-section">
            <div style="background: rgba(37, 211, 102, 0.1); padding: 15px; border-radius: 10px; margin-bottom: 25px; border: 1px solid rgba(37, 211, 102, 0.2);">
                <i class="fas fa-check-circle" style="color: #25D366;"></i> 
                <span style="color: #065f46; font-weight: 600; font-size: 14px;">Akses Diberikan</span>
            </div>

            <p style="margin-bottom: 20px; color: #4b5563; font-size: 15px;">
                Silakan pilih opsi di bawah ini untuk mendapatkan aplikasi dan lisensi Anda.
            </p>

            <!-- Tombol Download -->
            <a href="https://wa.me/6285882382854?text=Halo%20admin,%20saya%20sudah%20login.%20Saya%20ingin%20download%20aplikasi%20NETYS." class="btn btn-whatsapp" target="_blank">
                <i class="fab fa-whatsapp"></i> Download Sekarang
            </a>

            <!-- Tombol Ambil Kode -->
            <a href="https://wa.me/6285882382854?text=Halo%20admin,%20saya%20sudah%20login.%20Saya%20ingin%20mengambil%20Kode%20Aktivasi%20Premium." class="btn btn-whatsapp" style="background: white; color: #25D366; border: 2px solid #25D366;" target="_blank">
                <i class="fas fa-key"></i> Ambil Kode Aksesnya
            </a>
            
            <button onclick="logout()" style="margin-top: 15px; background: none; border: none; color: #9ca3af; font-size: 12px; cursor: pointer; text-decoration: underline;">
                Kembali ke Login
            </button>
        </div>

    </div>

    <script>
        // Konfigurasi Kode Akses
        const VALID_CODE = "AZFER.ID";
        const WA_NUMBER = "6285882382854";

        function verifyCode() {
            const inputCode = document.getElementById('access-code').value;
            const errorMsg = document.getElementById('error-message');
            const loginBtn = document.getElementById('login-btn');
            const btnText = document.getElementById('btn-text');
            const spinner = document.getElementById('btn-spinner');
            const loginSection = document.getElementById('login-section');
            const downloadSection = document.getElementById('download-section');

            // Reset Error
            errorMsg.style.display = 'none';

            // UI Loading State
            btnText.style.display = 'none';
            spinner.style.display = 'block';
            loginBtn.disabled = true;
            loginBtn.style.opacity = '0.7';

            // Simulasi proses verifikasi (delay 1.5 detik agar terasa "mikro")
            setTimeout(() => {
                if (inputCode === VALID_CODE) {
                    // SUKSES
                    loginSection.style.display = 'none';
                    downloadSection.style.display = 'block';
                    
                    // Tambahkan sedikit delay untuk animasi fade in
                    setTimeout(() => {
                        downloadSection.classList.add('fade-in');
                    }, 50);
                    
                } else {
                    // GAGAL
                    errorMsg.style.display = 'block';
                    document.getElementById('access-code').value = '';
                    document.getElementById('access-code').focus();
                    
                    // Kembalikan tombol ke keadaan semula
                    btnText.style.display = 'block';
                    spinner.style.display = 'none';
                    loginBtn.disabled = false;
                    loginBtn.style.opacity = '1';
                }
            }, 1200);
        }

        // Fitur tekan Enter untuk login
        document.getElementById('access-code').addEventListener("keypress", function(event) {
            if (event.key === "Enter") {
                verifyCode();
            }
        });

        function logout() {
            location.reload();
        }
    </script>
</body>
</html>
