<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Zetu Services - Uganda Services Marketplace</title>
<meta name="theme-color" content="#0A1F44">
<style>
*{margin:0;padding:0;box-sizing:border-box;font-family:Inter,Arial,sans-serif}
body{background:#f6f7fb;padding-bottom:90px}
.top{background:#0A1F44;color:#fff;padding:14px 16px;position:sticky;top:0;z-index:20}
.logo{font-size:22px;font-weight:900}.logo span{color:#FF6B00}
.loc{font-size:12px;opacity:.8}
.search{margin:12px 16px;background:#fff;border-radius:12px;padding:12px;display:flex;gap:8px;box-shadow:0 2px 10px rgba(0,0,0,.06)}
.search input{border:none;outline:none;width:100%;font-size:15px}
.chipRow{display:flex;gap:8px;overflow-x:auto;padding:0 16px}
.chip{background:#fff;border:1px solid #e5e5e5;padding:8px 14px;border-radius:20px;white-space:nowrap;font-size:13px;cursor:pointer}
.chip.active{background:#0A1F44;color:#fff}
.card{background:#fff;border-radius:16px;overflow:hidden;box-shadow:0 2px 10px rgba(0,0,0,.05)}
.card img{width:100%;height:110px;object-fit:cover}
.card .in{padding:10px}.price{font-weight:900;color:#0A1F44}.name{font-size:13px;font-weight:700}
.meta{font-size:11px;color:#666;margin:3px 0}
.btn{width:100%;border:none;padding:10px;border-radius:10px;font-weight:700;cursor:pointer;margin-top:6px}
.btnO{background:#FF6B00;color:#fff}.btnN{background:#0A1F44;color:#fff}.btnW{background:#25D366;color:#fff}.btnG{background:#eee}
.page{display:none}.page.active{display:block}
.box{background:#fff;margin:12px 16px;padding:16px;border-radius:16px}
input,select,textarea{width:100%;padding:12px;border:1px solid #ddd;border-radius:10px;margin:7px 0;font-size:14px}
.prov{display:flex;gap:12px;background:#fff;margin:12px 16px;padding:12px;border-radius:16px;align-items:center}
.prov img{width:60px;height:60px;border-radius:50%;object-fit:cover}
.badge{background:#e6f9ed;color:#0a7a33;font-size:11px;padding:3px 8px;border-radius:20px;font-weight:700}
.badgeP{background:#fff3e0;color:#FF6B00}
.nav{position:fixed;bottom:0;left:0;right:0;background:#fff;display:flex;justify-content:space-around;padding:10px 0;border-top:1px solid #eee;z-index:30}
.nav div{text-align:center;font-size:11px;color:#888;cursor:pointer}.nav .active{color:#FF6B00;font-weight:800}.nav .i{font-size:20px;display:block}
.catBig{display:grid;grid-template-columns:1fr 1fr;gap:12px;padding:12px 16px}
.catBig div{border-radius:16px;overflow:hidden;position:relative;height:110px;cursor:pointer}
.catBig img{width:100%;height:100%;object-fit:cover}.catBig span{position:absolute;bottom:0;left:0;right:0;background:linear-gradient(transparent,rgba(0,0,0,.8));color:#fff;padding:10px;font-weight:800;font-size:13px}
h3{padding:0 16px;margin-top:16px}
</style>
</head>
<body>
<div class="top"><div style="display:flex;justify-content:space-between"><div><div class="logo">Zetu <span>Services</span></div><div class="loc">📍 Kampala, Uganda ▾ • <span id="userLabel">Guest</span></div></div><div style="font-size:20px">🔔 👤</div></div></div>
<div id="page-home" class="page active">
<div class="search">🔍 <input id="q" placeholder="What service do you need? e.g. Plumber" oninput="doSearch()"></div>
<div class="chipRow" id="chips"></div>
<h3>Popular Services in Uganda</h3>
<div class="catBig" id="cats"></div>
<h3>Top Rated & Verified Providers Near You</h3>
<div id="providers"></div>
<div class="box"><h3>How Zetu Works</h3><p style="font-size:13px;line-height:1.7;margin-top:8px">1. Search service & location<br>2. Send request with photos<br>3. Get quotations from providers<br>4. Compare & book<br>5. Pay with MTN MoMo / Airtel Money<br>6. Rate provider after job</p></div>
<div class="box"><h3>Emergency? ⚡</h3><p style="font-size:13px">Plumber, Electrician, Mechanic available now in Kampala, Wakiso, Entebbe, Mukono.</p><button class="btn btnO" onclick="filterCat('Plumbing')">Find Emergency Plumber →</button></div>
<div class="box"><p style="font-size:11px;color:#888">© 2026 Zetu Services - Kampala, Uganda • Terms • Privacy</p></div>
</div>
<div id="page-bookings" class="page">
<h3>My Bookings & Requests</h3>
<div id="bookingList"></div>
<div class="box"><h3>➕ New Service Request</h3>
<select id="bCat"></select>
<input id="bDesc" placeholder="Describe work needed e.g. Kitchen sink leaking">
<input id="bLoc" placeholder="Location e.g. Ntinda, Kampala">
<input id="bDate" type="date">
<input id="bPhone" placeholder="Your phone e.g. 0700000000">
<button class="btn btnN" onclick="createBooking()">Send Request to Providers</button>
<p style="font-size:11px;color:#888;margin-top:6px">Providers will send quotations. You compare and accept. Payment is NOT marked successful until MoMo confirms.</p>
</div>
</div>
<div id="page-provider" class="page">
<div class="box"><h3>💼 Provider Dashboard</h3><p id="provStats" style="margin-top:8px;line-height:1.7"></p></div>
<div class="box"><h3>Become a Provider</h3>
<input id="pName" placeholder="Full name / Business name">
<input id="pPhone" placeholder="Phone / WhatsApp">
<select id="pCat2"></select>
<input id="pPrice" placeholder="Starting price UGX e.g. 50000" type="number">
<input id="pArea" placeholder="Service areas e.g. Kampala, Wakiso">
<button class="btn btnO" onclick="becomeProvider()">Create Provider Profile</button></div>
<div class="box"><h3>Subscription Plans</h3><p style="font-size:13px;line-height:1.7"><b>FREE:</b> Basic profile, limited listings<br><b>PRO - UGX 15,000/mo:</b> Portfolio, analytics, more visibility<br><b>BUSINESS - UGX 30,000/mo:</b> Priority, multiple listings, business analytics</p><button class="btn btnN" onclick="subscribe('PRO')">Upgrade to PRO - UGX 15,000</button><button class="btn btnO" onclick="subscribe('BUSINESS')">Upgrade to BUSINESS - UGX 30,000</button><p id="subStatus" style="font-size:12px;margin-top:6px"></p></div>
</div>
<div id="page-msg" class="page"><h3>Messages</h3><div id="msgList"></div><div class="box"><input id="msgText" placeholder="Type message to provider..."><button class="btn btnW" onclick="sendMsg()">Send on WhatsApp / Chat</button></div></div>
<div id="page-admin" class="page"><h3>🛡️ Master Admin Dashboard</h3><div class="box" id="adminStats"></div><div class="box"><h3>Verify Providers</h3><div id="adminProviders"></div></div><div class="box"><h3>Manage Categories</h3><input id="newCat" placeholder="New category name"><button class="btn btnN" onclick="addCat()">Add Category</button><p style="font-size:11px;color:#888">Admin can add, edit, disable, reorder categories. Prices are NOT hardcoded - edit in admin_settings.</p></div></div>
<div class="nav">
<div class="active" onclick="go('home',this)"><span class="i">🏠</span>Home</div>
<div onclick="go('bookings',this)"><span class="i">📅</span>Bookings</div>
<div onclick="go('provider',this)"><span class="i">💼</span>Provider</div>
<div onclick="go('msg',this)"><span class="i">💬</span>Messages</div>
<div onclick="go('admin',this)"><span class="i">🛡️</span>Admin</div>
</div>
<script>
let categories=[
{name:"Plumbing",img:"https://images.unsplash.com/photo-1585704032915-c3400ca199e7?w=800&q=80"},
{name:"Electrical services",img:"https://images.unsplash.com/photo-1621905251189-08b45d6a269e?w=800&q=80"},
{name:"House cleaning",img:"https://images.unsplash.com/photo-1581578731548-c64695cc6952?w=800&q=80"},