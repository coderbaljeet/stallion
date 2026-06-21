<!DOCTYPE html>
<html lang="en" data-theme="light">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover"/>
<meta name="theme-color" content="#0f172a"/>
<meta name="apple-mobile-web-app-capable" content="yes"/>
<meta name="apple-mobile-web-app-title" content="Stallion AI"/>
<meta name="description" content="Stallion — The Surface Expert AI for coatings, polishing, wall paints & more."/>
<title>Stallion — The Surface Expert</title>
<link rel="preconnect" href="https://fonts.googleapis.com"/>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800;900&family=Playfair+Display:wght@700;900&display=swap" rel="stylesheet"/>

<style>
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0;-webkit-tap-highlight-color:transparent}
html,body{height:100%;overflow:hidden;font-family:'Inter',system-ui,sans-serif}

/* ════ THEME TOKENS ════ */
[data-theme="light"]{
  --bg:#ffffff;
  --sidebar-bg:#f7f7f8;
  --surface:#ffffff;
  --surface2:#f7f7f8;
  --border:#e5e5e8;
  --border2:#d9d9de;
  --text:#1a1a1a;
  --text2:#3d3d3d;
  --text3:#6e6e80;
  --muted:#8e8ea0;
  --hover:#ececf1;
  --gold:#d97706;
  --gold2:#f59e0b;
  --gold-bg:#fff8e8;
  --gold-border:#fde68a;
  --accent:#1e3a8a;
  --accent2:#2563eb;
  --red:#dc2626;
  --bubble-user-bg:#f4f4f5;
  --bubble-user-text:#1a1a1a;
  --chat-bg:#ffffff;
  --input-bg:#ffffff;
  --input-border:#d9d9de;
  --shadow:0 2px 14px rgba(0,0,0,0.06);
  --sidebar-item-active:#ececf1;
}
[data-theme="dark"]{
  --bg:#212121;
  --sidebar-bg:#181818;
  --surface:#2a2a2a;
  --surface2:#212121;
  --border:#3a3a3a;
  --border2:#454545;
  --text:#ececec;
  --text2:#d4d4d4;
  --text3:#a0a0a0;
  --muted:#8e8ea0;
  --hover:#2f2f2f;
  --gold:#f59e0b;
  --gold2:#fbbf24;
  --gold-bg:#2a2110;
  --gold-border:#5a4310;
  --accent:#3b82f6;
  --accent2:#60a5fa;
  --red:#ef4444;
  --bubble-user-bg:#2f2f2f;
  --bubble-user-text:#ececec;
  --chat-bg:#212121;
  --input-bg:#2a2a2a;
  --input-border:#454545;
  --shadow:0 2px 14px rgba(0,0,0,0.3);
  --sidebar-item-active:#2f2f2f;
}

body{background:var(--bg);color:var(--text);transition:background .25s,color .25s}

/* ════ APP SHELL ════ */
#app{display:flex;height:100vh;width:100%;overflow:hidden}

/* ════ SIDEBAR ════ */
#sidebar{
  width:268px;flex-shrink:0;background:var(--sidebar-bg);
  display:flex;flex-direction:column;border-right:1px solid var(--border);
  transition:width .2s,transform .2s;
}
#sidebar.collapsed{width:0;border-right:none}
.sidebar-inner{width:268px;height:100%;display:flex;flex-direction:column;overflow:hidden}

.sidebar-header{padding:14px 12px 10px;flex-shrink:0}
.brand-row{display:flex;align-items:center;gap:10px;padding:8px 6px 14px}
.brand-logo{width:32px;height:32px;border-radius:9px;background:linear-gradient(135deg,var(--gold),var(--gold2));display:flex;align-items:center;justify-content:center;flex-shrink:0;box-shadow:0 2px 8px rgba(217,119,6,.35)}
.brand-text-name{font-family:'Playfair Display',serif;font-weight:900;font-size:1.05rem;color:var(--text);letter-spacing:-.01em;line-height:1}
.brand-text-sub{font-size:.6rem;font-weight:700;text-transform:uppercase;letter-spacing:.1em;color:var(--gold);margin-top:2px}

.new-chat-btn{
  display:flex;align-items:center;gap:9px;width:100%;
  background:transparent;border:1px solid var(--border2);border-radius:10px;
  padding:10px 12px;cursor:pointer;font-family:inherit;font-size:.84rem;font-weight:600;
  color:var(--text);transition:background .15s;
}
.new-chat-btn:hover{background:var(--hover)}

.sidebar-section{padding:6px 12px;overflow-y:auto;flex:1}
.sidebar-label{font-size:.68rem;font-weight:700;text-transform:uppercase;letter-spacing:.08em;color:var(--muted);padding:14px 8px 6px}

.topic-link{
  display:flex;align-items:center;gap:10px;width:100%;background:none;border:none;
  padding:9px 8px;border-radius:8px;cursor:pointer;text-align:left;font-family:inherit;
  font-size:.83rem;font-weight:500;color:var(--text2);transition:background .12s;
}
.topic-link:hover{background:var(--hover)}
.topic-link .t-icon{width:20px;height:20px;flex-shrink:0;display:flex;align-items:center;justify-content:center;opacity:.85}

