<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>SwiftVault Vanguard | Luxury Auto Care</title>
    
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <style>
        /* =========================================
           CORE CSS VARIABLES
           ========================================= */
        :root {
            --bg-body: #050505; 
            --bg-card: #111111; 
            --text-main: #FFFFFF;
            --text-muted: #999999;
            --accent-gold: #D4AF37; 
            --accent-gold-dark: #8a7122;
            
            --transition-luxury: all 0.8s cubic-bezier(0.22, 1, 0.36, 1);
            --transition-fast: all 0.3s ease;
            --font-family: 'Montserrat', sans-serif;
            --max-width-layout: 1440px; 
        }

        * { margin: 0; padding: 0; box-sizing: border-box; outline: none; -webkit-tap-highlight-color: transparent; }
        html { scroll-behavior: smooth; font-size: 16px; background-color: var(--bg-body); color: var(--text-main); font-family: var(--font-family); overflow-x: hidden; }
        body { max-width: var(--max-width-layout); margin: 0 auto; position: relative; }

        h1, h2, h3, h4 { font-weight: 700; letter-spacing: 1px; text-transform: uppercase; }
        p { font-weight: 300; color: var(--text-muted); line-height: 1.7; }
        a { text-decoration: none; color: inherit; transition: var(--transition-fast); }

        /* =========================================
           ANIMASI REVEAL
           ========================================= */
        .vanguard-reveal { opacity: 0; transform: translateY(30px); transition: var(--transition-luxury); }
        .vanguard-reveal.active { opacity: 1; transform: translateY(0); }

        /* =========================================
           NAVIGASI (HEADER) - DIPERBAIKI ANTI NUMPUK
           ========================================= */
        header {
            position: fixed; top: 0; width: 100%; max-width: var(--max-width-layout);
            padding: 25px 50px; display: flex; justify-content: space-between; align-items: center;
            background: rgba(5, 5, 5, 0.9); backdrop-filter: blur(20px); -webkit-backdrop-filter: blur(20px);
            z-index: 1000; border-bottom: 1px solid rgba(212, 175, 55, 0.15); transition: var(--transition-fast);
        }
        .brand-logo { font-size: 22px; font-weight: 800; letter-spacing: 5px; color: var(--text-main); position: relative; }
        .brand-logo span { color: var(--accent-gold); }
        
        .nav-contact { display: flex; gap: 30px; font-size: 12px; font-weight: 500; letter-spacing: 1.5px; align-items: center;}
        .nav-contact a { display: flex; align-items: center; }
        .nav-contact a:hover { color: var(--accent-gold); }
        .nav-contact i { color: var(--accent-gold); margin-right: 8px; font-size: 16px; }

        /* KUNCIAN KHUSUS MOBILE AGAR HEADER RAPI & MENYAMPING */
        @media (max-width: 768px) {
            header { 
                padding: 15px 20px; 
                flex-direction: row; /* Memaksa ke samping, BUKAN numpuk ke bawah */
                justify-content: space-between; 
            }
            .brand-logo { font-size: 18px; letter-spacing: 3px; }
            .nav-contact { gap: 20px; }
            .contact-text { display: none; } /* Menyembunyikan teks di HP agar tidak sumpek */
            .nav-contact i { margin-right: 0; font-size: 20px; } /* Ikon diperbesar sedikit sebagai tombol */
        }

        /* =========================================
           HERO SECTION PURE CSS (ANTI GAGAL)
           ========================================= */
        .hero {
            height: 100vh; display: flex; align-items: center; justify-content: center; text-align: center; padding: 0 20px;
            background: radial-gradient(circle at center, #1a1a1a 0%, #000000 100%);
            position: relative; overflow: hidden;
        }
        .hero::before {
            content: ''; position: absolute; width: 200%; height: 200%;
            background: repeating-linear-gradient(45deg, transparent, transparent 10px, rgba(212, 175, 55, 0.03) 10px, rgba(212, 175, 55, 0.03) 20px);
            z-index: 1; opacity: 0.5;
        }
        
        .hero-content { z-index: 2; max-width: 900px; position: relative; }
        .hero-content h1 { font-size: clamp(2.5rem, 6vw, 5rem); letter-spacing: 4px; margin-bottom: 20px; color: var(--accent-gold); }
        .hero-content p { font-size: clamp(1rem, 2vw, 1.2rem); letter-spacing: 3px; margin-bottom: 40px; color: #E0E0E0; }

        .btn-luxury {
            display: inline-block; padding: 18px 45px; border: 1px solid var(--accent-gold);
            color: var(--accent-gold); font-size: 13px; font-weight: 600; letter-spacing: 3px;
            text-transform: uppercase; transition: var(--transition-fast); position: relative; overflow: hidden;
        }
        .btn-luxury:hover { background: var(--accent-gold); color: #000; }

        /* =========================================
           TAB NAVIGATION SYSTEM
           ========================================= */
        .services-section { padding: 120px 0; background-color: var(--bg-body); }
        .section-title { text-align: center; font-size: 2.2rem; letter-spacing: 5px; margin-bottom: 50px; color: var(--text-main); }
        
        .tab-container { max-width: 1200px; margin: 0 auto; padding: 0 20px; }
        .tab-nav { display: flex; justify-content: center; gap: 15px; margin-bottom: 60px; flex-wrap: wrap; border-bottom: 1px solid #222; padding-bottom: 10px; }
        
        .tab-btn {
            background: none; border: none; color: var(--text-muted); font-family: var(--font-family);
            font-size: 13px; font-weight: 600; letter-spacing: 2px; text-transform: uppercase;
            padding: 15px 30px; cursor: pointer; transition: var(--transition-fast); position: relative;
        }
        .tab-btn::after { content: ''; position: absolute; bottom: -11px; left: 0; width: 0; height: 2px; background: var(--accent-gold); transition: var(--transition-fast); }
        .tab-btn:hover { color: var(--text-main); }
        .tab-btn.active { color: var(--accent-gold); }
        .tab-btn.active::after { width: 100%; }

        .tab-content { display: none; animation: fadeIn 0.8s ease; }
        .tab-content.active { display: block; }

        @keyframes fadeIn { from { opacity: 0; transform: translateY(20px); } to { opacity: 1; transform: translateY(0); } }

        /* =========================================
           SISTEM GRID KARTU (WAJIB GENAP / DIKUNCI)
           ========================================= */
        .grid-lock { display: grid; gap: 30px; grid-template-columns: repeat(2, 1fr); }
        @media (min-width: 1024px) { .grid-lock { grid-template-columns: repeat(4, 1fr); } }

        .card { background: var(--bg-card); border: 1px solid #1A1A1A; overflow: hidden; display: flex; flex-direction: column; transition: var(--transition-luxury); cursor: pointer; }
        .card:hover { transform: translateY(-10px); border-color: rgba(212, 175, 55, 0.4); box-shadow: 0 15px 40px rgba(0,0,0,0.5); }
        
        .css-visual { 
            width: 100%; height: 200px; 
            background: linear-gradient(135deg, #181818 0%, #0a0a0a 100%); 
            display: flex; align-items: center; justify-content: center;
            border-bottom: 1px solid #222; position: relative; overflow: hidden;
            transition: var(--transition-luxury);
        }
        .css-visual::before {
            content: ''; position: absolute; width: 150px; height: 150px;
            background: radial-gradient(circle, rgba(212, 175, 55, 0.1) 0%, transparent 70%);
            transition: var(--transition-luxury);
        }
        .css-visual i { font-size: 3.5rem; color: var(--accent-gold-dark); transition: var(--transition-luxury); z-index: 2; }
        
        .card:hover .css-visual { background: linear-gradient(135deg, #222 0%, #111 100%); }
        .card:hover .css-visual i { color: var(--accent-gold); transform: scale(1.1); }
        .card:hover .css-visual::before { transform: scale(1.5); background: radial-gradient(circle, rgba(212, 175, 55, 0.2) 0%, transparent 70%); }

        .card-body { padding: 25px; display: flex; flex-direction: column; flex-grow: 1; }
        .card-body h3 { font-size: 15px; margin-bottom: 12px; color: var(--text-main); }
        .card-body p { font-size: 12px; margin-bottom: 25px; flex-grow: 1; }
        .card-price { font-size: 14px; font-weight: 700; color: var(--accent-gold); border-top: 1px solid #222; padding-top: 15px; }

        @media (max-width: 600px) {
            .grid-lock { gap: 15px; }
            .css-visual { height: 140px; }
            .css-visual i { font-size: 2.5rem; }
            .card-body { padding: 15px; }
            .card-body h3 { font-size: 12px; }
            .card-body p { font-size: 10px; margin-bottom: 15px; }
            .card-price { font-size: 11px; }
            .tab-btn { padding: 10px 15px; font-size: 10px; }
        }

        /* =========================================
           FOOTER (KONTAK & POLICIES)
           ========================================= */
        footer { padding: 80px 40px 30px; background: #020202; border-top: 1px solid #111; text-align: center; }
        .footer-logo { font-size: 26px; font-weight: 800; letter-spacing: 6px; color: var(--accent-gold); margin-bottom: 40px; }
        
        .footer-grid { display: grid; grid-template-columns: repeat(2, 1fr); max-width: 700px; margin: 0 auto 50px; gap: 30px; }
        .footer-box { background: var(--bg-card); padding: 30px; border: 1px solid #1A1A1A; transition: var(--transition-fast); }
        .footer-box:hover { border-color: var(--accent-gold); }
        .footer-box i { font-size: 28px; color: var(--accent-gold); margin-bottom: 15px; }
        .footer-box h4 { font-size: 12px; margin-bottom: 10px; }
        .footer-box p { font-size: 14px; font-weight: 600; color: var(--text-main); }

        .policy-nav { display: flex; justify-content: center; gap: 30px; border-top: 1px solid #111; padding-top: 30px; margin-bottom: 20px; flex-wrap: wrap; }
        .policy-nav a { font-size: 11px; text-transform: uppercase; letter-spacing: 2px; color: var(--text-muted); }
        .policy-nav a:hover { color: var(--accent-gold); }
        .copyright { font-size: 11px; color: #555; letter-spacing: 1px; }

        @media (max-width: 768px) {
            .footer-grid { grid-template-columns: 1fr; }
            .policy-nav { gap: 15px; }
        }
    </style>
</head>
<body>

    <header>
        <a href="#" class="brand-logo vanguard-reveal">Swift<span>Vault</span></a>
        <div class="nav-contact vanguard-reveal">
            <a href="mailto:bangunalfa@gmail.com"><i class="fa-regular fa-envelope"></i> <span class="contact-text">bangunalfa@gmail.com</span></a>
            <a href="https://wa.me/6285168805646" target="_blank"><i class="fa-brands fa-whatsapp"></i> <span class="contact-text">+62 851 6880 5646</span></a>
        </div>
    </header>

    <section class="hero">
        <div class="hero-content vanguard-reveal active">
            <h1>VANGUARD AUTO</h1>
            <p>Eksklusivitas Dalam Setiap Detail Modifikasi & Perawatan</p>
            <a href="#services" class="btn-luxury">Lihat Layanan Kami</a>
        </div>
    </section>

    <section class="services-section" id="services">
        <h2 class="section-title vanguard-reveal">Layanan Profesional</h2>
        
        <div class="tab-container">
            <div class="tab-nav vanguard-reveal">
                <button class="tab-btn active" onclick="openTab(event, 'mesin')">Engine & Tuning</button>
                <button class="tab-btn" onclick="openTab(event, 'detail')">Auto Detailing</button>
                <button class="tab-btn" onclick="openTab(event, 'kaki')">Suspension & Wheels</button>
            </div>

            <div id="mesin" class="tab-content active">
                <div class="grid-lock">
                    <div class="card vanguard-reveal">
                        <div class="css-visual"><i class="fa-solid fa-wrench"></i></div>
                        <div class="card-body">
                            <h3>Vanguard Tune-Up</h3>
                            <p>Kalibrasi ECU dan pembersihan sistem pembakaran untuk performa maksimal.</p>
                            <div class="card-price">Rp 1.500.000</div>
                        </div>
                    </div>
                    <div class="card vanguard-reveal">
                        <div class="css-visual"><i class="fa-solid fa-oil-can"></i></div>
                        <div class="card-body">
                            <h3>Premium Oil Change</h3>
                            <p>Penggantian oli sintetik performa tinggi beserta filter original.</p>
                            <div class="card-price">Rp 950.000</div>
                        </div>
                    </div>
                    <div class="card vanguard-reveal">
                        <div class="css-visual"><i class="fa-solid fa-cogs"></i></div>
                        <div class="card-body">
                            <h3>Transmission Flush</h3>
                            <p>Pengurasan total cairan transmisi agar perpindahan gigi kembali mulus.</p>
                            <div class="card-price">Rp 1.800.000</div>
                        </div>
                    </div>
                    <div class="card vanguard-reveal">
                        <div class="css-visual"><i class="fa-solid fa-fan"></i></div>
                        <div class="card-body">
                            <h3>Cooling System Pro</h3>
                            <p>Pembersihan radiator dan pengisian cairan coolant standar racing.</p>
                            <div class="card-price">Rp 850.000</div>
                        </div>
                    </div>
                    <div class="card vanguard-reveal">
                        <div class="css-visual"><i class="fa-solid fa-bolt"></i></div>
                        <div class="card-body">
                            <h3>Iridium Spark Plugs</h3>
                            <p>Penggantian busi standar dengan iridium untuk efisiensi bahan bakar.</p>
                            <div class="card-price">Rp 1.200.000</div>
                        </div>
                    </div>
                    <div class="card vanguard-reveal">
                        <div class="css-visual"><i class="fa-solid fa-gauge-high"></i></div>
                        <div class="card-body">
                            <h3>Turbo Installation</h3>
                            <p>Pemasangan kit turbocharger untuk lonjakan tenaga yang buas.</p>
                            <div class="card-price">Hubungi Kami</div>
                        </div>
                    </div>
                    <div class="card vanguard-reveal">
                        <div class="css-visual"><i class="fa-solid fa-wind"></i></div>
                        <div class="card-body">
                            <h3>Custom Exhaust</h3>
                            <p>Pembuatan sistem knalpot kustom untuk suara dan tarikan optimal.</p>
                            <div class="card-price">Mulai Rp 3.500.000</div>
                        </div>
                    </div>
                    <div class="card vanguard-reveal">
                        <div class="css-visual"><i class="fa-solid fa-chart-line"></i></div>
                        <div class="card-body">
                            <h3>Dyno Test & Remap</h3>
                            <p>Pengujian tenaga mesin aktual dan penyesuaian parameter ECU.</p>
                            <div class="card-price">Rp 2.000.000</div>
                        </div>
                    </div>
                </div>
            </div>

            <div id="detail" class="tab-content">
                <div class="grid-lock">
                    <div class="card">
                        <div class="css-visual"><i class="fa-solid fa-spray-can-sparkles"></i></div>
                        <div class="card-body">
                            <h3>Nano Ceramic 9H</h3>
                            <p>Pelapisan cat dengan kristal nano untuk kilau basah permanen.</p>
                            <div class="card-price">Rp 4.500.000</div>
                        </div>
                    </div>
                    <div class="card">
                        <div class="css-visual"><i class="fa-solid fa-car-side"></i></div>
                        <div class="card-body">
                            <h3>Interior Deep Clean</h3>
                            <p>Pembersihan vakum ekstraksi dan perawatan jok kulit mewah.</p>
                            <div class="card-price">Rp 1.200.000</div>
                        </div>
                    </div>
                    <div class="card">
                        <div class="css-visual"><i class="fa-solid fa-hands-bubbles"></i></div>
                        <div class="card-body">
                            <h3>Engine Bay Detailing</h3>
                            <p>Pembersihan uap ruang mesin agar kembali seperti keluar pabrik.</p>
                            <div class="card-price">Rp 650.000</div>
                        </div>
                    </div>
                    <div class="card">
                        <div class="css-visual"><i class="fa-solid fa-wand-magic-sparkles"></i></div>
                        <div class="card-body">
                            <h3>Paint Correction</h3>
                            <p>Penghilangan baret halus dan swirl mark sebelum proses pelapisan.</p>
                            <div class="card-price">Rp 1.800.000</div>
                        </div>
                    </div>
                </div>
            </div>

            <div id="kaki" class="tab-content">
                <div class="grid-lock">
                    <div class="card">
                        <div class="css-visual"><i class="fa-solid fa-circle-stop"></i></div>
                        <div class="card-body">
                            <h3>Big Brake Kit Upgrade</h3>
                            <p>Pemasangan sistem pengereman performa tinggi dengan kaliper besar.</p>
                            <div class="card-price">Hubungi Kami</div>
                        </div>
                    </div>
                    <div class="card">
                        <div class="css-visual"><i class="fa-solid fa-compress-alt"></i></div>
                        <div class="card-body">
                            <h3>Coilover Installation</h3>
                            <p>Setting suspensi coilover untuk kenyamanan dan handling tajam.</p>
                            <div class="card-price">Mulai Rp 6.000.000</div>
                        </div>
                    </div>
                    <div class="card">
                        <div class="css-visual"><i class="fa-solid fa-circle-notch"></i></div>
                        <div class="card-body">
                            <h3>Alloy Wheel Balancing</h3>
                            <p>Spooring dan balancing 3D untuk menjaga stabilitas roda.</p>
                            <div class="card-price">Rp 400.000</div>
                        </div>
                    </div>
                    <div class="card">
                        <div class="css-visual"><i class="fa-soli
