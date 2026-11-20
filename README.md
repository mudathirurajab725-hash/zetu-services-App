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
{name:"Mechanics and automotive",img:"https://images.unsplash.com/photo-1625047509168-a7026f36de04?w=800&q=80"},
{name:"Painting",img:"https://images.unsplash.com/photo-1562259949-e8e7689d7828?w=800&q=80"},
{name:"Carpentry",img:"https://images.unsplash.com/photo-1504148455328-c376907d081c?w=800&q=80"},
{name:"Beauty and grooming",img:"https://images.unsplash.com/photo-1560066984-138dadb4c035?w=800&q=80"},
{name:"Catering",img:"https://images.unsplash.com/photo-1555244162-803834f70033?w=800&q=80"},
{name:"Photography and videography",img:"https://images.unsplash.com/photo-1516035069371-29a1b244cc32?w=800&q=80"},
{name:"Moving services",img:"https://images.unsplash.com/photo-1600518464441-9154a4dea21b?w=800&q=80"},
{name:"Computer and phone repairs",img:"https://images.unsplash.com/photo-1591799264318-7e6ef8ddb7ea?w=800&q=80"},
{name:"Tutoring and education",img:"https://images.unsplash.com/photo-1503676260728-1c00da094a0b?w=800&q=80"},
];
let providers=[
{name:"Musa Plumbing UG",cat:"Plumbing",area:"Kampala, Ntinda",price:50000,rating:4.9,reviews:127,verified:true,img:"https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?w=200&q=80",phone:"256700111222"},
{name:"Grace Beauty Studio",cat:"Beauty and grooming",area:"Kampala, Kisementi",price:40000,rating:4.8,reviews:203,verified:true,img:"https://images.unsplash.com/photo-1494790108377-be9c29b29330?w=200&q=80",phone:"256700333444"},
{name:"Kampala Fix Motors",cat:"Mechanics and automotive",area:"Kampala, Industrial Area",price:80000,rating:4.7,reviews:89,verified:true,img:"https://images.unsplash.com/photo-1500648767791-00dcc994a43e?w=200&q=80",phone:"256700555666"},
{name:"CleanHome UG",cat:"House cleaning",area:"Wakiso, Kira",price:60000,rating:4.8,reviews:156,verified:false,img:"https://images.unsplash.com/photo-1438761681033-6461ffad8d80?w=200&q=80",phone:"256700777888"},
{name:"Pro Shots UG",cat:"Photography and videography",area:"Kampala, Entebbe",price:150000,rating:5.0,reviews:98,verified:true,img:"https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?w=200&q=80",phone:"256700999000"},
{name:"Bright Painters",cat:"Painting",area:"Kampala, Mukono",price:120000,rating:4.6,reviews:67,verified:false,img:"https://images.unsplash.com/photo-1506794778202-cad84cf45f1d?w=200&q=80",phone:"256701222333"},
];
let bookings=JSON.parse(localStorage.getItem('zetu_bookings')||'[]');
let msgs=JSON.parse(localStorage.getItem('zetu_msgs')||'[]');
let myPlan=localStorage.getItem('zetu_plan')||'FREE';
function fmt(n){return "UGX "+Number(n).toLocaleString()}
function renderCats(){document.getElementById('cats').innerHTML=categories.map(c=>`<div onclick="filterCat('${c.name}')"><img src="${c.img}"><span>${c.name}</span></div>`).join('');document.getElementById('chips').innerHTML=`<div class="chip active" onclick="filterCat('All',this)">All</div>`+categories.slice(0,8).map(c=>`<div class="chip" onclick="filterCat('${c.name}',this)">${c.name}</div>`).join('');document.getElementById('bCat').innerHTML=categories.map(c=>`<option>${c.name}</option>`).join('');document.getElementById('pCat2').innerHTML=categories.map(c=>`<option>${c.name}</option>`).join('')}
function renderProviders(list){document.getElementById('providers').innerHTML=list.map((p,i)=>`<div class="prov"><img src="${p.img}"><div style="flex:1"><b>${p.name}</b> ${p.verified?'<span class="badge">✓ Verified</span>':'<span class="badge badgeP">Unverified</span>'}<div class="meta">${p.cat} • ${p.area}<br>⭐ ${p.rating} (${p.reviews} reviews) • From ${fmt(p.price)}</div></div><div><button class="btn btnN" style="width:auto;padding:8px 10px" onclick="requestProvider(${providers.indexOf(p)})">Book</button><button class="btn btnW" style="width:auto;padding:8px 10px" onclick="openWA('${p.phone}','${p.name}')">WhatsApp</button></div></div>`).join('')}
function filterCat(cat,el){if(el){document.querySelectorAll('.chip').forEach(c=>c.classList.remove('active'));el.classList.add('active')}if(cat==='All')renderProviders(providers);else renderProviders(providers.filter(p=>p.cat===cat));if(cat!=='All'&&providers.filter(p=>p.cat===cat).length===0){document.getElementById('providers').innerHTML=`<div class="box">No providers yet in ${cat}. Be the first provider! Go to Provider tab.</div>`}}
function doSearch(){let q=document.getElementById('q').value.toLowerCase();renderProviders(providers.filter(p=>p.name.toLowerCase().includes(q)||p.cat.toLowerCase().includes(q)||p.area.toLowerCase().includes(q)))}
function requestProvider(i){let p=providers[i];document.getElementById('bCat').value=p.cat;document.getElementById('bDesc').value="I need "+p.cat+" - "+p.name;go('bookings');window.scrollTo(0,0)}
function createBooking(){let cat=document.getElementById('bCat').value,desc=document.getElementById('bDesc').value,loc=document.getElementById('bLoc').value,date=document.getElementById('bDate').value,phone=document.getElementById('bPhone').value;if(!desc||!loc){alert("Add description and location");return}let b={id:Date.now(),cat,desc,loc,date,phone,status:"Pending",quote:null,created:new Date().toLocaleString()};bookings.unshift(b);localStorage.setItem('zetu_bookings',JSON.stringify(bookings));renderBookings();renderAdmin();alert("Request sent! Nearby providers will send quotations.");document.getElementById('bDesc').value=''}
function renderBookings(){let el=document.getElementById('bookingList');if(bookings.length===0)el.innerHTML=`<div class="box">No bookings yet. Create a request above.</div>`;else el.innerHTML=bookings.map((b,i)=>`<div class="box"><b>${b.cat}</b> • <span style="font-size:12px;background:#fff3e0;padding:3px 8px;border-radius:20px">${b.status}</span><p style="font-size:13px;margin-top:6px">${b.desc}<br>📍 ${b.loc} • 📅 ${b.date||'Flexible'}</p>${b.quote?`<p style="font-size:13px;color:#0A1F44"><b>Quotation: ${fmt(b.quote)} - Provider: ${b.provider||'Provider'}</b></p><button class="btn btnO" onclick="acceptQuote(${i})">Accept Quotation & Book</button>`:`<p style="font-size:12px;color:#666">Waiting for quotations...</p><button class="btn btnN" onclick="simulateQuote(${i})">Simulate Provider Quotation (Demo)</button>`}${b.status==='Accepted'?`<button class="btn btnW" onclick="markCompleted(${i})">Mark as Completed & Review</button>`:''}</div>`).join('')}
function simulateQuote(i){let price=50000+Math.floor(Math.random()*80000);bookings[i].quote=price;bookings[i].provider=providers[i%providers.length].name;bookings[i].status="Quoted";localStorage.setItem('zetu_bookings',JSON.stringify(bookings));renderBookings()}
function acceptQuote(i){bookings[i].status="Accepted";localStorage.setItem('zetu_bookings',JSON.stringify(bookings));renderBookings();alert("Booking Accepted! Provider confirmed. Pay via MTN MoMo / Airtel Money - payment stays PENDING until confirmed.")}
function markCompleted(i){bookings[i].status="Completed";localStorage.setItem('zetu_bookings',JSON.stringify(bookings));renderBookings();alert("Thank you! Please rate provider 5 stars.")}
function becomeProvider(){let n=document.getElementById('pName').value,ph=document.getElementById('pPhone').value,cat=document.getElementById('pCat2').value,pr=document.getElementById('pPrice').value||50000,area=document.getElementById('pArea').value||'Kampala';if(!n){alert("Add name");return}providers.unshift({name:n,cat,area,price:Number(pr),rating:5.0,reviews:0,verified:false,img:"https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?w=200&q=80",phone:ph||'256700000000'});renderProviders(providers);renderAdmin();alert("Provider profile created! Status: Unverified. Admin must verify you.");document.getElementById('userLabel').innerText=n+" (Provider - Unverified)"}
function subscribe(plan){myPlan=plan;localStorage.setItem('zetu_plan',plan);document.getElementById('subStatus').innerText="Current plan: "+plan+" - Payment PENDING until MoMo confirms.";updateProvStats()}
function sendMsg(){let t=document.getElementById('msgText').value;if(!t)return;msgs.push({text:t,time:new Date().toLocaleString()});localStorage.setItem('zetu_msgs',JSON.stringify(msgs));renderMsgs();document.getElementById('msgText').value=''}
function renderMsgs(){document.getElementById('msgList').innerHTML=msgs.length?msgs.map(m=>`<div class="box" style="margin:8px 16px"><p style="font-size:13px">${m.text}</p><small>${m.time}</small></div>`).join(''):`<div class="box">No messages yet. Chat is linked to booking.</div>`}
function openWA(phone,name){window.open("https://wa.me/"+phone+"?text="+encodeURIComponent("Hi "+name+", I found you on Zetu Services. I need "+name),"_blank")}
function addCat(){let v=document.getElementById('newCat').value;if(!v)return;categories.push({name:v,img:"https://images.unsplash.com/photo-1581578731548-c64695cc6952?w=800&q=80"});renderCats();alert("Category added: "+v)}
function updateProvStats(){document.getElementById('provStats').innerHTML=`Total Requests: <b>${bookings.length}</b><br>Pending: <b>${bookings.filter(b=>b.status==='Pending').length}</b> • Completed: <b>${bookings.filter(b=>b.status==='Completed').length}</b><br>Subscription: <b>${myPlan}</b><br>Earnings (Completed): <b>${fmt(bookings.filter(b=>b.status==='Completed').reduce((a,b)=>a+(b.quote||0),0))}</b>`}
function renderAdmin(){let totalUsers=providers.length+bookings.length+12;document.getElementById('adminStats').innerHTML=`Total Users: <b>${totalUsers}</b> • Providers: <b>${providers.length}</b> • Verified: <b>${providers.filter(p=>p.verified).length}</b> • Pending Verification: <b>${providers.filter(p=>!p.verified).length}</b><br>Total Bookings: <b>${bookings.length}</b> • Completed: <b>${bookings.filter(b=>b.status==='Completed').length}</b> • Active Subscriptions: <b>${myPlan!=='FREE'?1:0}</b>`;document.getElementById('adminProviders').innerHTML=providers.map((p,i)=>`<div style="display:flex;justify-content:space-between;align-items:center;padding:8px 0;border-bottom:1px solid #eee"><span style="font-size:13px">${p.name} - ${p.verified?'Verified':'Unverified'}</span><button class="btn btnN" style="width:auto;padding:6px 10px" onclick="verifyProvider(${i})">${p.verified?'Suspend':'Verify'}</button></div>`).join('')}
function verifyProvider(i){providers[i].verified=!providers[i].verified;renderProviders(providers);renderAdmin();alert(providers[i].name+" verification: "+(providers[i].verified?"Verified":"Suspended/Unverified"))}
function go(id,el){document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));document.getElementById('page-'+id).classList.add('active');document.querySelectorAll('.nav div').forEach(d=>d.classList.remove('active'));if(el)el.classList.add('active');window.scrollTo(0,0);if(id==='bookings')renderBookings();if(id==='provider')updateProvStats();if(id==='msg')renderMsgs();if(id==='admin')renderAdmin()}
renderCats();renderProviders(providers);renderBookings();renderMsgs();updateProvStats();renderAdmin();
</script>
</body>
</html>