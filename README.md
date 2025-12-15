<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>AeroostStudio | استودیو ایروست</title>
    <link href="https://fonts.googleapis.com/css2?family=Vazirmatn:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --bg-primary: #0a0a0f;
            --bg-secondary: #12121a;
            --bg-card: #16161f;
            --bg-card-hover: #1c1c28;
            --text-primary: #ffffff;
            --text-secondary: #a0a0b0;
            --text-muted: #6b6b7b;
            --accent: #6366f1;
            --accent-glow: rgba(99, 102, 241, 0.15);
            --border: #2a2a3a;
            --border-hover: #3a3a4a;
        }

        body {
            font-family: 'Vazirmatn', sans-serif;
            background-color: var(--bg-primary);
            color: var(--text-primary);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            line-height: 1.7;
        }

        /* Subtle background pattern */
        body::before {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: 
                radial-gradient(ellipse at 50% 0%, var(--accent-glow) 0%, transparent 50%),
                radial-gradient(circle at 80% 80%, rgba(99, 102, 241, 0.05) 0%, transparent 40%);
            pointer-events: none;
            z-index: -1;
        }

        .container {
            max-width: 900px;
            margin: 0 auto;
            padding: 0 24px;
            width: 100%;
        }

        /* Header */
        header {
            padding: 80px 0 60px;
            text-align: center;
        }

        .logo {
            font-size: 3rem;
            font-weight: 800;
            letter-spacing: -1px;
            margin-bottom: 12px;
            background: linear-gradient(135deg, #ffffff 0%, #a0a0b0 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .tagline {
            font-size: 1.1rem;
            color: var(--text-secondary);
            font-weight: 400;
        }

        /* Main Content */
        main {
            flex: 1;
            padding: 20px 0 80px;
        }

        .section-title {
            font-size: 0.85rem;
            color: var(--text-muted);
            text-transform: uppercase;
            letter-spacing: 2px;
            margin-bottom: 24px;
            font-weight: 500;
        }

        /* Project Cards Grid */
        .projects-grid {
            display: grid;
            grid-template-columns: 1fr;
            gap: 16px;
        }

        .project-card {
            display: flex;
            align-items: center;
            justify-content: space-between;
            background: var(--bg-card);
            border: 1px solid var(--border);
            border-radius: 16px;
            padding: 28px 32px;
            text-decoration: none;
            color: inherit;
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            position: relative;
            overflow: hidden;
        }

        .project-card::before {
            content: '';
            position: absolute;
            top: 0;
            right: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(135deg, var(--accent-glow) 0%, transparent 50%);
            opacity: 0;
            transition: opacity 0.3s ease;
        }

        .project-card:hover {
            background: var(--bg-card-hover);
            border-color: var(--border-hover);
            transform: translateY(-2px);
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
        }

        .project-card:hover::before {
            opacity: 1;
        }

        .project-info {
            position: relative;
            z-index: 1;
        }

        .project-name {
            font-size: 1.25rem;
            font-weight: 600;
            margin-bottom: 6px;
            color: var(--text-primary);
        }

        .project-desc {
            font-size: 0.95rem;
            color: var(--text-secondary);
            font-weight: 400;
        }

        .project-arrow {
            position: relative;
            z-index: 1;
            width: 44px;
            height: 44px;
            display: flex;
            align-items: center;
            justify-content: center;
            background: var(--bg-secondary);
            border-radius: 12px;
            transition: all 0.3s ease;
            flex-shrink: 0;
            margin-right: 20px;
        }

        .project-arrow svg {
            width: 20px;
            height: 20px;
            color: var(--text-secondary);
            transition: all 0.3s ease;
            transform: rotate(180deg);
        }

        .project-card:hover .project-arrow {
            background: var(--accent);
        }

        .project-card:hover .project-arrow svg {
            color: white;
            transform: rotate(180deg) translateX(3px);
        }

        /* Footer */
        footer {
            padding: 40px 0;
            border-top: 1px solid var(--border);
            text-align: center;
        }

        .footer-content {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 16px;
        }

        .footer-links {
            display: flex;
            gap: 24px;
            align-items: center;
        }

        .footer-link {
            display: flex;
            align-items: center;
            gap: 8px;
            color: var(--text-secondary);
            text-decoration: none;
            font-size: 0.9rem;
            transition: color 0.2s ease;
        }

        .footer-link:hover {
            color: var(--text-primary);
        }

        .footer-link svg {
            width: 18px;
            height: 18px;
        }

        .copyright {
            font-size: 0.85rem;
            color: var(--text-muted);
        }

        /* Responsive */
        @media (min-width: 640px) {
            header {
                padding: 100px 0 80px;
            }

            .logo {
                font-size: 3.5rem;
            }

            .tagline {
                font-size: 1.2rem;
            }

            .projects-grid {
                gap: 20px;
            }

            .project-card {
                padding: 32px 40px;
            }

            .project-name {
                font-size: 1.35rem;
            }
        }

        @media (min-width: 768px) {
            .footer-content {
                flex-direction: row;
                justify-content: space-between;
            }
        }

        /* Focus styles for accessibility */
        .project-card:focus {
            outline: 2px solid var(--accent);
            outline-offset: 2px;
        }

        .footer-link:focus {
            outline: 2px solid var(--accent);
            outline-offset: 2px;
        }
    </style>
</head>
<body>
    <header>
        <div class="container">
            <h1 class="logo">AeroostStudio</h1>
            <p class="tagline">استودیو توسعه اپلیکیشن و بازی</p>
        </div>
    </header>

    <main>
        <div class="container">
            <p class="section-title">پروژه‌ها</p>
            <div class="projects-grid">
                <!-- iCircuit -->
                <a href="https://aerooststudio.github.io/iCircuit/" class="project-card">
                    <div class="project-info">
                        <h2 class="project-name">iCircuit</h2>
                        <p class="project-desc">شبیه‌ساز و ابزار آموزشی مدارهای الکترونیکی</p>
                    </div>
                    <div class="project-arrow">
                        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M17 8l4 4m0 0l-4 4m4-4H3" />
                        </svg>
                    </div>
                </a>

                <!-- Game Project -->
                <a href="https://aerooststudio.github.io/game1/" class="project-card">
                    <div class="project-info">
                        <h2 class="project-name">پروژه بازی</h2>
                        <p class="project-desc">بازی موبایلی سرگرم‌کننده و چالش‌برانگیز</p>
                    </div>
                    <div class="project-arrow">
                        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M17 8l4 4m0 0l-4 4m4-4H3" />
                        </svg>
                    </div>
                </a>

                <!-- Tool Project -->
                <a href="https://aerooststudio.github.io/tool1/" class="project-card">
                    <div class="project-info">
                        <h2 class="project-name">ابزار کاربردی</h2>
                        <p class="project-desc">ابزار و اپلیکیشن کمکی برای کارهای روزمره</p>
                    </div>
                    <div class="project-arrow">
                        <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                            <path stroke-linecap="round" stroke-linejoin="round" d="M17 8l4 4m0 0l-4 4m4-4H3" />
                        </svg>
                    </div>
                </a>
            </div>
        </div>
    </main>

    <footer>
        <div class="container">
            <div class="footer-content">
                <p class="copyright">© ۲۰۲۵ AeroostStudio — تمامی حقوق محفوظ است</p>
                <div class="footer-links">
                    <a href="https://github.com/aerooststudio" class="footer-link" target="_blank" rel="noopener noreferrer">
                        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor">
                            <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
                        </svg>
                        گیت‌هاب
                    </a>
                </div>
            </div>
        </div>
    </footer>
</body>
</html>
