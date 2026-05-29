[torty-final.html](https://github.com/user-attachments/files/28401798/torty-final.html)
# -<!DOCTYPE html>
<html lang="uk">
<head> Торти
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Торти</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;1,400&family=Montserrat:wght@200;300;400;500&display=swap" rel="stylesheet">
<style>
:root {
  --bg: #8c8f52;
  --bg-dark: #7a7d42;
  --bg-darker: #6b6e36;
  --white: #ffffff;
  --gold: #d4a843;
  --muted: rgba(255,255,255,0.62);
  --line: rgba(255,255,255,0.18);
  --card: rgba(0,0,0,0.10);
  --card-h: rgba(0,0,0,0.18);
}

html, body {
  margin: 0; padding: 0;
  background-color: #8c8f52 !important;
  color: #ffffff;
  font-family: 'Montserrat', sans-serif;
  min-height: 100vh;
  -webkit-text-size-adjust: 100%;
}

/* Обгортка яка перекриває все */
#app {
  background-color: #8c8f52;
  min-height: 100vh;
  width: 100%;
  position: relative;
}

* { margin:0; padding:0; box-sizing:border-box; }

.header {
  padding: 44px 52px 28px;
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
  border-bottom: 1px solid var(--line);
}

.eyebrow {
  display: block;
  font-size: 10px; font-weight: 300;
  letter-spacing: 0.42em; text-transform: uppercase;
  color: rgba(255,255,255,0.65); margin-bottom: 8px;
}

.title-main {
  font-family: 'Playfair Display', serif;
  font-size: clamp(52px, 7.5vw, 100px);
  font-weight: 700; line-height: 0.9;
  color: #ffffff; letter-spacing: -0.01em;
}
.title-main .price-it {
  font-style: italic; font-weight: 400;
  font-size: 0.47em; color: var(--gold);
  vertical-align: middle; letter-spacing: 0.08em;
}

.header-right { display:flex; flex-direction:column; align-items:flex-end; gap:12px; }

.per-kg {
  font-family: 'Playfair Display', serif;
  font-style: italic; font-size: 19px; color: var(--gold);
}

