<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>BotForge — Bots e Sites Premium para Discord</title>
  <meta name="description" content="Criamos e mantemos bots inteligentes e sites modernos sob medida para o seu negócio ou comunidade. Solicite seu orçamento no Discord." />
  <meta name="keywords" content="bots discord, criação de bots, manutenção de bots, sites modernos, automação, integração discord" />
  <meta property="og:title" content="BotForge — Bots e Sites Premium para Discord" />
  <meta property="og:description" content="Automatize, escale e impressione. Bots e sites sob medida para o seu negócio." />
  <meta property="og:type" content="website" />
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;500;600;700;800&family=DM+Sans:ital,opsz,wght@0,9..40,300;0,9..40,400;0,9..40,500;0,9..40,600;1,9..40,300&display=swap" rel="stylesheet" />
  <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/gsap.min.js" defer></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.5/ScrollTrigger.min.js" defer></script>

  <style>
    /* ─────────────────────────────────────────────
       RESET & BASE
    ───────────────────────────────────────────── */
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    :root {
      --bg:        #06060a;
      --surface:   #0e0e16;
      --surface2:  #131320;
      --border:    rgba(255,255,255,0.07);
      --border2:   rgba(255,255,255,0.12);
      --accent:    #5b8df6;
      --accent2:   #8b5cf6;
      --accent3:   #06b6d4;
      --glow:      rgba(91,141,246,0.35);
      --glow2:     rgba(139,92,246,0.25);
      --text:      #ededf3;
      --muted:     #7070838a;
      --muted2:    #9898aa;
      --radius:    16px;
      --radius-lg: 24px;
      --font-head: 'Syne', sans-serif;
      --font-body: 'DM Sans', sans-serif;
    }

    html { scroll-behavior: smooth; }
    body {
      background: var(--bg);
      color: var(--text);
      font-family: var(--font-body);
      font-size: 16px;
      line-height: 1.6;
      overflow-x: hidden;
      -webkit-font-smoothing: antialiased;
    }

    @media (prefers-reduced-motion: reduce) {
      *, *::before, *::after { animation-duration: 0.01ms !important; transition-duration: 0.01ms !important; }
    }

    /* ─────────────────────────────────────────────
       SCROLLBAR
    ───────────────────────────────────────────── */
    ::-webkit-scrollbar { width: 6px; }
    ::-webkit-scrollbar-track { background: var(--bg); }
    ::-webkit-scrollbar-thumb { background: var(--surface2); border-radius: 99px; }

    /* ─────────────────────────────────────────────
       FOCUS VISIBLE
    ───────────────────────────────────────────── */
    :focus-visible {
      outline: 2px solid var(--accent);
      outline-offset: 3px;
      border-radius: 4px;
    }

    /* ─────────────────────────────────────────────
       TYPOGRAPHY UTILITIES
    ───────────────────────────────────────────── */
    .gradient-text {
      background: linear-gradient(135deg, #fff 20%, var(--accent) 60%, var(--accent2) 100%);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      background-size: 200% 200%;
      animation: gradShift 6s ease-in-out infinite;
    }
    @keyframes gradShift {
      0%,100% { background-position: 0% 50%; }
      50%      { background-position: 100% 50%; }
    }

    .shimmer-text {
      background: linear-gradient(90deg, var(--muted2) 0%, #fff 40%, var(--accent) 60%, var(--muted2) 100%);
      background-size: 200% auto;
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      animation: shimmer 4s linear infinite;
    }
    @keyframes shimmer { to { background-position: -200% center; } }

    h1,h2,h3,h4 { font-family: var(--font-head); font-weight: 700; line-height: 1.15; }

    .section-label {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      font-size: 12px;
      font-weight: 600;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      color: var(--accent);
      background: rgba(91,141,246,0.1);
      border: 1px solid rgba(91,141,246,0.2);
      padding: 6px 14px;
      border-radius: 99px;
      margin-bottom: 20px;
    }

    /* ─────────────────────────────────────────────
       LAYOUT
    ───────────────────────────────────────────── */
    .container {
      width: 100%;
      max-width: 1180px;
      margin: 0 auto;
      padding: 0 24px;
    }
    section { padding: 100px 0; }
    @media (max-width: 768px) { section { padding: 72px 0; } }

    /* ─────────────────────────────────────────────
       NOISE OVERLAY
    ───────────────────────────────────────────── */
    body::before {
      content: '';
      position: fixed;
      inset: 0;
      background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='1'/%3E%3C/svg%3E");
      opacity: 0.028;
      pointer-events: none;
      z-index: 9999;
    }

    /* ─────────────────────────────────────────────
       BUTTONS
    ───────────────────────────────────────────── */
    .btn {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      font-family: var(--font-body);
      font-size: 15px;
      font-weight: 600;
      padding: 14px 28px;
      border-radius: 99px;
      border: none;
      cursor: pointer;
      text-decoration: none;
      transition: all 0.3s cubic-bezier(0.23,1,0.32,1);
      position: relative;
      overflow: hidden;
      white-space: nowrap;
    }
    .btn::before {
      content: '';
      position: absolute;
      inset: 0;
      background: radial-gradient(circle at 50% 0%, rgba(255,255,255,0.15), transparent 70%);
      opacity: 0;
      transition: opacity 0.3s;
    }
    .btn:hover::before { opacity: 1; }

    .btn-primary {
      background: linear-gradient(135deg, var(--accent), var(--accent2));
      color: #fff;
      box-shadow: 0 0 0 0 var(--glow), 0 4px 24px rgba(91,141,246,0.3);
    }
    .btn-primary:hover {
      transform: translateY(-2px) scale(1.02);
      box-shadow: 0 0 32px var(--glow), 0 8px 32px rgba(91,141,246,0.4);
    }
    .btn-primary:active { transform: translateY(0) scale(0.99); }

    .btn-ghost {
      background: rgba(255,255,255,0.05);
      color: var(--text);
      border: 1px solid var(--border2);
      backdrop-filter: blur(8px);
    }
    .btn-ghost:hover {
      background: rgba(255,255,255,0.09);
      border-color: rgba(255,255,255,0.2);
      transform: translateY(-2px);
    }

    .btn-discord {
      background: #5865F2;
      color: #fff;
      box-shadow: 0 4px 24px rgba(88,101,242,0.4);
    }
    .btn-discord:hover {
      background: #6875f5;
      transform: translateY(-2px) scale(1.02);
      box-shadow: 0 8px 40px rgba(88,101,242,0.5);
    }

    /* ─────────────────────────────────────────────
       NAV
    ───────────────────────────────────────────── */
    #nav {
      position: fixed;
      top: 0; left: 0; right: 0;
      z-index: 1000;
      padding: 16px 0;
      transition: all 0.4s cubic-bezier(0.23,1,0.32,1);
    }
    #nav.scrolled {
      background: rgba(6,6,10,0.75);
      backdrop-filter: blur(20px);
      -webkit-backdrop-filter: blur(20px);
      border-bottom: 1px solid var(--border);
      padding: 12px 0;
    }
    .nav-inner {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 24px;
    }
    .nav-logo {
      font-family: var(--font-head);
      font-size: 20px;
      font-weight: 800;
      text-decoration: none;
      background: linear-gradient(135deg, #fff 30%, var(--accent));
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      letter-spacing: -0.02em;
      display: flex;
      align-items: center;
      gap: 8px;
    }
    .nav-logo-icon {
      width: 32px; height: 32px;
      background: linear-gradient(135deg, var(--accent), var(--accent2));
      border-radius: 8px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 16px;
      flex-shrink: 0;
    }
    .nav-links {
      display: flex;
      align-items: center;
      gap: 32px;
      list-style: none;
    }
    @media (max-width: 768px) { .nav-links { display: none; } }
    .nav-links a {
      font-size: 14px;
      font-weight: 500;
      color: var(--muted2);
      text-decoration: none;
      transition: color 0.2s;
    }
    .nav-links a:hover { color: var(--text); }
    .nav-cta { display: flex; align-items: center; gap: 12px; }
    .nav-cta .btn { padding: 10px 20px; font-size: 14px; }

    /* ─────────────────────────────────────────────
       HERO
    ───────────────────────────────────────────── */
    #hero {
      min-height: 100vh;
      display: flex;
      align-items: center;
      position: relative;
      overflow: hidden;
      padding: 120px 0 80px;
    }

    /* Bg grid */
    .hero-grid {
      position: absolute;
      inset: 0;
      background-image:
        linear-gradient(rgba(255,255,255,0.03) 1px, transparent 1px),
        linear-gradient(90deg, rgba(255,255,255,0.03) 1px, transparent 1px);
      background-size: 64px 64px;
      mask-image: radial-gradient(ellipse 80% 80% at 50% 50%, black 30%, transparent 100%);
      pointer-events: none;
    }

    /* Orbs */
    .orb {
      position: absolute;
      border-radius: 50%;
      filter: blur(120px);
      pointer-events: none;
      animation: orbFloat 8s ease-in-out infinite;
    }
    .orb-1 {
      width: 600px; height: 600px;
      background: radial-gradient(circle, rgba(91,141,246,0.18) 0%, transparent 70%);
      top: -200px; left: -100px;
      animation-delay: 0s;
    }
    .orb-2 {
      width: 500px; height: 500px;
      background: radial-gradient(circle, rgba(139,92,246,0.14) 0%, transparent 70%);
      top: -100px; right: -100px;
      animation-delay: -3s;
    }
    .orb-3 {
      width: 400px; height: 400px;
      background: radial-gradient(circle, rgba(6,182,212,0.1) 0%, transparent 70%);
      bottom: 0; left: 50%;
      transform: translateX(-50%);
      animation-delay: -5s;
    }
    @keyframes orbFloat {
      0%,100% { transform: translateY(0) scale(1); }
      50%      { transform: translateY(-30px) scale(1.05); }
    }

    .hero-content {
      position: relative;
      z-index: 2;
      text-align: center;
      max-width: 820px;
      margin: 0 auto;
    }

    .hero-badge {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      background: rgba(91,141,246,0.08);
      border: 1px solid rgba(91,141,246,0.25);
      border-radius: 99px;
      padding: 8px 16px;
      font-size: 13px;
      font-weight: 500;
      color: var(--accent);
      margin-bottom: 32px;
      opacity: 0;
      transform: translateY(20px);
      animation: fadeUp 0.8s 0.2s forwards;
    }
    .hero-badge .dot {
      width: 6px; height: 6px;
      background: var(--accent);
      border-radius: 50%;
      animation: pulse 2s infinite;
    }
    @keyframes pulse {
      0%,100% { opacity: 1; box-shadow: 0 0 0 0 rgba(91,141,246,0.5); }
      50%      { opacity: 0.7; box-shadow: 0 0 0 6px rgba(91,141,246,0); }
    }

    .hero-h1 {
      font-size: clamp(40px, 7vw, 80px);
      font-weight: 800;
      letter-spacing: -0.03em;
      margin-bottom: 24px;
      opacity: 0;
      transform: translateY(24px);
      animation: fadeUp 0.9s 0.35s forwards;
      line-height: 1.1;
    }

    .hero-sub {
      font-size: clamp(16px, 2.2vw, 20px);
      font-weight: 400;
      color: var(--muted2);
      max-width: 560px;
      margin: 0 auto 40px;
      line-height: 1.7;
      opacity: 0;
      transform: translateY(24px);
      animation: fadeUp 0.9s 0.5s forwards;
    }

    .hero-actions {
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 16px;
      flex-wrap: wrap;
      opacity: 0;
      transform: translateY(24px);
      animation: fadeUp 0.9s 0.65s forwards;
    }

    .hero-visual {
      position: relative;
      margin-top: 72px;
      opacity: 0;
      transform: translateY(32px);
      animation: fadeUp 1s 0.8s forwards;
    }

    .hero-card-wrap {
      display: flex;
      justify-content: center;
      gap: 20px;
      flex-wrap: wrap;
    }

    .hero-stat-card {
      background: rgba(255,255,255,0.04);
      border: 1px solid var(--border);
      border-radius: var(--radius);
      padding: 20px 28px;
      display: flex;
      align-items: center;
      gap: 14px;
      backdrop-filter: blur(12px);
      transition: all 0.3s cubic-bezier(0.23,1,0.32,1);
    }
    .hero-stat-card:hover {
      background: rgba(255,255,255,0.07);
      border-color: var(--border2);
      transform: translateY(-4px);
      box-shadow: 0 16px 48px rgba(0,0,0,0.4);
    }
    .stat-icon {
      width: 40px; height: 40px;
      border-radius: 10px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 18px;
      flex-shrink: 0;
    }
    .stat-icon.blue { background: rgba(91,141,246,0.15); }
    .stat-icon.purple { background: rgba(139,92,246,0.15); }
    .stat-icon.cyan { background: rgba(6,182,212,0.15); }
    .stat-value { font-family: var(--font-head); font-size: 22px; font-weight: 800; }
    .stat-label { font-size: 12px; color: var(--muted2); }

    @keyframes fadeUp {
      to { opacity: 1; transform: translateY(0); }
    }

    /* ─────────────────────────────────────────────
       MARQUEE
    ───────────────────────────────────────────── */
    .marquee-section {
      padding: 0;
      overflow: hidden;
      border-top: 1px solid var(--border);
      border-bottom: 1px solid var(--border);
      background: rgba(255,255,255,0.015);
    }
    .marquee-track {
      display: flex;
      width: max-content;
      animation: marquee 30s linear infinite;
    }
    .marquee-track:hover { animation-play-state: paused; }
    @keyframes marquee { to { transform: translateX(-50%); } }
    .marquee-item {
      display: flex;
      align-items: center;
      gap: 10px;
      padding: 16px 32px;
      font-size: 13px;
      font-weight: 500;
      letter-spacing: 0.08em;
      text-transform: uppercase;
      color: var(--muted2);
      white-space: nowrap;
      flex-shrink: 0;
    }
    .marquee-item .sep {
      width: 4px; height: 4px;
      background: var(--accent);
      border-radius: 50%;
      opacity: 0.6;
    }
    .marquee-item:hover { color: var(--text); }

    /* ─────────────────────────────────────────────
       SECTION HEADER
    ───────────────────────────────────────────── */
    .sec-header {
      text-align: center;
      margin-bottom: 64px;
    }
    .sec-header h2 {
      font-size: clamp(28px, 4.5vw, 52px);
      letter-spacing: -0.03em;
      margin-bottom: 16px;
    }
    .sec-header p {
      font-size: clamp(15px, 1.8vw, 18px);
      color: var(--muted2);
      max-width: 520px;
      margin: 0 auto;
      line-height: 1.7;
    }

    /* ─────────────────────────────────────────────
       SERVICES — BENTO GRID
    ───────────────────────────────────────────── */
    #services { background: linear-gradient(180deg, var(--bg) 0%, var(--surface) 100%); }

    .bento {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 16px;
    }
    @media (max-width: 900px) { .bento { grid-template-columns: repeat(2, 1fr); } }
    @media (max-width: 560px) { .bento { grid-template-columns: 1fr; } }

    .bento-card {
      background: var(--surface2);
      border: 1px solid var(--border);
      border-radius: var(--radius-lg);
      padding: 32px;
      position: relative;
      overflow: hidden;
      transition: all 0.4s cubic-bezier(0.23,1,0.32,1);
      cursor: default;
    }
    .bento-card::before {
      content: '';
      position: absolute;
      inset: 0;
      background: radial-gradient(circle at var(--mx,50%) var(--my,50%), rgba(91,141,246,0.08) 0%, transparent 60%);
      opacity: 0;
      transition: opacity 0.4s;
    }
    .bento-card:hover::before { opacity: 1; }
    .bento-card:hover {
      border-color: var(--border2);
      transform: translateY(-4px) scale(1.01);
      box-shadow: 0 20px 60px rgba(0,0,0,0.5), 0 0 0 1px rgba(91,141,246,0.1);
    }

    .bento-card.span-2 { grid-column: span 2; }
    @media (max-width: 900px) { .bento-card.span-2 { grid-column: span 2; } }
    @media (max-width: 560px) { .bento-card.span-2 { grid-column: span 1; } }

    .card-icon {
      width: 52px; height: 52px;
      border-radius: 14px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 22px;
      margin-bottom: 20px;
      position: relative;
      z-index: 1;
    }
    .card-icon.blue   { background: rgba(91,141,246,0.12);  box-shadow: 0 0 24px rgba(91,141,246,0.15); }
    .card-icon.purple { background: rgba(139,92,246,0.12);  box-shadow: 0 0 24px rgba(139,92,246,0.15); }
    .card-icon.cyan   { background: rgba(6,182,212,0.12);   box-shadow: 0 0 24px rgba(6,182,212,0.15); }
    .card-icon.green  { background: rgba(34,197,94,0.12);   box-shadow: 0 0 24px rgba(34,197,94,0.12); }

    .bento-card h3 {
      font-size: 18px;
      font-weight: 700;
      margin-bottom: 10px;
      position: relative; z-index: 1;
      letter-spacing: -0.02em;
    }
    .bento-card p {
      font-size: 14px;
      line-height: 1.65;
      color: var(--muted2);
      position: relative; z-index: 1;
    }
    .bento-tags {
      display: flex;
      flex-wrap: wrap;
      gap: 8px;
      margin-top: 20px;
      position: relative; z-index: 1;
    }
    .tag {
      font-size: 11px;
      font-weight: 600;
      padding: 4px 12px;
      border-radius: 99px;
      border: 1px solid rgba(255,255,255,0.08);
      background: rgba(255,255,255,0.04);
      color: var(--muted2);
      letter-spacing: 0.04em;
    }
    .tag.accent { border-color: rgba(91,141,246,0.3); background: rgba(91,141,246,0.08); color: var(--accent); }

    /* ─────────────────────────────────────────────
       HOW IT WORKS
    ───────────────────────────────────────────── */
    #how { position: relative; }
    #how::before {
      content: '';
      position: absolute;
      left: 50%;
      top: 0; bottom: 0;
      width: 1px;
      background: linear-gradient(180deg, transparent 0%, var(--border2) 20%, var(--border2) 80%, transparent 100%);
      transform: translateX(-50%);
      pointer-events: none;
    }
    @media (max-width: 768px) { #how::before { display: none; } }

    .steps-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 32px 80px;
      position: relative;
    }
    @media (max-width: 768px) {
      .steps-grid { grid-template-columns: 1fr; gap: 24px; }
    }

    .step-card {
      background: var(--surface2);
      border: 1px solid var(--border);
      border-radius: var(--radius-lg);
      padding: 36px 32px;
      position: relative;
      overflow: hidden;
      transition: all 0.4s cubic-bezier(0.23,1,0.32,1);
    }
    .step-card:hover {
      border-color: var(--border2);
      box-shadow: 0 16px 48px rgba(0,0,0,0.4);
      transform: translateY(-4px);
    }
    .step-number {
      font-family: var(--font-head);
      font-size: 72px;
      font-weight: 800;
      line-height: 1;
      position: absolute;
      top: 16px; right: 24px;
      background: linear-gradient(135deg, rgba(255,255,255,0.05), rgba(255,255,255,0.02));
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      background-clip: text;
      pointer-events: none;
      user-select: none;
    }
    .step-chip {
      display: inline-flex;
      align-items: center;
      gap: 6px;
      font-size: 11px;
      font-weight: 700;
      text-transform: uppercase;
      letter-spacing: 0.1em;
      padding: 5px 12px;
      border-radius: 99px;
      background: rgba(91,141,246,0.1);
      color: var(--accent);
      border: 1px solid rgba(91,141,246,0.2);
      margin-bottom: 16px;
    }
    .step-card h3 {
      font-size: 20px;
      letter-spacing: -0.02em;
      margin-bottom: 10px;
    }
    .step-card p { font-size: 14px; color: var(--muted2); line-height: 1.65; }

    /* ─────────────────────────────────────────────
       PRICING
    ───────────────────────────────────────────── */
    #pricing { background: linear-gradient(180deg, var(--surface) 0%, var(--bg) 100%); }

    .pricing-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 20px;
      align-items: start;
    }
    @media (max-width: 900px) { .pricing-grid { grid-template-columns: 1fr; max-width: 420px; margin: 0 auto; } }

    .pricing-card {
      background: var(--surface2);
      border: 1px solid var(--border);
      border-radius: var(--radius-lg);
      padding: 36px 32px;
      position: relative;
      overflow: hidden;
      transition: all 0.4s cubic-bezier(0.23,1,0.32,1);
    }
    .pricing-card:hover {
      transform: translateY(-6px);
      box-shadow: 0 24px 64px rgba(0,0,0,0.5);
    }
    .pricing-card.featured {
      border-color: rgba(91,141,246,0.4);
      background: linear-gradient(135deg, rgba(91,141,246,0.08), rgba(139,92,246,0.05));
      box-shadow: 0 0 60px rgba(91,141,246,0.12), inset 0 1px 0 rgba(255,255,255,0.08);
    }
    .pricing-card.featured:hover {
      box-shadow: 0 24px 80px rgba(91,141,246,0.25), inset 0 1px 0 rgba(255,255,255,0.1);
    }
    .pricing-badge {
      position: absolute;
      top: 20px; right: 20px;
      font-size: 10px;
      font-weight: 700;
      text-transform: uppercase;
      letter-spacing: 0.12em;
      padding: 5px 12px;
      border-radius: 99px;
      background: linear-gradient(135deg, var(--accent), var(--accent2));
      color: #fff;
    }
    .plan-name {
      font-size: 13px;
      font-weight: 600;
      letter-spacing: 0.08em;
      text-transform: uppercase;
      color: var(--muted2);
      margin-bottom: 12px;
    }
    .plan-price {
      font-family: var(--font-head);
      font-size: 48px;
      font-weight: 800;
      letter-spacing: -0.04em;
      margin-bottom: 4px;
      line-height: 1;
    }
    .plan-price span { font-size: 20px; font-weight: 500; color: var(--muted2); vertical-align: super; }
    .plan-note {
      font-size: 12px;
      color: var(--muted2);
      margin-bottom: 28px;
    }
    .plan-divider {
      height: 1px;
      background: var(--border);
      margin-bottom: 24px;
    }
    .plan-features {
      list-style: none;
      display: flex;
      flex-direction: column;
      gap: 12px;
      margin-bottom: 32px;
    }
    .plan-features li {
      display: flex;
      align-items: flex-start;
      gap: 10px;
      font-size: 14px;
      color: var(--muted2);
      line-height: 1.5;
    }
    .plan-features li .check {
      width: 18px; height: 18px;
      border-radius: 50%;
      background: rgba(91,141,246,0.12);
      border: 1px solid rgba(91,141,246,0.25);
      display: flex; align-items: center; justify-content: center;
      flex-shrink: 0;
      font-size: 10px;
      color: var(--accent);
      margin-top: 2px;
    }

    /* ─────────────────────────────────────────────
       TRUST / TESTIMONIALS
    ───────────────────────────────────────────── */
    #trust { position: relative; overflow: hidden; }
    #trust::before {
      content: '';
      position: absolute;
      width: 600px; height: 600px;
      border-radius: 50%;
      background: radial-gradient(circle, rgba(91,141,246,0.07) 0%, transparent 70%);
      top: 50%; left: 50%;
      transform: translate(-50%, -50%);
      pointer-events: none;
    }

    .trust-grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 16px;
      margin-bottom: 64px;
    }
    @media (max-width: 768px) { .trust-grid { grid-template-columns: 1fr; } }

    .trust-card {
      background: var(--surface2);
      border: 1px solid var(--border);
      border-radius: var(--radius);
      padding: 28px;
      transition: all 0.3s;
    }
    .trust-card:hover {
      border-color: var(--border2);
      transform: translateY(-3px);
      box-shadow: 0 12px 40px rgba(0,0,0,0.4);
    }
    .stars {
      display: flex;
      gap: 3px;
      margin-bottom: 16px;
    }
    .star { color: #f59e0b; font-size: 14px; }
    .trust-card blockquote {
      font-size: 14px;
      line-height: 1.7;
      color: var(--muted2);
      margin-bottom: 20px;
      font-style: italic;
    }
    .trust-author {
      display: flex;
      align-items: center;
      gap: 10px;
    }
    .avatar {
      width: 36px; height: 36px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 14px;
      font-weight: 700;
      color: #fff;
      flex-shrink: 0;
    }
    .author-name { font-size: 14px; font-weight: 600; }
    .author-role { font-size: 12px; color: var(--muted2); }

    .benefits-row {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 16px;
    }
    @media (max-width: 900px) { .benefits-row { grid-template-columns: repeat(2, 1fr); } }
    @media (max-width: 480px) { .benefits-row { grid-template-columns: 1fr; } }

    .benefit {
      display: flex;
      align-items: flex-start;
      gap: 14px;
      padding: 20px;
      background: rgba(255,255,255,0.02);
      border: 1px solid var(--border);
      border-radius: var(--radius);
      transition: all 0.3s;
    }
    .benefit:hover { background: rgba(255,255,255,0.04); border-color: var(--border2); }
    .benefit-icon {
      font-size: 20px;
      width: 40px; height: 40px;
      display: flex; align-items: center; justify-content: center;
      background: rgba(91,141,246,0.1);
      border-radius: 10px;
      flex-shrink: 0;
    }
    .benefit-text strong {
      display: block;
      font-size: 14px;
      font-weight: 600;
      margin-bottom: 4px;
    }
    .benefit-text span { font-size: 13px; color: var(--muted2); line-height: 1.5; }

    /* ─────────────────────────────────────────────
       FAQ
    ───────────────────────────────────────────── */
    #faq { background: linear-gradient(180deg, var(--bg) 0%, var(--surface) 100%); }

    .faq-list {
      max-width: 720px;
      margin: 0 auto;
      display: flex;
      flex-direction: column;
      gap: 12px;
    }
    .faq-item {
      background: var(--surface2);
      border: 1px solid var(--border);
      border-radius: var(--radius);
      overflow: hidden;
      transition: border-color 0.3s;
    }
    .faq-item.open { border-color: rgba(91,141,246,0.3); }

    .faq-q {
      width: 100%;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 16px;
      padding: 22px 24px;
      background: none;
      border: none;
      cursor: pointer;
      text-align: left;
      font-family: var(--font-body);
      font-size: 15px;
      font-weight: 600;
      color: var(--text);
      transition: background 0.2s;
    }
    .faq-q:hover { background: rgba(255,255,255,0.03); }
    .faq-icon {
      width: 28px; height: 28px;
      border-radius: 50%;
      border: 1px solid var(--border2);
      display: flex;
      align-items: center;
      justify-content: center;
      flex-shrink: 0;
      font-size: 14px;
      color: var(--muted2);
      transition: all 0.3s;
    }
    .faq-item.open .faq-icon {
      background: rgba(91,141,246,0.12);
      border-color: rgba(91,141,246,0.3);
      color: var(--accent);
      transform: rotate(45deg);
    }
    .faq-a {
      max-height: 0;
      overflow: hidden;
      transition: max-height 0.4s cubic-bezier(0.23,1,0.32,1);
    }
    .faq-a-inner {
      padding: 0 24px 22px;
      font-size: 14px;
      color: var(--muted2);
      line-height: 1.7;
    }

    /* ─────────────────────────────────────────────
       CTA BANNER
    ───────────────────────────────────────────── */
    #cta-banner {
      padding: 80px 0;
      position: relative;
      overflow: hidden;
    }
    .cta-inner {
      background: linear-gradient(135deg, rgba(91,141,246,0.12) 0%, rgba(139,92,246,0.1) 100%);
      border: 1px solid rgba(91,141,246,0.25);
      border-radius: 28px;
      padding: 72px 48px;
      text-align: center;
      position: relative;
      overflow: hidden;
    }
    .cta-inner::before {
      content: '';
      position: absolute;
      width: 500px; height: 500px;
      background: radial-gradient(circle, rgba(91,141,246,0.15), transparent 70%);
      top: 50%; left: 50%;
      transform: translate(-50%,-50%);
      pointer-events: none;
    }
    .cta-inner h2 {
      font-size: clamp(26px, 4vw, 44px);
      letter-spacing: -0.03em;
      margin-bottom: 16px;
      position: relative; z-index: 1;
    }
    .cta-inner p {
      font-size: 17px;
      color: var(--muted2);
      max-width: 460px;
      margin: 0 auto 40px;
      position: relative; z-index: 1;
      line-height: 1.7;
    }
    .cta-actions {
      display: flex;
      justify-content: center;
      gap: 16px;
      flex-wrap: wrap;
      position: relative; z-index: 1;
    }

    /* ─────────────────────────────────────────────
       FOOTER
    ───────────────────────────────────────────── */
    footer {
      padding: 48px 0 32px;
      border-top: 1px solid var(--border);
    }
    .footer-grid {
      display: grid;
      grid-template-columns: 1.5fr 1fr 1fr;
      gap: 48px;
      margin-bottom: 48px;
    }
    @media (max-width: 768px) {
      .footer-grid { grid-template-columns: 1fr; gap: 32px; }
    }
    .footer-brand p {
      font-size: 14px;
      color: var(--muted2);
      max-width: 280px;
      margin: 12px 0 24px;
      line-height: 1.7;
    }
    .social-links {
      display: flex;
      gap: 12px;
    }
    .social-link {
      width: 38px; height: 38px;
      border-radius: 10px;
      border: 1px solid var(--border);
      background: rgba(255,255,255,0.03);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 16px;
      text-decoration: none;
      color: var(--muted2);
      transition: all 0.25s;
    }
    .social-link:hover {
      background: rgba(255,255,255,0.08);
      border-color: var(--border2);
      color: var(--text);
      transform: translateY(-2px);
    }
    .footer-col h4 {
      font-size: 13px;
      font-weight: 700;
      text-transform: uppercase;
      letter-spacing: 0.08em;
      color: var(--text);
      margin-bottom: 16px;
    }
    .footer-col ul { list-style: none; display: flex; flex-direction: column; gap: 10px; }
    .footer-col ul a {
      font-size: 14px;
      color: var(--muted2);
      text-decoration: none;
      transition: color 0.2s;
    }
    .footer-col ul a:hover { color: var(--text); }
    .footer-bottom {
      display: flex;
      align-items: center;
      justify-content: space-between;
      flex-wrap: wrap;
      gap: 16px;
      border-top: 1px solid var(--border);
      padding-top: 24px;
    }
    .footer-bottom p { font-size: 13px; color: var(--muted2); }

    /* ─────────────────────────────────────────────
       SCROLL REVEAL
    ───────────────────────────────────────────── */
    .reveal {
      opacity: 0;
      transform: translateY(32px);
      transition: opacity 0.7s cubic-bezier(0.23,1,0.32,1), transform 0.7s cubic-bezier(0.23,1,0.32,1);
    }
    .reveal.visible {
      opacity: 1;
      transform: translateY(0);
    }
    .reveal-delay-1 { transition-delay: 0.1s; }
    .reveal-delay-2 { transition-delay: 0.2s; }
    .reveal-delay-3 { transition-delay: 0.3s; }
    .reveal-delay-4 { transition-delay: 0.4s; }

    /* ─────────────────────────────────────────────
       CUSTOM CURSOR (desktop only)
    ───────────────────────────────────────────── */
    @media (pointer: fine) {
      body { cursor: none; }
      a, button { cursor: none; }
      #cursor {
        position: fixed;
        width: 10px; height: 10px;
        border-radius: 50%;
        background: var(--accent);
        pointer-events: none;
        z-index: 10000;
        transform: translate(-50%, -50%);
        transition: width 0.3s, height 0.3s, opacity 0.3s;
        mix-blend-mode: normal;
      }
      #cursor-ring {
        position: fixed;
        width: 36px; height: 36px;
        border-radius: 50%;
        border: 1.5px solid rgba(91,141,246,0.5);
        pointer-events: none;
        z-index: 9999;
        transform: translate(-50%, -50%);
        transition: transform 0.12s cubic-bezier(0.23,1,0.32,1), width 0.3s, height 0.3s, border-color 0.3s;
      }
      body:has(a:hover) #cursor, body:has(button:hover) #cursor {
        width: 16px; height: 16px;
        opacity: 0.8;
      }
    }
    @media (pointer: coarse) {
      #cursor, #cursor-ring { display: none; }
    }

    /* ─────────────────────────────────────────────
       MOBILE NAV TOGGLE
    ───────────────────────────────────────────── */
    .nav-toggle {
      display: none;
      flex-direction: column;
      gap: 5px;
      background: none;
      border: none;
      cursor: pointer;
      padding: 8px;
    }
    @media (max-width: 768px) { .nav-toggle { display: flex; } }
    .nav-toggle span {
      display: block;
      width: 22px; height: 2px;
      background: var(--text);
      border-radius: 2px;
      transition: all 0.3s;
    }

    .nav-mobile {
      display: none;
      position: fixed;
      top: 64px; left: 0; right: 0;
      background: rgba(6,6,10,0.97);
      backdrop-filter: blur(20px);
      border-bottom: 1px solid var(--border);
      padding: 24px;
      z-index: 999;
      flex-direction: column;
      gap: 16px;
    }
    .nav-mobile.open { display: flex; }
    .nav-mobile a {
      font-size: 16px;
      font-weight: 500;
      color: var(--muted2);
      text-decoration: none;
      padding: 10px 0;
      border-bottom: 1px solid var(--border);
    }
    .nav-mobile a:last-child { border: none; }
    .nav-mobile a:hover { color: var(--text); }
  </style>
