<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>My YouTube Channel</title>
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <style>
    :root {
      --bg1: #050816;
      --bg2: #0b1220;
      --accent: #ff4b8b;
      --accent-soft: rgba(255, 75, 139, 0.18);
      --text-main: #f9fafb;
      --text-muted: #9ca3af;
      --card-bg: rgba(15, 23, 42, 0.85);
      --border-subtle: rgba(148, 163, 184, 0.25);
      --radius-lg: 22px;
      --radius-pill: 999px;
      --shadow-soft: 0 24px 60px rgba(15, 23, 42, 0.9);
      --blur: 22px;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      font-family: system-ui, -apple-system, BlinkMacSystemFont, "SF Pro Text",
        "Segoe UI", sans-serif;
      min-height: 100vh;
      color: var(--text-main);
      background:
        radial-gradient(circle at top left, #1d2440 0, transparent 55%),
        radial-gradient(circle at bottom right, #3b1d4f 0, transparent 55%),
        linear-gradient(135deg, var(--bg1), var(--bg2));
      display: flex;
      align-items: center;
      justify-content: center;
      padding: 32px 16px;
    }

    .noise {
      position: fixed;
      inset: 0;
      pointer-events: none;
      opacity: 0.08;
      mix-blend-mode: soft-light;
      background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 160 160' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='1.2' numOctaves='3' stitchTiles='noStitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.6'/%3E%3C/svg%3E");
      z-index: -1;
    }

    .shell {
      width: 100%;
      max-width: 1120px;
      display: grid;
      grid-template-columns: minmax(0, 3fr) minmax(0, 2.4fr);
      gap: 32px;
      background: radial-gradient(circle at top left, rgba(148, 163, 184, 0.12), transparent 55%);
      border-radius: 32px;
      padding: 28px;
      border: 1px solid rgba(148, 163, 184, 0.35);
      box-shadow: var(--shadow-soft);
      backdrop-filter: blur(26px);
      position: relative;
      overflow: hidden;
    }

    .shell::before {
      content: "";
      position: absolute;
      inset: -40%;
      background:
        radial-gradient(circle at 10% 0%, rgba(96, 165, 250, 0.18), transparent 55%),
        radial-gradient(circle at 90% 100%, rgba(244, 114, 182, 0.18), transparent 55%);
      opacity: 0.9;
      mix-blend-mode: screen;
      pointer-events: none;
    }

    .shell-inner {
      position: relative;
      z-index: 1;
      display: contents;
    }

    .left,
    .right {
      position: relative;
      z-index: 1;
    }

    .pill {
      display: inline-flex;
      align-items: center;
      gap: 8px;
      padding: 4px 14px 4px 4px;
      border-radius: var(--radius-pill);
      border: 1px solid rgba(148, 163, 184, 0.5);
      background: radial-gradient(circle at top left, rgba(148, 163, 184, 0.3), rgba(15, 23, 42, 0.9));
      box-shadow: 0 12px 30px rgba(15, 23, 42, 0.8);
      margin-bottom: 18px;
    }

    .pill-avatar {
      width: 26px;
      height: 26px;
      border-radius: 999px;
      background: conic-gradient(from 160deg, #f97316, #ec4899, #6366f1, #22c55e, #f97316);
      padding: 2px;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .pill-avatar-inner {
      width: 100%;
      height: 100%;
      border-radius: inherit;
      background: #020617;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 14px;
      font-weight: 700;
      color: #e5e7eb;
    }

    .pill-text-main {
      font-size: 13px;
      font-weight: 600;
      letter-spacing: 0.04em;
      text-transform: uppercase;
      color: #e5e7eb;
    }

    .pill-text-sub {
      font-size: 12px;
      color: var(--text-muted);
    }

    h1 {
      font-size: clamp(32px, 4vw, 40px);
      line-height: 1.1;
      letter-spacing: -0.03em;
      margin-bottom: 12px;
    }

    h1 span {
      background: linear-gradient(120deg, #f97316, #ec4899, #6366f1);
      -webkit-background-clip: text;
      color: transparent;
    }

    .subtitle {
      font-size: 15px;
      color: var(--text-muted);
      max-width: 460px;
      line-height: 1.6;
      margin-bottom: 22px;
    }

    .badges {
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      margin-bottom: 24px;
    }

    .badge {
      font-size: 12px;
      padding: 6px 12px;
      border-radius: var(--radius-pill);
      border: 1px solid rgba(148, 163, 184, 0.5);
      background: rgba(15, 23, 42, 0.9);
      color: #e5e7eb;
      display: inline-flex;
      align-items: center;
      gap: 6px;
    }

    .badge-dot {
      width: 7px;
      height: 7px;
      border-radius: 999px;
      background: #22c55e;
      box-shadow: 0 0 0 4px rgba(34, 197, 94, 0.25);
    }

    .actions {
      display: flex;
      flex-wrap: wrap;
      gap: 12px;
      margin-bottom: 26px;
    }

    .btn-primary,
    .btn-ghost {
      border-radius: var(--radius-pill);
      padding: 10px 18px;
      font-size: 14px;
      font-weight: 600;
      border: 1px solid transparent;
      cursor: pointer;
      display: inline-flex;
      align-items: center;
      gap: 8px;
      text-decoration: none;
      transition: transform 0.12s ease, box-shadow 0.12s ease, background 0.12s ease, border-color 0.12s ease;
      white-space: nowrap;
    }

    .btn-primary {
      background: radial-gradient(circle at top left, #f97316, #ec4899, #6366f1);
      color: #0b1120;
      box-shadow: 0 18px 40px rgba(15, 23, 42, 0.9);
    }

    .btn-primary:hover {
      transform: translateY(-1px);
      box-shadow: 0 22px 50px rgba(15, 23, 42, 1);
    }

    .btn-ghost {
      background: rgba(15, 23, 42, 0.9);
      border-color: rgba(148, 163, 184, 0.6);
      color: #e5e7eb;
    }

    .btn-ghost:hover {
      background: rgba(15, 23, 42, 1);
      transform: translateY(-1px);
      box-shadow: 0 16px 36px rgba(15, 23, 42, 0.9);
    }

    .btn-icon {
      width: 18px;
      height: 18px;
      border-radius: 999px;
      border: 1px solid rgba(15, 23, 42, 0.9);
      background: rgba(15, 23, 42, 0.9);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 11px;
    }

    .meta {
      display: flex;
      flex-wrap: wrap;
      gap: 16px;
      font-size: 12px;
      color: var(--text-muted);
    }

    .meta span {
      display: inline-flex;
      align-items: center;
      gap: 6px;
    }

    .meta-dot {
      width: 4px;
      height: 4px;
      border-radius: 999px;
      background: rgba(148, 163, 184, 0.8);
    }

    .right {
      display: flex;
      align-items: stretch;
    }

    .card {
      position: relative;
      border-radius: var(--radius-lg);
      background: radial-gradient(circle at top left, rgba(148, 163, 184, 0.3), rgba(15, 23, 42, 0.98));
      border: 1px solid rgba(148, 163, 184, 0.5);
      padding: 18px 18px 16px;
      width: 100%;
      display: flex;
      flex-direction: column;
      gap: 14px;
      box-shadow: 0 20px 50px rgba(15, 23, 42, 0.95);
      backdrop-filter: blur(var(--blur));
      overflow: hidden;
    }

    .card-header {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 10px;
    }

    .card-title {
      display: flex;
      flex-direction: column;
      gap: 2px;
    }

    .card-title-main {
      font-size: 14px;
      font-weight: 600;
      letter-spacing: 0.04em;
      text-transform: uppercase;
      color: #e5e7eb;
    }

    .card-title-sub {
      font-size: 12px;
      color: var(--text-muted);
    }

    .card-chip {
      font-size: 11px;
      padding: 4px 10px;
      border-radius: var(--radius-pill);
      border: 1px solid rgba(148, 163, 184, 0.7);
      background: rgba(15, 23, 42, 0.9);
      color: #e5e7eb;
    }

    .card-main {
      border-radius: 18px;
      background: radial-gradient(circle at top left, rgba(15, 23, 42, 0.9), rgba(15, 23, 42, 1));
      border: 1px solid rgba(15, 23, 42, 0.9);
      padding: 14px 14px 12px;
      display: grid;
      grid-template-columns: minmax(0, 1.4fr) minmax(0, 1.1fr);
      gap: 12px;
    }

    .card-video {
      border-radius: 14px;
      background: #020617;
      border: 1px solid rgba(15, 23, 42, 1);
      overflow: hidden;
      position: relative;
      min-height: 150px;
      display: flex;
      align-items: center;
      justify-content: center;
      color: #e5e7eb;
      font-size: 13px;
    }

    .card-video::before {
      content: "";
      position: absolute;
      inset: 0;
      background:
        radial-gradient(circle at 10% 0%, rgba(96, 165, 250, 0.25), transparent 55%),
        radial-gradient(circle at 90% 100%, rgba(244, 114, 182, 0.25), transparent 55%);
      opacity: 0.9;
      mix-blend-mode: screen;
      pointer-events: none;
    }

    .card-video-inner {
      position: relative;
      z-index: 1;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 10px;
    }

    .play-button {
      width: 52px;
      height: 52px;
      border-radius: 999px;
      border: 1px solid rgba(248, 250, 252, 0.9);
      background: radial-gradient(circle at top left, #f97316, #ec4899, #6366f1);
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow: 0 18px 40px rgba(15, 23, 42, 1);
    }

    .play-button-icon {
      width: 0;
      height: 0;
      border-top: 9px solid transparent;
      border-bottom: 9px solid transparent;
      border-left: 14px solid #020617;
      margin-left: 2px;
    }

    .card-video-label {
      font-size: 11px;
      text-transform: uppercase;
      letter-spacing: 0.16em;
      color: rgba(226, 232, 240, 0.9);
    }

    .card-video-title {
      font-size: 13px;
      font-weight: 500;
      text-align: center;
      max-width: 220px;
    }

    .card-stats {
      display: flex;
      flex-direction: column;
      gap: 10px;
      font-size: 12px;
      color: var(--text-muted);
    }

    .stat-row {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 8px;
    }

    .stat-label {
      display: inline-flex;
      align-items: center;
      gap: 6px;
    }

    .stat-dot {
      width: 7px;
      height: 7px;
      border-radius: 999px;
      background: #6366f1;
    }

    .stat-value {
      font-weight: 600;
      color: #e5e7eb;
    }

    .stat-pill {
      display: inline-flex;
      align-items: center;
      gap: 6px;
      padding: 5px 10px;
      border-radius: var(--radius-pill);
      border: 1px solid rgba(148, 163, 184, 0.7);
      background: rgba(15, 23, 42, 0.95);
      color: #e5e7eb;
    }

    .card-footer {
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 10px;
      font-size: 11px;
      color: var(--text-muted);
    }

    .card-footer-left {
      display: inline-flex;
      align-items: center;
      gap: 8px;
    }

    .card-footer-dot {
      width: 6px;
      height: 6px;
      border-radius: 999px;
      background: #22c55e;
      box-shadow: 0 0 0 4px rgba(34, 197, 94, 0.25);
    }

    .card-footer-right {
      display: inline-flex;
      align-items: center;
      gap: 6px;
    }

    .card-footer-pill {
      padding: 4px 9px;
      border-radius: var(--radius-pill);
      border: 1px solid rgba(148, 163, 184, 0.7);
      background: rgba(15, 23, 42, 0.95);
    }

    @media (max-width: 880px) {
      .shell {
        grid-template-columns: minmax(0, 1fr);
        padding: 22px;
      }

      .right {
        order: -1;
      }
    }

    @media (max-width: 640px) {
      body {
        padding: 18px 12px;
      }

      .shell {
        padding: 18px;
        border-radius: 24px;
      }

      .card-main {
        grid-template-columns: minmax(0, 1fr);
      }

      .actions {
        flex-direction: column;
        align-items: stretch;
      }

      .btn-primary,
      .btn-ghost {
        justify-content: center;
        width: 100%;
      }
    }
  </style>
</head>
<body>
  <div class="noise"></div>

  <main class="shell">
    <div class="shell-inner">
      <!-- LEFT SIDE -->
      <section class="left">
        <div class="pill">
          <div class="pill-avatar">
            <div class="pill-avatar-inner">
              <!-- Initials -->
              YT
            </div>
          </div>
          <div>
            <div class="pill-text-main">Creator Dashboard</div>
            <div class="pill-text-sub">Welcome to my little corner of the internet</div>
          </div>
        </div>

        <h1>
          <span>YourName</span> on YouTube
        </h1>

        <p class="subtitle">
          I make videos about gaming, tech, and whatever I’m obsessed with this week. New uploads, behind‑the‑scenes,
          and all my links in one clean place.
        </p>

        <div class="badges">
          <div class="badge">
            <span class="badge-dot"></span>
            Weekly uploads
          </div>
          <div class="badge">
            🎮 Gaming · 💬 Commentary · 🎧 Chill vibes
          </div>
        </div>

        <div class="actions">
          <a
            class="btn-primary"
            href="https://youtube.com/@YOURCHANNEL"
            target="_blank"
            rel="noopener noreferrer"
          >
            <span class="btn-icon">▶</span>
            Visit my YouTube channel
          </a>

          <a
            class="btn-ghost"
            href="#socials"
          >
            <span class="btn-icon">★</span>
            All my socials
          </a>
        </div>

        <div class="meta">
          <span>
            <span class="meta-dot"></span>
            New video every week
          </span>
          <span>
            <span class="meta-dot"></span>
            Open to collabs &amp; projects
          </span>
        </div>
      </section>

      <!-- RIGHT SIDE -->
      <section class="right">
        <article class="card">
          <header class="card-header">
            <div class="card-title">
              <div class="card-title-main">Channel snapshot</div>
              <div class="card-title-sub">A quick peek at what I do</div>
            </div>
            <div class="card-chip">Live preview</div>
          </header>

          <div class="card-main">
            <div class="card-video">
              <div class="card-video-inner">
                <div class="play-button">
                  <div class="play-button-icon"></div>
                </div>
                <div class="card-video-label">Featured upload</div>
                <div class="card-video-title">
                  “Title of your latest or favorite video goes here”
                </div>
              </div>
            </div>

            <div class="card-stats">
              <div class="stat-row">
                <div class="stat-label">
                  <span class="stat-dot"></span>
                  Subscribers
                </div>
                <div class="stat-value">1.2K+</div>
              </div>

              <div class="stat-row">
                <div class="stat-label">
                  <span class="stat-dot" style="background:#f97316;"></span>
                  Total views
                </div>
                <div class="stat-value">85K+</div>
              </div>

              <div class="stat-row">
                <div class="stat-label">
                  <span class="stat-dot" style="background:#22c55e;"></span>
                  Upload schedule
                </div>
                <div class="stat-value">Every Friday</div>
              </div>

              <div class="stat-row">
                <div class="stat-pill">
                  🎮 Main content:
                  <strong> Gaming &amp; commentary</strong>
                </div>
              </div>
            </div>
          </div>

          <footer class="card-footer">
            <div class="card-footer-left">
              <span class="card-footer-dot"></span>
              <span>Currently editing the next video</span>
            </div>
            <div class="card-footer-right">
              <span class="card-footer-pill">#YouTube</span>
              <span class="card-footer-pill">#Creator</span>
            </div>
          </footer>
        </article>
      </section>
    </div>
  </main>

  <!-- SOCIALS SECTION -->
  <section
    id="socials"
    style="
      position: fixed;
      inset-inline: 0;
      bottom: 18px;
      display: flex;
      justify-content: center;
      pointer-events: none;
    "
  >
    <div
      style="
        pointer-events: auto;
        display: inline-flex;
        align-items: center;
        gap: 10px;
        padding: 8px 14px;
        border-radius: 999px;
        border: 1px solid rgba(148, 163, 184, 0.6);
        background: rgba(15, 23, 42, 0.96);
        backdrop-filter: blur(18px);
        box-shadow: 0 18px 40px rgba(15, 23, 42, 0.95);
        font-size: 12px;
        color: #e5e7eb;
      "
    >
      <span style="opacity: 0.8;">Find me also on</span>
      <a
        href="https://twitter.com/"
        target="_blank"
        rel="noopener noreferrer"
        style="color: #e5e7eb; text-decoration: none;"
      >
        X / Twitter
      </a>
      <span style="opacity: 0.4;">•</span>
      <a
        href="https://instagram.com/"
        target="_blank"
        rel="noopener noreferrer"
        style="color: #e5e7eb; text-decoration: none;"
      >
        Instagram
      </a>
      <span style="opacity: 0.4;">•</span>
      <a
        href="https://discord.gg/"
        target="_blank"
        rel="noopener noreferrer"
        style="color: #e5e7eb; text-decoration: none;"
      >
        Discord
      </a>
    </div>
  </section>
</body>
</html>