.chat-history-item{
  display:flex;align-items:center;gap:8px;width:100%;background:none;border:none;
  padding:9px 8px;border-radius:8px;cursor:pointer;text-align:left;font-family:inherit;
  font-size:.82rem;color:var(--text2);transition:background .12s;overflow:hidden;
}
.chat-history-item span{white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.chat-history-item:hover{background:var(--hover)}
.chat-history-item.active{background:var(--sidebar-item-active);color:var(--text);font-weight:600}

.sidebar-footer{padding:10px 12px;border-top:1px solid var(--border);flex-shrink:0}
.theme-row{display:flex;align-items:center;justify-content:space-between;padding:8px;border-radius:9px}
.theme-row-label{display:flex;align-items:center;gap:9px;font-size:.83rem;font-weight:600;color:var(--text2)}

/* ════ TOGGLE SWITCH ════ */
.theme-toggle{position:relative;width:40px;height:22px;cursor:pointer;flex-shrink:0}
.theme-toggle input{opacity:0;width:0;height:0;position:absolute}
.toggle-track{width:40px;height:22px;border-radius:11px;background:var(--border2);transition:background .25s;display:block;position:relative}
.toggle-thumb{position:absolute;top:2px;left:2px;width:18px;height:18px;border-radius:50%;background:#fff;transition:transform .25s,background .25s;display:flex;align-items:center;justify-content:center;font-size:.6rem;box-shadow:0 1px 3px rgba(0,0,0,.3)}
input:checked + .toggle-track{background:var(--gold)}
input:checked + .toggle-track .toggle-thumb{transform:translateX(18px)}

/* ════ MAIN COLUMN ════ */
#main{flex:1;display:flex;flex-direction:column;min-width:0;background:var(--chat-bg)}

.main-topbar{
  display:flex;align-items:center;gap:10px;padding:12px 18px;
  border-bottom:1px solid var(--border);flex-shrink:0;background:var(--chat-bg);
}
.sidebar-toggle-btn{
  background:none;border:none;cursor:pointer;width:34px;height:34px;border-radius:8px;
  display:flex;align-items:center;justify-content:center;flex-shrink:0;color:var(--text2);
  transition:background .12s;
}
.sidebar-toggle-btn:hover{background:var(--hover)}
.main-topbar-title{font-weight:700;font-size:.95rem;color:var(--text);display:flex;align-items:center;gap:7px}
.online-pill{display:flex;align-items:center;gap:5px;font-size:.68rem;font-weight:700;color:var(--gold);background:var(--gold-bg);border:1px solid var(--gold-border);border-radius:20px;padding:3px 10px;margin-left:auto;flex-shrink:0}
.online-pill::before{content:'';width:6px;height:6px;border-radius:50%;background:#10b981;animation:pulse-dot 2s ease-in-out infinite}
@keyframes pulse-dot{0%,100%{opacity:1}50%{opacity:.55}}

/* ════ CHAT AREA ════ */
#chat-scroll{flex:1;overflow-y:auto;display:flex;flex-direction:column;align-items:center}
.chat-inner{width:100%;max-width:760px;padding:24px 20px 12px;display:flex;flex-direction:column;gap:22px}

/* ── Welcome / Empty state ── */
#welcome-view{flex:1;display:flex;flex-direction:column;align-items:center;justify-content:center;padding:20px;text-align:center;width:100%;max-width:720px;margin:0 auto}
.welcome-logo{width:64px;height:64px;border-radius:18px;background:linear-gradient(135deg,var(--gold),var(--gold2));display:flex;align-items:center;justify-content:center;margin-bottom:18px;box-shadow:0 8px 28px rgba(217,119,6,.3)}
.welcome-title{font-family:'Playfair Display',serif;font-weight:900;font-size:1.9rem;color:var(--text);letter-spacing:-.02em;margin-bottom:6px}
.welcome-sub{font-size:.95rem;color:var(--text3);margin-bottom:34px;max-width:440px;line-height:1.5}
.welcome-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:12px;width:100%;max-width:680px}
.welcome-card{
  background:var(--surface);border:1px solid var(--border);border-radius:14px;padding:16px 14px;
  cursor:pointer;text-align:left;transition:border-color .15s,transform .15s;display:flex;flex-direction:column;gap:8px;
}
.welcome-card:hover{border-color:var(--gold-border);transform:translateY(-2px)}
.welcome-card-icon{width:34px;height:34px;border-radius:9px;display:flex;align-items:center;justify-content:center}
.welcome-card-text{font-size:.82rem;font-weight:600;color:var(--text2);line-height:1.35}

/* ── Message rows ── */
.msg-row{display:flex;gap:14px;align-items:flex-start}
.msg-row.user{justify-content:flex-end}
.ai-avatar{width:30px;height:30px;border-radius:9px;background:linear-gradient(135deg,var(--gold),var(--gold2));display:flex;align-items:center;justify-content:center;flex-shrink:0;box-shadow:0 2px 8px rgba(217,119,6,.3)}
.msg-body{max-width:78%;font-size:.92rem;line-height:1.65}
.msg-row.user .msg-body{background:var(--bubble-user-bg);color:var(--bubble-user-text);padding:10px 15px;border-radius:16px}
.msg-row.ai .msg-body{color:var(--text);padding-top:3px}

/* Markdown */
.md-h1{font-family:'Playfair Display',serif;font-size:1.15rem;font-weight:700;color:var(--text);margin:4px 0 10px;line-height:1.3}
.md-h2{font-size:.95rem;font-weight:800;color:var(--gold);margin:14px 0 6px;text-transform:uppercase;letter-spacing:.04em}
.md-h3{font-size:.9rem;font-weight:700;color:var(--accent2);margin:10px 0 4px}
.md-p{margin:0 0 8px;color:var(--text2)}
.md-hr{border:none;border-top:1px solid var(--border);margin:12px 0}
.md-ul,.md-ol{margin:6px 0 10px}
.md-li{display:flex;gap:8px;margin-bottom:5px;color:var(--text2)}
.md-bullet{color:var(--gold);flex-shrink:0;font-weight:900;margin-top:1px}
.md-num{color:var(--gold);font-weight:800;flex-shrink:0;min-width:20px}
.md-code{background:var(--surface2);padding:2px 6px;border-radius:5px;font-size:.86em;font-family:'SF Mono',Consolas,monospace;color:var(--accent2);border:1px solid var(--border)}

/* Typing */
.typing{display:flex;gap:5px;align-items:center;padding:6px 0}
.dot{width:7px;height:7px;border-radius:50%;background:var(--gold);animation:bounce 1.2s ease-in-out infinite}
.dot:nth-child(2){animation-delay:.2s}.dot:nth-child(3){animation-delay:.4s}
@keyframes bounce{0%,80%,100%{opacity:.25;transform:scale(.85)}40%{opacity:1;transform:scale(1)}}

/* Store finder card */
.store-card{background:var(--surface);border:1px solid var(--border);border-radius:14px;padding:16px;max-width:380px;box-shadow:var(--shadow);margin-top:4px}
.store-card-head{display:flex;align-items:center;gap:9px;margin-bottom:9px}
.store-card-icon{width:32px;height:32px;border-radius:9px;background:var(--gold-bg);border:1px solid var(--gold-border);display:flex;align-items:center;justify-content:center;flex-shrink:0}
.store-card-title{font-weight:800;font-size:.9rem;color:var(--text)}
.store-card-desc{font-size:.85rem;color:var(--text2);margin-bottom:13px;line-height:1.5}
.store-card-btn{width:100%;background:linear-gradient(135deg,var(--gold),var(--gold2));border:none;border-radius:11px;padding:11px;color:#fff;font-weight:800;font-size:.86rem;cursor:pointer;display:flex;align-items:center;justify-content:center;gap:8px;font-family:inherit;transition:opacity .15s}
.store-card-btn:hover{opacity:.92}
.store-card-status{font-size:.72rem;color:var(--muted);margin-top:8px;text-align:center}

.error-box{background:#fef2f2;border:1px solid #fecaca;border-radius:12px;padding:12px 16px;color:var(--red);font-size:.85rem;max-width:520px}
[data-theme="dark"] .error-box{background:#2a1414;border-color:#5a1f1f}

/* ════ INPUT AREA ════ */
.input-zone{padding:14px 20px calc(18px + env(safe-area-inset-bottom,0px));display:flex;justify-content:center;flex-shrink:0}
.input-zone-inner{width:100%;max-width:760px}
.input-shell{
  display:flex;align-items:flex-end;gap:10px;background:var(--input-bg);
  border:1.5px solid var(--input-border);border-radius:20px;padding:11px 11px 11px 18px;
  box-shadow:var(--shadow);transition:border-color .2s;
}
.input-shell:focus-within{border-color:var(--gold)}
#chat-input{flex:1;border:none;outline:none;resize:none;font-family:inherit;font-size:.92rem;line-height:1.5;background:transparent;color:var(--text);max-height:160px;overflow-y:auto}
#chat-input::placeholder{color:var(--muted)}
.send-btn{border:none;border-radius:13px;width:36px;height:36px;display:flex;align-items:center;justify-content:center;cursor:pointer;flex-shrink:0;transition:all .15s}
.send-btn.on{background:linear-gradient(135deg,var(--gold),var(--gold2))}
.send-btn.off{background:var(--border2);cursor:not-allowed}
.input-footnote{text-align:center;font-size:.7rem;color:var(--muted);margin-top:9px}

/* ════ MOBILE ════ */
.mobile-topbar{display:none}
@media (max-width:860px){
  #sidebar{position:fixed;top:0;left:0;bottom:0;z-index:50;width:268px;transform:translateX(-100%);transition:transform .25s;box-shadow:0 0 40px rgba(0,0,0,.25)}
  #sidebar.mobile-open{transform:translateX(0)}
  #sidebar.collapsed{width:268px}
  #sidebar-backdrop{display:none;position:fixed;inset:0;background:rgba(0,0,0,.4);z-index:40}
  #sidebar-backdrop.visible{display:block}
  .welcome-grid{grid-template-columns:1fr 1fr}
  .welcome-title{font-size:1.5rem}
  .msg-body{max-width:88%}
  .chat-inner{padding:18px 14px 10px}
}
@media (max-width:480px){
  .welcome-grid{grid-template-columns:1fr}
}

/* Install banner */
#install-banner{display:none;position:fixed;bottom:20px;left:50%;transform:translateX(-50%);max-width:420px;width:calc(100% - 28px);background:var(--text);border-radius:14px;padding:13px 15px;box-shadow:0 10px 36px rgba(0,0,0,.35);z-index:100;align-items:center;gap:12px}
#install-banner.visible{display:flex}
[data-theme="light"] #install-banner{background:#1a1a1a}
.install-text .install-title{font-size:.83rem;font-weight:800;color:#fff}
.install-text .install-sub{font-size:.7rem;color:rgba(255,255,255,.6)}
.install-btn-el{background:linear-gradient(135deg,var(--gold),var(--gold2));border:none;border-radius:9px;padding:8px 14px;color:#fff;font-size:.78rem;font-weight:800;cursor:pointer;white-space:nowrap;font-family:inherit}
.install-close-el{background:rgba(255,255,255,.12);border:none;border-radius:8px;width:26px;height:26px;display:flex;align-items:center;justify-content:center;cursor:pointer;color:#fff;font-size:.85rem;flex-shrink:0}
</style>
</head>
<body>
<div id="app">
  <div id="sidebar-backdrop" onclick="closeMobileSidebar()"></div>

  <!-- ══════════ SIDEBAR ══════════ -->
  <div id="sidebar">
    <div class="sidebar-inner">
      <div class="sidebar-header">
        <div class="brand-row">
          <div class="brand-logo">
            <svg width="18" height="18" viewBox="0 0 100 100" fill="none"><path d="M72 18C72 18 78 12 82 14C86 16 84 22 80 24C84 24 88 28 86 34C84 40 78 40 74 38L72 46C74 52 72 60 66 64L64 80C63 84 58 86 56 82L55 68C50 70 44 70 40 68L39 82C38 86 32 86 31 82L30 66C24 62 20 54 22 46C24 38 30 34 36 34L38 28C34 26 32 20 36 16C40 12 46 16 46 22L50 24C54 22 58 18 62 18Z" fill="#fff" opacity="0.95"/></svg>
          </div>
          <div>
            <div class="brand-text-name">STALLION</div>
            <div class="brand-text-sub">Surface Expert</div>
          </div>
        </div>
        <button class="new-chat-btn" onclick="resetChat()">
          <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="12" y1="5" x2="12" y2="19"/><line x1="5" y1="12" x2="19" y2="12"/></svg>
          New chat
        </button>
      </div>

      <div class="sidebar-section">
        <div class="sidebar-label">Topics</div>
        <div id="topic-links"></div>

        <div class="sidebar-label">Recent</div>
        <div id="chat-history-list"></div>
      </div>

      <div class="sidebar-footer">
        <div class="theme-row">
          <div class="theme-row-label">
            <svg width="17" height="17" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 12.79A9 9 0 1111.21 3 7 7 0 0021 12.79z"/></svg>
            Dark mode
          </div>
          <label class="theme-toggle">
            <input type="checkbox" id="theme-toggle" onchange="toggleTheme(this)"/>
            <span class="toggle-track"><span class="toggle-thumb" id="toggle-thumb"></span></span>
          </label>
        </div>
      </div>
    </div>
  </div>

  <!-- ══════════ MAIN ══════════ -->
  <div id="main">
    <div class="main-topbar">
      <button class="sidebar-toggle-btn" onclick="toggleSidebar()">
        <svg width="19" height="19" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="3" y="3" width="18" height="18" rx="2"/><line x1="9" y1="3" x2="9" y2="21"/></svg>
      </button>
      <div class="main-topbar-title">
        <span id="current-chat-title">New conversation</span>
      </div>
      <div class="online-pill">Live AI</div>
    </div>

    <div id="chat-scroll">
      <div id="welcome-view">
        <div class="welcome-logo">
          <svg width="34" height="34" viewBox="0 0 100 100" fill="none"><path d="M72 18C72 18 78 12 82 14C86 16 84 22 80 24C84 24 88 28 86 34C84 40 78 40 74 38L72 46C74 52 72 60 66 64L64 80C63 84 58 86 56 82L55 68C50 70 44 70 40 68L39 82C38 86 32 86 31 82L30 66C24 62 20 54 22 46C24 38 30 34 36 34L38 28C34 26 32 20 36 16C40 12 46 16 46 22L50 24C54 22 58 18 62 18Z" fill="#fff" opacity="0.95"/></svg>
        </div>
        <div class="welcome-title">STALLION</div>
        <div class="welcome-sub">The Surface Expert. Ask me about wood finishing, metal polishing, glass care, wall paints, and coating systems.</div>
        <div class="welcome-grid" id="welcome-grid"></div>
      </div>

      <div class="chat-inner" id="chat-inner" style="display:none"></div>
    </div>

    <div class="input-zone">
      <div class="input-zone-inner">
        <div class="input-shell">
          <textarea id="chat-input" rows="1" placeholder="Message Stallion…"></textarea>
          <button class="send-btn off" id="chat-send-btn" onclick="sendChat()">
            <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="#94a3b8" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><line x1="22" y1="2" x2="11" y2="13"/><polygon points="22 2 15 22 11 13 2 9 22 2"/></svg>
          </button>
        </div>
        <div class="input-footnote">Stallion can make mistakes. Verify critical product specifications with the TDS.</div>
      </div>
    </div>
  </div>
</div>

<div id="install-banner">
  <div class="install-text">
    <div class="install-title">📲 Install Stallion</div>
    <div class="install-sub">Add to your device for quick access</div>
  </div>
  <button class="install-btn-el" id="install-btn">Install</button>
  <button class="install-close-el" onclick="dismissBanner()">✕</button>
</div>

<script>
// ── TOPIC & PROMPT DATA ───────────────────────────────────
const TOPICS = [
  { svg:`<svg width="17" height="17" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z"/></svg>`,
    color:"#d97706", label:"Wood & Veneer",
    query:"Tell me about wood and veneer finishing — veneers, solid wood, grit sequences, coatings." },
  { svg:`<svg width="17" height="17" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><circle cx="12" cy="12" r="4"/></svg>`,
    color:"#2563eb", label:"Metal Care",
    query:"Tell me about metal polishing and care — stainless steel, brass, aluminum, copper." },
  { svg:`<svg width="17" height="17" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 3h18v18H3zM3 9h18M9 3v18"/></svg>`,
    color:"#059669", label:"Glass Care",
    query:"Tell me about glass care — cleaning methods, scratch removal with cerium oxide, protective coatings." },
  { svg:`<svg width="17" height="17" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M3 9l9-7 9 7v11a2 2 0 01-2 2H5a2 2 0 01-2-2z"/><polyline points="9 22 9 12 15 12 15 22"/></svg>`,
    color:"#7c3aed", label:"Wall Paints",
    query:"Tell me about wall paints and coatings — interior, exterior, putty, primers, emulsions, waterproofing." },
  { svg:`<svg width="17" height="17" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="11" cy="11" r="8"/><line x1="21" y1="21" x2="16.65" y2="16.65"/></svg>`,
    color:"#dc2626", label:"Troubleshoot",
    query:"Help me troubleshoot a finishing defect — orange peel, fisheye, blushing, peeling, or cratering." },
  { svg:`<svg width="17" height="17" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="4" y1="9" x2="20" y2="9"/><line x1="4" y1="15" x2="20" y2="15"/><line x1="10" y1="3" x2="8" y2="21"/><line x1="16" y1="3" x2="14" y2="21"/></svg>`,
    color:"#0891b2", label:"Grit Sequences",
    query:"What grit sequences should I use? PU polish on wood, melamine, and metal polishing." },
];

const WELCOME_PROMPTS = [
  {icon:"🪵", text:"Best finish for White Ash veneer?", color:"#d97706"},
  {icon:"🔧", text:"How to fix orange peel on PU coating?", color:"#dc2626"},
  {icon:"📐", text:"Grit sequence before melamine polish", color:"#0891b2"},
  {icon:"🏠", text:"Exterior wall paint for humid climates", color:"#7c3aed"},
  {icon:"🔩", text:"How to polish stainless steel?", color:"#2563eb"},
  {icon:"📍", text:"Find a PU coating store near me", color:"#059669"},
];

const SYSTEM_PROMPT = `You are STALLION — The Surface Expert AI, a specialist created for the Stallion brand in surface care and finishing.

Your expertise covers:
- Wood finishing: PU coatings, Melamine, NC polish, UV coatings, water-based finishes, wood stains
- Veneer polishing: White Ash, White Oak, Red Oak, Teak, Walnut, and all major veneers
- Laminates and decorative panels
- Metal polishing: Stainless steel, brass, aluminum, copper
- Glass care: Cleaning, scratch removal, protective coatings
- Wall care: Putty, primers, interior/exterior paints, emulsions, texture paints, waterproofing
- Troubleshooting: blushing, orange peel, fisheye, peeling, cratering, and all finishing defects

Default to SHORT, direct answers — 3-6 sentences or a tight bullet list. Give the recommended product/process first, one line of why, and a single key safety or mistake note only if critical. Skip headers and the 5-part structure unless the person explicitly asks for a "detailed", "full", or "step-by-step" answer — only then use:
1. **Surface / Problem Identification**
2. **Diagnosis or Context**
3. **Recommended Products / Process** (step-by-step)
4. **Safety Precautions**
5. **Common Mistakes to Avoid**

Built-in recommendations:
- White Ash Veneer → PU Matt finish
- White Oak Veneer → Stain + PU Satin
- Red Oak → Dark Stain + PU Gloss
- Teak → Teak Oil or PU Matt
- Stainless Steel → Non-abrasive Metal Polish
- Glass scratches → Cerium Oxide Polish
- Interior Wall → Acrylic Emulsion with primer
- Exterior Wall (humid) → Weatherproof/Elastomeric Paint
- Melamine boards → Melamine coating system
- MDF → Grain filler + PU or water-based topcoat

Grit sequences:
- PU on wood: 80→120→180→240→320 (sealer), 400 (topcoat)
- Before Melamine: 80→120→180→240
- Metal: 220→400→600→800 wet/dry, then compound

Be concise by default. Never invent product specs. Avoid unnecessary preamble — get straight to the answer.

If the person asks where to buy a product or find a nearby store/dealer, give your normal product answer — the app will automatically show a "Find Nearby Stores" button below your reply, so don't tell them you can't help with that.`;

// ── STATE ─────────────────────────────────────────────────
let messages = [];
let loading = false;
let userCoords = null;
let sidebarCollapsed = false;
let chatStarted = false;

// ── INIT ──────────────────────────────────────────────────
document.addEventListener('DOMContentLoaded', () => {
  buildTopicLinks();
  buildWelcomeGrid();
  initInputListeners();
  registerSW();
});

// ── THEME ─────────────────────────────────────────────────
function toggleTheme(checkbox) {
  const dark = checkbox.checked;
  document.documentElement.setAttribute('data-theme', dark ? 'dark' : 'light');
  document.getElementById('toggle-thumb').textContent = dark ? '🌙' : '☀️';
}

// ── SIDEBAR ───────────────────────────────────────────────
function toggleSidebar() {
  const sb = document.getElementById('sidebar');
  if (window.innerWidth <= 860) {
    sb.classList.toggle('mobile-open');
    document.getElementById('sidebar-backdrop').classList.toggle('visible');
  } else {
    sidebarCollapsed = !sidebarCollapsed;
    sb.classList.toggle('collapsed', sidebarCollapsed);
  }
}
function closeMobileSidebar() {
  document.getElementById('sidebar').classList.remove('mobile-open');
  document.getElementById('sidebar-backdrop').classList.remove('visible');
}

// ── PWA ───────────────────────────────────────────────────
function registerSW() {
  if ('serviceWorker' in navigator) {
    const swCode = `const C='stallion-web-v1';self.addEventListener('install',e=>{e.waitUntil(caches.open(C).then(c=>c.addAll(['./']).catch(()=>{})));self.skipWaiting();});self.addEventListener('activate',e=>{e.waitUntil(caches.keys().then(keys=>Promise.all(keys.filter(k=>k!==C).map(k=>caches.delete(k)))));self.clients.claim();});self.addEventListener('fetch',e=>{if(e.request.url.includes('anthropic.com')||e.request.url.includes('fonts.googleapis.com')||e.request.url.includes('maps.google.com'))return;e.respondWith(fetch(e.request).catch(()=>caches.match(e.request)));});`;
    const blob = new Blob([swCode], {type:'application/javascript'});
    navigator.serviceWorker.register(URL.createObjectURL(blob)).catch(()=>{});
  }
  window.addEventListener('beforeinstallprompt', e => {
    e.preventDefault();
    window.deferredInstallPrompt = e;
    document.getElementById('install-banner').classList.add('visible');
  });
  document.getElementById('install-btn').addEventListener('click', async () => {
    if (!window.deferredInstallPrompt) return;
    window.deferredInstallPrompt.prompt();
    await window.deferredInstallPrompt.userChoice;
    window.deferredInstallPrompt = null; dismissBanner();
  });
  window.addEventListener('appinstalled', dismissBanner);
}
function dismissBanner(){ document.getElementById('install-banner').classList.remove('visible'); }

// ── BUILD SIDEBAR / WELCOME ───────────────────────────────
function buildTopicLinks() {
  const wrap = document.getElementById('topic-links');
  TOPICS.forEach(t => {
    const btn = document.createElement('button');
    btn.className = 'topic-link';
    btn.onclick = () => { closeMobileSidebar(); startConversation(t.query); };
    btn.innerHTML = `<span class="t-icon" style="color:${t.color}">${t.svg}</span><span>${t.label}</span>`;
    wrap.appendChild(btn);
  });
}

function buildWelcomeGrid() {
  const grid = document.getElementById('welcome-grid');
  WELCOME_PROMPTS.forEach(p => {
    const card = document.createElement('button');
    card.className = 'welcome-card';
    card.onclick = () => startConversation(p.text);
    card.innerHTML = `
      <div class="welcome-card-icon" style="background:${p.color}18">${p.icon}</div>
      <div class="welcome-card-text">${p.text}</div>`;
    grid.appendChild(card);
  });
}

function addHistoryItem(title) {
  const list = document.getElementById('chat-history-list');
  document.querySelectorAll('.chat-history-item').forEach(i => i.classList.remove('active'));
  const item = document.createElement('button');
  item.className = 'chat-history-item active';
  item.innerHTML = `
    <svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" style="flex-shrink:0;opacity:.6"><path d="M21 15a2 2 0 01-2 2H7l-4 4V5a2 2 0 012-2h14a2 2 0 012 2z"/></svg>
    <span>${escHtml(title)}</span>`;
  list.insertBefore(item, list.firstChild);
}

// ── CHAT FLOW ─────────────────────────────────────────────
function resetChat() {
  messages = [];
  chatStarted = false;
  document.getElementById('welcome-view').style.display = 'flex';
  document.getElementById('chat-inner').style.display = 'none';
  document.getElementById('chat-inner').innerHTML = '';
  document.getElementById('current-chat-title').textContent = 'New conversation';
  document.getElementById('chat-input').value = '';
  document.getElementById('chat-input').style.height = 'auto';
  updateSendBtn();
  closeMobileSidebar();
  document.querySelectorAll('.chat-history-item').forEach(i => i.classList.remove('active'));
}

function startConversation(text) {
  closeMobileSidebar();
  sendMessage(text);
}

function initInputListeners() {
  const ta = document.getElementById('chat-input');
  ta.addEventListener('input', () => {
    ta.style.height = 'auto';
    ta.style.height = Math.min(ta.scrollHeight, 160) + 'px';
    updateSendBtn();
  });
  ta.addEventListener('keydown', e => { if(e.key==='Enter'&&!e.shiftKey){e.preventDefault();sendChat();} });
}

function updateSendBtn() {
  const val = document.getElementById('chat-input').value.trim();
  const ok = val && !loading;
  const btn = document.getElementById('chat-send-btn');
  btn.className = 'send-btn ' + (ok ? 'on' : 'off');
  btn.querySelector('svg').setAttribute('stroke', ok ? '#fff' : '#94a3b8');
}

function sendChat() {
  const val = document.getElementById('chat-input').value.trim();
  if (!val || loading) return;
  document.getElementById('chat-input').value = '';
  document.getElementById('chat-input').style.height = 'auto';
  updateSendBtn();
  sendMessage(val);
}

// ── STORE FINDER ──────────────────────────────────────────
const STORE_INTENT_RE = /\b(where (can|do) i (buy|find|get)|find (a )?(store|shop|dealer|supplier)|near(by)? (me|stores?|shops?|dealers?)|local (store|shop|dealer|supplier)|buy .* (near|nearby)|store near|shop near|where to buy)\b/i;

function detectStoreIntent(text) { return STORE_INTENT_RE.test(text); }

function extractProductTerm(text) {
  const known = ['pu coating','melamine','nc polish','uv coating','wood stain','wood polish','veneer polish',
    'metal polish','stainless steel polish','brass polish','glass polish','cerium oxide','wall paint',
    'wall putty','primer','emulsion','waterproofing','texture paint','teak oil','lacquer','varnish','sealer'];
  const lower = text.toLowerCase();
  for (const k of known) { if (lower.includes(k)) return k; }
  return 'surface finishing products';
}

function requestLocation() {
  return new Promise(resolve => {
    if (!('geolocation' in navigator)) { resolve(null); return; }
    navigator.geolocation.getCurrentPosition(
      pos => resolve({lat:pos.coords.latitude, lng:pos.coords.longitude}),
      () => resolve(null),
      {timeout:8000, maximumAge:600000}
    );
  });
}

function buildMapsUrl(productTerm, coords) {
  const q = encodeURIComponent(productTerm + ' supplier near me');
  if (coords) return `https://www.google.com/maps/search/${q}/@${coords.lat},${coords.lng},14z`;
  return `https://www.google.com/maps/search/${q}`;
}

function showStoreFinderCard(productTerm) {
  const container = document.getElementById('chat-inner');
  const row = document.createElement('div');
  row.className = 'msg-row ai';

  const av = document.createElement('div');
  av.className = 'ai-avatar';
  av.innerHTML = `<svg width="16" height="16" viewBox="0 0 100 100" fill="none"><path d="M72 18C72 18 78 12 82 14C86 16 84 22 80 24C84 24 88 28 86 34C84 40 78 40 74 38L72 46C74 52 72 60 66 64L64 80C63 84 58 86 56 82L55 68C50 70 44 70 40 68L39 82C38 86 32 86 31 82L30 66C24 62 20 54 22 46C24 38 30 34 36 34L38 28C34 26 32 20 36 16C40 12 46 16 46 22L50 24C54 22 58 18 62 18Z" fill="#fff" opacity="0.95"/></svg>`;

  const card = document.createElement('div');
  card.className = 'store-card';
  card.innerHTML = `
    <div class="store-card-head">
      <div class="store-card-icon">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="var(--gold)" stroke-width="2.2"><path d="M21 10c0 7-9 13-9 13s-9-6-9-13a9 9 0 0118 0z"/><circle cx="12" cy="10" r="3"/></svg>
      </div>
      <div class="store-card-title">Find Nearby Stores</div>
    </div>
    <div class="store-card-desc">Open Maps with suppliers for <strong style="color:var(--text)">${escHtml(productTerm)}</strong> near you.</div>
    <button class="store-card-btn">
      <svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="#fff" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><polygon points="16.24 7.76 14.12 14.12 7.76 16.24 9.88 9.88 16.24 7.76"/></svg>
      Open in Google Maps
    </button>
    <div class="store-card-status"></div>`;

  row.appendChild(av); row.appendChild(card);
  container.appendChild(row);
  scrollBottom();

  const btn = card.querySelector('.store-card-btn');
  const status = card.querySelector('.store-card-status');
  btn.addEventListener('click', async () => {
    btn.disabled = true; btn.style.opacity = '.7';
    status.textContent = 'Getting your location…';
    if (!userCoords) userCoords = await requestLocation();
    status.textContent = userCoords ? '📍 Using your current location' : 'Location unavailable — showing general results';
    window.open(buildMapsUrl(productTerm, userCoords), '_blank');
    btn.disabled = false; btn.style.opacity = '1';
  });
}

// ── SEND MESSAGE (streaming) ──────────────────────────────
async function sendMessage(text) {
  if (!text || loading) return;

  if (!chatStarted) {
    chatStarted = true;
    document.getElementById('welcome-view').style.display = 'none';
    document.getElementById('chat-inner').style.display = 'flex';
    document.getElementById('chat-inner').style.flexDirection = 'column';
    document.getElementById('chat-inner').style.gap = '22px';
    document.getElementById('current-chat-title').textContent = text.length > 40 ? text.slice(0,40)+'…' : text;
    addHistoryItem(text);
  }

  addUserBubble(text);
  messages.push({role:'user', content:text});
  loading = true; updateSendBtn();
  document.querySelectorAll('.error-box').forEach(e => e.remove());

  const wantsStoreFinder = detectStoreIntent(text);
  const productTerm = wantsStoreFinder ? extractProductTerm(text) : null;

  const { row, bodyEl } = addLiveAiBubble();
  bodyEl.innerHTML = '<div class="typing"><div class="dot"></div><div class="dot"></div><div class="dot"></div></div>';
  scrollBottom();

  let fullText = '';
  let gotFirstToken = false;

  try {
    const res = await fetch('https://api.anthropic.com/v1/messages', {
      method:'POST',
      headers:{'Content-Type':'application/json'},
      body: JSON.stringify({model:'claude-sonnet-4-6', max_tokens:450, system:SYSTEM_PROMPT, messages, stream:true})
    });
    if (!res.ok) throw new Error('API '+res.status);

    const reader = res.body.getReader();
    const decoder = new TextDecoder();
    let buf = '';

    while (true) {
      const { done, value } = await reader.read();
      if (done) break;
      buf += decoder.decode(value, {stream:true});
      const lines = buf.split('\n');
      buf = lines.pop();

      for (const line of lines) {
        if (!line.startsWith('data: ')) continue;
        const payload = line.slice(6).trim();
        if (!payload || payload === '[DONE]') continue;
        let evt;
        try { evt = JSON.parse(payload); } catch { continue; }
        if (evt.type === 'content_block_delta' && evt.delta && evt.delta.type === 'text_delta') {
          if (!gotFirstToken) { gotFirstToken = true; bodyEl.innerHTML = ''; }
          fullText += evt.delta.text;
          bodyEl.innerHTML = renderMarkdown(fullText);
          scrollBottom();
        }
      }
    }

    if (!fullText) throw new Error('Empty response');
    messages.push({role:'assistant', content:fullText});
    if (wantsStoreFinder) showStoreFinderCard(productTerm);
  } catch(err) {
    row.remove();
    const e = document.createElement('div');
    e.className = 'error-box';
    e.textContent = 'Connection error. Please check your network and try again.';
    document.getElementById('chat-inner').appendChild(e);
  }
  loading = false; updateSendBtn(); scrollBottom();
}

// ── RENDER ────────────────────────────────────────────────
function addUserBubble(text) {
  const c = document.getElementById('chat-inner');
  const row = document.createElement('div');
  row.className = 'msg-row user';
  const body = document.createElement('div');
  body.className = 'msg-body';
  body.textContent = text;
  row.appendChild(body);
  c.appendChild(row);
  scrollBottom();
}

function addLiveAiBubble() {
  const c = document.getElementById('chat-inner');
  const row = document.createElement('div');
  row.className = 'msg-row ai';
  const av = document.createElement('div');
  av.className = 'ai-avatar';
  av.innerHTML = `<svg width="16" height="16" viewBox="0 0 100 100" fill="none"><path d="M72 18C72 18 78 12 82 14C86 16 84 22 80 24C84 24 88 28 86 34C84 40 78 40 74 38L72 46C74 52 72 60 66 64L64 80C63 84 58 86 56 82L55 68C50 70 44 70 40 68L39 82C38 86 32 86 31 82L30 66C24 62 20 54 22 46C24 38 30 34 36 34L38 28C34 26 32 20 36 16C40 12 46 16 46 22L50 24C54 22 58 18 62 18Z" fill="#fff" opacity="0.95"/></svg>`;
  const body = document.createElement('div');
  body.className = 'msg-body';
  row.appendChild(av); row.appendChild(body);
  c.appendChild(row);
  return { row, bodyEl: body };
}

function renderMarkdown(text) {
  const lines = text.split('\n');
  let html = '', i = 0;
  while (i < lines.length) {
    const l = lines[i];
    if (l.startsWith('# ')) html += `<div class="md-h1">${ir(l.slice(2))}</div>`;
    else if (l.startsWith('## ')) html += `<div class="md-h2">${ir(l.slice(3))}</div>`;
    else if (l.startsWith('### ')) html += `<div class="md-h3">${ir(l.slice(4))}</div>`;
    else if (l.startsWith('- ') || l.startsWith('* ')) {
      html += '<div class="md-ul">';
      while (i < lines.length && (lines[i].startsWith('- ') || lines[i].startsWith('* '))) {
        html += `<div class="md-li"><span class="md-bullet">•</span><span>${ir(lines[i].slice(2))}</span></div>`; i++;
      }
      html += '</div>'; continue;
    } else if (/^\d+\. /.test(l)) {
      html += '<div class="md-ol">'; let n=1;
      while (i < lines.length && /^\d+\. /.test(lines[i])) {
        html += `<div class="md-li"><span class="md-num">${n}.</span><span>${ir(lines[i].replace(/^\d+\. /,''))}</span></div>`; i++; n++;
      }
      html += '</div>'; continue;
    } else if (l.startsWith('---')) html += '<div class="md-hr"></div>';
    else if (l.trim() === '') html += '<div style="height:4px"></div>';
    else html += `<div class="md-p">${ir(l)}</div>`;
    i++;
  }
  return html;
}

function ir(t) {
  return t.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;')
    .replace(/\*\*(.*?)\*\*/g,'<strong style="color:var(--text);font-weight:800">$1</strong>')
    .replace(/\*(.*?)\*/g,'<em style="color:var(--text3)">$1</em>')
    .replace(/`(.*?)`/g,'<code class="md-code">$1</code>');
}

function escHtml(t) { return t.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;'); }

function scrollBottom() {
  setTimeout(() => {
    const c = document.getElementById('chat-scroll');
    c.scrollTop = c.scrollHeight;
  }, 50);
}
</script>
</body>
</html>
