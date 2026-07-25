<!DOCTYPE html>
<html lang="ku" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1,maximum-scale=1,user-scalable=no,viewport-fit=cover">
<title>مێنیۆی خواردن</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Noto+Sans+Arabic:wght@300;400;500;600;700;800;900&display=swap" rel="stylesheet">
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
<style>
:root{
--bg:#0b0d14;--bg2:#12151f;--bg3:#1a1e2e;--bg4:#232840;
--glass:rgba(255,255,255,0.04);--glass2:rgba(255,255,255,0.07);--glass3:rgba(255,255,255,0.12);
--border:rgba(255,255,255,0.08);--border2:rgba(255,255,255,0.15);
--text:#eaecf2;--text2:#8b90a5;--text3:#555a70;
--accent:#f0a500;--accent2:#ff6b35;--accent3:#00c9a7;
--danger:#ef4444;--success:#22c55e;
--nav-h:82px;--radius:18px;--radius-sm:12px;
--glass-blur:24px;
}
.light-mode{
--bg:#f2f3f7;--bg2:#ffffff;--bg3:#e8e9ef;--bg4:#dde0e8;
--glass:rgba(0,0,0,0.03);--glass2:rgba(0,0,0,0.06);--glass3:rgba(0,0,0,0.1);
--border:rgba(0,0,0,0.08);--border2:rgba(0,0,0,0.15);
--text:#1a1c28;--text2:#5a5e72;--text3:#8b8fa3;
}
*{margin:0;padding:0;box-sizing:border-box;-webkit-tap-highlight-color:transparent}
html,body{height:100%;overflow:hidden;font-family:'Noto Sans Arabic',sans-serif;background:var(--bg);color:var(--text);user-select:none;-webkit-user-select:none}

.liquid-shape{position:fixed;border-radius:50%;filter:blur(100px);opacity:.22;pointer-events:none;z-index:0;will-change:transform}
.liquid-shape.a{width:500px;height:500px;background:var(--accent);top:-150px;right:-150px;animation:lsA 22s ease-in-out infinite}
.liquid-shape.b{width:400px;height:400px;background:var(--accent2);bottom:-100px;left:-100px;animation:lsB 26s ease-in-out infinite}
.liquid-shape.c{width:350px;height:350px;background:var(--accent3);top:40%;left:30%;animation:lsC 30s ease-in-out infinite}
@keyframes lsA{0%,100%{transform:translate(0,0) scale(1)}33%{transform:translate(-80px,60px) scale(1.15)}66%{transform:translate(40px,-40px) scale(.9)}}
@keyframes lsB{0%,100%{transform:translate(0,0) scale(1)}33%{transform:translate(60px,-80px) scale(1.1)}66%{transform:translate(-30px,50px) scale(.85)}}
@keyframes lsC{0%,100%{transform:translate(0,0) scale(1)}50%{transform:translate(-60px,70px) scale(1.2)}}

#app{position:relative;z-index:1;height:100%;display:flex;flex-direction:column}
header{position:fixed;top:0;left:0;right:0;z-index:100;display:flex;align-items:center;justify-content:space-between;padding:10px 18px;height:60px;background:var(--glass);backdrop-filter:blur(var(--glass-blur));-webkit-backdrop-filter:blur(var(--glass-blur));border-bottom:1px solid var(--border)}
.header-right{display:flex;align-items:center;gap:10px}
.header-left{display:flex;align-items:center;gap:6px}
.hdr-btn{width:38px;height:38px;border-radius:12px;border:1px solid var(--border);background:var(--glass2);color:var(--text);display:flex;align-items:center;justify-content:center;cursor:pointer;font-size:15px;transition:transform .2s;position:relative}
.hdr-btn:active{transform:scale(.92)}
.notif-badge{position:absolute;top:-4px;right:-4px;min-width:18px;height:18px;border-radius:9px;background:var(--danger);color:#fff;font-size:10px;font-weight:700;display:flex;align-items:center;justify-content:center;padding:0 4px}
.app-title{font-size:18px;font-weight:700;background:linear-gradient(135deg,var(--accent),var(--accent2));-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text}
.lang-btn{font-size:12px;font-weight:600;width:auto;padding:0 10px}

.pages-wrap{flex:1;margin-top:60px;margin-bottom:var(--nav-h);overflow:hidden;position:relative}
.page{position:absolute;top:0;left:0;right:0;bottom:0;overflow-y:auto;overflow-x:hidden;padding:16px;opacity:0;pointer-events:none;transition:opacity .2s;-webkit-overflow-scrolling:touch}
.page.active{opacity:1;pointer-events:auto}
.page::-webkit-scrollbar{width:3px}
.page::-webkit-scrollbar-thumb{background:var(--border2);border-radius:3px}

.glass-card{background:var(--glass2);backdrop-filter:blur(var(--glass-blur));-webkit-backdrop-filter:blur(var(--glass-blur));border:1px solid var(--border);border-radius:var(--radius);padding:16px;position:relative;overflow:hidden;transition:transform .2s}
.glass-card::before{content:'';position:absolute;top:0;left:0;right:0;height:1px;background:linear-gradient(90deg,transparent,rgba(255,255,255,.15),transparent);pointer-events:none}
.glass-card:active{transform:scale(.98)}

.welcome-container{display:flex;flex-direction:column;align-items:center;justify-content:center;min-height:100%;text-align:center;padding:20px}
.welcome-logo{width:110px;height:110px;border-radius:28px;background:linear-gradient(135deg,var(--accent),var(--accent2));display:flex;align-items:center;justify-content:center;font-size:48px;color:#000;margin-bottom:22px;box-shadow:0 12px 40px rgba(240,165,0,.3);animation:logoFloat 3s ease-in-out infinite}
@keyframes logoFloat{0%,100%{transform:translateY(0)}50%{transform:translateY(-8px)}}
.welcome-title{font-size:26px;font-weight:900;margin-bottom:8px}
.welcome-sub{font-size:14px;color:var(--text2);margin-bottom:32px;line-height:1.6;max-width:280px}
.welcome-enter{padding:15px 55px;border-radius:28px;border:none;background:linear-gradient(135deg,var(--accent),var(--accent2));color:#000;font-size:16px;font-weight:800;font-family:inherit;cursor:pointer;box-shadow:0 8px 30px rgba(240,165,0,.3);transition:transform .2s}
.welcome-enter:active{transform:scale(.95)}

.tables-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(130px,1fr));gap:12px;padding-bottom:20px}
.table-card{text-align:center;padding:18px 10px;cursor:pointer}
.table-card.occupied{border-color:var(--accent);background:rgba(240,165,0,.08)}
.table-card .t-icon{font-size:28px;margin-bottom:6px;transition:transform .3s}
.table-card:active .t-icon{transform:scale(1.12)}
.table-card .t-name{font-size:14px;font-weight:700;margin-bottom:3px}
.table-card .t-status{font-size:11px;color:var(--text2);font-weight:500}
.table-card.occupied .t-status{color:var(--accent)}

.menu-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(155px,1fr));gap:12px;padding-bottom:20px}
.menu-item{cursor:pointer;border-radius:var(--radius);overflow:hidden;padding:0}
.menu-item .mi-img{width:100%;height:120px;object-fit:cover;display:block;transition:transform .4s}
.menu-item:active .mi-img{transform:scale(1.06)}
.menu-item .mi-body{padding:10px}
.menu-item .mi-name{font-size:13px;font-weight:700;margin-bottom:3px;line-height:1.3}
.menu-item .mi-price{font-size:14px;font-weight:800;color:var(--accent)}
.menu-item .mi-note{font-size:11px;color:var(--text2);margin-top:3px;line-height:1.3;display:-webkit-box;-webkit-line-clamp:2;-webkit-box-orient:vertical;overflow:hidden}