</head>

<body>
  <!-- Custom Cursor -->
  <div id="cursor" aria-hidden="true"></div>
  <div id="cursor-ring" aria-hidden="true"></div>

  <!-- ─── NAVBAR ──────────────────────────────── -->
  <nav id="nav" role="navigation" aria-label="Navegação principal">
    <div class="container">
      <div class="nav-inner">
        <a href="#" class="nav-logo" aria-label="BotForge - Página inicial">
          <div class="nav-logo-icon" aria-hidden="true">⚡</div>
          BotForge
        </a>

        <ul class="nav-links" role="list">
          <li><a href="#services">Serviços</a></li>
          <li><a href="#how">Como Funciona</a></li>
          <li><a href="#pricing">Planos</a></li>
          <li><a href="#faq">FAQ</a></li>
        </ul>

        <div class="nav-cta">
          <a href="https://discord.gg/seu-link" class="btn btn-discord" target="_blank" rel="noopener noreferrer" aria-label="Entrar no Discord">
            <svg width="18" height="14" viewBox="0 0 18 14" fill="none" aria-hidden="true"><path d="M15.25 1.18A14.87 14.87 0 0 0 11.57 0c-.17.31-.37.73-.5 1.06a13.74 13.74 0 0 0-4.14 0A11.3 11.3 0 0 0 6.43 0 14.88 14.88 0 0 0 2.74 1.19 15.77 15.77 0 0 0 0 10.94a14.9 14.9 0 0 0 4.56 2.31 11.3 11.3 0 0 0 .97-1.59 9.74 9.74 0 0 1-1.53-.74c.13-.09.25-.19.37-.29a10.62 10.62 0 0 0 9.26 0c.12.1.25.2.37.29a9.7 9.7 0 0 1-1.53.74c.28.57.6 1.11.97 1.59a14.85 14.85 0 0 0 4.55-2.31 15.73 15.73 0 0 0-2.75-9.76ZM6.01 8.96c-.9 0-1.63-.83-1.63-1.84s.72-1.84 1.63-1.84 1.64.83 1.63 1.84-.72 1.84-1.63 1.84Zm5.98 0c-.9 0-1.63-.83-1.63-1.84s.72-1.84 1.63-1.84 1.64.83 1.63 1.84-.72 1.84-1.63 1.84Z" fill="currentColor"/></svg>
            Discord
          </a>
          <button class="nav-toggle" aria-label="Abrir menu" aria-expanded="false" id="nav-toggle">
            <span></span><span></span><span></span>
          </button>
        </div>
      </div>
    </div>
  </nav>

  <!-- Mobile Nav -->
  <div class="nav-mobile" id="nav-mobile" role="dialog" aria-label="Menu mobile">
    <a href="#services" class="nav-mobile-link">Serviços</a>
    <a href="#how" class="nav-mobile-link">Como Funciona</a>
    <a href="#pricing" class="nav-mobile-link">Planos</a>
    <a href="#trust" class="nav-mobile-link">Depoimentos</a>
    <a href="#faq" class="nav-mobile-link">FAQ</a>
    <a href="https://discord.gg/seu-link" target="_blank" rel="noopener" class="btn btn-discord" style="margin-top:8px; justify-content:center;">Entrar no Discord →</a>
  </div>

  <main>
    <!-- ─── HERO ───────────────────────────────── -->
    <section id="hero" aria-labelledby="hero-title">
      <div class="hero-grid" aria-hidden="true"></div>
      <div class="orb orb-1" aria-hidden="true"></div>
      <div class="orb orb-2" aria-hidden="true"></div>
      <div class="orb orb-3" aria-hidden="true"></div>

      <div class="container">
        <div class="hero-content">
          <div class="hero-badge" aria-label="Status: Aceitando novos projetos">
            <span class="dot" aria-hidden="true"></span>
            Aceitando novos projetos
          </div>

          <h1 class="hero-h1" id="hero-title">
            Automatize seus apps e sites<br>
            com <span class="gradient-text">Bots exclusivos.</span>
          </h1>

          <p class="hero-sub">
            Criamos e mantemos robôs inteligentes sob medida para o seu negócio ou comunidade do Discord. Do briefing à hospedagem, cuidamos de tudo.
          </p>

          <div class="hero-actions">
            <a href="https://discord.gg/seu-link" class="btn btn-primary" target="_blank" rel="noopener noreferrer">
              <svg width="18" height="14" viewBox="0 0 18 14" fill="none" aria-hidden="true"><path d="M15.25 1.18A14.87 14.87 0 0 0 11.57 0c-.17.31-.37.73-.5 1.06a13.74 13.74 0 0 0-4.14 0A11.3 11.3 0 0 0 6.43 0 14.88 14.88 0 0 0 2.74 1.19 15.77 15.77 0 0 0 0 10.94a14.9 14.9 0 0 0 4.56 2.31 11.3 11.3 0 0 0 .97-1.59 9.74 9.74 0 0 1-1.53-.74c.13-.09.25-.19.37-.29a10.62 10.62 0 0 0 9.26 0c.12.1.25.2.37.29a9.7 9.7 0 0 1-1.53.74c.28.57.6 1.11.97 1.59a14.85 14.85 0 0 0 4.55-2.31 15.73 15.73 0 0 0-2.75-9.76ZM6.01 8.96c-.9 0-1.63-.83-1.63-1.84s.72-1.84 1.63-1.84 1.64.83 1.63 1.84-.72 1.84-1.63 1.84Zm5.98 0c-.9 0-1.63-.83-1.63-1.84s.72-1.84 1.63-1.84 1.64.83 1.63 1.84-.72 1.84-1.63 1.84Z" fill="currentColor"/></svg>
              Solicitar Orçamento no Discord
            </a>
            <a href="#services" class="btn btn-ghost">
              Ver Serviços ↓
            </a>
          </div>

          <div class="hero-visual" aria-hidden="true">
            <div class="hero-card-wrap">
              <div class="hero-stat-card">
                <div class="stat-icon blue">🤖</div>
                <div>
                  <div class="stat-value">50+</div>
                  <div class="stat-label">Bots entregues</div>
                </div>
              </div>
              <div class="hero-stat-card">
                <div class="stat-icon purple">⚡</div>
                <div>
                  <div class="stat-value">99.9%</div>
                  <div class="stat-label">Uptime garantido</div>
                </div>
              </div>
              <div class="hero-stat-card">
                <div class="stat-icon cyan">💬</div>
                <div>
                  <div class="stat-value">&lt; 24h</div>
                  <div class="stat-label">Resposta média</div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ─── MARQUEE ────────────────────────────── -->
    <div class="marquee-section" aria-hidden="true">
      <div class="marquee-track">
        <!-- duplicado para loop infinito -->
        <div class="marquee-item">🤖 Bots Discord<span class="sep"></span></div>
        <div class="marquee-item">🌐 Sites Modernos<span class="sep"></span></div>
        <div class="marquee-item">⚡ Automação<span class="sep"></span></div>
        <div class="marquee-item">🔗 Integrações<span class="sep"></span></div>
        <div class="marquee-item">🛠 Manutenção<span class="sep"></span></div>
        <div class="marquee-item">☁️ Hospedagem 24/7<span class="sep"></span></div>
        <div class="marquee-item">💳 Pagamentos<span class="sep"></span></div>
        <div class="marquee-item">📊 Dashboards<span class="sep"></span></div>
        <div class="marquee-item">🤖 Bots Discord<span class="sep"></span></div>
        <div class="marquee-item">🌐 Sites Modernos<span class="sep"></span></div>
        <div class="marquee-item">⚡ Automação<span class="sep"></span></div>
        <div class="marquee-item">🔗 Integrações<span class="sep"></span></div>
        <div class="marquee-item">🛠 Manutenção<span class="sep"></span></div>
        <div class="marquee-item">☁️ Hospedagem 24/7<span class="sep"></span></div>
        <div class="marquee-item">💳 Pagamentos<span class="sep"></span></div>
        <div class="marquee-item">📊 Dashboards<span class="sep"></span></div>
      </div>
    </div>

    <!-- ─── SERVICES ───────────────────────────── -->
    <section id="services" aria-labelledby="services-title">
      <div class="container">
        <div class="sec-header reveal">
          <div class="section-label">✦ Serviços</div>
          <h2 id="services-title">Tudo que você precisa,<br><span class="gradient-text">em um só lugar</span></h2>
          <p>Do conceito ao deploy, desenvolvemos soluções sob medida com código limpo, suporte contínuo e entrega rápida.</p>
        </div>

        <div class="bento" role="list">
          <div class="bento-card span-2 reveal" role="listitem">
            <div class="card-icon blue" aria-hidden="true">🤖</div>
            <h3>Criação de Bots Inteligentes</h3>
            <p>Desenvolvemos bots personalizados para Discord, Telegram e automações web — com comandos slash, menus de seleção, sistemas de tickets, moderação avançada, integrações com APIs e muito mais. Cada bot é construído do zero, sob a sua especificação.</p>
            <div class="bento-tags" aria-label="Tecnologias">
              <span class="tag accent">Discord.js</span>
              <span class="tag accent">Telegraf</span>
              <span class="tag">Node.js</span>
              <span class="tag">Python</span>
              <span class="tag">REST APIs</span>
            </div>
          </div>

          <div class="bento-card reveal reveal-delay-1" role="listitem">
            <div class="card-icon purple" aria-hidden="true">☁️</div>
            <h3>Hospedagem & Monitoramento</h3>
            <p>Seu bot online 24/7, com monitoramento em tempo real, reinicialização automática em caso de falhas e notificações imediatas. Zero downtime, máxima confiabilidade.</p>
            <div class="bento-tags">
              <span class="tag">Railway</span>
              <span class="tag">VPS</span>
              <span class="tag accent">24/7 Uptime</span>
            </div>
          </div>

          <div class="bento-card reveal reveal-delay-2" role="listitem">
            <div class="card-icon cyan" aria-hidden="true">🌐</div>
            <h3>Sites & Landing Pages</h3>
            <p>Criamos sites modernos, rápidos e otimizados para conversão. De portfólios a e-commerces, com design premium e SEO integrado.</p>
            <div class="bento-tags">
              <span class="tag">Next.js</span>
              <span class="tag">React</span>
              <span class="tag accent">Performance</span>
            </div>
          </div>

          <div class="bento-card reveal reveal-delay-1" role="listitem">
            <div class="card-icon green" aria-hidden="true">🔗</div>
            <h3>Integrações & Automações</h3>
            <p>Conectamos seu bot ou site com sistemas externos: pagamentos (Stripe, Mercado Pago), bancos de dados, webhooks, planilhas, APIs customizadas e painéis administrativos.</p>
            <div class="bento-tags">
              <span class="tag">Stripe</span>
              <span class="tag">Firebase</span>
              <span class="tag accent">Webhooks</span>
            </div>
          </div>

          <div class="bento-card span-2 reveal reveal-delay-2" role="listitem">
            <div class="card-icon blue" aria-hidden="true">🛠</div>
            <h3>Manutenção Contínua & Suporte</h3>
            <p>Não abandonamos você após a entrega. Oferecemos planos mensais de manutenção com atualizações, correção de bugs, otimizações de performance e suporte direto via Discord — respondendo dúvidas e ajustes sem burocracia.</p>
            <div class="bento-tags">
              <span class="tag accent">Suporte via Discord</span>
              <span class="tag">Atualizações</span>
              <span class="tag">Bug fixes</span>
              <span class="tag">Performance</span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ─── HOW IT WORKS ───────────────────────── -->
    <section id="how" aria-labelledby="how-title">
      <div class="container">
        <div class="sec-header reveal">
          <div class="section-label">✦ Processo</div>
          <h2 id="how-title">Como funciona?</h2>
          <p>Nosso processo é direto, transparente e pensado para entregar o máximo valor no menor tempo possível.</p>
        </div>

        <div class="steps-grid">
          <div class="step-card reveal" aria-label="Passo 1">
            <div class="step-number" aria-hidden="true">01</div>
            <div class="step-chip">Passo 1</div>
            <h3>Entre no Servidor</h3>
            <p>Acesse nosso servidor no Discord e abra um ticket de atendimento. Apresente sua ideia, compartilhe referências e tire dúvidas diretamente com a equipe.</p>
          </div>

          <div class="step-card reveal reveal-delay-1" aria-label="Passo 2">
            <div class="step-number" aria-hidden="true">02</div>
            <div class="step-chip">Passo 2</div>
            <h3>Alinhamento</h3>
            <p>Fazemos um briefing detalhado para entender cada detalhe do projeto. Você recebe um orçamento claro, prazo definido e sem surpresas. Só seguimos com sua aprovação.</p>
          </div>

          <div class="step-card reveal reveal-delay-2" aria-label="Passo 3">
            <div class="step-number" aria-hidden="true">03</div>
            <div class="step-chip">Passo 3</div>
            <h3>Desenvolvimento</h3>
            <p>Mãos na massa. Desenvolvemos com código limpo, boas práticas e atualizações frequentes. Você acompanha o progresso em tempo real e pode solicitar ajustes durante o processo.</p>
          </div>

          <div class="step-card reveal reveal-delay-3" aria-label="Passo 4">
            <div class="step-number" aria-hidden="true">04</div>
            <div class="step-chip">Passo 4</div>
            <h3>Hospedagem & Suporte</h3>
            <p>Após a entrega, o projeto entra em produção com monitoramento ativo. Suporte pós-entrega incluso e planos de manutenção disponíveis para quem quer manter tudo funcionando perfeitamente.</p>
          </div>
        </div>
      </div>
    </section>

    <!-- ─── PRICING ────────────────────────────── -->
    <section id="pricing" aria-labelledby="pricing-title">
      <div class="container">
        <div class="sec-header reveal">
          <div class="section-label">✦ Planos</div>
          <h2 id="pricing-title">Investimento <span class="gradient-text">transparente</span></h2>
          <p>Valores estimados de entrada. O orçamento final é definido após o briefing, conforme a complexidade e escopo do projeto.</p>
        </div>

        <div class="pricing-grid">

          <!-- Básico -->
          <div class="pricing-card reveal" aria-label="Plano Básico">
            <div class="plan-name">Plano Básico</div>
            <div class="plan-price"><span>R$</span>297</div>
            <div class="plan-note">a partir de · preço varia com escopo</div>
            <div class="plan-divider"></div>
            <ul class="plan-features" role="list">
              <li><span class="check" aria-hidden="true">✓</span> Bot com comandos essenciais</li>
              <li><span class="check" aria-hidden="true">✓</span> Até 5 funcionalidades customizadas</li>
              <li><span class="check" aria-hidden="true">✓</span> Entrega em até 5 dias úteis</li>
              <li><span class="check" aria-hidden="true">✓</span> Suporte por 7 dias após entrega</li>
              <li><span class="check" aria-hidden="true">✓</span> Código-fonte incluso</li>
            </ul>
            <a href="https://discord.gg/seu-link" class="btn btn-ghost" target="_blank" rel="noopener" style="width:100%;justify-content:center;">
              Solicitar orçamento →
            </a>
          </div>

          <!-- Avançado -->
          <div class="pricing-card featured reveal reveal-delay-1" aria-label="Plano Avançado — Mais popular">
            <div class="pricing-badge" aria-label="Mais popular">⭐ Popular</div>
            <div class="plan-name">Plano Avançado</div>
            <div class="plan-price"><span>R$</span>797</div>
            <div class="plan-note">a partir de · preço varia com escopo</div>
            <div class="plan-divider"></div>
            <ul class="plan-features" role="list">
              <li><span class="check" aria-hidden="true">✓</span> Bot completo e robusto</li>
              <li><span class="check" aria-hidden="true">✓</span> Funcionalidades ilimitadas</li>
              <li><span class="check" aria-hidden="true">✓</span> Integração com banco de dados</li>
              <li><span class="check" aria-hidden="true">✓</span> Painel administrativo web</li>
              <li><span class="check" aria-hidden="true">✓</span> Hospedagem por 30 dias</li>
              <li><span class="check" aria-hidden="true">✓</span> Suporte por 30 dias após entrega</li>
              <li><span class="check" aria-hidden="true">✓</span> Integrações com pagamentos</li>
            </ul>
            <a href="https://discord.gg/seu-link" class="btn btn-primary" target="_blank" rel="noopener" style="width:100%;justify-content:center;">
              Solicitar orçamento →
            </a>
          </div>

          <!-- Manutenção -->
          <div class="pricing-card reveal reveal-delay-2" aria-label="Plano de Manutenção Mensal">
            <div class="plan-name">Manutenção Mensal</div>
            <div class="plan-price"><span>R$</span>147</div>
            <div class="plan-note">por mês · faturamento recorrente</div>
            <div class="plan-divider"></div>
            <ul class="plan-features" role="list">
              <li><span class="check" aria-hidden="true">✓</span> Hospedagem 24/7 com uptime monitorado</li>
              <li><span class="check" aria-hidden="true">✓</span> Atualizações e correções de bugs</li>
              <li><span class="check" aria-hidden="true">✓</span> Pequenos ajustes mensais</li>
              <li><span class="check" aria-hidden="true">✓</span> Suporte direto no Discord</li>
              <li><span class="check" aria-hidden="true">✓</span> Relatório mensal de uso</li>
            </ul>
            <a href="https://discord.gg/seu-link" class="btn btn-ghost" target="_blank" rel="noopener" style="width:100%;justify-content:center;">
              Contratar manutenção →
            </a>
          </div>

        </div>
      </div>
    </section>

    <!-- ─── TRUST ──────────────────────────────── -->
    <section id="trust" aria-labelledby="trust-title">
      <div class="container">
        <div class="sec-header reveal">
          <div class="section-label">✦ Depoimentos</div>
          <h2 id="trust-title">O que nossos clientes <span class="gradient-text">dizem</span></h2>
          <p>Resultados reais de quem confiou no nosso trabalho.</p>
        </div>

        <div class="trust-grid">
          <div class="trust-card reveal">
            <div class="stars" aria-label="5 estrelas">
              <span class="star" aria-hidden="true">★</span><span class="star" aria-hidden="true">★</span>
              <span class="star" aria-hidden="true">★</span><span class="star" aria-hidden="true">★</span>
              <span class="star" aria-hidden="true">★</span>
            </div>
            <blockquote>"Contratei o bot de vendas e ficou perfeito. Automatizou todo o processo de compra no servidor, com confirmação automática, envio de produto e log de vendas. Profissionalismo do início ao fim."</blockquote>
            <div class="trust-author">
              <div class="avatar" style="background: linear-gradient(135deg, #5b8df6, #8b5cf6)" aria-hidden="true">MC</div>
              <div>
                <div class="author-name">Marcos C.</div>
                <div class="author-role">Dono de servidor de produtos digitais</div>
              </div>
            </div>
          </div>

          <div class="trust-card reveal reveal-delay-1">
            <div class="stars" aria-label="5 estrelas">
              <span class="star" aria-hidden="true">★</span><span class="star" aria-hidden="true">★</span>
              <span class="star" aria-hidden="true">★</span><span class="star" aria-hidden="true">★</span>
              <span class="star" aria-hidden="true">★</span>
            </div>
            <blockquote>"Precisava de uma landing page rápida, moderna e que convertesse. Recebi exatamente isso — otimizada, responsiva e com integração ao Discord. Comunicação impecável."</blockquote>
            <div class="trust-author">
              <div class="avatar" style="background: linear-gradient(135deg, #06b6d4, #5b8df6)" aria-hidden="true">AL</div>
              <div>
                <div class="author-name">Amanda L.</div>
                <div class="author-role">Criadora de conteúdo & empreendedora</div>
              </div>
            </div>
          </div>

          <div class="trust-card reveal reveal-delay-2">
            <div class="stars" aria-label="5 estrelas">
              <span class="star" aria-hidden="true">★</span><span class="star" aria-hidden="true">★</span>
              <span class="star" aria-hidden="true">★</span><span class="star" aria-hidden="true">★</span>
              <span class="star" aria-hidden="true">★</span>
            </div>
            <blockquote>"O plano de manutenção mensal vale muito. Meu bot fica 24/7 no ar, recebo alertas de qualquer instabilidade e os ajustes são feitos sem eu precisar nem pedir duas vezes."</blockquote>
            <div class="trust-author">
              <div class="avatar" style="background: linear-gradient(135deg, #8b5cf6, #ec4899)" aria-hidden="true">RB</div>
              <div>
                <div class="author-name">Rafael B.</div>
                <div class="author-role">Gestor de comunidade gamer</div>
              </div>
            </div>
          </div>
        </div>

        <!-- Benefits -->
        <div class="benefits-row" role="list">
          <div class="benefit reveal" role="listitem">
            <div class="benefit-icon" aria-hidden="true">⚡</div>
            <div class="benefit-text">
              <strong>Resposta em até 24h</strong>
              <span>Atendemos rápido e sem burocracia direto no Discord.</span>
            </div>
          </div>
          <div class="benefit reveal reveal-delay-1" role="listitem">
            <div class="benefit-icon" aria-hidden="true">✨</div>
            <div class="benefit-text">
              <strong>Código limpo e organizado</strong>
              <span>Entregamos documentação clara e código que você consegue entender.</span>
            </div>
          </div>
          <div class="benefit reveal reveal-delay-2" role="listitem">
            <div class="benefit-icon" aria-hidden="true">🤝</div>
            <div class="benefit-text">
              <strong>Suporte pós-entrega</strong>
              <span>Não sumimos após o pagamento. Ajudamos na instalação e uso.</span>
            </div>
          </div>
          <div class="benefit reveal reveal-delay-3" role="listitem">
            <div class="benefit-icon" aria-hidden="true">🔒</div>
            <div class="benefit-text">
              <strong>Entrega garantida</strong>
              <span>Prazo definido no briefing. Reembolso se não entregamos o combinado.</span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ─── FAQ ───────────────────────────────── -->
    <section id="faq" aria-labelledby="faq-title">
      <div class="container">
        <div class="sec-header reveal">
          <div class="section-label">✦ FAQ</div>
          <h2 id="faq-title">Perguntas <span class="gradient-text">frequentes</span></h2>
          <p>Tudo que você precisa saber antes de começar.</p>
        </div>

        <div class="faq-list reveal" role="list">

          <div class="faq-item" role="listitem">
            <button class="faq-q" aria-expanded="false" aria-controls="faq-a1">
              Quanto tempo leva para desenvolver um bot?
              <div class="faq-icon" aria-hidden="true">+</div>
            </button>
            <div class="faq-a" id="faq-a1" role="region">
              <div class="faq-a-inner">
                Depende da complexidade do projeto. Bots simples ficam prontos em 2 a 5 dias úteis. Projetos avançados com integrações, painel web e banco de dados podem levar de 1 a 3 semanas. O prazo exato é definido após o briefing completo.
              </div>
            </div>
          </div>

          <div class="faq-item" role="listitem">
            <button class="faq-q" aria-expanded="false" aria-controls="faq-a2">
              Vocês fazem manutenção contínua?
              <div class="faq-icon" aria-hidden="true">+</div>
            </button>
            <div class="faq-a" id="faq-a2" role="region">
              <div class="faq-a-inner">
                Sim! Oferecemos planos mensais de manutenção que incluem hospedagem 24/7, monitoramento ativo, correção de bugs e pequenos ajustes. É ideal para quem não quer se preocupar com infraestrutura e quer o projeto sempre funcionando.
              </div>
            </div>
          </div>

          <div class="faq-item" role="listitem">
            <button class="faq-q" aria-expanded="false" aria-controls="faq-a3">
              Vocês integram o bot com meu site?
              <div class="faq-icon" aria-hidden="true">+</div>
            </button>
            <div class="faq-a" id="faq-a3" role="region">
              <div class="faq-a-inner">
                Sim, essa é uma das nossas especialidades. Integramos bots do Discord com sites, painéis administrativos, sistemas de pagamento (Stripe, Mercado Pago), bancos de dados e qualquer API que você precise. Tudo funcionando em sincronia.
              </div>
            </div>
          </div>

          <div class="faq-item" role="listitem">
            <button class="faq-q" aria-expanded="false" aria-controls="faq-a4">
              Como funciona o processo de orçamento?
              <div class="faq-icon" aria-hidden="true">+</div>
            </button>
            <div class="faq-a" id="faq-a4" role="region">
              <div class="faq-a-inner">
                É simples: você entra no nosso servidor do Discord, abre um ticket e descreve o projeto. Fazemos um briefing para entender os detalhes e em até 24h enviamos um orçamento claro com prazo, escopo e valor. Nenhuma surpresa depois.
              </div>
            </div>
          </div>

          <div class="faq-item" role="listitem">
            <button class="faq-q" aria-expanded="false" aria-controls="faq-a5">
              O bot pode ficar online 24 horas por dia?
              <div class="faq-icon" aria-hidden="true">+</div>
            </button>
            <div class="faq-a" id="faq-a5" role="region">
              <div class="faq-a-inner">
                Com certeza. Nossos bots são hospedados em servidores dedicados ou VPS com monitoramento automático. Em caso de queda, o sistema reinicia sozinho em segundos. O uptime médio dos nossos projetos é de 99.9%.
              </div>
            </div>
          </div>

          <div class="faq-item" role="listitem">
            <button class="faq-q" aria-expanded="false" aria-controls="faq-a6">
              Atendem projetos pequenos e grandes?
              <div class="faq-icon" aria-hidden="true">+</div>
            </button>
            <div class="faq-a" id="faq-a6" role="region">
              <div class="faq-a-inner">
                Sim! Atendemos desde bots simples de boas-vindas até sistemas complexos com pagamentos, painéis web, integrações múltiplas e lógicas avançadas. Cada projeto recebe a mesma atenção, independente do tamanho. Fale conosco e veremos o que cabe no seu orçamento.
              </div>
            </div>
          </div>

        </div>
      </div>
    </section>

    <!-- ─── CTA BANNER ────────────────────────── -->
    <section id="cta-banner" aria-labelledby="cta-title">
      <div class="container">
        <div class="cta-inner reveal">
          <h2 id="cta-title">Pronto para<br><span class="gradient-text">automatizar de verdade?</span></h2>
          <p>Entre no nosso servidor, descreva seu projeto e receba um orçamento personalizado em até 24 horas.</p>
          <div class="cta-actions">
            <a href="https://discord.gg/seu-link" class="btn btn-primary" target="_blank" rel="noopener noreferrer" style="font-size:16px; padding:16px 36px;">
              <svg width="20" height="16" viewBox="0 0 18 14" fill="none" aria-hidden="true"><path d="M15.25 1.18A14.87 14.87 0 0 0 11.57 0c-.17.31-.37.73-.5 1.06a13.74 13.74 0 0 0-4.14 0A11.3 11.3 0 0 0 6.43 0 14.88 14.88 0 0 0 2.74 1.19 15.77 15.77 0 0 0 0 10.94a14.9 14.9 0 0 0 4.56 2.31 11.3 11.3 0 0 0 .97-1.59 9.74 9.74 0 0 1-1.53-.74c.13-.09.25-.19.37-.29a10.62 10.62 0 0 0 9.26 0c.12.1.25.2.37.29a9.7 9.7 0 0 1-1.53.74c.28.57.6 1.11.97 1.59a14.85 14.85 0 0 0 4.55-2.31 15.73 15.73 0 0 0-2.75-9.76ZM6.01 8.96c-.9 0-1.63-.83-1.63-1.84s.72-1.84 1.63-1.84 1.64.83 1.63 1.84-.72 1.84-1.63 1.84Zm5.98 0c-.9 0-1.63-.83-1.63-1.84s.72-1.84 1.63-1.84 1.64.83 1.63 1.84-.72 1.84-1.63 1.84Z" fill="currentColor"/></svg>
              Entrar no Discord agora
            </a>
            <a href="#services" class="btn btn-ghost" style="font-size:16px; padding:16px 36px;">Ver nossos serviços</a>
          </div>
        </div>
      </div>
    </section>
  </main>

  <!-- ─── FOOTER ────────────────────────────── -->
  <footer role="contentinfo">
    <div class="container">
      <div class="footer-grid">
        <div class="footer-brand">
          <a href="#" class="nav-logo" style="font-size:18px; display:inline-flex;">
            <div class="nav-logo-icon" aria-hidden="true">⚡</div>
            BotForge
          </a>
          <p>Desenvolvemos bots e sites premium para quem quer crescer com automação inteligente e tecnologia de ponta.</p>
          <div class="social-links" aria-label="Redes sociais">
            <a href="https://discord.gg/seu-link" class="social-link" aria-label="Discord" target="_blank" rel="noopener">
              <svg width="16" height="12" viewBox="0 0 18 14" fill="currentColor" aria-hidden="true"><path d="M15.25 1.18A14.87 14.87 0 0 0 11.57 0c-.17.31-.37.73-.5 1.06a13.74 13.74 0 0 0-4.14 0A11.3 11.3 0 0 0 6.43 0 14.88 14.88 0 0 0 2.74 1.19 15.77 15.77 0 0 0 0 10.94a14.9 14.9 0 0 0 4.56 2.31 11.3 11.3 0 0 0 .97-1.59 9.74 9.74 0 0 1-1.53-.74c.13-.09.25-.19.37-.29a10.62 10.62 0 0 0 9.26 0c.12.1.25.2.37.29a9.7 9.7 0 0 1-1.53.74c.28.57.6 1.11.97 1.59a14.85 14.85 0 0 0 4.55-2.31 15.73 15.73 0 0 0-2.75-9.76ZM6.01 8.96c-.9 0-1.63-.83-1.63-1.84s.72-1.84 1.63-1.84 1.64.83 1.63 1.84-.72 1.84-1.63 1.84Zm5.98 0c-.9 0-1.63-.83-1.63-1.84s.72-1.84 1.63-1.84 1.64.83 1.63 1.84-.72 1.84-1.63 1.84Z"/></svg>
            </a>
            <a href="#" class="social-link" aria-label="GitHub" target="_blank" rel="noopener">
              <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor" aria-hidden="true"><path d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0 0 24 12c0-6.63-5.37-12-12-12z"/></svg>
            </a>
            <a href="#" class="social-link" aria-label="Instagram" target="_blank" rel="noopener">
              <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor" aria-hidden="true"><path d="M12 2.163c3.204 0 3.584.012 4.85.07 3.252.148 4.771 1.691 4.919 4.919.058 1.265.069 1.645.069 4.849 0 3.205-.012 3.584-.069 4.849-.149 3.225-1.664 4.771-4.919 4.919-1.266.058-1.644.07-4.85.07-3.204 0-3.584-.012-4.849-.07-3.26-.149-4.771-1.699-4.919-4.92-.058-1.265-.07-1.644-.07-4.849 0-3.204.013-3.583.07-4.849.149-3.227 1.664-4.771 4.919-4.919 1.266-.057 1.645-.069 4.849-.069zm0-2.163c-3.259 0-3.667.014-4.947.072-4.358.2-6.78 2.618-6.98 6.98-.059 1.281-.073 1.689-.073 4.948 0 3.259.014 3.668.072 4.948.2 4.358 2.618 6.78 6.98 6.98 1.281.058 1.689.072 4.948.072 3.259 0 3.668-.014 4.948-.072 4.354-.2 6.782-2.618 6.979-6.98.059-1.28.073-1.689.073-4.948 0-3.259-.014-3.667-.072-4.947-.196-4.354-2.617-6.78-6.979-6.98-1.281-.059-1.69-.073-4.949-.073zm0 5.838c-3.403 0-6.162 2.759-6.162 6.162s2.759 6.163 6.162 6.163 6.162-2.759 6.162-6.163c0-3.403-2.759-6.162-6.162-6.162zm0 10.162c-2.209 0-4-1.79-4-4 0-2.209 1.791-4 4-4s4 1.791 4 4c0 2.21-1.791 4-4 4zm6.406-11.845c-.796 0-1.441.645-1.441 1.44s.645 1.44 1.441 1.44c.795 0 1.439-.645 1.439-1.44s-.644-1.44-1.439-1.44z"/></svg>
            </a>
          </div>
        </div>

        <div class="footer-col">
          <h4>Serviços</h4>
          <ul>
            <li><a href="#services">Criação de Bots</a></li>
            <li><a href="#services">Sites & Landing Pages</a></li>
            <li><a href="#services">Hospedagem & Uptime</a></li>
            <li><a href="#services">Integrações</a></li>
            <li><a href="#services">Manutenção Mensal</a></li>
          </ul>
        </div>

        <div class="footer-col">
          <h4>Empresa</h4>
          <ul>
            <li><a href="#how">Como Funciona</a></li>
            <li><a href="#pricing">Planos e Preços</a></li>
            <li><a href="#trust">Depoimentos</a></li>
            <li><a href="#faq">Perguntas Frequentes</a></li>
            <li><a href="https://discord.gg/seu-link" target="_blank" rel="noopener">Entrar no Discord</a></li>
          </ul>
        </div>
      </div>

      <div class="footer-bottom">
        <p>© 2025 BotForge. Todos os direitos reservados.</p>
        <a href="https://discord.gg/seu-link" class="btn btn-discord" target="_blank" rel="noopener noreferrer" style="padding:10px 20px; font-size:14px;">
          Entrar no Discord →
        </a>
      </div>
    </div>
  </footer>

  <script>
    // ─── SMOOTH SCROLL ───────────────────────────
    document.querySelectorAll('a[href^="#"]').forEach(a => {
      a.addEventListener('click', e => {
        const target = document.querySelector(a.getAttribute('href'));
        if (!target) return;
        e.preventDefault();
        target.scrollIntoView({ behavior: 'smooth' });
        // Close mobile nav
        document.getElementById('nav-mobile').classList.remove('open');
        const toggle = document.getElementById('nav-toggle');
        toggle.setAttribute('aria-expanded', 'false');
      });
    });

    // ─── STICKY NAV ──────────────────────────────
    const nav = document.getElementById('nav');
    window.addEventListener('scroll', () => {
      nav.classList.toggle('scrolled', window.scrollY > 40);
    }, { passive: true });

    // ─── MOBILE NAV TOGGLE ───────────────────────
    const toggle = document.getElementById('nav-toggle');
    const mobileNav = document.getElementById('nav-mobile');
    toggle.addEventListener('click', () => {
      const isOpen = mobileNav.classList.toggle('open');
      toggle.setAttribute('aria-expanded', isOpen);
    });

    // ─── SCROLL REVEAL ───────────────────────────
    const reveals = document.querySelectorAll('.reveal');
    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.classList.add('visible');
          observer.unobserve(entry.target);
        }
      });
    }, { threshold: 0.12, rootMargin: '0px 0px -40px 0px' });
    reveals.forEach(el => observer.observe(el));

    // ─── FAQ ACCORDION ───────────────────────────
    document.querySelectorAll('.faq-q').forEach(btn => {
      btn.addEventListener('click', () => {
        const item = btn.closest('.faq-item');
        const answer = item.querySelector('.faq-a');
        const isOpen = item.classList.contains('open');

        // Close all
        document.querySelectorAll('.faq-item').forEach(i => {
          i.classList.remove('open');
          i.querySelector('.faq-q').setAttribute('aria-expanded', 'false');
          const a = i.querySelector('.faq-a');
          a.style.maxHeight = '0';
        });

        // Open current
        if (!isOpen) {
          item.classList.add('open');
          btn.setAttribute('aria-expanded', 'true');
          answer.style.maxHeight = answer.scrollHeight + 'px';
        }
      });
    });

    // ─── CARD 3D TILT ───────────────────────────
    const tiltCards = document.querySelectorAll('.bento-card, .pricing-card, .step-card, .trust-card');
    const prefersReducedMotion = window.matchMedia('(prefers-reduced-motion: reduce)').matches;

    if (!prefersReducedMotion) {
      tiltCards.forEach(card => {
        card.addEventListener('mousemove', e => {
          const rect = card.getBoundingClientRect();
          const x = e.clientX - rect.left;
          const y = e.clientY - rect.top;
          const cx = rect.width / 2;
          const cy = rect.height / 2;
          const rx = ((y - cy) / cy) * -5;
          const ry = ((x - cx) / cx) * 5;

          // Update CSS var for spotlight
          card.style.setProperty('--mx', `${(x / rect.width) * 100}%`);
          card.style.setProperty('--my', `${(y / rect.height) * 100}%`);

          card.style.transform = `perspective(800px) rotateX(${rx}deg) rotateY(${ry}deg) translateY(-4px)`;
        });

        card.addEventListener('mouseleave', () => {
          card.style.transform = '';
        });
      });
    }

    // ─── MAGNETIC BUTTONS ────────────────────────
    if (!prefersReducedMotion && window.matchMedia('(pointer: fine)').matches) {
      document.querySelectorAll('.btn').forEach(btn => {
        btn.addEventListener('mousemove', e => {
          const rect = btn.getBoundingClientRect();
          const x = e.clientX - rect.left - rect.width / 2;
          const y = e.clientY - rect.top - rect.height / 2;
          btn.style.transform = `translate(${x * 0.15}px, ${y * 0.2}px) scale(1.03)`;
        });
        btn.addEventListener('mouseleave', () => {
          btn.style.transform = '';
        });
      });
    }

    // ─── CUSTOM CURSOR ───────────────────────────
    if (window.matchMedia('(pointer: fine)').matches) {
      const cursor = document.getElementById('cursor');
      const ring   = document.getElementById('cursor-ring');
      let mx = 0, my = 0, rx = 0, ry = 0;

      document.addEventListener('mousemove', e => {
        mx = e.clientX; my = e.clientY;
        cursor.style.left = mx + 'px';
        cursor.style.top  = my + 'px';
      });

      const animRing = () => {
        rx += (mx - rx) * 0.14;
        ry += (my - ry) * 0.14;
        ring.style.left = rx + 'px';
        ring.style.top  = ry + 'px';
        requestAnimationFrame(animRing);
      };
      animRing();
    }
  </script>
</body>
</html>