.cart-btn {
  background: #ffffff; color: #6b6e36;
  border: none; padding: 12px 22px;
  font-family: 'Montserrat', sans-serif;
  font-size: 10px; font-weight: 500;
  letter-spacing: 0.18em; text-transform: uppercase;
  cursor: pointer; transition: all .25s;
  display: flex; align-items: center; gap: 9px;
}
.cart-btn:hover { background: var(--gold); color: #ffffff; }

.cart-count {
  background: #6b6e36; color: #ffffff;
  width: 20px; height: 20px; border-radius: 50%;
  font-size: 11px; font-weight: 600;
  display: flex; align-items: center; justify-content: center;
  transition: transform .3s;
}
.cart-count.bump { transform: scale(1.5); }

/* FILTERS */
.filters {
  display: flex; gap: 6px;
  padding: 20px 52px; flex-wrap: wrap; align-items: center;
  border-bottom: 1px solid var(--line);
}
.filter-label {
  font-size: 9px; font-weight: 300;
  letter-spacing: 0.38em; text-transform: uppercase;
  color: var(--muted); margin-right: 6px;
}
.filter-btn {
  background: transparent;
  border: 1px solid rgba(255,255,255,0.26);
  color: rgba(255,255,255,0.7);
  padding: 6px 14px;
  font-family: 'Montserrat', sans-serif;
  font-size: 10px; font-weight: 300; letter-spacing: 0.06em;
  cursor: pointer; transition: all .2s;
}
.filter-btn:hover { border-color: var(--gold); color: var(--gold); }
.filter-btn.active {
  background: #ffffff; border-color: #ffffff;
  color: #6b6e36; font-weight: 500;
}

/* GRID */
.catalog {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 1px; padding: 1px 52px 52px; margin-top: 1px;
}

/* CARD */
.cake-card {
  background: rgba(0,0,0,0.10);
  padding: 24px 22px 18px;
  transition: background .28s, transform .28s;
  cursor: pointer;
  animation: fadeUp .4s ease both;
  position: relative;
}
.cake-card:hover { background: rgba(0,0,0,0.18); transform: translateY(-2px); }

@keyframes fadeUp {
  from { opacity:0; transform:translateY(14px); }
  to   { opacity:1; transform:translateY(0); }
}

.hit-badge {
  display: inline-block;
  background: var(--gold); color: #6b6e36;
  font-size: 8px; font-weight: 600;
  letter-spacing: 0.2em; text-transform: uppercase;
  padding: 3px 8px; margin-bottom: 10px;
}

.cake-emoji { font-size: 32px; margin-bottom: 10px; display: block; }

.cake-cat {
  font-size: 9px; font-weight: 300;
  letter-spacing: 0.34em; text-transform: uppercase;
  color: rgba(255,255,255,0.52); margin-bottom: 4px;
}

.cake-name {
  font-family: 'Playfair Display', serif;
  font-size: 24px; font-weight: 400;
  line-height: 1.15; color: #ffffff; margin-bottom: 6px;
}

.cake-desc {
  font-size: 11px; font-weight: 300;
  color: var(--muted); line-height: 1.6;
  margin-bottom: 16px; min-height: 32px;
}

.cake-footer {
  display: flex; align-items: center; justify-content: space-between;
  padding-top: 12px;
  border-top: 1px solid rgba(255,255,255,0.14);
}

.cake-price {
  font-family: 'Playfair Display', serif;
  font-size: 28px; font-weight: 400;
  color: #ffffff; letter-spacing: -0.02em;
}
.cake-price sup {
  font-size: 10px; font-family: 'Montserrat', sans-serif;
  font-weight: 200; color: var(--muted);
}

.add-btn {
  background: rgba(255,255,255,0.12);
  color: #ffffff;
  border: 1px solid rgba(255,255,255,0.3);
  width: 36px; height: 36px; font-size: 20px;
  cursor: pointer; transition: all .2s;
  display: flex; align-items: center; justify-content: center;
}
.add-btn:hover { background: var(--gold); border-color: var(--gold); color: #6b6e36; }
.add-btn.added { background: var(--gold); border-color: var(--gold); color: #6b6e36; font-size: 15px; }

/* FOOTER NOTE */
.page-footer {
  border-top: 1px solid var(--line);
  padding: 18px 52px;
  background: rgba(0,0,0,0.12);
  font-size: 11px; font-weight: 300;
  color: var(--muted); line-height: 1.8;
}
.page-footer strong { color: #ffffff; font-weight: 400; }

/* MODAL */
.modal-overlay {
  position: fixed; inset: 0;
  background: rgba(40,43,18,.8);
  backdrop-filter: blur(6px);
  z-index: 100;
  display: flex; align-items: center; justify-content: center;
  opacity: 0; pointer-events: none;
  transition: opacity .3s; padding: 20px;
}
.modal-overlay.open { opacity:1; pointer-events:all; }

.order-panel {
  background: #6b6e36;
  border: 1px solid rgba(255,255,255,0.15);
  width: 100%; max-width: 460px; max-height: 88vh;
  overflow-y: auto;
  transform: translateY(24px); transition: transform .32s ease;
}
.modal-overlay.open .order-panel { transform: translateY(0); }

.panel-header {
  padding: 22px 26px 16px;
  border-bottom: 1px solid var(--line);
  display: flex; align-items: center; justify-content: space-between;
  position: sticky; top:0; background: #6b6e36; z-index:1;
}
.panel-header h2 {
  font-family: 'Playfair Display', serif;
  font-size: 22px; font-weight: 400; color: #ffffff;
}
.close-btn {
  background: none; border: none; font-size: 18px;
  cursor: pointer; color: var(--muted); transition: color .2s;
}
.close-btn:hover { color: #ffffff; }

.cart-items { padding: 14px 26px; }
.cart-empty {
  text-align: center; padding: 30px 0;
  color: var(--muted); font-weight: 300; font-size: 13px;
}
.cart-empty span { display:block; font-size:34px; margin-bottom:8px; }

.cart-item {
  display: grid; grid-template-columns: 1fr auto;
  gap: 10px; align-items: start;
  padding: 12px 0; border-bottom: 1px solid rgba(255,255,255,0.1);
}
.cart-item-name { font-family: 'Playfair Display', serif; font-size: 17px; color: #ffffff; }
.cart-item-sub { font-size: 10px; font-weight: 300; color: var(--muted); margin-top: 3px; }
.weight-row { display:flex; gap:4px; margin-top:6px; flex-wrap:wrap; }
.weight-chip {
  background: rgba(255,255,255,0.09);
  border: 1px solid rgba(255,255,255,0.2);
  color: rgba(255,255,255,.65);
  padding: 2px 8px;
  font-family: 'Montserrat', sans-serif;
  font-size: 10px; font-weight: 300; cursor: pointer; transition: all .16s;
}
.weight-chip.active { background: var(--gold); border-color: var(--gold); color: #6b6e36; font-weight:500; }
.weight-chip:hover:not(.active) { border-color: var(--gold); color: var(--gold); }

.cart-item-right { display:flex; flex-direction:column; align-items:flex-end; gap:6px; }
.qty-ctrl { display:flex; align-items:center; gap:7px; }
.qty-btn {
  background: rgba(255,255,255,0.1); border:none; color: #ffffff;
  width:24px; height:24px; cursor:pointer; font-size:13px;
  display:flex; align-items:center; justify-content:center; transition: background .2s;
}
.qty-btn:hover { background: rgba(255,255,255,.2); }
.qty-num { font-size:13px; color:#ffffff; min-width:14px; text-align:center; }
.item-total { font-family:'Playfair Display',serif; font-size:18px; color:var(--gold); }

.total-bar {
  padding: 14px 26px; border-top: 1px solid var(--line);
  background: rgba(0,0,0,.2); position: sticky; bottom:0;
}
.total-row { display:flex; justify-content:space-between; align-items:center; margin-bottom:12px; }
.total-label { font-size:9px; font-weight:300; letter-spacing:.24em; text-transform:uppercase; color:var(--muted); }
.total-sum { font-family:'Playfair Display',serif; font-size:30px; font-weight:400; color:#ffffff; }

.order-cta {
  width:100%; background:#ffffff; color:#6b6e36;
  border:none; padding:13px;
  font-family:'Montserrat',sans-serif; font-size:10px; font-weight:500;
  letter-spacing:.22em; text-transform:uppercase; cursor:pointer; transition:all .25s;
}
.order-cta:hover { background:var(--gold); color:#ffffff; }
.order-cta:disabled { background:rgba(255,255,255,.15); color:var(--muted); cursor:default; }

.success-msg { display:none; text-align:center; padding:36px 26px; }
.success-msg.show { display:block; }
.success-msg .s-icon { font-size:44px; margin-bottom:10px; }
.success-msg h3 { font-family:'Playfair Display',serif; font-size:26px; font-weight:400; color:#ffffff; margin-bottom:8px; }
.success-msg p { font-size:12px; font-weight:300; color:var(--muted); line-height:1.7; }
.success-msg .order-cta { max-width:190px; margin:16px auto 0; display:block; }

::-webkit-scrollbar { width:3px; }
::-webkit-scrollbar-track { background:transparent; }
::-webkit-scrollbar-thumb { background:rgba(255,255,255,.2); }

@media (max-width:640px) {
  .header { padding:26px 18px 20px; flex-direction:column; align-items:flex-start; gap:14px; }
  .filters { padding:14px 18px; }
  .catalog { padding:1px 18px 36px; grid-template-columns:1fr; }
  .page-footer { padding:14px 18px; }
}
</style>
</head>
<body>
<div id="app">

<header class="header">
  <div>
    <span class="eyebrow">Авторська кондитерська</span>
    <h1 class="title-main">ТОРТИ <span class="price-it">price</span></h1>
  </div>
  <div class="header-right">
    <span class="per-kg">грн / 1 кг</span>
    <button class="cart-btn" onclick="openCart()">
      🛒 Кошик
      <span class="cart-count" id="cartCount">0</span>
    </button>
  </div>
</header>

<div class="filters">
  <span class="filter-label">Категорія:</span>
  <button class="filter-btn active" onclick="filterCakes('all',this)">Всі</button>
  <button class="filter-btn" onclick="filterCakes('classic',this)">Класика</button>
  <button class="filter-btn" onclick="filterCakes('premium',this)">Преміум</button>
  <button class="filter-btn" onclick="filterCakes('chocolate',this)">Шоколадні</button>
  <button class="filter-btn" onclick="filterCakes('fruit',this)">Фруктові</button>
  <button class="filter-btn" onclick="filterCakes('cheese',this)">Крем-чіз</button>
</div>

<div class="catalog" id="catalog"></div>

<div class="page-footer">
  <strong>Дизайн за вашим бажанням.</strong> Мінімальний входить у вартість (фрукти / надпис — не більше 3 слів).
  Додатково: коробка, складний дизайн, цукрова картинка / декор. <strong>Цукрова картинка — 200 грн / 1 шт.</strong>
</div>

<div class="modal-overlay" id="modal" onclick="closeOnOverlay(event)">
  <div class="order-panel">
    <div class="panel-header">
      <h2>Ваше замовлення</h2>
      <button class="close-btn" onclick="closeCart()">✕</button>
    </div>
    <div id="cartContent">
      <div class="cart-items" id="cartItems">
        <div class="cart-empty"><span>🎂</span>Оберіть торт з каталогу</div>
      </div>
      <div class="total-bar">
        <div class="total-row">
          <span class="total-label">Приблизна сума</span>
          <span class="total-sum" id="totalSum">0 ₴</span>
        </div>
        <button class="order-cta" id="orderBtn" onclick="placeOrder()" disabled>Замовити через Instagram</button>
      </div>
    </div>
    <div class="success-msg" id="successMsg">
      <div class="s-icon">🎉</div>
      <h3>Дякуємо!</h3>
      <p>Ваше замовлення сформовано.<br>Напишіть нам у Instagram і надішліть скріншот.</p>
      <button class="order-cta" onclick="resetCart()">Нове замовлення</button>
    </div>
  </div>
</div>

</div><!-- /#app -->

<script>
const CAKES = [
  {id:1,  name:'Фруктовий',        emoji:'🍓', desc:'Вершки · Ванільний бісквіт, сезонні фрукти',                                   price:750,  price2:null, category:['classic','fruit'],          featured:false},
  {id:16, name:'Фруктовий',        emoji:'🍓', desc:'Крем-чіз · Ванільний бісквіт, сезонні фрукти',                                  price:900,  price2:null, category:['classic','fruit','cheese'], featured:true},
  {id:2,  name:'Київський торт',   emoji:'🌰', desc:'Масляно-заварний крем, горіхове безе',                                          price:1000, category:['classic'],                  featured:true },
  {id:3,  name:'Прага',            emoji:'🍫', desc:'Шоколадний бісквіт, масляний шоколадний крем',                                  price:900,  category:['classic','chocolate'],      featured:false},
  {id:4,  name:'Шок манже',        emoji:'🍮', desc:'Шоколадний бісквіт, крем з вершкового масла і згущеного молока',               price:900,  category:['classic','chocolate'],      featured:false},
  {id:5,  name:'Три шоколади',     emoji:'🤎', desc:'Мус на основі чорного, молочного та білого шоколаду',                          price:900,  category:['premium','chocolate'],      featured:true },
  {id:6,  name:'Чізкейк',          emoji:'🧀', desc:'Основа пісочне тісто / орео, крем-чіз',                                        price:900,  category:['classic','cheese'],         featured:false},
  {id:7,  name:'Естерхазі',        emoji:'🥜', desc:'Коржі на основі грецького горіха, вершковий крем з волоськими горіхами',       price:1000, category:['premium'],                  featured:true },
  {id:8,  name:'Медовик',          emoji:'🍯', desc:'Вершково-сметанний крем, медові коржі',                                        price:800,  category:['classic'],                  featured:false},
  {id:9,  name:'Павлова',          emoji:'🫐', desc:'Безе, крем-чіз, маскарпоне, ягоди всередині',                                  price:1000, category:['premium','fruit','cheese'], featured:true },
  {id:10, name:'Тирамісу',         emoji:'☕', desc:'Вершковий мус маскарпоне, печиво савоярді з кавовим просоченням',              price:900,  category:['premium'],                  featured:false},
  {id:11, name:'Наполеон',         emoji:'🥐', desc:'Листкові коржі, заварний крем і згущене молоко за бажанням',                  price:800,  category:['classic'],                  featured:false},
  {id:12, name:'Захер',            emoji:'🍒', desc:'Шоколадний бісквіт, малиновий / абрикосовий джем',                            price:800,  category:['classic','chocolate'],      featured:false},
  {id:13, name:'Лаванда',          emoji:'💜', desc:'Лавандовий бісквіт, крем-чіз, конфі із смородини',                            price:900,  category:['premium','cheese'],         featured:false},
  {id:14, name:'Маракуйя–шпинат',  emoji:'💚', desc:'Шпинатний бісквіт, крем-чіз, маракуйя',                                      price:900,  category:['premium','fruit','cheese'], featured:false},
  {id:15, name:'Червоний оксамит', emoji:'❤️', desc:'Традиційно червоний бісквіт, крем-чіз',                                      price:900,  category:['premium','cheese'],         featured:false},
];

const WEIGHTS = [1,1.5,2,2.5,3];
let cart = {}, activeFilter = 'all';

function renderCatalog(filter) {
  activeFilter = filter;
  const el = document.getElementById('catalog');
  el.innerHTML = '';
  const shown = filter==='all' ? CAKES : CAKES.filter(c=>c.category.includes(filter));
  shown.forEach((cake,i) => {
    const inCart = !!cart[cake.id];
    const card = document.createElement('div');
    card.className = 'cake-card';
    card.style.animationDelay = (i*0.05)+'s';
    card.innerHTML = `
      ${cake.featured?'<span class="hit-badge">Хіт</span>':''}
      <span class="cake-emoji">${cake.emoji}</span>
      <div class="cake-cat">${cake.category.includes('premium')?'Преміум':'Класика'}</div>
      <div class="cake-name">${cake.name}</div>
      <div class="cake-desc">${cake.desc}</div>
      <div class="cake-footer">
        <div class="cake-price">${cake.price.toLocaleString()}<sup> ₴/кг</sup></div>
        <button class="add-btn ${inCart?'added':''}" onclick="addToCart(${cake.id})">${inCart?'✓':'+'}</button>
      </div>`;
    el.appendChild(card);
  });
}

function filterCakes(type,btn) {
  document.querySelectorAll('.filter-btn').forEach(b=>b.classList.remove('active'));
  btn.classList.add('active');
  renderCatalog(type);
}

function addToCart(id) {
  const cake = CAKES.find(c=>c.id===id);
  if (!cart[id]) cart[id]={cake,weight:1.5,qty:1};
  else cart[id].qty++;
  updateCartUI(); bumpCount(); renderCatalog(activeFilter); openCart();
}

function changeWeight(id,w) { if(cart[id]){cart[id].weight=w; renderCartItems();} }
function changeQty(id,delta) {
  if (!cart[id]) return;
  cart[id].qty+=delta;
  if (cart[id].qty<=0) delete cart[id];
  updateCartUI();
}

function updateCartUI() {
  const count = Object.values(cart).reduce((s,i)=>s+i.qty,0);
  document.getElementById('cartCount').textContent = count;
  renderCartItems();
  document.getElementById('orderBtn').disabled = count===0;
}

function renderCartItems() {
  const el = document.getElementById('cartItems');
  const items = Object.values(cart);
  if (!items.length) {
    el.innerHTML='<div class="cart-empty"><span>🎂</span>Оберіть торт з каталогу</div>';
    document.getElementById('totalSum').textContent='0 ₴'; return;
  }
  let total=0;
  el.innerHTML = items.map(({cake,weight,qty})=>{
    const sum=cake.price*weight*qty; total+=sum;
    return `<div class="cart-item">
      <div>
        <div class="cart-item-name">${cake.emoji} ${cake.name}</div>
        <div class="cart-item-sub">Оберіть вагу:</div>
        <div class="weight-row">
          ${WEIGHTS.map(w=>`<button class="weight-chip ${w===weight?'active':''}" onclick="changeWeight(${cake.id},${w})">${w} кг</button>`).join('')}
        </div>
      </div>
      <div class="cart-item-right">
        <div class="qty-ctrl">
          <button class="qty-btn" onclick="changeQty(${cake.id},-1)">−</button>
          <span class="qty-num">${qty}</span>
          <button class="qty-btn" onclick="changeQty(${cake.id},+1)">+</button>
        </div>
        <div class="item-total">${sum.toLocaleString()} ₴</div>
      </div>
    </div>`;
  }).join('');
  document.getElementById('totalSum').textContent=total.toLocaleString()+' ₴';
}

function bumpCount() {
  const el=document.getElementById('cartCount');
  el.classList.add('bump'); setTimeout(()=>el.classList.remove('bump'),300);
}

function openCart()  { document.getElementById('modal').classList.add('open'); }
function closeCart() { document.getElementById('modal').classList.remove('open'); }
function closeOnOverlay(e) { if(e.target===document.getElementById('modal')) closeCart(); }
function placeOrder() {
  document.getElementById('cartContent').style.display='none';
  document.getElementById('successMsg').classList.add('show');
}
function resetCart() {
  cart={}; updateCartUI();
  document.getElementById('cartContent').style.display='';
  document.getElementById('successMsg').classList.remove('show');
  closeCart(); renderCatalog('all');
  document.querySelectorAll('.filter-btn').forEach((b,i)=>b.classList.toggle('active',i===0));
}

renderCatalog('all');
</script>
</body>
</html>