.cat-tabs{display:flex;gap:8px;overflow-x:auto;padding-bottom:10px;margin-bottom:14px;-webkit-overflow-scrolling:touch}
.cat-tabs::-webkit-scrollbar{display:none}
.cat-tab{flex-shrink:0;padding:7px 16px;border-radius:22px;border:1px solid var(--border);background:var(--glass);color:var(--text2);font-size:12px;font-weight:600;cursor:pointer;transition:all .2s;white-space:nowrap}
.cat-tab.active{background:var(--accent);color:#000;border-color:var(--accent);box-shadow:0 4px 18px rgba(240,165,0,.25)}
.cat-tab:active{transform:scale(.95)}

.cart-section{margin-bottom:16px}
.cart-title{font-size:15px;font-weight:700;margin-bottom:10px;display:flex;align-items:center;gap:8px}
.cart-item{display:flex;align-items:center;gap:10px;padding:10px;border-radius:var(--radius-sm);background:var(--glass);margin-bottom:8px;border:1px solid var(--border)}
.cart-item img{width:48px;height:48px;border-radius:10px;object-fit:cover}
.cart-item .ci-info{flex:1;min-width:0}
.cart-item .ci-name{font-size:13px;font-weight:600;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.cart-item .ci-price{font-size:12px;color:var(--accent);font-weight:700}
.cart-item .ci-qty{display:flex;align-items:center;gap:6px}
.cart-item .ci-qty button{width:26px;height:26px;border-radius:7px;border:1px solid var(--border);background:var(--glass2);color:var(--text);font-size:12px;cursor:pointer;display:flex;align-items:center;justify-content:center}
.cart-item .ci-qty span{font-weight:700;min-width:18px;text-align:center;font-size:13px}
.cart-item .ci-del{color:var(--danger);cursor:pointer;font-size:14px;padding:4px}
.submit-order-btn{width:100%;padding:13px;border-radius:var(--radius);border:none;background:linear-gradient(135deg,var(--accent),var(--accent2));color:#000;font-size:15px;font-weight:800;font-family:inherit;cursor:pointer;box-shadow:0 6px 25px rgba(240,165,0,.25);margin-top:10px}
.submit-order-btn:active{transform:scale(.97)}
.total-bar{display:flex;justify-content:space-between;align-items:center;padding:10px 0;border-top:1px solid var(--border);margin-top:6px}
.total-bar .tl{font-size:13px;font-weight:600;color:var(--text2)}
.total-bar .tv{font-size:18px;font-weight:900;color:var(--accent)}

.notif-item{padding:12px;border-radius:var(--radius-sm);background:var(--glass);border:1px solid var(--border);margin-bottom:8px}
.notif-item .ni-head{display:flex;justify-content:space-between;align-items:center;margin-bottom:5px}
.notif-item .ni-table{font-weight:700;font-size:13px;color:var(--accent)}
.notif-item .ni-time{font-size:11px;color:var(--text3)}
.notif-item .ni-items{font-size:12px;color:var(--text2);line-height:1.5}
.ni-status{display:inline-block;padding:2px 10px;border-radius:16px;font-size:10px;font-weight:700;margin-top:5px}
.ni-status.new{background:rgba(240,165,0,.15);color:var(--accent)}
.ni-status.preparing{background:rgba(0,201,167,.15);color:var(--accent3)}
.ni-status.done{background:rgba(34,197,94,.15);color:var(--success)}
.empty-state{text-align:center;padding:50px 20px;color:var(--text3)}
.empty-state i{font-size:42px;margin-bottom:14px;opacity:.4}
.empty-state p{font-size:14px}

.admin-tabs{display:flex;flex-wrap:wrap;gap:6px;margin-bottom:16px}
.admin-tab{flex:1 1 auto;min-width:0;padding:10px 6px;text-align:center;font-size:11px;font-weight:700;cursor:pointer;color:var(--text2);border:1px solid var(--border);background:var(--glass);border-radius:var(--radius-sm);font-family:inherit;transition:all .2s;white-space:nowrap}
.admin-tab.active{background:var(--accent);color:#000;border-color:var(--accent)}
.admin-tab:active{opacity:.8}
.admin-tab i{display:block;font-size:16px;margin-bottom:3px}

.admin-mi{display:flex;align-items:stretch;gap:0;border-radius:var(--radius);overflow:hidden;background:var(--glass);border:1px solid var(--border);margin-bottom:10px;min-height:80px}
.admin-mi-img{width:90px;min-height:80px;flex-shrink:0;object-fit:cover}
.admin-mi-body{flex:1;padding:10px 12px;display:flex;flex-direction:column;justify-content:center;min-width:0}
.admin-mi-name{font-size:14px;font-weight:700;margin-bottom:2px;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.admin-mi-meta{font-size:12px;color:var(--accent);font-weight:700}
.admin-mi-actions{display:flex;flex-direction:column;justify-content:center;gap:6px;padding:10px}
.admin-mi-actions button{width:38px;height:38px;border-radius:10px;border:1px solid var(--border);background:var(--glass2);color:var(--text);font-size:14px;cursor:pointer;display:flex;align-items:center;justify-content:center;transition:transform .15s}
.admin-mi-actions button:active{transform:scale(.9)}
.admin-mi-actions button.del-btn{color:var(--danger);border-color:rgba(239,68,68,.2)}

.admin-form{display:flex;flex-direction:column;gap:9px}
.form-group{display:flex;flex-direction:column;gap:3px}
.form-group label{font-size:11px;font-weight:600;color:var(--text2)}
.form-input{padding:10px 12px;border-radius:var(--radius-sm);border:1px solid var(--border);background:var(--glass);color:var(--text);font-family:inherit;font-size:13px;outline:none;transition:border .2s}
.form-input:focus{border-color:var(--accent)}
.form-select{appearance:none;background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='12' viewBox='0 0 24 24' fill='none' stroke='%238b90a5' stroke-width='2'%3E%3Cpath d='M6 9l6 6 6-6'/%3E%3C/svg%3E");background-repeat:no-repeat;background-position:left 12px center}
.img-upload{border:2px dashed var(--border2);border-radius:var(--radius-sm);padding:16px;text-align:center;cursor:pointer;color:var(--text2);font-size:12px;position:relative;overflow:hidden}
.img-upload input{position:absolute;inset:0;opacity:0;cursor:pointer}
.img-upload .preview-img{max-height:70px;border-radius:8px;margin-top:6px}
.admin-btn{padding:10px;border-radius:var(--radius-sm);border:none;font-family:inherit;font-size:13px;font-weight:700;cursor:pointer;transition:transform .15s}
.admin-btn:active{transform:scale(.97)}
.admin-btn.primary{background:var(--accent);color:#000}
.admin-btn.danger{background:rgba(239,68,68,.15);color:var(--danger);border:1px solid rgba(239,68,68,.2)}
.admin-btn.success{background:rgba(0,201,167,.15);color:var(--accent3);border:1px solid rgba(0,201,167,.2)}

.modal-overlay{position:fixed;inset:0;z-index:200;background:rgba(0,0,0,.6);backdrop-filter:blur(10px);-webkit-backdrop-filter:blur(10px);display:none;align-items:center;justify-content:center;padding:20px}
.modal-overlay.show{display:flex}
.modal-box{background:var(--bg3);border:1px solid var(--border2);border-radius:var(--radius);padding:26px;width:100%;max-width:340px}
.modal-box h3{font-size:17px;font-weight:800;margin-bottom:5px;text-align:center}
.modal-box p{font-size:12px;color:var(--text2);text-align:center;margin-bottom:16px}
.modal-box .form-input{text-align:center;margin-bottom:10px}
.modal-box .error-msg{color:var(--danger);font-size:12px;text-align:center;margin-bottom:6px;min-height:16px}

.detail-modal .modal-box{max-width:380px;padding:0;overflow:hidden}
.detail-img{width:100%;height:180px;object-fit:cover}
.detail-body{padding:18px}
.detail-body h3{font-size:18px;font-weight:800;margin-bottom:3px;text-align:right}
.detail-body .d-price{font-size:20px;font-weight:900;color:var(--accent);margin-bottom:6px}
.detail-body .d-note{font-size:12px;color:var(--text2);line-height:1.6;margin-bottom:14px}
.detail-qty{display:flex;align-items:center;gap:14px;justify-content:center;margin-bottom:14px}
.detail-qty button{width:38px;height:38px;border-radius:12px;border:1px solid var(--border);background:var(--glass2);color:var(--text);font-size:16px;cursor:pointer;display:flex;align-items:center;justify-content:center}
.detail-qty button:active{transform:scale(.9)}
.detail-qty span{font-size:20px;font-weight:900;min-width:28px;text-align:center}
.detail-add-btn{width:100%;padding:13px;border-radius:var(--radius);border:none;background:linear-gradient(135deg,var(--accent),var(--accent2));color:#000;font-size:15px;font-weight:800;font-family:inherit;cursor:pointer}
.detail-add-btn:active{transform:scale(.97)}

.order-note-input{width:100%;padding:10px;border-radius:var(--radius-sm);border:1px solid var(--border);background:var(--glass);color:var(--text);font-family:inherit;font-size:13px;resize:none;margin-top:6px;outline:none}
.order-note-input:focus{border-color:var(--accent)}

.back-btn{display:inline-flex;align-items:center;gap:6px;padding:7px 14px;border-radius:22px;border:1px solid var(--border);background:var(--glass);color:var(--text);font-family:inherit;font-size:12px;font-weight:600;cursor:pointer;margin-bottom:14px}
.back-btn:active{transform:scale(.95)}

nav{position:fixed;bottom:0;left:0;right:0;z-index:100;height:var(--nav-h);display:flex;align-items:center;justify-content:space-around;padding:0 8px;padding-bottom:env(safe-area-inset-bottom,0px);transition:transform .3s cubic-bezier(.4,0,.2,1)}
nav.hidden-nav{transform:translateY(100%)}
.nav-bg{position:absolute;inset:0;background:var(--glass);backdrop-filter:blur(var(--glass-blur));-webkit-backdrop-filter:blur(var(--glass-blur));border-top:1px solid var(--border);z-index:-1}
.nav-pill{position:absolute;bottom:8px;height:46px;border-radius:23px;background:linear-gradient(135deg,var(--accent),var(--accent2));box-shadow:0 4px 22px rgba(240,165,0,.3);transition:all .45s cubic-bezier(.4,0,.2,1);z-index:-1}
.nav-item{display:flex;flex-direction:column;align-items:center;justify-content:center;gap:2px;flex:1;height:100%;cursor:pointer;color:var(--text3);font-size:10px;font-weight:600;transition:color .2s;position:relative;z-index:1}
.nav-item i{font-size:19px;transition:all .35s cubic-bezier(.4,0,.2,1)}
.nav-item.active{color:#000}
.nav-item.active i{transform:scale(1.12) translateY(-2px)}

.toast-container{position:fixed;top:68px;left:50%;transform:translateX(-50%);z-index:300;display:flex;flex-direction:column;gap:6px;pointer-events:none;width:88%;max-width:340px}
.toast{padding:10px 16px;border-radius:var(--radius-sm);backdrop-filter:blur(16px);-webkit-backdrop-filter:blur(16px);font-size:12px;font-weight:600;animation:toastIn .3s ease-out,toastOut .3s .8s ease-in forwards;pointer-events:auto;display:flex;align-items:center;gap:6px}
.toast.success{background:rgba(34,197,94,.2);color:var(--success);border:1px solid rgba(34,197,94,.25)}
.toast.error{background:rgba(239,68,68,.2);color:var(--danger);border:1px solid rgba(239,68,68,.25)}
.toast.info{background:rgba(240,165,0,.2);color:var(--accent);border:1px solid rgba(240,165,0,.25)}
@keyframes toastIn{0%{opacity:0;transform:translateY(-16px) scale(.95)}100%{opacity:1;transform:translateY(0) scale(1)}}
@keyframes toastOut{to{opacity:0;transform:translateY(-16px)}}

.page-title{font-size:20px;font-weight:900;margin-bottom:14px}

@media(min-width:600px){.tables-grid{grid-template-columns:repeat(4,1fr)}.menu-grid{grid-template-columns:repeat(3,1fr)}.admin-mi-img{width:110px}}
@media(min-width:900px){.tables-grid{grid-template-columns:repeat(5,1fr)}.menu-grid{grid-template-columns:repeat(4,1fr)}.admin-mi-img{width:130px;min-height:90px}.admin-tabs{flex-wrap:nowrap}.admin-tab{min-width:auto}}
</style>
</head>
<body>

<div class="liquid-shape a"></div>
<div class="liquid-shape b"></div>
<div class="liquid-shape c"></div>

<div id="app">
<header>
<div class="header-right"><span class="app-title" data-i18n="appName">مێنیۆی خواردن</span></div>
<div class="header-left">
<button class="hdr-btn lang-btn" onclick="toggleLang()" id="langBtn">KU</button>
<button class="hdr-btn" onclick="toggleTheme()" id="themeBtn"><i class="fas fa-moon"></i></button>
<button class="hdr-btn" onclick="showNotifPage()" id="notifBtn"><i class="fas fa-bell"></i><span class="notif-badge" id="notifBadge" style="display:none">0</span></button>
<button class="hdr-btn" onclick="openAdminModal()"><i class="fas fa-user-shield"></i></button>
</div>
</header>

<div class="pages-wrap">
<div class="page active" id="page-welcome"></div>
<div class="page" id="page-tables"></div>
<div class="page" id="page-table-1"></div><div class="page" id="page-table-2"></div><div class="page" id="page-table-3"></div>
<div class="page" id="page-table-4"></div><div class="page" id="page-table-5"></div><div class="page" id="page-table-6"></div>
<div class="page" id="page-table-7"></div><div class="page" id="page-table-8"></div><div class="page" id="page-table-9"></div>
<div class="page" id="page-table-10"></div><div class="page" id="page-table-11"></div><div class="page" id="page-table-12"></div>
<div class="page" id="page-table-13"></div><div class="page" id="page-table-14"></div><div class="page" id="page-table-15"></div>
<div class="page" id="page-table-16"></div><div class="page" id="page-table-17"></div><div class="page" id="page-table-18"></div>
<div class="page" id="page-table-19"></div><div class="page" id="page-table-20"></div>
<div class="page" id="page-notif"></div>
<div class="page" id="page-admin"></div>
</div>

<nav id="navbar" class="hidden-nav">
<div class="nav-bg"></div>
<div class="nav-pill" id="navPill"></div>
<div class="nav-item active" data-tab="tables" onclick="switchTab('tables')"><i class="fas fa-utensils"></i><span data-i18n="navTables">مێزەکان</span></div>
<div class="nav-item" data-tab="notif" onclick="switchTab('notif')"><i class="fas fa-bell"></i><span data-i18n="navNotif">نۆتفیکەیشن</span></div>
<div class="nav-item" data-tab="admin" onclick="switchTab('admin')"><i class="fas fa-cog"></i><span data-i18n="navAdmin">بەڕێوبەر</span></div>
</nav>
</div>

<div class="modal-overlay" id="passwordModal">
<div class="modal-box">
<h3 data-i18n="login">چوونەژوورەوە</h3>
<p data-i18n="enterPass">تکایە پاسۆرد بنووسە</p>
<div class="error-msg" id="passError"></div>
<input type="password" class="form-input" id="passInput" placeholder="Password" autocomplete="off">
<button class="admin-btn primary" style="width:100%;margin-top:4px" onclick="checkPassword()" data-i18n="enter">چوونەژوورەوە</button>
<button class="admin-btn danger" style="width:100%;margin-top:6px" onclick="closePasswordModal()" data-i18n="cancel">پاشگەزبوونەوە</button>
</div>
</div>

<div class="modal-overlay detail-modal" id="detailModal">
<div class="modal-box" id="detailBox"></div>
</div>

<div class="modal-overlay" id="orderNoteModal">
<div class="modal-box">
<h3 data-i18n="orderNote">تێبینی داواکردن</h3>
<p style="font-size:12px;color:var(--text2);margin-bottom:10px" data-i18n="orderNoteDesc">تێبینی دڵخواز بنووسە</p>
<textarea class="order-note-input" id="orderNoteInput" placeholder="..."></textarea>
<button class="admin-btn primary" style="width:100%;margin-top:10px" onclick="confirmOrderWithNote()" data-i18n="confirm">پشتڕاستکردنەوە</button>
<button class="admin-btn danger" style="width:100%;margin-top:6px" onclick="closeOrderNoteModal()" data-i18n="cancel">پاشگەزبوونەوە</button>
</div>
</div>

<div class="toast-container" id="toastContainer"></div>

<script>
var DM=[
{id:1,ku:{name:'کەباب',note:'کەبابی بریانکراو لەگەڵ سەوزە و نان'},en:{name:'Kebab',note:'Grilled kebab with vegetables and bread'},ar:{name:'كباب',note:'كباب مشوي مع خضروات وخبز'},price:15000,img:'https://picsum.photos/seed/kebab1/400/300',cat:'food'},
{id:2,ku:{name:'بەریانی مریشک',note:'مریشکی بەریانکراو لەگەڵ برنج'},en:{name:'Grilled Chicken',note:'Grilled chicken with rice'},ar:{name:'دجاج مشوي',note:'دجاج مشوي مع أرز'},price:12000,img:'https://picsum.photos/seed/chicken2/400/300',cat:'food'},
{id:3,ku:{name:'تیلاڤ',note:'تیلاڤی برنج لەگەڵ دارچین'},en:{name:'Rice Pilaf',note:'Rice pilaf with cinnamon'},ar:{name:'بصمة أرز',note:'أرز بهارات مع قرفة'},price:5000,img:'https://picsum.photos/seed/rice3/400/300',cat:'food'},
{id:4,ku:{name:'سەلاتە',note:'سەلاتەی تازە لەگەڵ پەیتە و گەشە'},en:{name:'Salad',note:'Fresh salad with lettuce and tomato'},ar:{name:'سلطة',note:'سلطة طازجة مع خس وطماطم'},price:4000,img:'https://picsum.photos/seed/salad4/400/300',cat:'food'},
{id:5,ku:{name:'سوپ',note:'سوپی ڕۆژانە'},en:{name:'Soup',note:'Daily soup'},ar:{name:'شوربة',note:'شوربة يومية'},price:3500,img:'https://picsum.photos/seed/soup5/400/300',cat:'food'},
{id:6,ku:{name:'فلافل',note:'فلافلی کرنە لەگەڵ سەس'},en:{name:'Falafel',note:'Crispy falafel with sauce'},ar:{name:'فلافل',note:'فلافل مقرمش مع صوص'},price:3000,img:'https://picsum.photos/seed/falafel6/400/300',cat:'food'},
{id:7,ku:{name:'دۆڵمە',note:'دۆڵمەی تەماتە و بروکاڵی'},en:{name:'Dolma',note:'Stuffed tomato and cabbage'},ar:{name:'دولمة',note:'دولمة طماطم وملفوف'},price:8000,img:'https://picsum.photos/seed/dolma7/400/300',cat:'food'},
{id:8,ku:{name:'کوفتە',note:'کوفتەی بریانکراو لەگەڵ سەس'},en:{name:'Meatballs',note:'Grilled meatballs with sauce'},ar:{name:'كفتة',note:'كفتة مشوية مع صوص'},price:10000,img:'https://picsum.photos/seed/kofta8/400/300',cat:'food'},
{id:9,ku:{name:'ناسا بریانی',note:'ناسی بریانی تەماتەدار'},en:{name:'Tomato Rice',note:'Spiced tomato rice'},ar:{name:'أرز بندورة',note:'أرز بهارات بالطماطم'},price:5000,img:'https://picsum.photos/seed/nas9/400/300',cat:'food'},
{id:10,ku:{name:'چێشتنی مریشک',note:'چێشتنی دەستی لەگەڵ برنج'},en:{name:'Chicken Stew',note:'Homemade chicken stew with rice'},ar:{name:'يخنة دجاج',note:'يخنة دجاج منزلية مع أرز'},price:11000,img:'https://picsum.photos/seed/stew10/400/300',cat:'food'},
{id:11,ku:{name:'عەرەقی',note:'عەرەقی ڕوون و پاک'},en:{name:'Arak',note:'Clear and pure arak'},ar:{name:'عرق',note:'عرق نقي وصافٍ'},price:2000,img:'https://picsum.photos/seed/arak11/400/300',cat:'drink'},
{id:12,ku:{name:'شەربەتی لیمۆ',note:'شەربەتی لیمۆی تازە'},en:{name:'Lemon Juice',note:'Fresh lemon juice'},ar:{name:'عصير ليمون',note:'عصير ليمون طازج'},price:2500,img:'https://picsum.photos/seed/lemon12/400/300',cat:'drink'},
{id:13,ku:{name:'چای',note:'چایی کوردی لەگەڵ نەخشە'},en:{name:'Tea',note:'Kurdish tea with pattern glass'},ar:{name:'شاي',note:'شاي كردي مع كأس مزخرف'},price:1500,img:'https://picsum.photos/seed/tea13/400/300',cat:'drink'},
{id:14,ku:{name:'قاوە',note:'قاوەی تازەی تورک'},en:{name:'Coffee',note:'Fresh Turkish coffee'},ar:{name:'قهوة',note:'قهوة تركية طازجة'},price:3000,img:'https://picsum.photos/seed/coffee14/400/300',cat:'drink'},
{id:15,ku:{name:'شەربەتی توت',note:'شەربەتی توتی ڕەش و سپی'},en:{name:'Mulberry Juice',note:'Black and white mulberry juice'},ar:{name:'عصير توت',note:'عصير توت أسود وأبيض'},price:2500,img:'https://picsum.photos/seed/mulberry15/400/300',cat:'drink'},
{id:16,ku:{name:'دووغ',note:'دووغی سارد و تازە'},en:{name:'Doogh',note:'Cold and fresh doogh'},ar:{name:'دوغ',note:'دوغ بارد وطازج'},price:1500,img:'https://picsum.photos/seed/doogh16/400/300',cat:'drink'},
{id:17,ku:{name:'کەلانە',note:'کەلانەی تەماتە و پەیتە'},en:{name:'Klana Dessert',note:'Tomato and date dessert'},ar:{name:'كالنة',note:'حلوى طماطم وتمر'},price:2000,img:'https://picsum.photos/seed/dessert17/400/300',cat:'dessert'},
{id:18,ku:{name:'بامیه',note:'بامیەی شیرین لەگەڵ شەکر'},en:{name:'Bamieh',note:'Sweet bamieh with sugar syrup'},ar:{name:'بامية',note:'بامية حلوة مع قطر السكر'},price:3000,img:'https://picsum.photos/seed/bamieh18/400/300',cat:'dessert'},
{id:19,ku:{name:'کنافە',note:'کنافەی پەنیری دەریایی'},en:{name:'Kunafa',note:'Sea cheese kunafa'},ar:{name:'كنافة',note:'كنافة جبنة بحرية'},price:4000,img:'https://picsum.photos/seed/kunafa19/400/300',cat:'dessert'},
{id:20,ku:{name:'بەستنی قەیو',note:'بەستنی قەیووی تازە'},en:{name:'Quince Dessert',note:'Fresh quince dessert'},ar:{name:'بستنة سفرجل',note:'بستنة سفرجل طازجة'},price:3500,img:'https://picsum.photos/seed/quince20/400/300',cat:'dessert'}
];

var I18N={
ku:{appName:'مێنیۆی خواردن',welcome:'بەخێربێیت',welcomeSub:'سیستەمی داواکردنی خواردن بۆ ڕستۆرانەکان',enterApp:'چوونە ناو ئەپەکە',tables:'مێزەکان',notifications:'نۆتفیکەیشنەکان',admin:'بەڕێوبەر',navTables:'مێزەکان',navNotif:'نۆتفیکەیشن',navAdmin:'بەڕێوبەر',empty:'تا ئێستا هیچ شتێک نییە',emptyCart:'سەبەتەکە بەتاڵە',addFood:'خواردن',addDrink:'خواردەنەوە',addDessert:'شیرینی',name:'ناو',price:'نرخ',note:'تێبینی',category:'جۆر',food:'خواردن',drink:'خواردەنەوە',dessert:'شیرینی',all:'هەمووی',save:'پاشەکەوت',edit:'دەستکاری',delete:'سڕینەوە',cancel:'پاشگەزبوونەوە',confirm:'پشتڕاستکردنەوە',login:'چوونەژوورەوە',enterPass:'تکایە پاسۆرد بنووسە',enter:'چوونەژوورەوە',wrongPass:'پاسۆرد هەڵەیە!',orderNote:'تێبینی داواکردن',orderNoteDesc:'تێبینی دڵخواز بنووسە',sendOrder:'ناردنی داواکاری',orderSent:'داواکارییەکە نێردرا!',addToCart:'زیادکرا بۆ سەبەتە',table:'مێزی ',total:'کۆی گشتی',imgUpload:'کلیک بکە یان وێنە هەڵبژێرە',changeImg:'گۆڕینی وێنە',newOrder:'داواکاری نوێ',preparing:'ئامادەکردن',done:'تەواو',noNotif:'هیچ نۆتفیکەیشنێک نییە',cart:'سەبەتە',back:'گەڕانەوە',orders:'داواکارییەکان',menuManage:'مێنیۆ',accountant:'ژمێریار',orderSum:'کۆی داواکارییەکان'},
en:{appName:'Food Menu',welcome:'Welcome',welcomeSub:'Fast food ordering system for restaurants',enterApp:'Enter App',tables:'Tables',notifications:'Notifications',admin:'Admin',navTables:'Tables',navNotif:'Notifications',navAdmin:'Admin',empty:'Nothing yet',emptyCart:'Cart is empty',addFood:'Food',addDrink:'Drinks',addDessert:'Desserts',name:'Name',price:'Price',note:'Note',category:'Category',food:'Food',drink:'Drinks',dessert:'Desserts',all:'All',save:'Save',edit:'Edit',delete:'Delete',cancel:'Cancel',confirm:'Confirm',login:'Login',enterPass:'Enter password',enter:'Login',wrongPass:'Wrong password!',orderNote:'Order Note',orderNoteDesc:'Write a note',sendOrder:'Send Order',orderSent:'Order sent!',addToCart:'Added to cart',table:'Table ',total:'Total',imgUpload:'Click to select image',changeImg:'Change Image',newOrder:'New Order',preparing:'Preparing',done:'Done',noNotif:'No notifications',cart:'Cart',back:'Back',orders:'Orders',menuManage:'Menu',accountant:'Accountant',orderSum:'Order Summary'},
ar:{appName:'قائمة الطعام',welcome:'مرحباً',welcomeSub:'نظام طلب الطعام للمطاعم',enterApp:'دخول',tables:'الطاولات',notifications:'الإشعارات',admin:'المدير',navTables:'الطاولات',navNotif:'الإشعارات',navAdmin:'المدير',empty:'لا يوجد شيء',emptyCart:'السلة فارغة',addFood:'طعام',addDrink:'مشروبات',addDessert:'حلويات',name:'الاسم',price:'السعر',note:'ملاحظة',category:'النوع',food:'طعام',drink:'مشروبات',dessert:'حلويات',all:'الكل',save:'حفظ',edit:'تعديل',delete:'حذف',cancel:'إلغاء',confirm:'تأكيد',login:'تسجيل الدخول',enterPass:'أدخل كلمة المرور',enter:'دخول',wrongPass:'كلمة مرور خاطئة!',orderNote:'ملاحظة الطلب',orderNoteDesc:'اكتب ملاحظة',sendOrder:'إرسال الطلب',orderSent:'تم الإرسال!',addToCart:'أضيف للسلة',table:'طاولة ',total:'المجموع',imgUpload:'اضغط لاختيار صورة',changeImg:'تغيير الصورة',newOrder:'طلب جديد',preparing:'جاري التحضير',done:'مكتمل',noNotف:'لا إشعارات',cart:'السلة',back:'رجوع',orders:'الطلبات',menuManage:'القائمة',accountant:'المحاسب',orderSum:'ملخص الطلبات'}
};

var S={
lang:localStorage.getItem('lang')||'ku',
theme:localStorage.getItem('theme')||'dark',
menu:JSON.parse(localStorage.getItem('menu'))||JSON.parse(JSON.stringify(DM)),
carts:JSON.parse(localStorage.getItem('carts'))||{},
orders:JSON.parse(localStorage.getItem('orders'))||[],
notifs:JSON.parse(localStorage.getItem('notifs'))||[],
isAdmin:false,page:'welcome',table:null,cat:'all',editId:null,pendingTable:null,imgData:'',
adminTab:'orders'
};

function t(k){return(I18N[S.lang]||I18N.ku)[k]||k}
function gt(it){return it[S.lang]||it.ku||{}}
function sv(k,v){localStorage.setItem(k,JSON.stringify(v))}
function ss(){sv('menu',S.menu);sv('carts',S.carts);sv('orders',S.orders);sv('notifs',S.notifs)}
function fp(p){return Number(p).toLocaleString()}
function nid(){return S.menu.length?Math.max.apply(null,S.menu.map(function(i){return i.id}))+1:1}
function gc(tn){return S.carts[tn]||[]}
function sc(tn,i){S.carts[tn]=i;sv('carts',S.carts)}
function isOcc(tn){return(gc(tn).length>0)||S.orders.some(function(o){return o.table===tn&&o.status!=='done'})}

function toast(m,tp){
var c=document.getElementById('toastContainer'),d=document.createElement('div');
d.className='toast '+tp;
var ic={success:'fa-check-circle',error:'fa-times-circle',info:'fa-info-circle'};
d.innerHTML='<i class="fas '+(ic[tp]||ic.info)+'"></i>'+m;
c.appendChild(d);setTimeout(function(){if(d.parentNode)d.remove()},1200);
}

function applyLang(){
document.querySelectorAll('[data-i18n]').forEach(function(el){
var k=el.getAttribute('data-i18n');
if(I18N[S.lang]&&I18N[S.lang][k])el.textContent=I18N[S.lang][k];
});
var h=document.documentElement;
h.setAttribute('dir',S.lang==='en'?'ltr':'rtl');
h.setAttribute('lang',S.lang);
document.getElementById('langBtn').textContent=S.lang.toUpperCase();
renderPage();
}
function toggleLang(){var l=['ku','en','ar'];S.lang=l[(l.indexOf(S.lang)+1)%3];localStorage.setItem('lang',S.lang);applyLang()}

function applyTheme(){document.body.classList.toggle('light-mode',S.theme==='light');document.querySelector('#themeBtn i').className=S.theme==='light'?'fas fa-sun':'fas fa-moon'}
function toggleTheme(){S.theme=S.theme==='dark'?'light':'dark';localStorage.setItem('theme',S.theme);applyTheme()}

function movePill(tab){
var el=document.querySelector('.nav-item[data-tab="'+tab+'"]'),pill=document.getElementById('navPill'),nb=document.getElementById('navbar');
if(!el||!pill||!nb)return;
var r=el.getBoundingClientRect(),nr=nb.getBoundingClientRect();
pill.style.left=(r.left-nr.left+(r.width-110)/2)+'px';
pill.style.width='110px';
}
function setNav(tab){document.querySelectorAll('.nav-item').forEach(function(n){n.classList.toggle('active',n.dataset.tab===tab)});movePill(tab)}
function showNav(){document.getElementById('navbar').classList.remove('hidden-nav')}
function hideNav(){document.getElementById('navbar').classList.add('hidden-nav')}

function showP(id){document.querySelectorAll('.page').forEach(function(p){p.classList.remove('active')});var p=document.getElementById(id);if(p)p.classList.add('active')}
function renderPage(){
if(S.page==='welcome')renderWelcome();
else if(S.page==='tables')renderTables();
else if(S.page==='notif')renderNotifs();
else if(S.page==='admin'&&S.isAdmin)renderAdmin();
else if(S.page.indexOf('table-')===0){var n=parseInt(S.page.replace('table-',''));if(n)renderTP(n)}
}

function renderWelcome(){
document.getElementById('page-welcome').innerHTML='<div class="welcome-container"><div class="welcome-logo"><i class="fas fa-utensils"></i></div><div class="welcome-title">'+t('welcome')+'</div><div class="welcome-sub">'+t('welcomeSub')+'</div><button class="welcome-enter" onclick="enterApp()">'+t('enterApp')+'</button></div>';
}
function enterApp(){S.page='tables';showNav();showP('page-tables');setNav('tables');renderTables();movePill('tables')}

function switchTab(tab){
if(tab==='admin'&&!S.isAdmin){openAdminModal();return}
S.page=tab;S.table=null;showNav();showP('page-'+tab);setNav(tab);
if(tab==='tables')renderTables();else if(tab==='notif')renderNotifs();else if(tab==='admin')renderAdmin();
}

function renderTables(){
var h='<h2 class="page-title">'+t('tables')+'</h2><div class="tables-grid">';
for(var i=1;i<=20;i++){var o=isOcc(i);h+='<div class="glass-card table-card '+(o?'occupied':'')+'" onclick="openTP('+i+')"><div class="t-icon"><i class="fas fa-chair" style="color:'+(o?'var(--accent)':'var(--text3)')+'"></i></div><div class="t-name">'+t('table')+i+'</div><div class="t-status">'+(o?t('newOrder'):t('empty'))+'</div></div>'}
h+='</div>';document.getElementById('page-tables').innerHTML=h;
}

function openTP(n){S.table=n;S.cat='all';S.page='table-'+n;hideNav();showP('page-table-'+n);renderTP(n)}
function backToTables(){S.table=null;S.page='tables';showNav();showP('page-tables');setNav('tables');renderTables()}

function renderTP(n){
var pg=document.getElementById('page-table-'+n);if(!pg)return;
var cart=gc(n),cats=['all','food','drink','dessert'],cl={all:t('all'),food:t('food'),drink:t('drink'),dessert:t('dessert')};
var fl=S.cat==='all'?S.menu:S.menu.filter(function(i){return i.cat===S.cat});

var ch='<div class="cat-tabs">';cats.forEach(function(c){ch+='<div class="cat-tab '+(S.cat===c?'active':'')+'" onclick="fCat(\''+c+'\','+n+')">'+cl[c]+'</div>'});ch+='</div>';

var mh='<div class="menu-grid">';
fl.forEach(function(it){var tx=gt(it);mh+='<div class="glass-card menu-item" onclick="showDet('+it.id+','+n+')"><img class="mi-img" src="'+it.img+'" alt="" onerror="this.src=\'https://picsum.photos/seed/fb'+it.id+'/400/300\'"><div class="mi-body"><div class="mi-name">'+(tx.name||'')+'</div><div class="mi-price">'+fp(it.price)+'</div>'+(tx.note?'<div class="mi-note">'+tx.note+'</div>':'')+'</div></div>'});
mh+='</div>';

var crh='<div class="cart-section"><div class="cart-title"><i class="fas fa-shopping-cart" style="color:var(--accent)"></i> '+t('cart')+'</div>';
if(!cart.length){crh+='<div class="empty-state" style="padding:16px"><p>'+t('emptyCart')+'</p></div>'}
else{cart.forEach(function(ci,idx){var tx=gt(ci);crh+='<div class="cart-item"><img src="'+ci.img+'" alt="" onerror="this.src=\'https://picsum.photos/seed/fb'+ci.id+'/100/100\'"><div class="ci-info"><div class="ci-name">'+(tx.name||'')+'</div><div class="ci-price">'+fp(ci.price*ci.qty)+'</div></div><div class="ci-qty"><button onclick="event.stopPropagation();cQty('+n+','+idx+',-1)"><i class="fas fa-minus" style="font-size:9px"></i></button><span>'+ci.qty+'</span><button onclick="event.stopPropagation();cQty('+n+','+idx+',1)"><i class="fas fa-plus" style="font-size:9px"></i></button></div><div class="ci-del" onclick="event.stopPropagation();cRem('+n+','+idx+')"><i class="fas fa-trash-alt"></i></div></div>'});
var tot=cart.reduce(function(s,c){return s+c.price*c.qty},0);crh+='<div class="total-bar"><span class="tl">'+t('total')+'</span><span class="tv">'+fp(tot)+'</span></div><button class="submit-order-btn" onclick="sendOrd('+n+')">'+t('sendOrder')+'</button>'}
crh+='</div>';

pg.innerHTML='<button class="back-btn" onclick="backToTables()"><i class="fas fa-arrow-right"></i> '+t('back')+'</button><h2 class="page-title">'+t('table')+n+'</h2>'+ch+mh+crh;
}
function fCat(c,n){S.cat=c;renderTP(n)}

var dQty=1;
function showDet(id,n){
var it=S.menu.find(function(i){return i.id===id});if(!it)return;
var tx=gt(it),cart=gc(n),ex=cart.find(function(c){return c.id===id});
dQty=ex?ex.qty:1;
document.getElementById('detailBox').innerHTML='<img class="detail-img" src="'+it.img+'" alt="" onerror="this.src=\'https://picsum.photos/seed/fb'+id+'/400/300\'"><div class="detail-body"><h3>'+(tx.name||'')+'</h3><div class="d-price">'+fp(it.price)+'</div>'+(tx.note?'<div class="d-note">'+tx.note+'</div>':'')+'<div class="detail-qty"><button onclick="dQC(-1)"><i class="fas fa-minus"></i></button><span id="dQV">'+dQty+'</span><button onclick="dQC(1)"><i class="fas fa-plus"></i></button></div><button class="detail-add-btn" onclick="addFC('+id+','+n+')"><i class="fas fa-cart-plus"></i> '+t('addToCart')+'</button></div>';
document.getElementById('detailModal').classList.add('show');
}
function dQC(d){dQty=Math.max(1,dQty+d);var e=document.getElementById('dQV');if(e)e.textContent=dQty}
function addFC(id,n){
var it=S.menu.find(function(i){return i.id===id});if(!it)return;
var cart=gc(n),ex=cart.find(function(c){return c.id===id});
if(ex)ex.qty+=dQty;else{var nw=JSON.parse(JSON.stringify(it));nw.qty=dQty;cart.push(nw)}
sc(n,cart);dQty=1;document.getElementById('detailModal').classList.remove('show');toast(t('addToCart'),'success');renderTP(n);
}
function cQty(n,i,d){var c=gc(n);c[i].qty+=d;if(c[i].qty<=0)c.splice(i,1);sc(n,c);renderTP(n)}
function cRem(n,i){var c=gc(n);c.splice(i,1);sc(n,c);renderTP(n)}

function sendOrd(n){if(!gc(n).length)return;S.pendingTable=n;document.getElementById('orderNoteInput').value='';document.getElementById('orderNoteModal').classList.add('show')}
function closeOrderNoteModal(){document.getElementById('orderNoteModal').classList.remove('show')}
function confirmOrderWithNote(){
var n=S.pendingTable;if(!n)return;
var note=document.getElementById('orderNoteInput').value.trim(),cart=gc(n);if(!cart.length)return;
var now=new Date(),time=now.toLocaleTimeString(S.lang==='en'?'en-US':S.lang==='ar'?'ar-IQ':'ku',{hour:'2-digit',minute:'2-digit'});
var ord={id:Date.now(),table:n,items:JSON.parse(JSON.stringify(cart)),note:note,status:'new',time:time};
S.orders.push(ord);
S.notifs.unshift({id:Date.now()+1,orderId:ord.id,table:n,items:cart.map(function(c){return(gt(c).name||'')+' x'+c.qty}).join('، '),status:'new',time:time,read:false});
sc(n,[]);ss();closeOrderNoteModal();toast(t('orderSent'),'success');updBadge();renderTP(n);
}

function updBadge(){var u=S.notifs.filter(function(n){return!n.read}).length,b=document.getElementById('notifBadge');if(u>0){b.style.display='flex';b.textContent=u>99?'99+':u}else b.style.display='none'}
function showNotifPage(){switchTab('notif')}
function renderNotifs(){
var h='<h2 class="page-title">'+t('notifications')+'</h2>';
if(!S.notifs.length)h+='<div class="empty-state"><i class="fas fa-bell-slash"></i><p>'+t('noNotif')+'</p></div>';
else{S.notifs.forEach(function(n){n.read=true});ss();updBadge();S.notifs.forEach(function(n){h+='<div class="notif-item"><div class="ni-head"><span class="ni-table"><i class="fas fa-chair"></i> '+t('table')+n.table+'</span><span class="ni-time">'+n.time+'</span></div><div class="ni-items">'+n.items+'</div><span class="ni-status '+n.status+'">'+t(n.status)+'</span></div>'})}
document.getElementById('page-notif').innerHTML=h;
}

function openAdminModal(){if(S.isAdmin){switchTab('admin');return}document.getElementById('passError').textContent='';document.getElementById('passInput').value='';document.getElementById('passwordModal').classList.add('show');setTimeout(function(){document.getElementById('passInput').focus()},30)}
function closePasswordModal(){document.getElementById('passwordModal').classList.remove('show')}
function checkPassword(){
if(document.getElementById('passInput').value==='sayd'){S.isAdmin=true;closePasswordModal();switchTab('admin');toast(t('login')+' ✓','success')}
else{document.getElementById('passError').textContent=t('wrongPass');document.getElementById('passInput').value='';document.getElementById('passInput').focus()}
}
document.getElementById('passInput').addEventListener('keydown',function(e){if(e.key==='Enter')checkPassword()});

function renderAdmin(){
var c=document.getElementById('page-admin'),cl={food:t('food'),drink:t('drink'),dessert:t('dessert')};
var tabs=[
{key:'orders',label:t('orders'),icon:'fa-receipt'},
{key:'accountant',label:t('accountant'),icon:'fa-calculator'},
{key:'food',label:t('addFood'),icon:'fa-hamburger'},
{key:'drink',label:t('addDrink'),icon:'fa-glass-water'},
{key:'dessert',label:t('addDessert'),icon:'fa-ice-cream'},
{key:'manage',label:t('menuManage'),icon:'fa-list-alt'}
];

var th='<h2 class="page-title">'+t('admin')+'</h2><div class="admin-tabs">';
tabs.forEach(function(tb){th+='<button class="admin-tab '+(S.adminTab===tb.key?'active':'')+'" onclick="S.adminTab=\''+tb.key+'\';renderAdmin()"><i class="fas '+tb.icon+'"></i> '+tb.label+'</button>'});
th+='</div>';

var content='';

if(S.adminTab==='orders'){
if(!S.orders.length)content='<div class="empty-state"><i class="fas fa-receipt"></i><p>'+t('empty')+'</p></div>';
else S.orders.slice().reverse().forEach(function(o){
content+='<div class="notif-item"><div class="ni-head"><span class="ni-table"><i class="fas fa-chair"></i> '+t('table')+o.table+'</span><span class="ni-time">'+o.time+'</span></div><div class="ni-items">'+o.items.map(function(i){return(gt(i).name||'')+' x'+i.qty}).join('، ')+'</div>'+(o.note?'<div style="font-size:11px;color:var(--text3);margin-top:3px"><i class="fas fa-sticky-note"></i> '+o.note+'</div>':'')+'<div style="display:flex;gap:6px;margin-top:6px;flex-wrap:wrap"><span class="ni-status '+o.status+'">'+t(o.status)+'</span>'+(o.status==='new'?'<button class="admin-btn primary" style="padding:3px 10px;font-size:10px" onclick="updOS('+o.id+',\'preparing\')">'+t('preparing')+'</button>':'')+(o.status==='preparing'?'<button class="admin-btn success" style="padding:3px 10px;font-size:10px" onclick="updOS('+o.id+',\'done\')">'+t('done')+'</button>':'')+'</div></div>';
});
}

else if(S.adminTab==='accountant'){
var done=S.orders.filter(function(o){return o.status==='done'});
var grand=0;
content='<div class="glass-card" style="padding:20px"><h3 style="font-size:16px;font-weight:800;margin-bottom:14px"><i class="fas fa-calculator" style="color:var(--accent3);margin-left:6px"></i> '+t('orderSum')+'</h3>';
if(!done.length)content+='<div class="empty-state" style="padding:16px"><p>'+t('empty')+'</p></div>';
else{done.forEach(function(o){var tot=o.items.reduce(function(s,i){return s+i.price*i.qty},0);grand+=tot;
content+='<div style="display:flex;justify-content:space-between;align-items:center;padding:8px 0;border-bottom:1px solid var(--border);font-size:13px"><span>'+t('table')+o.table+' <span style="color:var(--text3);font-size:11px">'+o.time+'</span></span><span style="font-weight:800;color:var(--accent3)">'+fp(tot)+'</span></div>';
});
content+='<div style="display:flex;justify-content:space-between;align-items:center;padding:12px 0;font-size:18px;font-weight:900"><span>'+t('total')+'</span><span style="color:var(--accent)">'+fp(grand)+'</span></div>'}
content+='</div>';
}

else if(S.adminTab==='manage'){
if(!S.menu.length)content='<div class="empty-state"><i class="fas fa-list"></i><p>'+t('empty')+'</p></div>';
else S.menu.forEach(function(it){var tx=gt(it);content+='<div class="admin-mi"><img class="admin-mi-img" src="'+it.img+'" alt="" onerror="this.src=\'https://picsum.photos/seed/fb'+it.id+'/200/200\'"><div class="admin-mi-body"><div class="admin-mi-name">'+(tx.name||'')+'</div><div class="admin-mi-meta">'+fp(it.price)+' — '+(cl[it.cat]||it.cat)+'</div></div><div class="admin-mi-actions"><button onclick="editMI('+it.id+')"><i class="fas fa-pen"></i></button><button class="del-btn" onclick="delMI('+it.id+')"><i class="fas fa-trash"></i></button></div></div>'});
}

else{
var fc=S.adminTab==='food'?'food':S.adminTab==='drink'?'drink':'dessert';
var ed=S.editId?S.menu.find(function(i){return i.id===S.editId}):null;
content='<div class="glass-card"><div class="admin-form">'
+'<div class="form-group"><label>'+t('name')+' (کوردی)</label><input class="form-input" id="aNK" value="'+(ed?ed.ku.name||'':'')+'"></div>'
+'<div class="form-group"><label>'+t('name')+' (English)</label><input class="form-input" id="aNE" value="'+(ed&&ed.en?ed.en.name||'':'')+'" dir="ltr"></div>'
+'<div class="form-group"><label>'+t('name')+' (عربي)</label><input class="form-input" id="aNA" value="'+(ed&&ed.ar?ed.ar.name||'':'')+'"></div>'
+'<div class="form-group"><label>'+t('price')+'</label><input class="form-input" id="aP" type="number" value="'+(ed?ed.price:'')+'"></div>'
+'<div class="form-group"><label>'+t('note')+' (کوردی)</label><input class="form-input" id="aNK2" value="'+(ed?ed.ku.note||'':'')+'"></div>'
+'<div class="form-group"><label>'+t('note')+' (English)</label><input class="form-input" id="aNE2" value="'+(ed&&ed.en?ed.en.note||'':'')+'" dir="ltr"></div>'
+'<div class="form-group"><label>'+t('note')+' (عربي)</label><input class="form-input" id="aNA2" value="'+(ed&&ed.ar?ed.ar.note||'':'')+'"></div>'
+'<div class="form-group"><label>'+t('changeImg')+'</label><div class="img-upload"><input type="file" accept="image/*" onchange="hImg(event)"><i class="fas fa-cloud-upload-alt" style="font-size:22px;margin-bottom:4px;display:block"></i>'+t('imgUpload')+'<div id="aIP">'+(ed?'<img src="'+ed.img+'" class="preview-img">':'')+'</div></div></div>'
+'<button class="admin-btn primary" style="width:100%" onclick="saveMI(\''+fc+'\')">'+(ed?t('edit'):t('save'))+'</button>'
+(ed?'<button class="admin-btn danger" style="width:100%;margin-top:6px" onclick="cancelEd()">'+t('cancel')+'</button>':'')
+'</div></div>';
}

c.innerHTML=th+content;
}

function hImg(e){var f=e.target.files[0];if(!f)return;var r=new FileReader();r.onload=function(ev){S.imgData=ev.target.result;var p=document.getElementById('aIP');if(p)p.innerHTML='<img src="'+S.imgData+'" class="preview-img">'};r.readAsDataURL(f)}

function saveMI(cat){
var nk=document.getElementById('aNK').value.trim(),ne=document.getElementById('aNE').value.trim(),na=document.getElementById('aNA').value.trim();
var pr=parseInt(document.getElementById('aP').value)||0;
var nk2=document.getElementById('aNK2').value.trim(),ne2=document.getElementById('aNE2').value.trim(),na2=document.getElementById('aNA2').value.trim();
if(!nk||!pr){toast(t('name')+' / '+t('price')+' !','error');return}
var img=S.imgData||'https://picsum.photos/seed/'+Date.now()+'/400/300';

if(S.editId){
var it=S.menu.find(function(i){return i.id===S.editId});
if(it){it.cat=cat;it.ku={name:nk,note:nk2};it.en={name:ne,note:ne2};it.ar={name:na,note:na2};it.price=pr;if(S.imgData)it.img=img}
S.editId=null;
}else{
S.menu.push({id:nid(),cat:cat,ku:{name:nk,note:nk2},en:{name:ne,note:ne2},ar:{name:na,note:na2},price:pr,img:img});
}
S.imgData='';ss();toast(t('save')+' ✓','success');S.adminTab='manage';renderAdmin();
}

function editMI(id){S.editId=id;S.imgData='';var it=S.menu.find(function(i){return i.id===id});S.adminTab=it?it.cat:'food';renderAdmin();var pg=document.getElementById('page-admin');setTimeout(function(){pg.scrollTo({top:pg.scrollHeight,behavior:'smooth'})},50)}
function cancelEd(){S.editId=null;S.imgData='';S.adminTab='manage';renderAdmin()}
function delMI(id){S.menu=S.menu.filter(function(i){return i.id!==id});Object.keys(S.carts).forEach(function(tn){S.carts[tn]=S.carts[tn].filter(function(c){return c.id!==id})});ss();toast(t('delete')+' ✓','error');renderAdmin()}
function updOS(id,st){var o=S.orders.find(function(x){return x.id===id});if(o){o.status=st;var n=S.notifs.find(function(x){return x.orderId===id});if(n)n.status=st;ss();renderAdmin();toast(t(st)+' ✓','success')}}

document.querySelectorAll('.modal-overlay').forEach(function(m){m.addEventListener('click',function(e){if(e.target===m){m.classList.remove('show');if(m.id==='detailModal')dQty=1}})});

applyTheme();hideNav();renderWelcome();updBadge();
window.addEventListener('resize',function(){if(!document.getElementById('navbar').classList.contains('hidden-nav'))movePill(document.querySelector('.nav-item.active')?document.querySelector('.nav-item.active').dataset.tab:'tables')});
</script>
</body>
</html>
