<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>AWWOOF</title>
<meta name="viewport" content="width=device-width, initial-scale=1">

<style>
/* ---------- BASE ---------- */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: "Inter", sans-serif;
  background: #000;
  color: #fff;
  overflow-x: hidden;
}

/* ---------- BACKGROUND FX ---------- */
.bg {
  position: fixed;
  inset: 0;
  background:
    radial-gradient(circle at 20% 30%, rgba(0, 140, 255, 0.15), transparent 60%),
    radial-gradient(circle at 80% 70%, rgba(255, 0, 120, 0.15), transparent 60%),
    #000;
  filter: blur(40px);
  z-index: -2;
}

.noise {
  position: fixed;
  inset: 0;
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='200' height='200'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.8' numOctaves='4'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.15'/%3E%3C/svg%3E");
  opacity: 0.18;
  z-index: -1;
  pointer-events: none;
}

/* ---------- CENTER CARD ---------- */
.container {
  max-width: 900px;
  margin: 80px auto;
  padding: 40px;
  border-radius: 30px;
  background: rgba(255, 255, 255, 0.05);
  backdrop-filter: blur(25px);
  border: 1px solid rgba(255, 255, 255, 0.08);
  box-shadow: 0 0 40px rgba(0, 0, 0, 0.6);
  animation: fadeIn 1.2s ease forwards;
  transform: translateY(20px);
  opacity: 0;
}

@keyframes fadeIn {
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

/* ---------- TITLE ---------- */
h1 {
  font-size: 48px;
  font-weight: 700;
  text-align: center;
  margin-bottom: 10px;
  background: linear-gradient(120deg, #00aaff, #ff008c);
  -webkit-background-clip: text;
  color: transparent;
}

p.desc {
  text-align: center;
  font-size: 16px;
  opacity: 0.7;
  margin-bottom: 40px;
}

/* ---------- SOCIAL ICON GRID ---------- */
.socials {
  display: flex;
  justify-content: center;
  gap: 22px;
  flex-wrap: wrap;
}

.socials a {
  width: 70px;
  height: 70px;
  border-radius: 20px;
  background: rgba(255, 255, 255, 0.06);
  backdrop-filter: blur(20px);
  border: 1px solid rgba(255, 255, 255, 0.12);
  display: flex;
  align-items: center;
  justify-content: center;
  transition: 0.25s ease;
  box-shadow: 0 0 20px rgba(0,0,0,0.4);
}

.socials a:hover {
  transform: translateY(-6px) scale(1.05);
  border-color: rgba(255, 255, 255, 0.25);
  box-shadow: 0 0 25px rgba(0, 150, 255, 0.4);
}

/* ---------- ICONS ---------- */
.socials img {
  width: 34px;
  height: 34px;
  opacity: 0.9;
}

/* ---------- FOOTER ---------- */
footer {
  text-align: center;
  margin-top: 40px;
  opacity: 0.4;
  font-size: 13px;
}
</style>
</head>

<body>
<div class="bg"></div>
<div class="noise"></div>

<div class="container">
  <h1>AWWOOF</h1>
  <p class="desc">just a guy who plays games sometimes.</p>

  <div class="socials">

    <!-- Steam -->
    <a href="https://steamcommunity.com/id/cze0/" target="_blank">
      <img src="https://cdn.jsdelivr.net/gh/simple-icons/simple-icons/icons/steam.svg">
    </a>

    <!-- Roblox -->
    <a href="https://www.roblox.com/users/1319161590/profile" target="_blank">
      <img src="https://cdn.jsdelivr.net/gh/simple-icons/simple-icons/icons/roblox.svg">
    </a>

    <!-- YouTube -->
    <a href="https://www.youtube.com/@AWWOOF" target="_blank">
      <img src="https://cdn.jsdelivr.net/gh/simple-icons/simple-icons/icons/youtube.svg">
    </a>

    <!-- Discord -->
    <a href="https://discord.com/users/0" title="awwoof" target="_blank">
      <img src="https://cdn.jsdelivr.net/gh/simple-icons/simple-icons/icons/discord.svg">
    </a>

    <!-- Instagram -->
    <a href="https://www.instagram.com/awwoof_" target="_blank">
      <img src="https://cdn.jsdelivr.net/gh/simple-icons/simple-icons/icons/instagram.svg">
    </a>

  </div>

  <footer>© 2026 awwoof</footer>
</div>

</body>
</html>
