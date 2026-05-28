<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Neatlyst – Descarga la app</title>
  <style>
    * { margin: 0; padding: 0; box-sizing: border-box; }
    body {
      font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
      background: #0a0a0a;
      min-height: 100vh;
      display: flex;
      align-items: center;
      justify-content: center;
    }
    .card {
      background: #fff;
      border-radius: 28px;
      padding: 2.5rem 2rem;
      width: 90%;
      max-width: 340px;
      text-align: center;
    }
    .icon {
      width: 80px; height: 80px;
      border-radius: 20px;
      background: linear-gradient(135deg, #1a1a2e, #0f3460);
      margin: 0 auto 1.25rem;
      display: flex; align-items: center; justify-content: center;
    }
    .icon svg { width: 40px; height: 40px; }
    h1 { font-size: 1.6rem; font-weight: 700; color: #111; margin-bottom: .4rem; }
    .sub { font-size: .9rem; color: #888; margin-bottom: 2rem; line-height: 1.5; }
    .spinner {
      width: 32px; height: 32px;
      border: 3px solid #eee; border-top-color: #111;
      border-radius: 50%;
      animation: spin .7s linear infinite;
      margin: 0 auto .75rem;
    }
    @keyframes spin { to { transform: rotate(360deg); } }
    .msg { font-size: .8rem; color: #aaa; margin-bottom: 1.5rem; }
    .btn {
      display: flex; align-items: center; justify-content: center; gap: 10px;
      width: 100%; padding: 14px 20px;
      border-radius: 14px; border: none;
      font-size: .95rem; font-weight: 600;
      cursor: pointer; text-decoration: none;
      margin-bottom: 10px;
      transition: opacity .15s;
    }
    .btn:active { opacity: .8; }
    .btn-ios { background: #111; color: #fff; }
    .btn-android { background: #01875f; color: #fff; }
    .btn-ios svg, .btn-android svg { width: 20px; height: 20px; flex-shrink: 0; }
    .footer { font-size: .75rem; color: #ccc; margin-top: 1.25rem; }
    #buttons { display: none; }
  </style>
</head>
<body>
<div class="card">
  <div class="icon">
    <svg viewBox="0 0 40 40" fill="none">
      <circle cx="20" cy="20" r="15" fill="white" opacity=".15"/>
      <path d="M20 9 L29 26 H11 Z" fill="white" opacity=".9"/>
      <circle cx="20" cy="29" r="2.5" fill="white" opacity=".7"/>
    </svg>
  </div>
  <h1>Neatlyst</h1>
  <p class="sub">Descarga la aplicación en tu dispositivo</p>

  <div id="detecting">
    <div class="spinner"></div>
    <div class="msg" id="detect-msg">Detectando tu dispositivo…</div>
  </div>

  <div id="buttons">
    <a class="btn btn-ios" href="https://apps.apple.com/us/app/neatlyst/id1091657112" id="ios-btn">
      <svg viewBox="0 0 24 24" fill="currentColor"><path d="M18.71 19.5c-.83 1.24-1.71 2.45-3.05 2.47-1.34.03-1.77-.79-3.29-.79-1.53 0-2 .77-3.27.82-1.31.05-2.3-1.32-3.14-2.53C4.25 17 2.94 12.45 4.7 9.39c.87-1.52 2.43-2.48 4.12-2.51 1.28-.02 2.5.87 3.29.87.78 0 2.26-1.07 3.8-.91.65.03 2.47.26 3.64 1.98-.09.06-2.17 1.28-2.15 3.81.03 3.02 2.65 4.03 2.68 4.04-.03.07-.42 1.44-1.38 2.83M13 3.5c.73-.83 1.94-1.46 2.94-1.5.13 1.17-.34 2.35-1.04 3.19-.69.85-1.83 1.51-2.95 1.42-.15-1.15.41-2.35 1.05-3.11z"/></svg>
      Descargar en App Store
    </a>
    <a class="btn btn-android" href="https://play.google.com/store/apps/details?id=com.neatlyst.neatlystapp" id="android-btn">
      <svg viewBox="0 0 24 24" fill="currentColor"><path d="M3.18 23.76a2 2 0 0 1-.95-1.73V1.97A2 2 0 0 1 3.18.24l11.51 11.76zm14.73-7.77L5.43 23.03l8.1-4.68zm.78-.45L20.77 12l-2.08-3.54L5.43.97l13.26 7.04zM5.43.97l12.49 7.07L20.77 12l-2.08 3.54L5.43 23.03z"/></svg>
      Descargar en Google Play
    </a>
  </div>
  <div class="footer" id="footer-msg"></div>
</div>

<script>
  const IOS_URL = 'https://apps.apple.com/us/app/neatlyst/id1091657112';
  const ANDROID_URL = 'https://play.google.com/store/apps/details?id=com.neatlyst.neatlystapp';
  const ua = navigator.userAgent || navigator.vendor || window.opera;
  const isIOS = /iPad|iPhone|iPod/.test(ua) && !window.MSStream;
  const isAndroid = /android/i.test(ua);

  if (isIOS) {
    document.getElementById('detect-msg').textContent = 'iPhone / iPad detectado ✓';
    setTimeout(() => { window.location.href = IOS_URL; }, 1800);
    document.getElementById('footer-msg').textContent = 'Redirigiendo a App Store…';
  } else if (isAndroid) {
    document.getElementById('detect-msg').textContent = 'Android detectado ✓';
    setTimeout(() => { window.location.href = ANDROID_URL; }, 1800);
    document.getElementById('footer-msg').textContent = 'Redirigiendo a Google Play…';
  } else {
    document.getElementById('detecting').style.display = 'none';
    document.getElementById('buttons').style.display = 'block';
    document.getElementById('ios-btn').style.display = 'flex';
    document.getElementById('android-btn').style.display = 'flex';
    document.getElementById('footer-msg').textContent = 'Elige tu plataforma';
  }
</script>
</body>
</html># NEATLYSTAPP
