<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>TradingBay — Where traders meet</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800;900&family=JetBrains+Mono:wght@400;500;600&display=swap" rel="stylesheet">
<style>
  :root{
    --brand:#6BFFC7;
    --brand-2:#3DD9A4;
    --brand-ink:#04140e;
    --amber:#FFB74A;
    --pink:#FF6B9D;
    --gold:#FFD166;
    --bg:#08080d;
    --bg-1:#0f0f15;
    --bg-2:#15151c;
    --bg-3:#1c1c25;
    --bg-hover:#22222d;
    --line:#1f1f2a;
    --line-2:#2a2a37;
    --ink:#f0f0f3;
    --ink-2:#c0c0cc;
    --muted:#7c7c8c;
    --faint:#4a4a58;
    --ok:#6BFFC7;
    --warn:#FFB74A;
    --signal:#FF6B6B;
  }
  *{box-sizing:border-box}
  html,body{margin:0;background:var(--bg);color:var(--ink);font-family:'Inter',sans-serif;font-size:14px;line-height:1.5;-webkit-font-smoothing:antialiased;letter-spacing:-.005em}
  body{background:radial-gradient(circle at 20% 0%,rgba(107,255,199,.06) 0%,transparent 40%),radial-gradient(circle at 80% 30%,rgba(255,107,157,.05) 0%,transparent 40%),var(--bg);min-height:100vh}
  .mono{font-family:'JetBrains Mono',monospace;font-variant-numeric:tabular-nums}
  a{color:inherit;text-decoration:none;cursor:pointer}
  button{font-family:inherit;cursor:pointer;border:0;background:transparent;color:inherit}
  hr{border:0;border-top:1px solid var(--line);margin:20px 0}

  /* ─── topbar ───────────────────────────────────────────────────── */
  .nav{position:sticky;top:0;z-index:40;backdrop-filter:blur(20px);-webkit-backdrop-filter:blur(20px);background:rgba(8,8,13,.78);border-bottom:1px solid var(--line)}
  .nav-inner{max-width:1320px;margin:0 auto;padding:14px 32px;display:flex;align-items:center;gap:28px}
  .brand{display:flex;align-items:center;gap:9px;font-weight:700;font-size:17.5px;letter-spacing:-.025em;cursor:pointer}
  .brand .m{width:30px;height:30px;border-radius:9px;background:linear-gradient(135deg,var(--brand),var(--brand-2));display:grid;place-items:center;color:var(--brand-ink);font-weight:900;font-size:13px}
  .brand b{color:var(--brand);font-weight:700}
  .nav-links{display:flex;gap:2px;flex:1;justify-content:center}
  .nav-links a{padding:9px 14px;border-radius:9px;font-size:13.5px;color:var(--muted);font-weight:500;transition:all .15s ease}
  .nav-links a:hover{color:var(--ink);background:var(--bg-2)}
  .nav-links a.active{color:var(--brand);background:rgba(107,255,199,.07)}
  .nav-search{position:relative;width:280px}
  .nav-search input{width:100%;background:var(--bg-2);border:1px solid var(--line);border-radius:10px;padding:9px 11px 9px 36px;color:var(--ink);font-size:13px;font-family:'Inter';outline:none;transition:all .15s ease}
  .nav-search input:focus{border-color:var(--brand);background:var(--bg-3)}
  .nav-search .ic{position:absolute;left:11px;top:50%;transform:translateY(-50%);color:var(--faint);font-size:13px}
  .nav-cta{display:flex;align-items:center;gap:10px}
  .av-tiny{width:34px;height:34px;border-radius:50%;background:linear-gradient(135deg,var(--brand),var(--brand-2));color:var(--brand-ink);display:grid;place-items:center;font-weight:700;font-size:12px;cursor:pointer}

  /* ─── general ──────────────────────────────────────────────────── */
  main{max-width:1320px;margin:0 auto;padding:32px}
  h1{font-size:38px;font-weight:700;letter-spacing:-.025em;line-height:1.1;margin:0 0 8px}
  h2{font-size:22px;font-weight:700;letter-spacing:-.015em;margin:0 0 4px}
  h3{font-size:17px;font-weight:600;letter-spacing:-.01em;margin:0 0 4px}
  .eyebrow{font-size:11px;letter-spacing:.18em;text-transform:uppercase;color:var(--muted);font-weight:600;margin-bottom:6px}
  .lead{color:var(--ink-2);font-size:15px;line-height:1.55;margin:0 0 24px;max-width:640px}
  .section{margin-bottom:48px}
  .section-h{display:flex;justify-content:space-between;align-items:flex-end;margin-bottom:20px}
  .section-h a{font-size:13px;color:var(--muted);font-weight:500}
  .section-h a:hover{color:var(--brand)}

  /* ─── buttons ──────────────────────────────────────────────────── */
  .btn{display:inline-flex;align-items:center;justify-content:center;gap:7px;padding:9px 16px;border-radius:10px;font-size:13.5px;font-weight:600;font-family:inherit;cursor:pointer;transition:all .15s ease;background:var(--bg-3);color:var(--ink);border:1px solid var(--line-2);white-space:nowrap}
  .btn:hover{background:var(--bg-hover);border-color:var(--line-2)}
  .btn.primary{background:var(--brand);color:var(--brand-ink);border-color:var(--brand)}
  .btn.primary:hover{background:var(--brand-2);border-color:var(--brand-2);transform:translateY(-1px);box-shadow:0 10px 30px -10px var(--brand)}
  .btn.ghost{background:transparent;border-color:var(--line-2);color:var(--ink-2)}
  .btn.ghost:hover{color:var(--ink);border-color:var(--brand);background:rgba(107,255,199,.04)}
  .btn.lg{padding:12px 22px;font-size:14.5px;border-radius:11px}
  .btn.sm{padding:6px 11px;font-size:12px;border-radius:8px}

  /* ─── cards ────────────────────────────────────────────────────── */
  .card{background:var(--bg-1);border:1px solid var(--line);border-radius:14px;padding:22px;transition:all .15s ease}
  .card.hov{cursor:pointer}
  .card.hov:hover{border-color:var(--line-2);background:var(--bg-2);transform:translateY(-2px)}

  /* ─── pill / tags ─────────────────────────────────────────────── */
  .pill{display:inline-flex;align-items:center;gap:4px;padding:3px 10px;border-radius:99px;font-size:11px;font-weight:500;background:var(--bg-3);border:1px solid var(--line);color:var(--ink-2)}
  .pill.brand{color:var(--brand-ink);background:var(--brand);border-color:var(--brand);font-weight:600}
  .pill.brand-soft{color:var(--brand);background:rgba(107,255,199,.08);border-color:rgba(107,255,199,.30)}
  .pill.amber{color:var(--amber);background:rgba(255,183,74,.08);border-color:rgba(255,183,74,.30)}
  .pill.pink{color:var(--pink);background:rgba(255,107,157,.08);border-color:rgba(255,107,157,.30)}
  .pill.gold{color:var(--gold);background:rgba(255,209,102,.08);border-color:rgba(255,209,102,.30)}
  .pill.role{font-size:10px;letter-spacing:.06em;text-transform:uppercase;padding:2px 8px;font-weight:600}

  .verified{color:var(--brand);font-size:14px;margin-left:2px;display:inline-block}

  /* ─── home hero ───────────────────────────────────────────────── */
  .hero{position:relative;background:linear-gradient(135deg,rgba(107,255,199,.10) 0%,rgba(255,107,157,.06) 50%,rgba(255,183,74,.04) 100%);border:1px solid var(--line);border-radius:20px;padding:48px;overflow:hidden;margin-bottom:48px}
  .hero::before{content:"";position:absolute;top:-100px;right:-100px;width:380px;height:380px;background:radial-gradient(circle,rgba(107,255,199,.18),transparent 70%);pointer-events:none}
  .hero-content{position:relative;max-width:580px}
  .hero h1{font-size:46px;font-weight:800;letter-spacing:-.03em;line-height:1.05;margin-bottom:14px}
  .hero h1 b{background:linear-gradient(135deg,var(--brand),var(--brand-2));-webkit-background-clip:text;background-clip:text;color:transparent;font-weight:800}
  .hero p{font-size:16px;color:var(--ink-2);line-height:1.6;margin:0 0 28px}
  .hero-stats{display:flex;gap:36px;margin-top:36px;padding-top:28px;border-top:1px solid var(--line)}
  .hero-stats .stat{display:flex;flex-direction:column}
  .hero-stats .stat b{font-size:24px;font-weight:700;letter-spacing:-.015em;font-family:'JetBrains Mono'}
  .hero-stats .stat span{font-size:11px;letter-spacing:.14em;text-transform:uppercase;color:var(--muted);font-weight:600;margin-top:3px}

  /* ─── feed cards ──────────────────────────────────────────────── */
  .feed{display:grid;grid-template-columns:1fr 1fr;gap:18px}
  .feed-item{position:relative;background:var(--bg-1);border:1px solid var(--line);border-radius:16px;padding:22px;cursor:pointer;transition:all .2s ease;display:flex;flex-direction:column;gap:14px;min-height:200px}
  .feed-item:hover{border-color:var(--line-2);background:var(--bg-2);transform:translateY(-2px)}
  .feed-item .top{display:flex;align-items:center;gap:10px}
  .feed-item .com{font-size:12px;color:var(--brand);font-weight:600}
  .feed-item .meta{font-size:11.5px;color:var(--muted);display:flex;align-items:center;gap:6px}
  .feed-item .title{font-size:17px;font-weight:600;letter-spacing:-.01em;line-height:1.35;color:var(--ink)}
  .feed-item .preview{font-size:13.5px;color:var(--ink-2);line-height:1.55;display:-webkit-box;-webkit-line-clamp:3;-webkit-box-orient:vertical;overflow:hidden}
  .feed-item .author{display:flex;align-items:center;gap:9px;margin-top:auto;padding-top:14px;border-top:1px solid var(--line)}
  .feed-item .author .av-sm{width:30px;height:30px;border-radius:50%;display:grid;place-items:center;font-weight:600;font-size:11px;color:var(--brand-ink);background:linear-gradient(135deg,var(--brand),var(--brand-2))}
  .feed-item .author .nm{font-size:12.5px;font-weight:500;color:var(--ink)}
  .feed-item .author .hh{font-size:11px;color:var(--muted)}
  .feed-item .actions{display:flex;gap:14px;color:var(--muted);font-size:11.5px;align-items:center;margin-left:auto}
  .feed-item .img-block{height:140px;border-radius:11px;background:linear-gradient(135deg,var(--bg-3),var(--bg-2));display:grid;place-items:center;color:var(--faint);font-size:11px;font-family:'JetBrains Mono'}
  .feed-item .img-block.tint-1{background:linear-gradient(135deg,rgba(107,255,199,.18),rgba(61,217,164,.08))}
  .feed-item .img-block.tint-2{background:linear-gradient(135deg,rgba(255,183,74,.18),rgba(255,107,157,.08))}
  .feed-item .img-block.tint-3{background:linear-gradient(135deg,rgba(255,209,102,.16),rgba(255,107,157,.10))}
  .feed-item .img-block.tint-4{background:linear-gradient(135deg,rgba(107,196,255,.14),rgba(124,255,203,.08))}

  /* ─── carousel of avatars ─────────────────────────────────────── */
  .row-scroll{display:flex;gap:16px;overflow-x:auto;padding-bottom:6px;scroll-snap-type:x mandatory;scrollbar-width:none}
  .row-scroll::-webkit-scrollbar{display:none}
  .row-scroll > *{scroll-snap-align:start;flex:none}

  /* ─── creator card ────────────────────────────────────────────── */
  .creator{width:280px;background:var(--bg-1);border:1px solid var(--line);border-radius:16px;overflow:hidden;cursor:pointer;transition:all .2s ease}
  .creator:hover{border-color:var(--brand);transform:translateY(-3px)}
  .creator .cover{height:90px;background:linear-gradient(135deg,var(--brand),var(--brand-2));position:relative}
  .creator .cover.c1{background:linear-gradient(135deg,#FF6B9D,#FFB74A)}
  .creator .cover.c2{background:linear-gradient(135deg,#6BFFC7,#3DD9A4)}
  .creator .cover.c3{background:linear-gradient(135deg,#FFD166,#FF6B9D)}
  .creator .cover.c4{background:linear-gradient(135deg,#6BC4FF,#6BFFC7)}
  .creator .cover.c5{background:linear-gradient(135deg,#A78BFA,#FF6B9D)}
  .creator .body{padding:0 18px 18px;margin-top:-32px;position:relative}
  .creator .av{width:64px;height:64px;border-radius:50%;background:var(--brand);color:var(--brand-ink);display:grid;place-items:center;font-weight:700;font-size:21px;border:3px solid var(--bg-1);margin-bottom:10px}
  .creator .name{font-size:15.5px;font-weight:600;letter-spacing:-.01em;display:flex;align-items:center;gap:4px}
  .creator .handle{font-size:11.5px;color:var(--muted);font-family:'JetBrains Mono'}
  .creator .role{margin-top:8px}
  .creator .stats{display:flex;gap:14px;margin-top:14px;font-size:11.5px;color:var(--muted)}
  .creator .stats b{color:var(--ink);font-weight:600;font-family:'JetBrains Mono'}
  .creator .tagline{font-size:12.5px;color:var(--ink-2);margin-top:10px;line-height:1.5;display:-webkit-box;-webkit-line-clamp:2;-webkit-box-orient:vertical;overflow:hidden;min-height:32px}

  /* ─── community tile ──────────────────────────────────────────── */
  .com-tile{position:relative;background:var(--bg-1);border:1px solid var(--line);border-radius:16px;overflow:hidden;cursor:pointer;transition:all .2s ease;min-height:200px;display:flex;flex-direction:column}
  .com-tile:hover{transform:translateY(-3px);border-color:var(--line-2)}
  .com-tile .banner{height:96px;position:relative;overflow:hidden}
  .com-tile .banner::after{content:"";position:absolute;inset:0;background:linear-gradient(to bottom,transparent 30%,var(--bg-1) 100%)}
  .com-tile .body{padding:0 20px 22px;margin-top:-30px;position:relative;z-index:1;flex:1;display:flex;flex-direction:column}
  .com-tile .icon{width:54px;height:54px;border-radius:14px;display:grid;place-items:center;color:var(--brand-ink);font-weight:800;font-size:21px;border:3px solid var(--bg-1);margin-bottom:14px;letter-spacing:-.02em}
  .com-tile .slug{font-size:16px;font-weight:700;letter-spacing:-.01em}
  .com-tile .desc{font-size:12.5px;color:var(--ink-2);margin-top:6px;line-height:1.5;flex:1}
  .com-tile .foot{display:flex;justify-content:space-between;align-items:center;margin-top:14px;font-size:11.5px;color:var(--muted)}
  .com-tile .foot b{color:var(--ink);font-weight:600}

  /* ─── prop firm row ───────────────────────────────────────────── */
  .firm-row{display:flex;align-items:center;gap:18px;padding:20px 22px;background:var(--bg-1);border:1px solid var(--line);border-radius:14px;cursor:pointer;transition:all .15s ease;position:relative}
  .firm-row:hover{border-color:var(--line-2);background:var(--bg-2);transform:translateX(2px)}
  .firm-row.featured{background:linear-gradient(135deg,rgba(107,255,199,.05),transparent 50%);border-color:rgba(107,255,199,.20)}
  .firm-row.featured::before{content:"";position:absolute;left:0;top:14px;bottom:14px;width:3px;border-radius:3px;background:var(--brand)}
  .firm-row .icon{width:64px;height:64px;border-radius:14px;display:grid;place-items:center;color:var(--brand-ink);font-weight:800;font-size:24px;flex:none;letter-spacing:-.025em}
  .firm-row .core{flex:1;min-width:0}
  .firm-row .head{display:flex;align-items:center;gap:9px;flex-wrap:wrap;margin-bottom:4px}
  .firm-row .head .name{font-size:17px;font-weight:700;letter-spacing:-.01em}
  .firm-row .head .rate{color:var(--gold);font-size:13px}
  .firm-row .head .rate .n{color:var(--muted);font-family:'JetBrains Mono';margin-left:4px;font-size:12px}
  .firm-row .tagline{font-size:13px;color:var(--ink-2);margin-bottom:9px}
  .firm-row .meta{display:flex;gap:18px;flex-wrap:wrap;font-size:11.5px;color:var(--muted)}
  .firm-row .meta b{color:var(--ink);font-weight:600;font-family:'JetBrains Mono'}
  .firm-row .right{text-align:right;flex:none;display:flex;flex-direction:column;gap:6px;align-items:flex-end}

  /* ─── course card ─────────────────────────────────────────────── */
  .course-card{background:var(--bg-1);border:1px solid var(--line);border-radius:16px;overflow:hidden;cursor:pointer;transition:all .2s ease;display:flex;flex-direction:column}
  .course-card:hover{transform:translateY(-3px);border-color:var(--line-2)}
  .course-card .hero{height:140px;display:grid;place-items:center;color:rgba(255,255,255,.85);font-family:'JetBrains Mono';font-size:11px;letter-spacing:.16em;text-transform:uppercase;font-weight:600;position:relative;overflow:hidden}
  .course-card .hero::after{content:"";position:absolute;inset:0;background:linear-gradient(135deg,rgba(0,0,0,.18) 0%,transparent 100%)}
  .course-card .hero.h1{background:linear-gradient(135deg,#6BFFC7,#3DD9A4)}
  .course-card .hero.h2{background:linear-gradient(135deg,#FF6B9D,#FFB74A)}
  .course-card .hero.h3{background:linear-gradient(135deg,#FFD166,#FF6B9D)}
  .course-card .hero.h4{background:linear-gradient(135deg,#6BC4FF,#A78BFA)}
  .course-card .hero.h5{background:linear-gradient(135deg,#A78BFA,#FF6B9D)}
  .course-card .hero.h6{background:linear-gradient(135deg,#FFB74A,#6BFFC7)}
  .course-card .body{padding:18px 20px 20px;flex:1;display:flex;flex-direction:column}
  .course-card .name{font-size:15.5px;font-weight:700;letter-spacing:-.005em;line-height:1.4;margin-bottom:8px}
  .course-card .by{font-size:12px;color:var(--muted);margin-bottom:14px}
  .course-card .by b{color:var(--ink);font-weight:500}
  .course-card .foot{display:flex;justify-content:space-between;align-items:center;margin-top:auto}
  .course-card .price{font-family:'JetBrains Mono';font-weight:700;font-size:18px;color:var(--brand);letter-spacing:-.01em}
  .course-card .rate{color:var(--gold);font-size:12.5px}
  .course-card .rate .n{color:var(--muted);font-family:'JetBrains Mono';margin-left:3px;font-size:11.5px}

  /* ─── profile page ────────────────────────────────────────────── */
  .profile-hero{position:relative;border-radius:20px;overflow:hidden;margin-bottom:28px;border:1px solid var(--line)}
  .profile-hero .cover{height:200px;background:linear-gradient(135deg,#6BFFC7,#3DD9A4);position:relative}
  .profile-hero .cover.c1{background:linear-gradient(135deg,#FF6B9D,#FFB74A)}
  .profile-hero .cover.c2{background:linear-gradient(135deg,#6BFFC7,#3DD9A4)}
  .profile-hero .cover.c3{background:linear-gradient(135deg,#FFD166,#FF6B9D)}
  .profile-hero .cover.c4{background:linear-gradient(135deg,#6BC4FF,#A78BFA)}
  .profile-hero .cover.c5{background:linear-gradient(135deg,#A78BFA,#FF6B9D)}
  .profile-hero .cover.c6{background:linear-gradient(135deg,#08080d,#1c1c25)}
  .profile-hero .body{padding:0 32px 28px;margin-top:-60px;position:relative;background:var(--bg-1)}
  .profile-hero .av-lg{width:120px;height:120px;border-radius:50%;background:var(--brand);color:var(--brand-ink);display:grid;place-items:center;font-weight:800;font-size:42px;border:5px solid var(--bg-1);margin-bottom:18px;letter-spacing:-.03em}
  .profile-hero .av-lg.firm{border-radius:24px;background:linear-gradient(135deg,#FF6B9D,#6BFFC7)}
  .profile-hero h1{font-size:32px;font-weight:700;letter-spacing:-.02em;display:flex;align-items:center;gap:8px;flex-wrap:wrap}
  .profile-hero .handle{font-size:14px;color:var(--muted);font-family:'JetBrains Mono';margin-top:2px}
  .profile-hero .tagline{font-size:16px;color:var(--ink-2);margin-top:14px;line-height:1.55;max-width:680px}
  .profile-hero .chips{display:flex;gap:8px;margin-top:16px;flex-wrap:wrap}
  .profile-hero .ctas{position:absolute;right:32px;top:14px;display:flex;gap:8px}

  .stat-bar{display:grid;grid-template-columns:repeat(5,1fr);gap:1px;background:var(--line);border-radius:14px;overflow:hidden;border:1px solid var(--line);margin-bottom:28px}
  .stat-bar .it{background:var(--bg-1);padding:18px 20px}
  .stat-bar .it .l{font-size:10.5px;letter-spacing:.14em;text-transform:uppercase;color:var(--muted);font-weight:600;margin-bottom:5px}
  .stat-bar .it .v{font-size:22px;font-weight:700;letter-spacing:-.015em;font-family:'JetBrains Mono'}
  .stat-bar .it .v.brand{color:var(--brand)}
  .stat-bar .it .v.gold{color:var(--gold)}
  .stat-bar .it.acc{background:rgba(107,255,199,.04)}

  /* ─── tabs ────────────────────────────────────────────────────── */
  .tabs{display:flex;gap:0;border-bottom:1px solid var(--line);margin-bottom:24px}
  .tabs a{padding:13px 18px;font-size:13.5px;color:var(--muted);font-weight:500;border-bottom:2px solid transparent;cursor:pointer;transition:all .15s ease;margin-bottom:-1px}
  .tabs a:hover{color:var(--ink)}
  .tabs a.active{color:var(--brand);border-bottom-color:var(--brand);font-weight:600}

  /* ─── subscription tiers (Patreon-style) ───────────────────────── */
  .tiers{display:grid;grid-template-columns:1fr 1fr 1fr;gap:16px}
  .tier{background:var(--bg-1);border:1px solid var(--line);border-radius:18px;padding:26px 24px;position:relative;transition:all .2s ease}
  .tier:hover{border-color:var(--line-2);transform:translateY(-3px)}
  .tier.featured{border-color:var(--brand);background:linear-gradient(180deg,rgba(107,255,199,.04),transparent 50%)}
  .tier.featured::before{content:"Most popular";position:absolute;top:-12px;left:24px;background:var(--brand);color:var(--brand-ink);padding:4px 12px;border-radius:99px;font-size:10.5px;font-weight:700;letter-spacing:.06em;text-transform:uppercase}
  .tier .name{font-size:18px;font-weight:700;letter-spacing:-.01em;margin-bottom:6px}
  .tier .desc{font-size:12.5px;color:var(--muted);margin-bottom:18px;line-height:1.5;min-height:36px}
  .tier .price{font-size:38px;font-weight:800;letter-spacing:-.025em;font-family:'JetBrains Mono';color:var(--brand);line-height:1}
  .tier .per{font-size:13px;color:var(--muted);margin-bottom:22px;margin-top:5px}
  .tier ul{list-style:none;padding:0;margin:0 0 22px;display:flex;flex-direction:column;gap:9px}
  .tier li{font-size:13px;color:var(--ink-2);display:flex;align-items:flex-start;gap:8px;line-height:1.45}
  .tier li::before{content:"✓";color:var(--brand);font-weight:700;flex:none}
  .tier .btn{width:100%}

  /* ─── story section ──────────────────────────────────────────── */
  .story{display:grid;grid-template-columns:1fr 320px;gap:32px}
  .story-main{font-size:15px;line-height:1.75;color:var(--ink-2)}
  .story-main h3{margin:28px 0 10px;font-size:20px;font-weight:700;color:var(--ink);letter-spacing:-.015em}
  .story-main p{margin:0 0 14px}
  .story-main blockquote{border-left:3px solid var(--brand);padding:6px 0 6px 20px;margin:20px 0;font-style:italic;color:var(--ink);font-size:17px;line-height:1.55}
  .story-side{display:flex;flex-direction:column;gap:18px}
  .story-side .card{padding:20px}
  .story-side h3{font-size:14px;font-weight:600}
  .story-side .links{display:flex;flex-direction:column;gap:8px;margin-top:12px}
  .story-side .links a{display:flex;align-items:center;justify-content:space-between;padding:11px 14px;background:var(--bg-2);border:1px solid var(--line);border-radius:10px;font-size:13px;color:var(--ink);transition:all .15s ease}
  .story-side .links a:hover{border-color:var(--brand);color:var(--brand)}
  .story-side .links a span{color:var(--muted);font-size:11px;font-family:'JetBrains Mono'}

  /* ─── reviews ─────────────────────────────────────────────────── */
  .review-grid{display:grid;grid-template-columns:1fr 1fr;gap:16px}
  .review{background:var(--bg-1);border:1px solid var(--line);border-radius:14px;padding:22px}
  .review .head{display:flex;align-items:center;gap:11px;margin-bottom:12px}
  .review .head .av-sm{width:38px;height:38px;border-radius:50%;background:linear-gradient(135deg,var(--brand),var(--brand-2));color:var(--brand-ink);display:grid;place-items:center;font-weight:600;font-size:13px}
  .review .head .who{flex:1}
  .review .head .who .nm{font-weight:600;font-size:13.5px;display:flex;align-items:center;gap:5px}
  .review .head .who .dt{font-size:11px;color:var(--muted);margin-top:1px}
  .review .stars{color:var(--gold);font-size:14px;margin-bottom:8px}
  .review .body{font-size:13.5px;color:var(--ink-2);line-height:1.6}
  .review .verified-tag{font-size:10px;letter-spacing:.08em;text-transform:uppercase;color:var(--ok);background:rgba(107,255,199,.08);padding:2px 8px;border-radius:99px;font-weight:600;margin-left:6px;border:1px solid rgba(107,255,199,.30)}

  /* ─── grid helpers ───────────────────────────────────────────── */
  .grid-2{display:grid;grid-template-columns:1fr 1fr;gap:18px}
  .grid-3{display:grid;grid-template-columns:1fr 1fr 1fr;gap:18px}
  .grid-4{display:grid;grid-template-columns:repeat(auto-fill,minmax(260px,1fr));gap:18px}

  /* ─── sign-in ─────────────────────────────────────────────────── */
  .signin-shell{min-height:100vh;display:grid;place-items:center;background:radial-gradient(circle at 30% 20%,rgba(107,255,199,.10) 0%,transparent 50%),radial-gradient(circle at 70% 80%,rgba(255,107,157,.06) 0%,transparent 50%),var(--bg);padding:32px}
  .signin{width:520px;max-width:100%;background:var(--bg-1);border:1px solid var(--line);border-radius:22px;padding:40px 36px}
  .signin .brand{font-size:26px;margin-bottom:28px}
  .signin .brand .m{width:38px;height:38px;font-size:16px}
  .signin h1{font-size:30px;font-weight:800;letter-spacing:-.025em;margin:0 0 8px}
  .signin .sub{color:var(--ink-2);font-size:14.5px;margin:0 0 26px;line-height:1.55}
  .signin h3{font-size:11px;letter-spacing:.18em;text-transform:uppercase;color:var(--muted);font-weight:700;margin:22px 0 12px}
  .roles{display:grid;grid-template-columns:1fr 1fr;gap:8px}
  .roles .r{padding:16px;background:var(--bg-2);border:1px solid var(--line);border-radius:12px;text-align:left;cursor:pointer;transition:all .15s ease}
  .roles .r:hover{border-color:var(--brand);background:var(--bg-3);transform:translateY(-2px)}
  .roles .r b{font-weight:600;font-size:13.5px;display:block;margin-bottom:2px}
  .roles .r span{font-size:11.5px;color:var(--muted);line-height:1.45}
  .demo-users{max-height:200px;overflow-y:auto;display:flex;flex-direction:column;gap:5px;margin-top:8px}
  .demo-users button{padding:9px 12px;background:var(--bg-2);border:1px solid var(--line);border-radius:9px;text-align:left;font-size:12.5px;color:var(--ink);display:flex;align-items:center;gap:10px;transition:all .12s ease}
  .demo-users button:hover{border-color:var(--brand)}
  .demo-users button .av-sm{width:26px;height:26px;border-radius:50%;background:linear-gradient(135deg,var(--brand),var(--brand-2));color:var(--brand-ink);display:grid;place-items:center;font-weight:700;font-size:10.5px}
  .demo-users button span{color:var(--muted);font-size:10.5px;font-family:'JetBrains Mono'}

  /* ─── PLATFORMS PAGE ──────────────────────────────────────────────── */
function renderPlatformsPage(){
  const list = [...platforms].sort((a,b)=>b.rating-a.rating);
  return renderShell(`
    <div class="eyebrow">Where you trade</div>
    <h1>Trading platforms</h1>
    <p class="lead">${platforms.length} platforms compared. Find the right one for your prop firm, your style, your asset class.</p>
    <div style="display:flex;flex-direction:column;gap:12px">
      ${list.map(renderPlatformRow).join('')}
    </div>
  `);
}
function renderPlatformRow(pl){
  const tintMap={c1:'linear-gradient(135deg,#FF6B9D,#FFB74A)',c2:'linear-gradient(135deg,#6BFFC7,#3DD9A4)',c3:'linear-gradient(135deg,#FFD166,#FF6B9D)',c4:'linear-gradient(135deg,#6BC4FF,#A78BFA)',c5:'linear-gradient(135deg,#A78BFA,#FF6B9D)'};
  return `
    <div class="firm-row" onclick="go('#/platform/${pl.slug}')">
      <div class="icon" style="background:${tintMap[pl.tint]||tintMap.c2}">${pl.mark}</div>
      <div class="core">
        <div class="head">
          <span class="name">${esc(pl.name)}</span>
          <span class="rate">${stars(pl.rating)} ${pl.rating} <span class="n">(${pl.reviewCount})</span></span>
        </div>
        <div class="tagline">${esc(pl.tagline)}</div>
        <div class="meta">
          <span>Type <b>${esc(pl.type)}</b></span>
          <span>Brokers <b>${pl.brokerCount}+</b></span>
          <span>Founded <b>${pl.founded}</b></span>
        </div>
      </div>
      <div class="right">
        <button class="btn sm primary">Details →</button>
      </div>
    </div>`;
}

function renderPlatformDetail(slug){
  const pl = platformBySlug(slug);
  if(!pl) return renderShell('<div class="empty">Platform not found.</div>');
  const tab = (route.split('?tab=')[1])||'overview';
  const tintMap={c1:'c1',c2:'c2',c3:'c3',c4:'c4',c5:'c5'};
  return renderShell(`
    <div class="profile-hero">
      <div class="cover ${tintMap[pl.tint]||'c2'}"></div>
      <div class="body">
        <div class="av-lg firm">${pl.mark}</div>
        <h1>${esc(pl.name)}</h1>
        <div class="handle">${esc(pl.website)} · ${esc(pl.hq)}</div>
        <div class="tagline">${esc(pl.tagline)}</div>
        <div class="chips">
          <span class="pill brand-soft">${stars(pl.rating)} ${pl.rating} · ${pl.reviewCount} reviews</span>
          <span class="pill">${esc(pl.type)}</span>
          <span class="pill">${pl.brokerCount}+ brokers</span>
          <span class="pill">Founded ${pl.founded}</span>
        </div>
        <div class="ctas">
          <button class="btn ghost">Save</button>
          <button class="btn primary">Visit website →</button>
        </div>
      </div>
    </div>

    <div class="stat-bar">
      <div class="it"><div class="l">Rating</div><div class="v gold">${pl.rating}</div></div>
      <div class="it"><div class="l">Brokers</div><div class="v brand">${pl.brokerCount}+</div></div>
      <div class="it"><div class="l">Type</div><div class="v" style="font-size:14px">${esc(pl.type.split(' + ')[0])}</div></div>
      <div class="it"><div class="l">Founded</div><div class="v">${pl.founded}</div></div>
      <div class="it"><div class="l">Pricing</div><div class="v brand" style="font-size:14px">Free</div></div>
    </div>

    <div class="tabs">
      <a class="${tab==='overview'?'active':''}" onclick="go('#/platform/${slug}?tab=overview')">Overview</a>
      <a class="${tab==='features'?'active':''}" onclick="go('#/platform/${slug}?tab=features')">Features</a>
      <a class="${tab==='proscons'?'active':''}" onclick="go('#/platform/${slug}?tab=proscons')">Pros & cons</a>
    </div>

    ${tab==='features'?`
      <div class="grid-2">
        ${pl.features.map(f=>`<div class="card" style="padding:18px"><div style="display:flex;align-items:flex-start;gap:11px"><span style="color:var(--brand);font-weight:700;font-size:18px;line-height:1">✓</span><span style="font-size:14px;color:var(--ink-2);line-height:1.5">${esc(f)}</span></div></div>`).join('')}
      </div>
    `:tab==='proscons'?`
      <div class="grid-2">
        <div class="card" style="border-left:3px solid var(--brand)"><h3 style="color:var(--brand)">Pros</h3><p style="font-size:14px;color:var(--ink-2);line-height:1.65;margin-top:10px">${esc(pl.pros)}</p></div>
        <div class="card" style="border-left:3px solid var(--signal)"><h3 style="color:var(--signal)">Cons</h3><p style="font-size:14px;color:var(--ink-2);line-height:1.65;margin-top:10px">${esc(pl.cons)}</p></div>
      </div>
      <div class="card" style="margin-top:18px"><h3>Best for</h3><p style="font-size:14px;color:var(--ink-2);margin-top:8px">${esc(pl.bestFor)}</p></div>
    `:`
      <div class="story">
        <div class="story-main">
          <div class="eyebrow">About the platform</div>
          <h3>The story</h3>
          ${pl.storyHtml||`<p>${esc(pl.tagline)}</p>`}
          <h3>Supported assets</h3>
          <p>${esc(pl.supports)}</p>
          <h3>Best for</h3>
          <p>${esc(pl.bestFor)}</p>
        </div>
        <div class="story-side">
          <div class="card">
            <h3>Quick facts</h3>
            <div style="display:flex;flex-direction:column;gap:11px;margin-top:14px">
              <div style="display:flex;justify-content:space-between;font-size:13px"><span style="color:var(--muted)">Type</span><b>${esc(pl.type)}</b></div>
              <div style="display:flex;justify-content:space-between;font-size:13px"><span style="color:var(--muted)">Founded</span><b>${pl.founded}</b></div>
              <div style="display:flex;justify-content:space-between;font-size:13px"><span style="color:var(--muted)">HQ</span><b>${esc(pl.hq)}</b></div>
              <div style="display:flex;justify-content:space-between;font-size:13px"><span style="color:var(--muted)">Pricing</span><b>${esc(pl.pricing)}</b></div>
              <div style="display:flex;justify-content:space-between;font-size:13px"><span style="color:var(--muted)">Brokers</span><b>${pl.brokerCount}+</b></div>
            </div>
          </div>
          <div class="card">
            <h3>Links</h3>
            <div class="links">
              <a href="https://${esc(pl.website)}" target="_blank">Website <span>↗</span></a>
            </div>
          </div>
        </div>
      </div>
    `}
  `);
}

/* ─── modals ──────────────────────────────────────────────────── */
  .modal-bg{position:fixed;inset:0;background:rgba(0,0,0,.7);backdrop-filter:blur(6px);display:grid;place-items:center;z-index:50;padding:28px}
  .modal{background:var(--bg-1);border:1px solid var(--line);border-radius:18px;width:560px;max-width:100%;max-height:90vh;overflow:auto}
  .modal-h{display:flex;justify-content:space-between;align-items:center;padding:22px 26px;border-bottom:1px solid var(--line)}
  .modal-h h3{font-size:17px;margin:0}
  .modal-h .x{cursor:pointer;color:var(--muted);font-size:22px;line-height:1}
  .modal-h .x:hover{color:var(--ink)}
  .modal-b{padding:24px 26px}
  .modal-f{padding:18px 26px;border-top:1px solid var(--line);display:flex;justify-content:flex-end;gap:10px}
  .field{display:flex;flex-direction:column;gap:7px;margin-bottom:16px}
  .field label{font-size:11px;letter-spacing:.14em;text-transform:uppercase;color:var(--muted);font-weight:600}
  .field input,.field select,.field textarea{background:var(--bg-2);border:1px solid var(--line);color:var(--ink);font-size:13.5px;padding:11px 13px;border-radius:10px;font-family:'Inter';width:100%;outline:none;transition:all .12s ease}
  .field input:focus,.field select:focus,.field textarea:focus{border-color:var(--brand);background:var(--bg-3)}
  .field textarea{resize:vertical;min-height:120px}

  /* ─── community detail community feed ─────────────────────────── */
  .com-hero{position:relative;border-radius:20px;overflow:hidden;margin-bottom:28px;border:1px solid var(--line)}
  .com-hero .banner{height:160px}
  .com-hero .body{padding:0 32px 26px;margin-top:-50px;position:relative;display:flex;gap:20px;align-items:flex-end}
  .com-hero .icon{width:96px;height:96px;border-radius:22px;display:grid;place-items:center;color:var(--brand-ink);font-weight:800;font-size:34px;border:5px solid var(--bg-1);flex:none;letter-spacing:-.025em}
  .com-hero .core{flex:1;padding-bottom:8px}
  .com-hero .core h1{font-size:30px;font-weight:700;letter-spacing:-.02em;margin:0 0 6px}
  .com-hero .core p{font-size:14.5px;color:var(--ink-2);margin:0 0 8px}
  .com-hero .core .stats{display:flex;gap:18px;color:var(--muted);font-size:12px}
  .com-hero .core .stats b{color:var(--ink);font-weight:600;font-family:'JetBrains Mono'}
  .com-hero .actions{padding-bottom:8px}

  /* ─── post detail ─────────────────────────────────────────────── */
  .post-detail{max-width:780px;margin:0 auto}
  .post-detail .head{display:flex;align-items:center;gap:11px;font-size:12.5px;color:var(--muted);margin-bottom:14px}
  .post-detail .head .av-sm{width:36px;height:36px;border-radius:50%;background:linear-gradient(135deg,var(--brand),var(--brand-2));color:var(--brand-ink);display:grid;place-items:center;font-weight:600;font-size:12px}
  .post-detail .head .nm{color:var(--ink);font-weight:500}
  .post-detail h1{font-size:32px;font-weight:700;letter-spacing:-.02em;line-height:1.2;margin:0 0 20px}
  .post-detail .body{font-size:16px;line-height:1.75;color:var(--ink-2);white-space:pre-wrap}
  .post-detail .body-img{height:280px;border-radius:14px;background:linear-gradient(135deg,rgba(107,255,199,.18),rgba(255,107,157,.10));display:grid;place-items:center;color:var(--brand);font-family:'JetBrains Mono';font-size:12px;margin:24px 0}
  .post-detail .actions-bar{display:flex;align-items:center;gap:18px;padding:18px 0;border-top:1px solid var(--line);border-bottom:1px solid var(--line);margin-top:30px;color:var(--muted);font-size:13px}
  .post-detail .actions-bar .like{display:flex;align-items:center;gap:7px;cursor:pointer}
  .post-detail .actions-bar .like:hover,.post-detail .actions-bar .like.on{color:var(--brand)}
  .post-detail .comments{margin-top:28px}
  .post-detail .comments h2{font-size:18px;margin-bottom:18px}
  .comment{padding:16px 0;border-top:1px solid var(--line)}
  .comment:first-of-type{border-top:0}
  .comment .top{display:flex;align-items:center;gap:9px;font-size:12px;color:var(--muted);margin-bottom:7px}
  .comment .top .av-sm{width:26px;height:26px;border-radius:50%;background:linear-gradient(135deg,var(--brand),var(--brand-2));color:var(--brand-ink);display:grid;place-items:center;font-weight:600;font-size:10.5px}
  .comment .top .nm{color:var(--ink);font-weight:500}
  .comment .body{font-size:14px;line-height:1.6;color:var(--ink-2)}
  .comment .actions{margin-top:8px;display:flex;gap:14px;font-size:11.5px;color:var(--muted)}
  .comment .actions span{cursor:pointer}
  .comment .actions span:hover{color:var(--brand)}
  .comment.indent{margin-left:30px;padding-left:18px;border-left:2px solid var(--line)}

  /* ─── utility ─────────────────────────────────────────────────── */
  .empty{padding:60px 30px;text-align:center;color:var(--muted);font-size:14px;background:var(--bg-1);border:1px dashed var(--line);border-radius:14px}
  .empty .ic{font-size:34px;margin-bottom:12px;color:var(--faint)}
  .flash{position:fixed;top:80px;right:24px;padding:12px 16px;background:var(--bg-2);border:1px solid var(--brand);color:var(--brand);font-size:13px;border-radius:10px;z-index:100;box-shadow:0 10px 30px -10px rgba(107,255,199,.4)}

  /* ─── mobile ──────────────────────────────────────────────────── */
  @media(max-width:960px){
    .nav-links{display:none}
    .nav-search{width:160px}
    .feed,.grid-2,.tiers,.story{grid-template-columns:1fr}
    .grid-3,.stat-bar{grid-template-columns:1fr 1fr}
    .hero{padding:32px 26px}
    .hero h1{font-size:32px}
    .row-scroll .creator{width:240px}
    .profile-hero .ctas{position:static;margin-top:14px}
    main{padding:24px 18px}
  }
</style>
</head>
<body>
<div id="app"></div>
<script>
/* ─── state ────────────────────────────────────────────────────────── */
const STATE_VERSION = 'tb-v2-2026-06';
const STATE_KEY = 'tradingbay-v2';

const ROLE_LABELS = {
  TRADER:'Trader', INFLUENCER:'Influencer', GURU:'Guru',
  PROP_FIRM:'Prop Firm', ANALYST:'Analyst', BRAND:'Brand',
};

let session = { userId:'u-cian' };

let users = [
  // Gurus (teachers w/ courses)
  { id:'u-mike', name:'Mike Henderson', handle:'@protradermike', role:'GURU', avatar:'MH', tint:'c2',
    location:'London, UK', funded:true, verified:true,
    bio:'Forex scalper, 7 years funded. Reformed corporate dropout. Now I teach what I wish I knew at 22.',
    tagline:'I help new traders pass their first funded challenge in under 60 days.',
    followers:124230, students:1284, karma:9870, rating:4.8, joinedAt:'2024-02-18',
    website:'protradermike.com', youtube:'youtube.com/@protradermike', twitter:'x.com/protradermike',
    storyHtml:`
      <p>I was 26 when I lost £47,000 in three months trading my own money. I'd quit a perfectly good consulting job in London because I'd watched too many YouTube videos about forex traders making millions from beach houses. The reality of trying to do it alone, with no system and no discipline, was savage.</p>
      <p>It took me 18 months and another £12,000 of losses before I sat down and rebuilt everything from scratch — risk management first, then a single setup I traded for six months until I knew it cold.</p>
      <h3>The turning point</h3>
      <p>I passed my first FTMO 100K challenge in 2022 with a 7.4% gain over 17 trading days. From there I scaled into multiple funded accounts and have been profitable every quarter for three years.</p>
      <blockquote>You don't need a complicated edge. You need to actually use the simple one for long enough.</blockquote>
      <h3>What I teach</h3>
      <p>My course covers the exact framework I use today: the one setup, the one risk rule, the journaling discipline, and how to think about challenge-firm rules without going broke trying to pass.</p>
      <p>I keep my student count under 1,500 so I can actually engage in Discord. If that fills, you'll see a waitlist.</p>
    ` },
  { id:'u-sara', name:'Sara Klein', handle:'@forexlady', role:'GURU', avatar:'SK', tint:'c3',
    location:'Berlin, DE', funded:false, verified:true,
    bio:'1:1 coaching for new traders. Mostly indices. Former institutional analyst.',
    tagline:'Personal coaching for traders who need a teacher, not a Discord channel.',
    followers:48230, students:124, karma:3240, rating:4.9, joinedAt:'2024-06-04',
    website:'sarakleincoaching.com', youtube:'youtube.com/@forexlady',
    storyHtml:`
      <p>I spent eight years at a German trading desk before going independent in 2023. The institutional world taught me one thing above all else: discipline beats prediction. Every time. I now teach this to a handful of traders at a time.</p>
      <h3>My coaching philosophy</h3>
      <p>I take 5–10 students per cohort. Six weeks. Weekly 1:1 sessions, daily chart reviews, and access to me on Telegram during market hours. I won't take you if you can't commit to journaling every trade.</p>
      <blockquote>I'm not here to make you rich. I'm here to make you consistent.</blockquote>
      <h3>Who this is for</h3>
      <p>New traders who've been losing for 6 to 18 months and know it's because of psychology, not strategy. If you've taken three courses and still can't follow your own rules, I can probably help.</p>
    ` },
  { id:'u-dan', name:'Daniel Cruz', handle:'@cryptodan', role:'GURU', avatar:'DC', tint:'c4',
    location:'Lisbon, PT', funded:false, verified:true,
    bio:'BTC/ETH macro analyst. Newsletter @ cryptodan.io. Former hedge fund.',
    tagline:'I read derivatives positioning so you don\'t have to.',
    followers:96400, students:702, karma:5180, rating:4.7, joinedAt:'2024-09-30',
    website:'cryptodan.io', twitter:'x.com/cryptodan',
    storyHtml:`
      <p>I ran a crypto book at a small Singapore fund from 2020 to 2024. The macro framework I built there — funding rates, open interest, options skew, on-chain flows — is what I now teach.</p>
      <h3>What changed in 2024</h3>
      <p>The fund closed when our principal retired. I started writing a daily newsletter mostly to keep myself honest and it grew faster than I expected. Now I run the newsletter, a Telegram, and a small advanced course.</p>
      <blockquote>If you're still drawing trend lines on BTC charts in 2026, you're going to lose to people who understand derivatives positioning.</blockquote>
      <h3>What I won't do</h3>
      <p>I don't give signals. I don't predict price. I give frameworks. If you want green/red arrows on your screen, this isn't the place.</p>
    ` },

  // Influencers (community, posts, social)
  { id:'u-lisa', name:'Lisa Romero', handle:'@forexcafe', role:'INFLUENCER', avatar:'LR', tint:'c1',
    location:'Madrid, ES', funded:true, verified:true,
    bio:'Daily forex commentary. Coffee + charts. Newsletter (~12K subs) + daily Twitter posts.',
    tagline:'Your morning forex briefing. Five minutes, four pairs, three takes.',
    followers:73210, students:0, karma:1245, rating:4.6, joinedAt:'2025-03-14',
    website:'theforexcafe.com', twitter:'x.com/forexcafe', youtube:'youtube.com/@forexcafe',
    storyHtml:`
      <p>I started writing a daily newsletter in 2024 as a way to force myself to do real pre-market analysis. People started subscribing. The newsletter grew to about 12,000 readers and the YouTube channel followed.</p>
      <p>I'm not a trading teacher. I'm a commentator. I share what I'm watching, why I'm watching it, and what would change my mind. You can copy the trades or ignore them.</p>
    ` },
  { id:'u-aria', name:'Aria Patel', handle:'@traderaria', role:'INFLUENCER', avatar:'AP', tint:'c5',
    location:'Mumbai, IN', funded:true, verified:false,
    bio:'Swing trader. Crypto + commodities. TikTok-first.',
    tagline:'Trading content for the algorithm generation.',
    followers:42100, students:0, karma:512, rating:4.4, joinedAt:'2025-11-22',
    website:'', twitter:'x.com/traderaria',
    storyHtml:`
      <p>I started making trading TikToks in 2023 because every other trading creator looked like they were 50 years old and talking to camera in a study. I'm 24 and I wanted to see myself in this space.</p>
      <p>I post setups, journal entries, and a lot of "this is what went wrong today" content. I don't sell courses. I do partner with a couple of brands.</p>
    ` },
  { id:'u-jonas', name:'Jonas Weber', handle:'@scalpking', role:'INFLUENCER', avatar:'JW', tint:'c2',
    location:'Frankfurt, DE', funded:false, verified:false,
    bio:'DAX scalper. Frankfurt. Streams the open Mon-Fri.',
    tagline:'Live scalping streams. 9am Frankfurt time.',
    followers:18700, students:0, karma:218, rating:4.2, joinedAt:'2026-01-08',
    website:'', twitter:'',
    storyHtml:`<p>I stream the DAX open every weekday on Twitch. That's basically it. I get pinned for being too aggressive.</p>` },

  // Other community members
  { id:'u-cian', name:'Cian Hansard', handle:'@cian', role:'TRADER', avatar:'CH', tint:'c4',
    location:'Dublin, IE', funded:false, verified:false,
    bio:'Learning to trade. Long on patience.', tagline:'',
    followers:14, students:0, karma:142, rating:0, joinedAt:'2025-09-12',
    website:'', twitter:'', storyHtml:`` },
  { id:'u-jordan', name:'Jordan Field', handle:'@meanreversion', role:'ANALYST', avatar:'JF', tint:'c4',
    location:'New York, US', funded:true, verified:false,
    bio:'Quant + statistics. Mean-reversion fan.', tagline:'',
    followers:6400, students:218, karma:740, rating:4.6, joinedAt:'2026-02-09',
    website:'meanreversion.io', twitter:'x.com/meanreversionio', storyHtml:`` },
  { id:'u-marco', name:'Marco Bianchi', handle:'@signalsmarco', role:'BRAND', avatar:'MB', tint:'c3',
    location:'Milan, IT', funded:false, verified:false,
    bio:'Telegram signal group. Italy.', tagline:'',
    followers:34000, students:0, karma:88, rating:3.4, joinedAt:'2026-03-01',
    website:'', storyHtml:`` },

  // Prop firms
  { id:'u-atlas', name:'Atlas Funded', handle:'@atlasfunded', role:'PROP_FIRM', avatar:'A', isFirm:true,
    tint:'c2', location:'Dubai, AE', funded:false, verified:true,
    bio:'7 account types. Fast payouts. Built by traders.',
    tagline:'Become a funded trader. Up to $200K. 80% profit share.',
    followers:0, students:0, karma:2800, rating:4.7, joinedAt:'2024-04-01',
    website:'atlasfunded.com', storyHtml:`` },
];

let communities = [
  { id:'c-forex', slug:'r/Forex', name:'Forex', desc:'All things FX — pairs, sessions, news, analysis.', members:84231, tint:'#6BFFC7', bannerCol:'c2', mark:'F' },
  { id:'c-scalping', slug:'r/Scalping', name:'Scalping', desc:'Fast trades, M1–M5 setups, prop-firm-friendly scalping.', members:21090, tint:'#FF6B9D', bannerCol:'c1', mark:'S' },
  { id:'c-swing', slug:'r/SwingTrading', name:'Swing Trading', desc:'Multi-day setups across FX, indices, commodities.', members:17540, tint:'#FFB74A', bannerCol:'c3', mark:'Sw' },
  { id:'c-prop', slug:'r/PropFirms', name:'Prop Firms', desc:'Reviews, comparisons, payout reports, evaluation tips.', members:32104, tint:'#6BC4FF', bannerCol:'c4', mark:'P' },
  { id:'c-crypto', slug:'r/Crypto', name:'Crypto', desc:'BTC, ETH, alts. Technical and macro.', members:62390, tint:'#FFD166', bannerCol:'c3', mark:'C' },
  { id:'c-psych', slug:'r/Psychology', name:'Psychology', desc:'Mindset, journaling, dealing with losses, discipline.', members:14802, tint:'#A78BFA', bannerCol:'c5', mark:'Ψ' },
  { id:'c-indices', slug:'r/Indices', name:'Indices', desc:'US30, NAS100, SPX500, DAX. Sessions, news, opens.', members:9840, tint:'#6BFFC7', bannerCol:'c2', mark:'I' },
  { id:'c-news', slug:'r/News', name:'News Trading', desc:'FOMC, NFP, CPI. The calendar that moves markets.', members:11220, tint:'#FF6B9D', bannerCol:'c1', mark:'N' },
];

let posts = [
  { id:'p1', authorId:'u-mike', communityId:'c-prop', kind:'TEXT', tint:1,
    title:'I passed Atlas Funded\'s 1 Step in 9 trading days — here\'s exactly what I did',
    body:'Started a $50k 1 Step on April 4th and just finished today. Used a strict 1% risk per trade, only traded London open, took no setups during news windows. Hit profit target on day 9 with 32 trades total, 71% win rate.\n\nKey takeaways: Skipping news days was non-negotiable. Two losing days back-to-back I sat out. All trades on NAS100 and EURUSD.',
    likes:412, createdAt:'2026-04-30T14:22:00Z' },
  { id:'p2', authorId:'u-dan', communityId:'c-crypto', kind:'TEXT', tint:3,
    title:'BTC weekly: rejection at $76K + open interest unwind = ?',
    body:'Looking at the BTC weekly chart, this week\'s rejection at $76.2K coincides with a sharp drop in perp open interest. Historically this combination has preceded 8-15% retracements within 10 days. Watching $68K as next major support.',
    likes:287, createdAt:'2026-04-30T09:15:00Z' },
  { id:'p3', authorId:'u-sara', communityId:'c-psych', kind:'TEXT', tint:4,
    title:'How I stopped revenge trading',
    body:'For 3 years I lost more money chasing losses than I ever lost on the original trade. What finally worked: hard rule that after 2 losing trades in a row I close the platform for 24 hours. No exceptions. Saved my account twice this month.',
    likes:524, createdAt:'2026-04-29T18:40:00Z' },
  { id:'p4', authorId:'u-jordan', communityId:'c-forex', kind:'TEXT', tint:2,
    title:'EURUSD mean reversion stats — last 5 years',
    body:'Ran an analysis on EURUSD 4H closes returning to the 20-period SMA. Mean reversion happens within 12 candles 84% of the time. Stop wider than 1.5x ATR and you cap losses at ~12% of trade count.',
    likes:198, createdAt:'2026-04-30T11:30:00Z' },
  { id:'p5', authorId:'u-aria', communityId:'c-swing', kind:'IMAGE', tint:3,
    title:'XAUUSD weekly setup — going long',
    body:'Daily chart on gold breaking above 4750 with strong volume. Entered Friday close at 4770 with stops below 4700. Target 4900 for a 2.6R trade.',
    likes:156, createdAt:'2026-04-30T07:08:00Z' },
  { id:'p6', authorId:'u-jonas', communityId:'c-scalping', kind:'IMAGE', tint:1,
    title:'NAS100 London open scalp — 47 ticks in 8 minutes',
    body:'Hit 47 ticks on the London open scalp this morning. Order block from yesterday\'s NY close, entered on the retest. Three quick fills, out before the news at 8:30.',
    likes:89, createdAt:'2026-04-30T08:12:00Z' },
  { id:'p7', authorId:'u-lisa', communityId:'c-news', kind:'TEXT', tint:2,
    title:'NFP coming up — my checklist before any trade today',
    body:'NFP is at 13:30 UTC today. My personal rules: no trades opened 15 min before or after. No trades held through the release. Spreads widen 5-8x on EURUSD around release. If I really must trade, USDJPY tends to be cleaner post-release.',
    likes:341, createdAt:'2026-04-30T10:05:00Z' },
  { id:'p8', authorId:'u-dan', communityId:'c-crypto', kind:'TEXT', tint:3,
    title:'Stop calling it a "bull run" — this is consolidation',
    body:'Hot take: BTC ranging between $68K and $78K for 4 months is not a bull run, it\'s consolidation. Real breakout would need decisive close above $80K with volume.',
    likes:478, createdAt:'2026-04-29T22:15:00Z' },
];

let comments = [
  { id:'cm1', postId:'p1', authorId:'u-sara', body:'Congrats! Quick Q — were the two days you sat out planned news days, or did the market just feel off?', likes:18, createdAt:'2026-04-30T14:55:00Z', parentId:null },
  { id:'cm2', postId:'p1', authorId:'u-mike', body:'Both. One was FOMC day, one was just chop with no clear bias.', likes:12, createdAt:'2026-04-30T15:08:00Z', parentId:'cm1' },
  { id:'cm3', postId:'p1', authorId:'u-aria', body:'71% win rate is wild. What was your average RR?', likes:8, createdAt:'2026-04-30T15:30:00Z', parentId:null },
  { id:'cm4', postId:'p1', authorId:'u-mike', body:'1:1.5 average. Tight stops, modest targets.', likes:9, createdAt:'2026-04-30T15:42:00Z', parentId:'cm3' },
  { id:'cm5', postId:'p3', authorId:'u-mike', body:'Closing the platform is so simple it sounds dumb but it\'s the only thing that ever worked for me too.', likes:34, createdAt:'2026-04-29T19:15:00Z', parentId:null },
  { id:'cm6', postId:'p7', authorId:'u-cian', body:'New trader here — does this apply for indices too or just FX pairs?', likes:6, createdAt:'2026-04-30T10:25:00Z', parentId:null },
  { id:'cm7', postId:'p7', authorId:'u-lisa', body:'Indices widen too but less dramatically. Bigger risk is the post-release reversal — they move 1.5% in 90 seconds then reverse half of it.', likes:11, createdAt:'2026-04-30T10:38:00Z', parentId:'cm6' },
];

let courses = [
  { id:'co-1', authorId:'u-mike', title:'Funded Trader Roadmap: $0 to $200K', priceCents:24900, durationHours:18, level:'Intermediate', rating:4.8, reviewCount:312, sales:1284, tint:'h1',
    tagline:'Land your first funded payout in 30 days', description:'Nine modules covering exactly how I built up to a $200K funded account across three prop firms. Includes my exact entry rules, risk management spreadsheet, and journal template.' },
  { id:'co-2', authorId:'u-sara', title:'1:1 Indices Coaching · 6-Week Program', priceCents:89900, durationHours:24, level:'Beginner', rating:4.9, reviewCount:78, sales:124, tint:'h3',
    tagline:'Personal guidance for new index traders', description:'Six weeks. Weekly 1-hour sessions. Daily chart reviews. Telegram support during market hours. I take 5–10 students per cohort.' },
  { id:'co-3', authorId:'u-dan', title:'Crypto Macro: Reading the Cycle', priceCents:14900, durationHours:8, level:'Advanced', rating:4.7, reviewCount:189, sales:702, tint:'h4',
    tagline:'Stop trading lines, start trading flows', description:'On-chain metrics, derivatives positioning, and macro flows that actually predict BTC turning points.' },
  { id:'co-4', authorId:'u-lisa', title:'Daily Forex Routine: A Year of Trades', priceCents:9900, durationHours:6, level:'Beginner', rating:4.5, reviewCount:421, sales:2087, tint:'h2',
    tagline:'The routine that turned me consistent', description:'My exact daily routine: pre-market checklist, session prep, journal template, and how I review losses without spiralling.' },
  { id:'co-5', authorId:'u-jordan', title:'Statistical Edge Bootcamp', priceCents:34900, durationHours:14, level:'Advanced', rating:4.6, reviewCount:67, sales:218, tint:'h5',
    tagline:'Math your way to a real edge', description:'How to backtest properly, measure edge, and stop fooling yourself with curve-fit metrics. Heavy Python use.' },
  { id:'co-6', authorId:'u-sara', title:'Trading Psychology · The Quiet Mind', priceCents:7900, durationHours:4, level:'All Levels', rating:4.9, reviewCount:533, sales:3211, tint:'h6',
    tagline:'Fix the head before the strategy', description:'Short, focused course on the mental side: revenge trading, fear of pulling the trigger, fear of giving back profits.' },
];

let tiers = [
  // Per-user subscription tiers (creator economy)
  { id:'t-mike-1', userId:'u-mike', name:'Free', priceCents:0, period:'forever', desc:'Public posts and weekly recap',
    features:['Daily public posts','Weekly market recap','Comment on posts'], featured:false },
  { id:'t-mike-2', userId:'u-mike', name:'Trader', priceCents:1900, period:'month', desc:'Daily setups + private Discord',
    features:['Daily setup alerts','Private Discord access','Monthly Q&A live','Risk calculator templates'], featured:true },
  { id:'t-mike-3', userId:'u-mike', name:'Pro', priceCents:4900, period:'month', desc:'Everything + 1:1 monthly review',
    features:['Everything in Trader','1:1 chart review monthly','Direct DM access','Early access to courses'], featured:false },

  { id:'t-sara-1', userId:'u-sara', name:'Newsletter', priceCents:0, period:'forever', desc:'Free weekly insights',
    features:['Weekly newsletter','Public market analysis'], featured:false },
  { id:'t-sara-2', userId:'u-sara', name:'Member', priceCents:2900, period:'month', desc:'Daily journals + member calls',
    features:['Daily trade journals','Monthly group calls','Member-only podcast'], featured:true },
  { id:'t-sara-3', userId:'u-sara', name:'Coaching', priceCents:89900, period:'6-week program', desc:'1:1 personal coaching',
    features:['Weekly 1:1 sessions','Daily Telegram support','Personalised plan','Trade reviews'], featured:false },

  { id:'t-dan-1', userId:'u-dan', name:'Free', priceCents:0, period:'forever', desc:'Public substack',
    features:['Weekly Friday digest','Open comments'], featured:false },
  { id:'t-dan-2', userId:'u-dan', name:'Pro', priceCents:2900, period:'month', desc:'Daily report + dashboards',
    features:['Daily macro report','Live dashboards','Telegram alerts'], featured:true },
  { id:'t-dan-3', userId:'u-dan', name:'Institutional', priceCents:24900, period:'month', desc:'API access + custom reports',
    features:['API data access','Custom analytics','Quarterly call'], featured:false },

  { id:'t-lisa-1', userId:'u-lisa', name:'Newsletter', priceCents:0, period:'forever', desc:'Free morning briefing',
    features:['Daily 5-min email','Public posts'], featured:false },
  { id:'t-lisa-2', userId:'u-lisa', name:'Café Member', priceCents:1500, period:'month', desc:'Extended analysis + Discord',
    features:['Extended morning briefing','Private Discord','Weekly Sunday review'], featured:true },
];

let firms = [
  { id:'f-atlas', name:'Atlas Funded', slug:'atlas-funded', mark:'A', tint:'c2',
    tagline:'7 account types. Fast payouts. Built by traders.', founded:2023, hq:'Dubai, UAE',
    accounts:'$5K – $200K', payoutDays:'1–3 days', payoutSplit:80, refund:'Refund on first payout',
    listingTier:'FEATURED', rating:4.7, reviewCount:284,
    promo:'Spring promo · 30% off all challenges with code SPRING30',
    website:'atlasfunded.com',
    storyHtml:`
      <p>Atlas Funded was founded in 2023 by a team of independent traders frustrated with the existing prop firm landscape. Aggressive marketing, opaque rules, slow payouts.</p>
      <p>We launched with three commitments: clear rules, fast payouts, no hidden traps. We back this up with public payout reports every quarter and the fastest payout speed in the industry — averaging 36 hours from request to bank.</p>
    `,
    accountTypes:[
      { name:'Instant Funded',  size:'$5K – $50K', daily:'3%', max:'6%',  split:'80%', price:'$49 – $649' },
      { name:'1 Step',          size:'$10K – $200K', daily:'4%', max:'8%',  split:'80%', price:'$89 – $999' },
      { name:'2 Step',          size:'$10K – $200K', daily:'5%', max:'10%', split:'80%', price:'$59 – $749' },
      { name:'3 Step',          size:'$25K – $100K', daily:'4%', max:'8%',  split:'85%', price:'$99 – $499' },
    ] },
  { id:'f-ftmo', name:'FTMO', slug:'ftmo', mark:'F', tint:'c1',
    tagline:'Industry veteran. Strict but fair.', founded:2015, hq:'Prague, CZ',
    accounts:'$10K – $200K', payoutDays:'1 day', payoutSplit:90, refund:'Refund on first payout',
    listingTier:'FEATURED', rating:4.6, reviewCount:1872, promo:'',
    website:'ftmo.com', storyHtml:``,
    accountTypes:[
      { name:'FTMO Challenge', size:'$10K – $200K', daily:'5%', max:'10%', split:'90%', price:'$155 – $1,080' },
    ] },
  { id:'f-mff', name:'MyForexFunds', slug:'mff', mark:'M', tint:'c3',
    tagline:'Aggressive payout splits. Lighter rules.', founded:2020, hq:'Toronto, CA',
    accounts:'$5K – $300K', payoutDays:'2–5 days', payoutSplit:85, refund:'No refund',
    listingTier:'BASIC', rating:3.9, reviewCount:920, promo:'',
    website:'myforexfunds.com', storyHtml:``,
    accountTypes:[] },
  { id:'f-tradeify', name:'Tradeify', slug:'tradeify', mark:'T', tint:'c4',
    tagline:'Beginner-friendly programs.', founded:2024, hq:'Sydney, AU',
    accounts:'$10K – $100K', payoutDays:'3 days', payoutSplit:80, refund:'30-day refund',
    listingTier:'BASIC', rating:4.4, reviewCount:142, promo:'New trader welcome bonus',
    website:'tradeify.com', storyHtml:``,
    accountTypes:[] },
  { id:'f-fnext', name:'FundedNext', slug:'funded-next', mark:'FN', tint:'c1',
    tagline:'Multiple account types. Flexible rules.', founded:2022, hq:'Singapore',
    accounts:'$5K – $200K', payoutDays:'2 days', payoutSplit:90, refund:'Refund on first payout',
    listingTier:'FEATURED', rating:4.5, reviewCount:670, promo:'',
    website:'fundednext.com', storyHtml:``,
    accountTypes:[] },
  { id:'f-fa', name:'Funded Academy', slug:'funded-academy', mark:'FA', tint:'c5',
    tagline:'Community + funding combo.', founded:2025, hq:'London, UK',
    accounts:'$25K – $100K', payoutDays:'5 days', payoutSplit:75, refund:'No refund',
    listingTier:'BASIC', rating:4.0, reviewCount:48, promo:'',
    website:'fundedacademy.com', storyHtml:``,
    accountTypes:[] },
];

// Add discount/promo codes to firms (TradingPilot/PropFirmMatch style)
firms[0].promoCode = 'SPRING30'; firms[0].promoDiscount = '30% off';
firms[1].promoCode = 'TBAY10';   firms[1].promoDiscount = '10% off';
firms[4].promoCode = 'NEXT15';   firms[4].promoDiscount = '15% off';
firms[3].promoCode = 'WELCOME';  firms[3].promoDiscount = '$25 credit';

let platforms = [
  { id:'pl-tradelocker', name:'TradeLocker', slug:'tradelocker', mark:'TL', tint:'c2',
    tagline:'The fastest-growing prop trading platform of 2025.',
    type:'Web + Mobile', supports:'Forex, indices, commodities, crypto',
    brokerCount:42, rating:4.6, reviewCount:312, founded:2023, hq:'Dublin, IE',
    pricing:'Free for traders · brokers pay',
    features:['Browser-based, no install needed','Built-in news + economic calendar','Multi-account dashboard','Native mobile apps','Copy-trading built in','Detailed analytics','Heatmaps + sentiment data'],
    bestFor:'Prop firm traders, multi-account users',
    pros:'Modern interface, fast execution, growing broker network',
    cons:'Smaller indicator library than MT5, no EA support yet',
    website:'tradelocker.com',
    storyHtml:`
      <p>TradeLocker launched in 2023 specifically to fix the things prop firm traders complained about with MT4 and MT5: clunky UI, no native mobile, and weak analytics. In two years it's become the default platform of choice for most newer prop firms.</p>
      <h3>Why traders pick it</h3>
      <p>Web-first means no install across multiple devices. The trade analytics dashboard is the best of any retail platform we've tested. Order execution is consistently fast across the broker network.</p>
    ` },
  { id:'pl-mt5', name:'MetaTrader 5', slug:'mt5', mark:'M5', tint:'c1',
    tagline:'The institutional standard. Powerful, complex, everywhere.',
    type:'Desktop + Web + Mobile', supports:'Forex, indices, commodities, stocks, crypto, futures',
    brokerCount:880, rating:4.3, reviewCount:2104, founded:2010, hq:'Limassol, CY',
    pricing:'Free for traders · brokers pay license',
    features:['Multi-asset coverage','Expert Advisors (algorithmic trading)','Strategy Tester for backtesting','100+ built-in indicators','MQL5 development language','News & economic calendar','Multi-currency depth of market'],
    bestFor:'Algo traders, multi-asset traders, advanced users',
    pros:'Industry standard, massive ecosystem of EAs and indicators, supports almost every broker',
    cons:'Dated UI, steep learning curve, mobile experience lags',
    website:'metatrader5.com',
    storyHtml:`
      <p>MetaTrader 5 launched in 2010 as the successor to MT4, with expanded asset coverage and better backtesting. Adoption was slow for a decade — most brokers stayed on MT4 because their clients refused to move.</p>
      <p>Since 2022 most new prop firms have launched MT5-only (no MT4), and traders have come around. Today MT5 is the workhorse platform across forex and CFD trading.</p>
    ` },
  { id:'pl-mt4', name:'MetaTrader 4', slug:'mt4', mark:'M4', tint:'c3',
    tagline:'The legacy king. Still the most used forex platform on earth.',
    type:'Desktop + Web + Mobile', supports:'Forex, indices, commodities, crypto',
    brokerCount:1240, rating:4.0, reviewCount:5012, founded:2005, hq:'Limassol, CY',
    pricing:'Free for traders',
    features:['Massive third-party EA + indicator library','Lightweight installer','Stable, battle-tested','Custom MQL4 scripts','Built-in marketplace','One-click trading'],
    bestFor:'Forex purists, EA users, traders on legacy broker stacks',
    pros:'Lightest platform, decades of resources, best EA library',
    cons:'Discontinued for new development, no native multi-asset support',
    website:'metatrader4.com',
    storyHtml:`
      <p>MetaTrader 4 has been the default retail forex platform since 2005. MetaQuotes officially stopped releasing new MT4 versions in 2018, but the platform is so deeply entrenched that it remains the most-used trading software in the world.</p>
      <p>If you've taken any online forex course, the chances are good the screenshots are from MT4. The third-party EA and indicator ecosystem is unmatched.</p>
    ` },
  { id:'pl-ctrader', name:'cTrader', slug:'ctrader', mark:'cT', tint:'c4',
    tagline:'The transparent ECN-focused platform with depth of market.',
    type:'Desktop + Web + Mobile', supports:'Forex, indices, commodities, crypto, stocks',
    brokerCount:88, rating:4.5, reviewCount:412, founded:2010, hq:'London, UK',
    pricing:'Free for traders',
    features:['Level II depth of market','Algo trading via cAlgo (C#)','Transparent ECN execution','Advanced charting (Trading Central)','Symbol-level commission display','Copy trading platform'],
    bestFor:'ECN-style traders, transparent pricing fans, C# developers',
    pros:'Best DOM display, true ECN routing, beautiful UI',
    cons:'Smaller broker network, weaker indicator library than MT4/5',
    website:'ctrader.com',
    storyHtml:`<p>cTrader has always been the "professional retail" platform — designed for traders who want to see real order book depth, transparent commissions, and proper ECN execution.</p>` },
  { id:'pl-matchtrader', name:'Match-Trader', slug:'match-trader', mark:'MT', tint:'c5',
    tagline:'The fast-rising prop-firm-friendly broker tech.',
    type:'Web + Mobile', supports:'Forex, indices, commodities, crypto',
    brokerCount:36, rating:4.4, reviewCount:188, founded:2019, hq:'Warsaw, PL',
    pricing:'Free for traders · brokers pay',
    features:['Web-first with fast execution','Built-in CRM for brokers','Real-time risk analytics','Multi-language support','Modern API','Copy trading'],
    bestFor:'Prop firm traders, newer broker stacks',
    pros:'Modern UI, fast execution, growing in prop firm space',
    cons:'Smaller ecosystem than MT4/5, fewer indicators',
    website:'match-trade.com',
    storyHtml:`<p>Match-Trader emerged from the broker-tech side, building infrastructure for newer brokers and prop firms. Its trader-facing app has caught up rapidly in 2025.</p>` },
  { id:'pl-tv', name:'TradingView', slug:'tradingview', mark:'TV', tint:'c2',
    tagline:'The charting platform of choice. Now with execution.',
    type:'Web + Mobile', supports:'Forex, indices, commodities, crypto, stocks',
    brokerCount:50, rating:4.8, reviewCount:8420, founded:2011, hq:'New York, US',
    pricing:'Free tier + paid plans $14.95–$59.95/month',
    features:['Best-in-class charting','Pine Script for indicators & strategies','Massive community of indicators','Multi-broker execution','Built-in social network','Mobile chart parity'],
    bestFor:'Multi-asset traders, chart obsessives, screenshot creators',
    pros:'Unmatched charting, best mobile experience, social features',
    cons:'Execution layer still maturing, broker integration uneven',
    website:'tradingview.com',
    storyHtml:`<p>TradingView started as a charting tool in 2011 and became the most-used charting platform on the planet. Since 2022 they've added direct execution through partner brokers, slowly moving from charting layer to full trading platform.</p>` },
  { id:'pl-ninja', name:'NinjaTrader', slug:'ninjatrader', mark:'NT', tint:'c1',
    tagline:'Futures-first. Serious tools for serious traders.',
    type:'Desktop + Web', supports:'Futures, forex, stocks',
    brokerCount:18, rating:4.5, reviewCount:920, founded:2003, hq:'Denver, US',
    pricing:'Free with funded account · $1,499 lifetime license',
    features:['Order Flow + Volume Profile','Advanced charting','C# strategy development','Market replay','Direct futures broker integration','Strategy automation'],
    bestFor:'Futures traders, US-based, prop futures challengers',
    pros:'Best for US futures, deep order-flow tools, mature platform',
    cons:'Steep learning curve, weaker FX/CFD presence outside US',
    website:'ninjatrader.com',
    storyHtml:`<p>NinjaTrader is the default platform for US futures traders. Most futures-focused prop firms (Apex, TopstepTrader, etc.) use NinjaTrader as their trader platform.</p>` },
  { id:'pl-dxtrade', name:'DXTrade', slug:'dxtrade', mark:'DX', tint:'c3',
    tagline:'White-label trading tech powering newer brokers.',
    type:'Web + Mobile', supports:'Forex, indices, commodities, crypto',
    brokerCount:24, rating:4.2, reviewCount:142, founded:2002, hq:'Limassol, CY',
    pricing:'Free for traders · brokers pay license',
    features:['Customisable UI per broker','Risk management modules','Algorithmic trading API','Real-time market data','Multi-language'],
    bestFor:'Traders on white-label brokers, multi-account users',
    pros:'Modern web UI, flexible for brokers',
    cons:'Smaller ecosystem, varies by broker implementation',
    website:'dxtrade.com',
    storyHtml:`<p>DXTrade is Devexperts' trading platform, used as the engine behind several mid-tier brokers and prop firms. Trader experience varies by which broker has implemented it.</p>` },
];

let reviews = [
  // Firm reviews
  { id:'rv1', targetType:'FIRM', targetId:'f-atlas', authorId:'u-mike', rating:5, verifiedPurchase:true, createdAt:'2026-04-12',
    body:'Best payout speed I\'ve seen. Last payout hit my bank in 36 hours from request. Rules are tight but clear — read them and you won\'t get caught.' },
  { id:'rv2', targetType:'FIRM', targetId:'f-atlas', authorId:'u-jonas', rating:4, verifiedPurchase:true, createdAt:'2026-04-08',
    body:'Solid firm. Sub-3-min rule got me twice as a scalper — be aware of that going in. Otherwise great experience.' },
  { id:'rv3', targetType:'FIRM', targetId:'f-atlas', authorId:'u-aria', rating:5, verifiedPurchase:true, createdAt:'2026-03-25',
    body:'I\'m a swing trader so the rules barely affect me. Funded account felt real, profit splits arrived as promised.' },
  { id:'rv4', targetType:'FIRM', targetId:'f-mff', authorId:'u-dan', rating:3, verifiedPurchase:true, createdAt:'2026-03-30',
    body:'Decent payouts but their evaluation rules changed twice during my challenge. Communication was poor.' },
  { id:'rv5', targetType:'FIRM', targetId:'f-ftmo', authorId:'u-sara', rating:5, verifiedPurchase:true, createdAt:'2026-04-01',
    body:'The benchmark. Rules are strict but they\'ve been transparent for almost a decade. You know what you\'re signing up for.' },

  // User reviews
  { id:'rv6', targetType:'USER', targetId:'u-mike', authorId:'u-cian', rating:5, verifiedPurchase:true, createdAt:'2026-04-26',
    body:'Bought his Roadmap course — actually no fluff. Concrete entry rules, real backtests, his journal template is gold.' },
  { id:'rv7', targetType:'USER', targetId:'u-mike', authorId:'u-aria', rating:4, verifiedPurchase:true, createdAt:'2026-04-20',
    body:'Course is great but the Discord can be slow to respond. Material itself is 5/5.' },
  { id:'rv8', targetType:'USER', targetId:'u-sara', authorId:'u-cian', rating:5, verifiedPurchase:true, createdAt:'2026-04-15',
    body:'Sara\'s 1:1 coaching changed how I think about losing trades. Best money I\'ve spent on trading.' },
  { id:'rv9', targetType:'USER', targetId:'u-dan', authorId:'u-jordan', rating:5, verifiedPurchase:true, createdAt:'2026-04-10',
    body:'Macro course is sharp. Few people understand derivatives positioning at this level.' },
  { id:'rv10', targetType:'USER', targetId:'u-lisa', authorId:'u-jonas', rating:5, verifiedPurchase:false, createdAt:'2026-04-22',
    body:'Five minutes a morning, and I trade better because of it. Real, no-noise commentary.' },
];

let likes = {}; // key=`${userId}:${postId|commentId}` value=1
let follows = new Set(); // `${followerId}:${targetId}`
let joinedCommunities = new Set(['u-cian:c-forex','u-cian:c-prop','u-cian:c-psych']);

/* ─── persistence ─────────────────────────────────────────────────── */
function saveState(){
  try{ localStorage.setItem(STATE_KEY, JSON.stringify({version:STATE_VERSION,session,users,communities,posts,comments,courses,tiers,firms,platforms,reviews,likes,follows:[...follows],joinedCommunities:[...joinedCommunities]})); }catch(e){}
}
function loadState(){
  try{
    const raw=localStorage.getItem(STATE_KEY); if(!raw) return false;
    const p=JSON.parse(raw); if(p.version!==STATE_VERSION) return false;
    if(p.session) session=p.session;
    if(p.users) users=p.users;
    if(p.communities) communities=p.communities;
    if(p.posts) posts=p.posts;
    if(p.comments) comments=p.comments;
    if(p.courses) courses=p.courses;
    if(p.tiers) tiers=p.tiers;
    if(p.firms) firms=p.firms;
    if(p.platforms) platforms=p.platforms;
    if(p.reviews) reviews=p.reviews;
    if(p.likes) likes=p.likes;
    if(p.follows) follows=new Set(p.follows);
    if(p.joinedCommunities) joinedCommunities=new Set(p.joinedCommunities);
    return true;
  }catch(e){return false;}
}
function resetState(){ if(!confirm('Reset all demo data?'))return; localStorage.removeItem(STATE_KEY); location.reload(); }

/* ─── helpers ─────────────────────────────────────────────────────── */
function esc(s){return String(s??'').replace(/[&<>"']/g,c=>({"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#39;"}[c]))}
function timeAgo(iso){const d=Math.floor((Date.now()-Date.parse(iso))/1000);if(d<60)return d+'s ago';if(d<3600)return Math.floor(d/60)+'m ago';if(d<86400)return Math.floor(d/3600)+'h ago';if(d<86400*30)return Math.floor(d/86400)+'d ago';if(d<86400*365)return Math.floor(d/86400/30)+'mo ago';return Math.floor(d/86400/365)+'y ago';}
function fmtCount(n){if(n<1000)return String(n);if(n<10000)return (n/1000).toFixed(1)+'K';if(n<1000000)return Math.round(n/1000)+'K';return (n/1000000).toFixed(1)+'M';}
function fmtPrice(c){if(c===0)return 'Free';return '$'+(c/100).toLocaleString('en-US',{minimumFractionDigits:0,maximumFractionDigits:0});}
function stars(r){if(!r)return '☆☆☆☆☆';const f=Math.floor(r);let s='';for(let i=0;i<5;i++)s+=i<f?'★':'☆';return s;}
function flash(msg){const el=document.createElement('div');el.className='flash';el.textContent=msg;document.body.appendChild(el);setTimeout(()=>el.remove(),2200);}

const userById=id=>users.find(u=>u.id===id);
const comById=id=>communities.find(c=>c.id===id);
const comBySlug=slug=>communities.find(c=>c.slug===slug||c.id===slug);
const postById=id=>posts.find(p=>p.id===id);
const courseById=id=>courses.find(c=>c.id===id);
const firmBySlug=slug=>firms.find(f=>f.slug===slug);
const platformBySlug=slug=>platforms.find(pl=>pl.slug===slug);
const reviewsFor=(t,id)=>reviews.filter(r=>r.targetType===t&&r.targetId===id);
const avgRating=rs=>rs.length===0?0:rs.reduce((s,r)=>s+r.rating,0)/rs.length;
const isFollowing=id=>follows.has(session.userId+':'+id);
const isInCommunity=id=>joinedCommunities.has(session.userId+':'+id);
const tiersFor=uid=>tiers.filter(t=>t.userId===uid);

let route = window.location.hash || '#/home';
function go(h){window.location.hash=h;}
window.addEventListener('hashchange',()=>{route=window.location.hash||'#/home';render();});
const isActive=h=>{if(h==='#/home')return route==='#/home'||route===''||route==='#';if(route===h)return 'active';if(route.startsWith(h.replace(/s$/,''))&&!h.endsWith('home'))return 'active';return '';};

/* ─── shell ───────────────────────────────────────────────────────── */
function renderShell(content){
  const me = userById(session.userId);
  return `
    <div class="nav">
      <div class="nav-inner">
        <a class="brand" onclick="go('#/home')"><span class="m">TB</span><span>Trading<b>Bay</b></span></a>
        <nav class="nav-links">
          <a class="${isActive('#/home')}" onclick="go('#/home')">Home</a>
          <a class="${isActive('#/communities')}" onclick="go('#/communities')">Communities</a>
          <a class="${isActive('#/firms')}" onclick="go('#/firms')">Prop Firms</a>
          <a class="${isActive('#/influencers')}" onclick="go('#/influencers')">Influencers</a>
          <a class="${isActive('#/gurus')}" onclick="go('#/gurus')">Gurus</a>
          <a class="${isActive('#/platforms')}" onclick="go('#/platforms')">Platforms</a>
        </nav>
        <div class="nav-search">
          <span class="ic">⌕</span>
          <input type="text" placeholder="Search…" />
        </div>
        <div class="nav-cta">
          <button class="btn primary sm" onclick="openCompose()">+ Post</button>
          <div class="av-tiny" onclick="go('#/profile/${session.userId}')" title="${esc(me?.name)}">${esc(me?.avatar||'?')}</div>
        </div>
      </div>
    </div>
    <main>${content}</main>
    ${composeOpen?renderCompose():''}
    ${reviewOpen?renderReviewModal():''}`;
}

/* ─── HOME ─────────────────────────────────────────────────────────── */
function renderHome(){
  const me = userById(session.userId);
  const featuredGurus = users.filter(u=>u.role==='GURU');
  const featuredInfluencers = users.filter(u=>u.role==='INFLUENCER');
  const popularCommunities = [...communities].sort((a,b)=>b.members-a.members).slice(0,4);
  const topFirms = firms.filter(f=>f.listingTier==='FEATURED').slice(0,3);
  const trendingPosts = [...posts].sort((a,b)=>b.likes-a.likes).slice(0,6);

  return renderShell(`
    <div class="hero">
      <div class="hero-content">
        <div class="eyebrow">Welcome back, ${esc(me?.name.split(' ')[0])}</div>
        <h1>The home for <b>real traders.</b></h1>
        <p>Find your community, learn from verified gurus, compare prop firms with exclusive promo codes, and pick the right platform. Everything you need in one clean place.</p>
        <div style="display:flex;gap:10px;flex-wrap:wrap">
          <button class="btn primary lg" onclick="go('#/firms')">Find your prop firm →</button>
          <button class="btn ghost lg" onclick="go('#/platforms')">Compare platforms</button>
        </div>
        <div class="hero-stats">
          <div class="stat"><b>${fmtCount(users.length*2400)}</b><span>Traders</span></div>
          <div class="stat"><b>${firms.length}</b><span>Prop firms</span></div>
          <div class="stat"><b>${platforms.length}</b><span>Platforms</span></div>
          <div class="stat"><b>${courses.length}</b><span>Courses</span></div>
        </div>
      </div>
    </div>

    <div class="section">
      <div class="section-h">
        <div><div class="eyebrow">Save money</div><h2>Active promo codes</h2></div>
        <a onclick="go('#/firms')">All firms →</a>
      </div>
      <div class="grid-4">
        ${firms.filter(f=>f.promoCode).map(f=>{
          const tintMap={c1:'linear-gradient(135deg,#FF6B9D,#FFB74A)',c2:'linear-gradient(135deg,#6BFFC7,#3DD9A4)',c3:'linear-gradient(135deg,#FFD166,#FF6B9D)',c4:'linear-gradient(135deg,#6BC4FF,#A78BFA)',c5:'linear-gradient(135deg,#A78BFA,#FF6B9D)'};
          return `
          <div class="card hov" style="padding:18px" onclick="go('#/firm/${f.slug}')">
            <div style="display:flex;align-items:center;gap:12px;margin-bottom:14px">
              <div style="width:44px;height:44px;border-radius:10px;background:${tintMap[f.tint]||tintMap.c2};display:grid;place-items:center;color:var(--brand-ink);font-weight:800;font-size:16px;letter-spacing:-.025em">${f.mark}</div>
              <div style="flex:1;min-width:0"><div style="font-weight:700;font-size:14px">${esc(f.name)}</div><div style="font-size:11px;color:var(--gold)">${stars(f.rating)} ${f.rating}</div></div>
            </div>
            <div style="background:var(--bg-2);border:1px dashed var(--brand);border-radius:10px;padding:11px 14px">
              <div style="font-size:10px;letter-spacing:.16em;text-transform:uppercase;color:var(--brand);font-weight:700;margin-bottom:3px">${esc(f.promoDiscount)}</div>
              <div style="font-family:'JetBrains Mono';font-weight:800;font-size:16px;color:var(--brand);letter-spacing:.04em">${esc(f.promoCode)}</div>
            </div>
            <button class="btn primary sm" style="width:100%;margin-top:12px" onclick="event.stopPropagation();copyCode('${f.promoCode}')">Copy code</button>
          </div>`;
        }).join('')}
      </div>
    </div>

    <div class="section">
      <div class="section-h">
        <div><div class="eyebrow">Discover</div><h2>Featured gurus</h2></div>
        <a onclick="go('#/gurus')">See all gurus →</a>
      </div>
      <div class="row-scroll">
        ${featuredGurus.map(u=>renderCreatorCard(u)).join('')}
      </div>
    </div>

    <div class="section">
      <div class="section-h">
        <div><div class="eyebrow">Trending now</div><h2>Hot in the community</h2></div>
        <a onclick="go('#/communities')">All posts →</a>
      </div>
      <div class="feed">
        ${trendingPosts.map(renderFeedItem).join('')}
      </div>
    </div>

    <div class="section">
      <div class="section-h">
        <div><div class="eyebrow">Where traders gather</div><h2>Popular communities</h2></div>
        <a onclick="go('#/communities')">All communities →</a>
      </div>
      <div class="grid-4">
        ${popularCommunities.map(renderCommunityTile).join('')}
      </div>
    </div>

    <div class="section">
      <div class="section-h">
        <div><div class="eyebrow">Get funded</div><h2>Top-rated prop firms</h2></div>
        <a onclick="go('#/firms')">Compare all firms →</a>
      </div>
      <div style="display:flex;flex-direction:column;gap:12px">
        ${topFirms.map(renderFirmRow).join('')}
      </div>
    </div>

    <div class="section">
      <div class="section-h">
        <div><div class="eyebrow">Follow</div><h2>Voices to know</h2></div>
        <a onclick="go('#/influencers')">All influencers →</a>
      </div>
      <div class="row-scroll">
        ${featuredInfluencers.map(u=>renderCreatorCard(u)).join('')}
      </div>
    </div>
  `);
}

function renderFeedItem(p){
  const au = userById(p.authorId);
  const c = comById(p.communityId);
  const liked = likes[session.userId+':'+p.id];
  return `
    <div class="feed-item" onclick="go('#/p/${p.id}')">
      ${p.kind==='IMAGE'?`<div class="img-block tint-${p.tint||1}">CHART · ${esc(p.title.split(' ').slice(0,3).join(' '))}</div>`:''}
      <div>
        <div class="top">
          <span class="com">${esc(c.slug)}</span>
          <span class="meta">· ${timeAgo(p.createdAt)}</span>
        </div>
        <div class="title" style="margin-top:8px">${esc(p.title)}</div>
        <div class="preview" style="margin-top:6px">${esc(p.body)}</div>
      </div>
      <div class="author">
        <div class="av-sm">${esc(au.avatar)}</div>
        <div>
          <div class="nm">${esc(au.name)}${au.verified?'<span class="verified">✓</span>':''}</div>
          <div class="hh">${esc(au.handle)}</div>
        </div>
        <div class="actions">
          <span style="cursor:pointer;${liked?'color:var(--brand)':''}" onclick="event.stopPropagation();toggleLike('${p.id}')">${liked?'♥':'♡'} ${p.likes+(liked?1:0)}</span>
          <span>💬 ${comments.filter(cm=>cm.postId===p.id).length}</span>
        </div>
      </div>
    </div>`;
}

function renderCreatorCard(u){
  return `
    <div class="creator" onclick="go('#/u/${u.id}')">
      <div class="cover ${u.tint||''}"></div>
      <div class="body">
        <div class="av">${esc(u.avatar)}</div>
        <div class="name">${esc(u.name)}${u.verified?'<span class="verified">✓</span>':''}</div>
        <div class="handle">${esc(u.handle)}</div>
        <span class="pill role brand-soft" style="margin-top:8px">${ROLE_LABELS[u.role]}</span>
        <div class="tagline">${esc(u.tagline||u.bio||'')}</div>
        <div class="stats">
          <span><b>${fmtCount(u.followers)}</b> followers</span>
          ${u.students>0?`<span><b>${fmtCount(u.students)}</b> students</span>`:''}
        </div>
      </div>
    </div>`;
}

function renderCommunityTile(c){
  const tintMap={c1:'linear-gradient(135deg,#FF6B9D,#FFB74A)',c2:'linear-gradient(135deg,#6BFFC7,#3DD9A4)',c3:'linear-gradient(135deg,#FFD166,#FF6B9D)',c4:'linear-gradient(135deg,#6BC4FF,#A78BFA)',c5:'linear-gradient(135deg,#A78BFA,#FF6B9D)'};
  const tint = tintMap[c.bannerCol]||tintMap.c2;
  const joined = isInCommunity(c.id);
  return `
    <div class="com-tile" onclick="go('#/c/${encodeURIComponent(c.slug)}')">
      <div class="banner" style="background:${tint}"></div>
      <div class="body">
        <div class="icon" style="background:${c.tint}">${c.mark}</div>
        <div class="slug">${esc(c.slug)}</div>
        <div class="desc">${esc(c.desc)}</div>
        <div class="foot">
          <span><b>${fmtCount(c.members)}</b> members</span>
          <span class="pill ${joined?'brand-soft':''}">${joined?'Joined':'Open'}</span>
        </div>
      </div>
    </div>`;
}

function renderFirmRow(f){
  const r = avgRating(reviewsFor('FIRM',f.id))||f.rating;
  const tintMap={c1:'linear-gradient(135deg,#FF6B9D,#FFB74A)',c2:'linear-gradient(135deg,#6BFFC7,#3DD9A4)',c3:'linear-gradient(135deg,#FFD166,#FF6B9D)',c4:'linear-gradient(135deg,#6BC4FF,#A78BFA)',c5:'linear-gradient(135deg,#A78BFA,#FF6B9D)'};
  const tint = tintMap[f.tint]||tintMap.c2;
  return `
    <div class="firm-row ${f.listingTier==='FEATURED'?'featured':''}" onclick="go('#/firm/${f.slug}')">
      <div class="icon" style="background:${tint}">${f.mark}</div>
      <div class="core">
        <div class="head">
          <span class="name">${esc(f.name)}</span>
          ${f.listingTier==='FEATURED'?'<span class="pill brand-soft role">Featured</span>':''}
          <span class="rate">${stars(r)} ${r.toFixed(1)} <span class="n">(${f.reviewCount})</span></span>
        </div>
        <div class="tagline">${esc(f.tagline)}</div>
        <div class="meta">
          <span>Accounts <b>${esc(f.accounts)}</b></span>
          <span>Payout <b>${esc(f.payoutDays)}</b></span>
          <span>Split <b>${f.payoutSplit}%</b></span>
          <span>Founded <b>${f.founded}</b></span>
        </div>
      </div>
      <div class="right">
        ${f.promoCode?`<div style="text-align:right;margin-bottom:6px">
          <div style="font-size:10px;letter-spacing:.16em;text-transform:uppercase;color:var(--brand);font-weight:700;margin-bottom:2px">${esc(f.promoDiscount||'Promo')}</div>
          <div style="font-family:'JetBrains Mono';font-size:12.5px;font-weight:700;background:var(--brand);color:var(--brand-ink);padding:3px 8px;border-radius:6px;display:inline-block">${esc(f.promoCode)}</div>
        </div>`:''}
        <button class="btn sm primary">View →</button>
      </div>
    </div>`;
}

/* ─── COMMUNITIES PAGE ─────────────────────────────────────────────── */
function renderCommunitiesPage(){
  return renderShell(`
    <div class="eyebrow">Where traders gather</div>
    <h1>Communities</h1>
    <p class="lead">Find your people. Join any community to follow its posts in your home feed.</p>
    <div class="grid-4">
      ${communities.map(renderCommunityTile).join('')}
    </div>
  `);
}

/* ─── COMMUNITY DETAIL ─────────────────────────────────────────────── */
function renderCommunity(slug){
  const c = comBySlug(decodeURIComponent(slug));
  if(!c) return renderShell('<div class="empty">Community not found.</div>');
  const list = posts.filter(p=>p.communityId===c.id).sort((a,b)=>b.likes-a.likes);
  const joined = isInCommunity(c.id);
  const tintMap={c1:'linear-gradient(135deg,#FF6B9D,#FFB74A)',c2:'linear-gradient(135deg,#6BFFC7,#3DD9A4)',c3:'linear-gradient(135deg,#FFD166,#FF6B9D)',c4:'linear-gradient(135deg,#6BC4FF,#A78BFA)',c5:'linear-gradient(135deg,#A78BFA,#FF6B9D)'};
  return renderShell(`
    <div class="com-hero">
      <div class="banner" style="background:${tintMap[c.bannerCol]}"></div>
      <div class="body">
        <div class="icon" style="background:${c.tint}">${c.mark}</div>
        <div class="core">
          <h1>${esc(c.slug)}</h1>
          <p>${esc(c.desc)}</p>
          <div class="stats">
            <span><b>${fmtCount(c.members)}</b> members</span>
            <span><b>${list.length}</b> posts</span>
            <span><b>~${Math.round(list.length/30)}</b> per day</span>
          </div>
        </div>
        <div class="actions">
          <button class="btn ${joined?'ghost':'primary'}" onclick="toggleCommunity('${c.id}')">${joined?'✓ Joined':'+ Join community'}</button>
        </div>
      </div>
    </div>
    <div class="feed">
      ${list.length===0?'<div class="empty">No posts yet.</div>':list.map(renderFeedItem).join('')}
    </div>
  `);
}

/* ─── POST DETAIL ──────────────────────────────────────────────────── */
function renderPostDetail(id){
  const p = postById(id);
  if(!p) return renderShell('<div class="empty">Post not found.</div>');
  const au = userById(p.authorId);
  const c = comById(p.communityId);
  const liked = likes[session.userId+':'+p.id];
  const cms = comments.filter(cm=>cm.postId===p.id);
  const roots = cms.filter(c=>!c.parentId);

  function commentNode(cm){
    const au = userById(cm.authorId);
    const replies = cms.filter(r=>r.parentId===cm.id);
    return `
      <div class="comment">
        <div class="top">
          <div class="av-sm">${esc(au.avatar)}</div>
          <span class="nm">${esc(au.name)}</span>${au.verified?'<span class="verified">✓</span>':''}
          <span>· ${timeAgo(cm.createdAt)}</span>
        </div>
        <div class="body">${esc(cm.body)}</div>
        <div class="actions"><span>♡ ${cm.likes}</span><span>Reply</span></div>
        ${replies.length>0?`<div style="margin-left:24px;border-left:2px solid var(--line);padding-left:18px;margin-top:8px">${replies.map(commentNode).join('')}</div>`:''}
      </div>`;
  }

  return renderShell(`
    <div class="post-detail">
      <div style="margin-bottom:14px">
        <a onclick="go('#/c/${encodeURIComponent(c.slug)}')" class="pill brand-soft role" style="cursor:pointer">${esc(c.slug)}</a>
      </div>
      <h1>${esc(p.title)}</h1>
      <div class="head">
        <div class="av-sm">${esc(au.avatar)}</div>
        <span class="nm" onclick="go('#/u/${au.id}')" style="cursor:pointer">${esc(au.name)}</span>${au.verified?'<span class="verified">✓</span>':''}
        <span>· ${timeAgo(p.createdAt)}</span>
      </div>
      ${p.kind==='IMAGE'?`<div class="body-img">📈 chart screenshot</div>`:''}
      <div class="body">${esc(p.body)}</div>
      <div class="actions-bar">
        <span class="like ${liked?'on':''}" onclick="toggleLike('${p.id}')">${liked?'♥':'♡'} ${p.likes+(liked?1:0)}</span>
        <span class="like">💬 ${cms.length}</span>
        <span class="like" onclick="flash('Shared')">↗ Share</span>
        <span class="like" onclick="flash('Saved')">⌥ Save</span>
      </div>
      <div class="comments">
        <h2>${cms.length} comments</h2>
        <div class="field">
          <textarea id="newComment" placeholder="What do you think?"></textarea>
          <div style="display:flex;justify-content:flex-end;margin-top:8px"><button class="btn primary" onclick="postComment('${p.id}')">Comment</button></div>
        </div>
        ${roots.length===0?'<div class="empty">Be the first to comment.</div>':roots.map(commentNode).join('')}
      </div>
    </div>
  `);
}

/* ─── PROP FIRMS PAGE ──────────────────────────────────────────────── */
function renderFirmsPage(){
  const sorted = [...firms].sort((a,b)=>{
    if(a.listingTier==='FEATURED'&&b.listingTier!=='FEATURED')return -1;
    if(b.listingTier==='FEATURED'&&a.listingTier!=='FEATURED')return 1;
    return b.rating-a.rating;
  });
  return renderShell(`
    <div class="eyebrow">Get funded</div>
    <h1>Prop firms directory</h1>
    <p class="lead">Compare ${firms.length} prop firms by rating, payout speed, refund policy, and verified community reviews. Featured listings are paid; community reviews are not.</p>
    <div style="display:flex;flex-direction:column;gap:12px">
      ${sorted.map(renderFirmRow).join('')}
    </div>
  `);
}

/* ─── FIRM DETAIL ──────────────────────────────────────────────────── */
function renderFirmDetail(slug){
  const f = firmBySlug(slug);
  if(!f) return renderShell('<div class="empty">Firm not found.</div>');
  const rs = reviewsFor('FIRM', f.id);
  const r = avgRating(rs)||f.rating;
  const tab = (route.split('?tab=')[1])||'overview';

  return renderShell(`
    <div class="profile-hero">
      <div class="cover ${f.tint||''}"></div>
      <div class="body">
        <div class="av-lg firm">${f.mark}</div>
        <h1>${esc(f.name)}${f.listingTier==='FEATURED'?'<span class="pill brand-soft role">Featured</span>':''}</h1>
        <div class="handle">${esc(f.website)} · ${esc(f.hq)}</div>
        <div class="tagline">${esc(f.tagline)}</div>
        <div class="chips">
          <span class="pill brand-soft">${stars(r)} ${r.toFixed(1)} · ${rs.length||f.reviewCount} reviews</span>
          <span class="pill">Founded ${f.founded}</span>
          ${f.promo?`<span class="pill amber">🔥 ${esc(f.promo)}</span>`:''}
        </div>
        <div class="ctas">
          <button class="btn ghost">Save</button>
          <button class="btn primary">Visit website →</button>
        </div>
      </div>
    </div>

    <div class="stat-bar">
      <div class="it"><div class="l">Rating</div><div class="v gold">${r.toFixed(1)}</div></div>
      <div class="it"><div class="l">Accounts</div><div class="v">${esc(f.accounts.split(' ')[0])}</div></div>
      <div class="it"><div class="l">Payout speed</div><div class="v brand">${esc(f.payoutDays.split('–')[0].trim())}</div></div>
      <div class="it"><div class="l">Profit split</div><div class="v brand">${f.payoutSplit}%</div></div>
      <div class="it"><div class="l">Reviews</div><div class="v">${rs.length||f.reviewCount}</div></div>
    </div>

    <div class="tabs">
      <a class="${tab==='overview'?'active':''}" onclick="go('#/firm/${slug}?tab=overview')">Overview</a>
      <a class="${tab==='accounts'?'active':''}" onclick="go('#/firm/${slug}?tab=accounts')">Account types & pricing</a>
      <a class="${tab==='reviews'?'active':''}" onclick="go('#/firm/${slug}?tab=reviews')">Reviews (${rs.length||f.reviewCount})</a>
    </div>

    ${tab==='accounts'?`
      <div class="grid-2">
        ${f.accountTypes.length===0?'<div class="empty">Detailed pricing not available yet.</div>':f.accountTypes.map(at=>`
          <div class="card">
            <h3>${esc(at.name)}</h3>
            <p style="color:var(--muted);font-size:13px;margin:0 0 18px">Range ${esc(at.size)}</p>
            <div style="display:grid;grid-template-columns:1fr 1fr;gap:14px;margin-bottom:18px">
              <div><div style="font-size:10.5px;letter-spacing:.14em;text-transform:uppercase;color:var(--muted);font-weight:600;margin-bottom:3px">Daily DD</div><div class="mono" style="font-size:18px;font-weight:700">${esc(at.daily)}</div></div>
              <div><div style="font-size:10.5px;letter-spacing:.14em;text-transform:uppercase;color:var(--muted);font-weight:600;margin-bottom:3px">Max DD</div><div class="mono" style="font-size:18px;font-weight:700">${esc(at.max)}</div></div>
              <div><div style="font-size:10.5px;letter-spacing:.14em;text-transform:uppercase;color:var(--muted);font-weight:600;margin-bottom:3px">Profit split</div><div class="mono" style="font-size:18px;font-weight:700;color:var(--brand)">${esc(at.split)}</div></div>
              <div><div style="font-size:10.5px;letter-spacing:.14em;text-transform:uppercase;color:var(--muted);font-weight:600;margin-bottom:3px">Price</div><div class="mono" style="font-size:18px;font-weight:700">${esc(at.price)}</div></div>
            </div>
            <button class="btn primary" style="width:100%">Start challenge →</button>
          </div>`).join('')}
      </div>
    `:tab==='reviews'?`
      <div class="grid-2" style="margin-bottom:18px">
        ${rs.length===0?'<div class="empty">No reviews yet. Be the first.</div>':rs.map(renderReviewCard).join('')}
      </div>
      <button class="btn primary" onclick="openReview('FIRM','${f.id}')">+ Write a review</button>
    `:`
      <div class="story">
        <div class="story-main">
          <div class="eyebrow">About the firm</div>
          <h3>The story</h3>
          ${f.storyHtml||`<p>${esc(f.tagline)}</p>`}
          <h3>Why traders pick ${esc(f.name)}</h3>
          <p>Strong community ratings, ${esc(f.payoutDays)} payout windows, and a ${f.payoutSplit}% profit split put ${esc(f.name)} in the top tier of prop firms for 2026. Read the reviews tab for unfiltered community feedback.</p>
        </div>
        <div class="story-side">
          <div class="card">
            <h3>Quick facts</h3>
            <div style="display:flex;flex-direction:column;gap:11px;margin-top:14px">
              <div style="display:flex;justify-content:space-between;font-size:13px"><span style="color:var(--muted)">Founded</span><b>${f.founded}</b></div>
              <div style="display:flex;justify-content:space-between;font-size:13px"><span style="color:var(--muted)">HQ</span><b>${esc(f.hq)}</b></div>
              <div style="display:flex;justify-content:space-between;font-size:13px"><span style="color:var(--muted)">Refund policy</span><b>${esc(f.refund)}</b></div>
              <div style="display:flex;justify-content:space-between;font-size:13px"><span style="color:var(--muted)">Payout speed</span><b>${esc(f.payoutDays)}</b></div>
              <div style="display:flex;justify-content:space-between;font-size:13px"><span style="color:var(--muted)">Profit split</span><b>${f.payoutSplit}%</b></div>
            </div>
          </div>
          <div class="card">
            <h3>Links</h3>
            <div class="links">
              <a href="https://${esc(f.website)}" target="_blank">Website <span>↗</span></a>
              <a onclick="openReview('FIRM','${f.id}')">Write a review <span>+</span></a>
            </div>
          </div>
        </div>
      </div>
    `}
  `);
}

/* ─── INFLUENCERS PAGE ─────────────────────────────────────────────── */
function renderInfluencersPage(){
  const list = users.filter(u=>u.role==='INFLUENCER'||u.role==='ANALYST');
  return renderShell(`
    <div class="eyebrow">Follow</div>
    <h1>Influencers & creators</h1>
    <p class="lead">Trading commentators, market voices, and creators worth following. Subscribe to their content tiers or just follow for free.</p>
    <div class="grid-4">
      ${list.map(u=>renderCreatorCard(u)).join('')}
    </div>
  `);
}

/* ─── GURUS PAGE ───────────────────────────────────────────────────── */
function renderGurusPage(){
  const list = users.filter(u=>u.role==='GURU');
  return renderShell(`
    <div class="eyebrow">Learn</div>
    <h1>Trading gurus & teachers</h1>
    <p class="lead">The people who teach. Real backgrounds, actual courses, verified students, public reviews. No fake gurus from Instagram.</p>
    <div class="grid-3">
      ${list.map(u=>{
        const cs = courses.filter(c=>c.authorId===u.id);
        const rs = reviewsFor('USER',u.id);
        return `
          <div class="card hov" onclick="go('#/u/${u.id}')">
            <div style="display:flex;gap:14px;align-items:center;margin-bottom:14px">
              <div class="av-lg" style="width:64px;height:64px;font-size:22px;border:0;margin:0">${esc(u.avatar)}</div>
              <div>
                <div style="font-size:17px;font-weight:700;letter-spacing:-.015em;display:flex;align-items:center;gap:5px">${esc(u.name)}${u.verified?'<span class="verified">✓</span>':''}</div>
                <div style="font-size:12px;color:var(--muted);font-family:'JetBrains Mono'">${esc(u.handle)}</div>
              </div>
            </div>
            <div style="font-size:13.5px;color:var(--ink-2);line-height:1.55;margin-bottom:14px">${esc(u.tagline||u.bio)}</div>
            <div style="display:flex;gap:18px;font-size:12px;color:var(--muted);padding-top:14px;border-top:1px solid var(--line)">
              <span><b style="color:var(--ink);font-weight:600">${cs.length}</b> course${cs.length===1?'':'s'}</span>
              <span><b style="color:var(--ink);font-weight:600">${fmtCount(u.students)}</b> students</span>
              <span style="color:var(--gold)">${stars(u.rating)} <b style="color:var(--ink);font-weight:600">${u.rating}</b></span>
            </div>
          </div>`;
      }).join('')}
    </div>
  `);
}

/* ─── USER PROFILE ─────────────────────────────────────────────────── */
function renderProfile(uid){
  const u = userById(uid);
  if(!u) return renderShell('<div class="empty">User not found.</div>');
  const isFirm = u.role==='PROP_FIRM';
  const cs = courses.filter(c=>c.authorId===uid);
  const ps = posts.filter(p=>p.authorId===uid);
  const rs = reviewsFor('USER',uid);
  const ts = tiersFor(uid);
  const following = isFollowing(uid);
  const me = u.id===session.userId;
  const tab = (route.split('?tab=')[1])||'story';

  const tabsByRole = {
    GURU:[['story','Story'],['courses','Courses'],['subscriptions','Subscriptions'],['reviews','Reviews']],
    INFLUENCER:[['story','About'],['posts','Posts'],['subscriptions','Subscriptions'],['reviews','Reviews']],
    ANALYST:[['story','About'],['posts','Posts'],['subscriptions','Subscriptions'],['reviews','Reviews']],
    TRADER:[['story','About'],['posts','Posts'],['reviews','Reviews']],
    BRAND:[['story','About'],['posts','Posts'],['reviews','Reviews']],
    PROP_FIRM:[['story','About'],['posts','Posts'],['reviews','Reviews']],
  };
  const visibleTabs = tabsByRole[u.role]||tabsByRole.TRADER;

  return renderShell(`
    <div class="profile-hero">
      <div class="cover ${u.tint||''}"></div>
      <div class="body">
        <div class="av-lg ${isFirm?'firm':''}">${esc(u.avatar)}</div>
        <h1>${esc(u.name)}${u.verified?'<span class="verified">✓</span>':''}</h1>
        <div class="handle">${esc(u.handle)}${u.location?' · '+esc(u.location):''}${u.funded?' · <span class="pill brand-soft role" style="vertical-align:middle">Funded trader</span>':''}</div>
        <div class="tagline">${esc(u.tagline||u.bio)}</div>
        <div class="chips">
          <span class="pill role brand-soft">${ROLE_LABELS[u.role]}</span>
          ${u.followers?`<span class="pill"><b>${fmtCount(u.followers)}</b> &nbsp;followers</span>`:''}
          ${u.students?`<span class="pill"><b>${fmtCount(u.students)}</b> &nbsp;students</span>`:''}
          ${u.rating?`<span class="pill gold">${stars(u.rating)} ${u.rating}</span>`:''}
        </div>
        ${!me?`
        <div class="ctas">
          <button class="btn ghost">DM</button>
          <button class="btn ${following?'':'primary'}" onclick="toggleFollow('${u.id}')">${following?'✓ Following':'+ Follow'}</button>
        </div>`:`<div class="ctas"><button class="btn ghost">Edit profile</button></div>`}
      </div>
    </div>

    <div class="stat-bar">
      <div class="it"><div class="l">Karma</div><div class="v">${fmtCount(u.karma)}</div></div>
      <div class="it"><div class="l">Posts</div><div class="v">${ps.length}</div></div>
      <div class="it"><div class="l">Courses</div><div class="v">${cs.length}</div></div>
      <div class="it"><div class="l">Rating</div><div class="v gold">${u.rating||'—'}</div></div>
      <div class="it"><div class="l">On TradingBay</div><div class="v">${timeAgo(u.joinedAt).replace(' ago','')}</div></div>
    </div>

    <div class="tabs">
      ${visibleTabs.map(([k,l])=>`<a class="${tab===k?'active':''}" onclick="go('#/u/${u.id}?tab=${k}')">${l}</a>`).join('')}
    </div>

    ${tab==='story'?`
      <div class="story">
        <div class="story-main">
          ${u.storyHtml?u.storyHtml:`<p>${esc(u.bio||'No story yet.')}</p>`}
        </div>
        <div class="story-side">
          ${ts.length>0?`
            <div class="card">
              <h3>Subscribe to ${esc(u.name.split(' ')[0])}</h3>
              <p style="font-size:12.5px;color:var(--muted);margin:6px 0 12px">From ${fmtPrice((ts.find(t=>t.priceCents>0)||ts[0]).priceCents)}${(ts.find(t=>t.priceCents>0)?.period)?'/'+(ts.find(t=>t.priceCents>0).period):''}</p>
              <button class="btn primary" style="width:100%" onclick="go('#/u/${u.id}?tab=subscriptions')">See tiers →</button>
            </div>`:''}
          ${cs.length>0?`
            <div class="card">
              <h3>Courses by ${esc(u.name.split(' ')[0])}</h3>
              <div style="display:flex;flex-direction:column;gap:9px;margin-top:14px">
                ${cs.slice(0,3).map(c=>`
                  <a onclick="go('#/course/${c.id}')" style="padding:11px 12px;background:var(--bg-2);border:1px solid var(--line);border-radius:10px;display:block;cursor:pointer">
                    <div style="font-size:12.5px;font-weight:600;color:var(--ink);margin-bottom:3px">${esc(c.title)}</div>
                    <div style="font-size:11.5px;color:var(--brand);font-family:'JetBrains Mono';font-weight:600">${fmtPrice(c.priceCents)}</div>
                  </a>`).join('')}
              </div>
            </div>`:''}
          ${(u.website||u.twitter||u.youtube)?`
            <div class="card">
              <h3>Links</h3>
              <div class="links">
                ${u.website?`<a href="https://${esc(u.website)}" target="_blank">${esc(u.website)} <span>↗</span></a>`:''}
                ${u.twitter?`<a href="https://${esc(u.twitter)}" target="_blank">X / Twitter <span>↗</span></a>`:''}
                ${u.youtube?`<a href="https://${esc(u.youtube)}" target="_blank">YouTube <span>↗</span></a>`:''}
              </div>
            </div>`:''}
        </div>
      </div>
    `:tab==='courses'?`
      ${cs.length===0?'<div class="empty">No courses yet.</div>':`<div class="grid-3">${cs.map(renderCourseCard).join('')}</div>`}
    `:tab==='subscriptions'?`
      ${ts.length===0?'<div class="empty">No subscription tiers yet.</div>':`
        <div style="max-width:880px">
          <p class="lead">Pick the level that fits. Cancel anytime. All tiers include access to ${esc(u.name)}'s public posts.</p>
          <div class="tiers">
            ${ts.map(t=>`
              <div class="tier ${t.featured?'featured':''}">
                <div class="name">${esc(t.name)}</div>
                <div class="desc">${esc(t.desc)}</div>
                <div class="price">${fmtPrice(t.priceCents)}</div>
                <div class="per">${t.priceCents>0?'per '+esc(t.period):esc(t.period)}</div>
                <ul>${t.features.map(f=>`<li>${esc(f)}</li>`).join('')}</ul>
                <button class="btn ${t.featured?'primary':'ghost'}" onclick="subscribeTier('${t.id}')">${t.priceCents>0?'Subscribe':'Get free access'}</button>
              </div>`).join('')}
          </div>
        </div>`}
    `:tab==='reviews'?`
      <div class="grid-2" style="margin-bottom:18px">
        ${rs.length===0?'<div class="empty">No reviews yet.</div>':rs.map(renderReviewCard).join('')}
      </div>
      ${!me?`<button class="btn primary" onclick="openReview('USER','${u.id}')">+ Write a review for ${esc(u.name)}</button>`:''}
    `:tab==='posts'?`
      ${ps.length===0?'<div class="empty">No posts yet.</div>':`<div class="feed">${ps.map(renderFeedItem).join('')}</div>`}
    `:''}
  `);
}

function renderCourseCard(c){
  const au = userById(c.authorId);
  return `
    <div class="course-card" onclick="go('#/course/${c.id}')">
      <div class="hero ${c.tint||'h1'}">${esc(c.level)}</div>
      <div class="body">
        <div class="name">${esc(c.title)}</div>
        <div class="by">by <b>${esc(au?.name||'?')}</b>${au?.verified?'<span class="verified">✓</span>':''} · ${c.durationHours}h</div>
        <div class="foot">
          <span class="price">${fmtPrice(c.priceCents)}</span>
          <span class="rate">${stars(c.rating)} <span class="n">${c.rating} (${c.reviewCount})</span></span>
        </div>
      </div>
    </div>`;
}

function renderReviewCard(r){
  const au = userById(r.authorId);
  return `
    <div class="review">
      <div class="head">
        <div class="av-sm">${esc(au?.avatar||'?')}</div>
        <div class="who">
          <div class="nm">${esc(au?.name||'?')}${au?.verified?'<span class="verified">✓</span>':''}${r.verifiedPurchase?'<span class="verified-tag">Verified purchase</span>':''}</div>
          <div class="dt">${timeAgo(r.createdAt)}</div>
        </div>
      </div>
      <div class="stars">${stars(r.rating)}</div>
      <div class="body">${esc(r.body)}</div>
    </div>`;
}

/* ─── COURSE DETAIL ────────────────────────────────────────────────── */
function renderCourseDetail(id){
  const c = courseById(id);
  if(!c) return renderShell('<div class="empty">Course not found.</div>');
  const au = userById(c.authorId);
  return renderShell(`
    <div style="display:grid;grid-template-columns:1fr 360px;gap:30px">
      <div>
        <div class="course-card" style="cursor:default;margin-bottom:22px">
          <div class="hero ${c.tint}" style="height:220px;font-size:13px">${esc(c.level)}</div>
        </div>
        <h1 style="font-size:30px">${esc(c.title)}</h1>
        <p class="lead" style="font-size:16px">${esc(c.tagline)}</p>
        <div style="display:flex;align-items:center;gap:14px;font-size:13px;color:var(--muted);margin-bottom:24px">
          <span>By <b style="color:var(--ink)" onclick="go('#/u/${au.id}')" style="cursor:pointer">${esc(au.name)}</b>${au.verified?'<span class="verified">✓</span>':''}</span>
          <span class="rate" style="color:var(--gold)">${stars(c.rating)} ${c.rating} (${c.reviewCount})</span>
          <span>${fmtCount(c.sales)} students</span>
        </div>
        <div style="font-size:14.5px;line-height:1.7;color:var(--ink-2)">${esc(c.description)}</div>
      </div>
      <div>
        <div class="card" style="position:sticky;top:90px">
          <div style="font-size:36px;font-weight:800;font-family:'JetBrains Mono';color:var(--brand);letter-spacing:-.02em;line-height:1">${fmtPrice(c.priceCents)}</div>
          <div style="font-size:12px;color:var(--muted);margin:6px 0 20px">One-time · lifetime access</div>
          <button class="btn primary lg" style="width:100%" onclick="buyCourse('${c.id}')">Buy course</button>
          <button class="btn ghost" style="width:100%;margin-top:8px">Add to wishlist</button>
          <hr/>
          <div style="display:flex;flex-direction:column;gap:11px;font-size:13px">
            <div style="display:flex;justify-content:space-between"><span style="color:var(--muted)">Duration</span><b>${c.durationHours} hours</b></div>
            <div style="display:flex;justify-content:space-between"><span style="color:var(--muted)">Students</span><b>${fmtCount(c.sales)}</b></div>
            <div style="display:flex;justify-content:space-between"><span style="color:var(--muted)">Level</span><b>${esc(c.level)}</b></div>
            <div style="display:flex;justify-content:space-between"><span style="color:var(--muted)">Guarantee</span><b>30-day refund</b></div>
          </div>
        </div>
      </div>
    </div>
  `);
}

/* ─── modals ───────────────────────────────────────────────────────── */
let composeOpen=false, reviewOpen=null;
function openCompose(){composeOpen=true;render();}
function closeCompose(){composeOpen=false;render();}
function renderCompose(){
  return `
    <div class="modal-bg" onclick="if(event.target===this)closeCompose()">
      <div class="modal">
        <div class="modal-h"><h3>Create a post</h3><span class="x" onclick="closeCompose()">×</span></div>
        <div class="modal-b">
          <div class="field"><label>Community</label>
            <select id="cmpCom">${communities.map(c=>`<option value="${c.id}" ${isInCommunity(c.id)?'selected':''}>${esc(c.slug)}</option>`).join('')}</select>
          </div>
          <div class="field"><label>Title</label><input id="cmpTitle" placeholder="What's the post about?" /></div>
          <div class="field"><label>Body</label><textarea id="cmpBody" placeholder="Add details, charts, your setup…"></textarea></div>
        </div>
        <div class="modal-f">
          <button class="btn ghost" onclick="closeCompose()">Cancel</button>
          <button class="btn primary" onclick="submitCompose()">Post</button>
        </div>
      </div>
    </div>`;
}
function openReview(type,id){reviewOpen={type,id,rating:5};render();}
function closeReview(){reviewOpen=null;render();}
function renderReviewModal(){
  const target = reviewOpen.type==='USER'?userById(reviewOpen.id):firms.find(f=>f.id===reviewOpen.id);
  return `
    <div class="modal-bg" onclick="if(event.target===this)closeReview()">
      <div class="modal">
        <div class="modal-h"><h3>Write a review for ${esc(target?.name)}</h3><span class="x" onclick="closeReview()">×</span></div>
        <div class="modal-b">
          <div class="field"><label>Rating</label>
            <div style="display:flex;gap:6px;font-size:28px;cursor:pointer">
              ${[1,2,3,4,5].map(n=>`<span onclick="setRating(${n})" style="color:${n<=reviewOpen.rating?'var(--gold)':'var(--faint)'}">★</span>`).join('')}
            </div>
          </div>
          <div class="field"><label>Your review</label><textarea id="rvBody" placeholder="What was your experience?"></textarea></div>
        </div>
        <div class="modal-f">
          <button class="btn ghost" onclick="closeReview()">Cancel</button>
          <button class="btn primary" onclick="submitReview()">Submit</button>
        </div>
      </div>
    </div>`;
}
function setRating(n){reviewOpen.rating=n;render();}

/* ─── actions ──────────────────────────────────────────────────────── */
function signOut(){session.userId=null;saveState();render();}
function copyCode(code){navigator.clipboard?.writeText(code);flash('Code copied · '+code);}
function signInAs(uid){session.userId=uid;saveState();go('#/home');}
function signUp(role){
  const name = prompt(`Welcome! What name should we show on your TradingBay ${ROLE_LABELS[role]} profile?`);
  if(!name) return;
  const id='u-new-'+Date.now().toString(36);
  const handle='@'+name.toLowerCase().replace(/[^a-z0-9]+/g,'').slice(0,15);
  const initials=name.split(/\s+/).map(s=>s[0]).slice(0,2).join('').toUpperCase();
  users.unshift({id,name,handle,role,avatar:initials,bio:'New on TradingBay.',tagline:'',followers:0,students:0,karma:0,verified:false,joinedAt:new Date().toISOString().slice(0,10),funded:false,tint:'c2',website:'',twitter:'',storyHtml:``});
  signInAs(id);
}
function toggleLike(id){
  const k = session.userId+':'+id;
  if(likes[k]){ delete likes[k]; const p=postById(id); if(p)p.likes--; }
  else { likes[k]=1; const p=postById(id); if(p)p.likes++; }
  saveState(); render();
}
function toggleFollow(id){
  const k=session.userId+':'+id;
  if(follows.has(k)) follows.delete(k); else follows.add(k);
  saveState(); render(); flash(follows.has(k)?'Followed':'Unfollowed');
}
function toggleCommunity(cid){
  const k=session.userId+':'+cid;
  if(joinedCommunities.has(k)){joinedCommunities.delete(k);flash('Left community');}
  else{joinedCommunities.add(k);flash('Joined community');}
  saveState(); render();
}
function submitCompose(){
  const cid=document.getElementById('cmpCom').value;
  const title=document.getElementById('cmpTitle').value.trim();
  const body=document.getElementById('cmpBody').value.trim();
  if(!title||!body){flash('Title and body required');return;}
  posts.unshift({id:'p-'+Date.now().toString(36),authorId:session.userId,communityId:cid,kind:'TEXT',tint:Math.floor(Math.random()*4)+1,title,body,likes:1,createdAt:new Date().toISOString()});
  closeCompose(); flash('Posted!'); saveState();
}
function postComment(pid){
  const body=document.getElementById('newComment')?.value?.trim();
  if(!body)return;
  comments.push({id:'cm-'+Date.now().toString(36),postId:pid,authorId:session.userId,body,likes:1,createdAt:new Date().toISOString(),parentId:null});
  saveState(); render();
}
function submitReview(){
  const body=document.getElementById('rvBody').value.trim();
  if(!body){flash('Add a review body');return;}
  reviews.unshift({id:'rv-'+Date.now().toString(36),targetType:reviewOpen.type,targetId:reviewOpen.id,authorId:session.userId,rating:reviewOpen.rating,verifiedPurchase:true,createdAt:new Date().toISOString().slice(0,10),body});
  closeReview(); flash('Review submitted'); saveState();
}
function buyCourse(id){if(!confirm('Buy this course (demo)?'))return;flash('Course purchased! Lifetime access added.');}
function subscribeTier(id){const t=tiers.find(x=>x.id===id);if(t.priceCents===0)flash('Free tier added');else if(confirm(`Subscribe to ${t.name} (${fmtPrice(t.priceCents)}/${t.period})?`))flash('Subscribed!');}

/* ─── sign-in ──────────────────────────────────────────────────────── */
function renderSignIn(){
  return `
    <div class="signin-shell">
      <div class="signin">
        <div class="brand"><span class="m">TB</span><span>Trading<b>Bay</b></span></div>
        <h1>Where traders meet.</h1>
        <p class="sub">The home for traders. Communities, prop firms, gurus, influencers — all in one clean place.</p>
        <h3>Sign up as</h3>
        <div class="roles">
          ${[['TRADER','Trader','Learn, post, vote, follow.'],['GURU','Guru / Teacher','Sell courses & coaching.'],['INFLUENCER','Influencer','Build following, share posts.'],['PROP_FIRM','Prop firm','List your firm.'],['ANALYST','Analyst','Newsletter, research, calls.'],['BRAND','Brand','Tools, signals, services.']].map(([r,n,d])=>`<button class="r" onclick="signUp('${r}')"><b>${n}</b><span>${d}</span></button>`).join('')}
        </div>
        <h3>Or jump in as a demo user</h3>
        <div class="demo-users">
          ${users.map(u=>`<button onclick="signInAs('${u.id}')"><span class="av-sm">${esc(u.avatar)}</span><span style="flex:1"><b style="color:var(--ink)">${esc(u.name)}</b> <span>${esc(u.handle)} · ${ROLE_LABELS[u.role]}</span></span>${u.verified?'<span class="verified">✓</span>':''}</button>`).join('')}
        </div>
      </div>
    </div>`;
}

/* ─── master render ────────────────────────────────────────────────── */
let __loaded=false;
function render(){
  if(!__loaded){__loaded=true;loadState();}
  const root=document.getElementById('app');
  if(!session.userId){root.innerHTML=renderSignIn();return;}

  let body='';
  const path = route.split('?')[0];
  if(path==='#/home'||path==='#'||path===''){body=renderHome();}
  else if(path==='#/communities'){body=renderCommunitiesPage();}
  else if(path==='#/firms'){body=renderFirmsPage();}
  else if(path==='#/influencers'){body=renderInfluencersPage();}
  else if(path==='#/gurus'){body=renderGurusPage();}
  else if(path==='#/platforms'){body=renderPlatformsPage();}
  else if(path.startsWith('#/platform/')){body=renderPlatformDetail(path.slice(11));}
  else if(path.startsWith('#/c/')){body=renderCommunity(path.slice(4));}
  else if(path.startsWith('#/p/')){body=renderPostDetail(path.slice(4));}
  else if(path.startsWith('#/u/')){body=renderProfile(path.slice(4));}
  else if(path.startsWith('#/firm/')){body=renderFirmDetail(path.slice(7));}
  else if(path.startsWith('#/course/')){body=renderCourseDetail(path.slice(9));}
  else if(path.startsWith('#/profile/')){body=renderProfile(path.slice(10));}
  else{body=renderHome();}
  root.innerHTML=body;
}

render();
</script>
</body>
</html>
