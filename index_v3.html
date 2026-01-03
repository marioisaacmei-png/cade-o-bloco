<!doctype html>
<html lang="pt-br">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Cadê o Bloco? — MVP (Mapa + Filtros + Cards)</title>

  <!-- Leaflet -->
  <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" />
  <script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>

  <style>
    :root{
      --bg:#0f0f0f;
      --panel:#121212;
      --line:#2b2b2b;
      --muted:#a8a8a8;

      --purple:#8b5cf6;
      --green:#00ff7f;
      --yellow:#ffd24d;
      --gray:#9a9a9a;
      --red:#ff4d4d;
      --orange:#ff8c00;

      --shadow: 0 12px 40px rgba(0,0,0,.55);
    }
    *{ box-sizing:border-box; }
    html,body{ height:100%; }
    body{
      margin:0;
      font-family: Arial, sans-serif;
      background:var(--bg);
      color:#fff;
      overflow-x:hidden;
    }

    /* TOPBAR */
    .topbar{
      position:sticky; top:0; z-index:10000;
      height:56px;
      display:flex; align-items:center; gap:12px;
      padding:10px 12px;
      background:linear-gradient(#121212,#0f0f0f);
      border-bottom:1px solid var(--line);
    }
    .brand{ font-weight:900; font-size:14px; white-space:nowrap; letter-spacing:.2px; }
    .search{
      flex:1; min-width:0;
      display:flex; align-items:center; gap:10px;
      background:#0c0c0c;
      border:1px solid var(--line);
      border-radius:999px;
      padding:10px 14px;
    }
    .search .icon{ color:var(--muted); }
    .search input{
      flex:1; min-width:0;
      background:transparent; border:none; outline:none;
      color:#fff; font-size:14px;
    }
    .actions{ display:flex; gap:10px; align-items:center; flex-shrink:0; }
    .btn{
      cursor:pointer;
      font-weight:900;
      border-radius:12px;
      padding:10px 12px;
      background:#141414;
      color:#fff;
      border:1px solid var(--line);
      display:flex; align-items:center; gap:8px;
      user-select:none;
      white-space:nowrap;
    }
    .btn.primary{ background:rgba(139,92,246,.18); border-color:rgba(139,92,246,.55); }
    .btn.tiny{ padding:10px 10px; }
    .dot{ width:8px; height:8px; border-radius:50%; background:var(--purple); }

    /* BANNER (file://) */
    .banner{
      display:none;
      padding:10px 12px;
      background:rgba(255,140,0,.14);
      border-bottom:1px solid rgba(255,140,0,.35);
      font-size:12px;
      color:#fff;
    }
    .banner b{ color:#fff; }

    /* MAP */
    #map{
      height:54vh;
      width:100%;
      position:relative;
      z-index:1;
    }

    /* CONTENT */
    .content{
      padding:12px;
      max-width:1200px;
      margin:0 auto;
      width:100%;
    }
    .sectionTitle{ font-weight:900; margin:10px 0 6px; font-size:14px; }
    .subtle{ color:var(--muted); font-size:12px; margin:0 0 10px; }

    .legend{
      display:flex; gap:10px; flex-wrap:wrap;
      margin:8px 0 12px;
      font-size:12px; color:var(--muted);
    }
    .legItem{ display:flex; align-items:center; gap:8px; }
    .legDot{ width:8px; height:8px; border-radius:50%; background:var(--gray); }
    .legDot.live{ background:var(--green); }
    .legDot.end{ background:var(--yellow); }
    .legDot.off{ background:var(--red); }
    .legDot.sched{ background:var(--gray); }

    .list{ display:flex; flex-direction:column; gap:10px; padding-bottom:34px; }

    /* CARD */
    .card{
      background:linear-gradient(#151515,#121212);
      border:1px solid var(--line);
      border-radius:14px;
      padding:12px;
      display:flex;
      justify-content:space-between;
      gap:12px;
      align-items:flex-start;
      box-shadow: 0 10px 28px rgba(0,0,0,.25);
      cursor:pointer;
    }
    .card:active{ transform: translateY(1px); }
    .left{ flex:1; min-width:0; }
    .titleRow{ display:flex; align-items:center; gap:8px; margin-bottom:6px; min-width:0; }
    .pin{ width:8px; height:8px; border-radius:50%; background:var(--gray); flex-shrink:0; }
    .pin.rolando{ background:var(--green); }
    .pin.terminando{ background:var(--yellow); }
    .pin.programado{ background:var(--gray); }
    .pin.encerrado{ background:var(--red); }

    .title{
      font-weight:900; font-size:14px;
      overflow:hidden; text-overflow:ellipsis; white-space:nowrap;
    }
    .meta{
      font-size:12px; color:var(--muted);
      display:flex; flex-direction:column; gap:4px;
      line-height:1.25;
    }
    .badges{
      display:flex; flex-direction:column; gap:8px;
      align-items:flex-end; flex-shrink:0;
      min-width:160px;
    }
    .badge{
      font-size:11px;
      padding:6px 10px;
      border-radius:999px;
      border:1px solid var(--line);
      background:#0e0e0e;
      color:#fff;
      white-space:nowrap;
    }
    .badge.green{ border-color:rgba(0,255,127,.35); background:rgba(0,255,127,.08); }
    .badge.yellow{ border-color:rgba(255,210,77,.35); background:rgba(255,210,77,.08); }
    .badge.gray{ border-color:rgba(154,154,154,.35); background:rgba(154,154,154,.08); }
    .badge.red{ border-color:rgba(255,77,77,.35); background:rgba(255,77,77,.08); }
    .badge.orange{ border-color:rgba(255,140,0,.35); background:rgba(255,140,0,.08); }

    .actionsRow{ margin-top:10px; display:flex; gap:10px; flex-wrap:wrap; }
    .btnSmall{
      cursor:pointer;
      font-weight:900;
      font-size:12px;
      border-radius:12px;
      padding:10px 12px;
      background:#141414;
      color:#fff;
      border:1px solid var(--line);
    }
    .btnSmall.primary{ background:rgba(255,210,77,.14); border-color:rgba(255,210,77,.35); }

    /* DRAWER (FILTROS) */
    .overlay{
      position:fixed; inset:0;
      background:rgba(0,0,0,.45);
      opacity:0; pointer-events:none;
      transition:opacity .18s ease;
      z-index:9998;
    }
    .overlay.open{ opacity:1; pointer-events:auto; }

    .drawer{
      position:fixed; top:0; right:0; height:100%;
      width:min(360px,92vw);
      background:linear-gradient(#121212,#0f0f0f);
      border-left:1px solid var(--line);
      transform:translateX(102%);
      transition:transform .18s ease;
      z-index:9999;
      padding:14px;
      display:flex; flex-direction:column; gap:12px;
      box-shadow:var(--shadow);
    }
    .drawer.open{ transform:translateX(0); }

    .drawerHeader{
      display:flex; align-items:center; justify-content:space-between; gap:10px;
      padding-top:6px;
    }
    .drawerTitle{ font-weight:900; font-size:14px; }
    .drawerTag{
      font-size:12px; color:var(--muted);
      padding:6px 10px;
      border:1px solid var(--line);
      border-radius:999px;
      background:#0c0c0c;
      white-space:nowrap;
    }
    .panel{
      background:linear-gradient(#141414,#101010);
      border:1px solid var(--line);
      border-radius:16px;
      padding:12px;
    }
    .panel h4{
      margin:0 0 10px;
      font-size:12px;
      color:var(--muted);
      font-weight:900;
      letter-spacing:.2px;
    }
    .chipRow{ display:flex; flex-wrap:wrap; gap:8px; }
    .chip{
      cursor:pointer; user-select:none;
      padding:8px 10px;
      border-radius:999px;
      border:1px solid var(--line);
      background:#0f0f0f;
      font-size:12px;
      font-weight:900;
      color:#fff;
    }
    .chip.active{ border-color:rgba(139,92,246,.55); background:rgba(139,92,246,.18); }

    .select{
      width:100%;
      background:#0c0c0c;
      border:1px solid var(--line);
      border-radius:12px;
      padding:10px 12px;
      color:#fff;
      outline:none;
      appearance:auto;
    }
    .hint{ font-size:12px; color:var(--muted); margin-top:8px; line-height:1.25; }

    .drawerActions{ margin-top:auto; display:flex; gap:10px; }
    .drawerActions .btn{ flex:1; justify-content:center; }

    /* MODAL (detalhe do bloco) */
    .modalOverlay{
      position:fixed; inset:0;
      background:rgba(0,0,0,.55);
      opacity:0; pointer-events:none;
      transition:opacity .18s ease;
      z-index:10020;
    }
    .modalOverlay.open{ opacity:1; pointer-events:auto; }

    .modal{
      position:fixed;
      left:50%; top:50%;
      transform:translate(-50%,-46%) scale(.98);
      width:min(520px,92vw);
      background:linear-gradient(#141414,#0f0f0f);
      border:1px solid var(--line);
      border-radius:18px;
      box-shadow:var(--shadow);
      padding:14px;
      opacity:0;
      pointer-events:none;
      transition:opacity .18s ease, transform .18s ease;
      z-index:10021;
    }
    .modal.open{
      opacity:1;
      pointer-events:auto;
      transform:translate(-50%,-50%) scale(1);
    }
    .modalHeader{ display:flex; justify-content:space-between; align-items:flex-start; gap:10px; }
    .modalTitle{ font-weight:900; font-size:16px; line-height:1.15; }
    .modalClose{
      cursor:pointer;
      border:1px solid var(--line);
      background:#0c0c0c;
      color:#fff;
      border-radius:12px;
      padding:8px 10px;
      font-weight:900;
      white-space:nowrap;
    }
    .modalBody{ margin-top:10px; color:var(--muted); font-size:13px; line-height:1.35; }
    .modalGrid{ display:grid; grid-template-columns:1fr 1fr; gap:10px; margin-top:10px; }
    .miniCard{
      border:1px solid var(--line);
      background:#0c0c0c;
      border-radius:14px;
      padding:10px;
      color:#fff;
      font-size:12px;
    }
    .miniCard b{ display:block; margin-bottom:4px; font-size:11px; color:var(--muted); }
    .modalActions{ margin-top:12px; display:flex; gap:10px; flex-wrap:wrap; }
    .modalActions a, .modalActions button{
      text-decoration:none;
      cursor:pointer;
      border:1px solid var(--line);
      background:#0c0c0c;
      color:#fff;
      border-radius:12px;
      padding:10px 12px;
      font-weight:900;
      font-size:12px;
    }
    .modalActions a.primary, .modalActions button.primary{
      background:rgba(255,210,77,.14);
      border-color:rgba(255,210,77,.35);
    }

    /* Leaflet fix */
    .leaflet-pane, .leaflet-top, .leaflet-bottom, .leaflet-control-container{ z-index:10 !important; }
    .leaflet-control-zoom a{
      background:#0f0f0f !important;
      color:#fff !important;
      border:1px solid var(--line) !important;
    }

    @media (max-width:560px){
      .badges{ min-width:120px; }
      #map{ height:52vh; }
      .btn{ padding:10px 10px; }
      .modalGrid{ grid-template-columns:1fr; }
    }
  </style>
</head>

<body>
  <div class="banner" id="bannerFile">
    Você abriu como <b>arquivo local</b>. No Android, o GPS pode falhar em <b>file://</b>.
    Use o link <b>HTTPS</b> (GitHub Pages/Netlify) para o botão <b>Eu</b> funcionar.
  </div>

  <div class="topbar">
    <div class="brand">CADÊ O BLOCO?</div>

    <div class="search">
      <span class="icon">🔎</span>
      <input id="q" type="text" placeholder="Buscar bloco (ex.: Serasa)" />
    </div>

    <div class="actions">
      <button class="btn primary" id="btnEu" type="button" title="Centralizar em mim (GPS)">
        <span class="dot"></span> Eu
      </button>
      <button class="btn tiny" id="btnMapMode" type="button" title="Alternar Mapa/Satélite">🛰 Satélite</button>
      <button class="btn" id="btnFiltros" type="button" title="Abrir filtros">⚙️ Filtros</button>
    </div>
  </div>

  <div id="map"></div>

  <div class="content">
    <div class="sectionTitle">Blocos próximos</div>
    <div class="subtle" id="subtitle">Ordenado por distância (se GPS permitido)</div>

    <div class="legend">
      <div class="legItem"><span class="legDot live"></span>Ao vivo</div>
      <div class="legItem"><span class="legDot end"></span>Terminando</div>
      <div class="legItem"><span class="legDot sched"></span>Programado</div>
      <div class="legItem"><span class="legDot off"></span>Encerrado</div>
    </div>

    <div class="list" id="list"></div>
  </div>

  <!-- Drawer -->
  <div class="overlay" id="overlay"></div>
  <aside class="drawer" id="drawer" aria-hidden="true">
    <div class="drawerHeader">
      <div class="drawerTitle">Filtros (MVP)</div>
      <div class="drawerTag">DEMO</div>
    </div>

    <div class="panel">
      <h4>Status</h4>
      <div class="chipRow" id="statusChips">
        <div class="chip active" data-status="">Todos</div>
        <div class="chip" data-status="rolando">Ao vivo</div>
        <div class="chip" data-status="programado">Programado</div>
        <div class="chip" data-status="encerrado">Encerrado</div>
      </div>
      <div class="hint">“Terminando” aparece no card, mas não precisa ser filtro no MVP.</div>
    </div>

    <div class="panel">
      <h4>Proximidade</h4>
      <select class="select" id="radius">
        <option value="">Sem filtro</option>
        <option value="1">Até 1 km</option>
        <option value="3" selected>Até 3 km</option>
        <option value="5">Até 5 km</option>
      </select>
      <div class="hint">Sem GPS, este filtro não bloqueia a lista (melhor para demo).</div>
    </div>

    <div class="panel">
      <h4>Região</h4>
      <select class="select" id="region">
        <option value="">Todas</option>
      </select>
      <div class="hint">Busca por nome cobre grande parte da intenção do usuário.</div>
    </div>

    <div class="panel" style="opacity:.55">
      <h4>Estilo musical (Fase 2)</h4>
      <div class="hint">Desativado no MVP. Campo <b>genres</b> já existe no JSON.</div>
    </div>

    <div class="drawerActions">
      <button class="btn" id="clear" type="button">Limpar</button>
      <button class="btn primary" id="apply" type="button">Aplicar</button>
    </div>
  </aside>

  <!-- Modal detalhe -->
  <div class="modalOverlay" id="modalOverlay"></div>
  <div class="modal" id="modal">
    <div class="modalHeader">
      <div class="modalTitle" id="modalTitle">Bloco</div>
      <button class="modalClose" id="modalClose" type="button">Fechar</button>
    </div>
    <div class="modalBody" id="modalBody"></div>
    <div class="modalGrid" id="modalGrid"></div>
    <div class="modalActions" id="modalActions"></div>
  </div>

  <script>
    // ===== DADOS (10 blocos) =====
    const BLOCOS = [
      { id:"serasa", name:"Bloco do Serasa ✅", street:"Rua Augusta", region:"Consolação", status:"rolando", started_at:"15:10", crowd_level:"alto", nearby_people:12300, location:{lat:-23.5587,lng:-46.6622}, genres:["Samba/Pagode","Pop"] },
      { id:"se", name:"Bloco Alegria da Sé 🎉", street:"Praça da Sé", region:"Sé", status:"programado", started_at:"17:00", crowd_level:"medio", nearby_people:5200, location:{lat:-23.5505,lng:-46.6333}, genres:["Diversos"] },
      { id:"santacecilia", name:"Bloco Santa Cecília 🔥", street:"Av. São João", region:"Santa Cecília", status:"terminando", started_at:"14:20", crowd_level:"medio", nearby_people:7800, location:{lat:-23.5406,lng:-46.6517}, genres:["Rock"] },
      { id:"pinheiros", name:"Bloco de Pinheiros 🌿", street:"Rua dos Pinheiros", region:"Pinheiros", status:"rolando", started_at:"16:05", crowd_level:"alto", nearby_people:9600, location:{lat:-23.5619,lng:-46.6816}, genres:["Pop","Eletrônica"] },
      { id:"vilamadalena", name:"Bloco Vila Madalena 🎨", street:"Rua Aspicuelta", region:"Vila Madalena", status:"programado", started_at:"18:00", crowd_level:"medio", nearby_people:4300, location:{lat:-23.5566,lng:-46.6923}, genres:["Diversos"] },
      { id:"moema", name:"Bloco de Moema ✈️", street:"Av. Ibirapuera", region:"Moema", status:"rolando", started_at:"15:40", crowd_level:"medio", nearby_people:6100, location:{lat:-23.6030,lng:-46.6629}, genres:["Axé","Pop"] },
      { id:"ibirapuera", name:"Bloco do Ibirapuera 🌳", street:"Parque Ibirapuera", region:"Ibirapuera", status:"programado", started_at:"11:00", crowd_level:"baixo", nearby_people:1900, location:{lat:-23.5874,lng:-46.6576}, genres:["Família"] },
      { id:"casaverde", name:"Bloco Casa Verde 💚", street:"Av. Casa Verde", region:"Casa Verde", status:"encerrado", started_at:"12:00", crowd_level:"baixo", nearby_people:0, location:{lat:-23.5099,lng:-46.6557}, genres:["Samba/Pagode"] },
      { id:"tatutape", name:"Bloco do Tatuapé 🐯", street:"Rua Itapura", region:"Tatuapé", status:"rolando", started_at:"15:30", crowd_level:"medio", nearby_people:5400, location:{lat:-23.5403,lng:-46.5765}, genres:["Funk","Pop"] },
      { id:"barrafunda", name:"Bloco Barra Funda ⚽", street:"Rua Água Branca", region:"Barra Funda", status:"programado", started_at:"19:00", crowd_level:"medio", nearby_people:2600, location:{lat:-23.5250,lng:-46.6680}, genres:["Rock","Pop"] }
    ];

    // ===== MAPA (OSM + SATÉLITE) =====
    const map = L.map("map", { zoomControl:true }).setView([-23.5505, -46.6333], 12);

    const osm = L.tileLayer("https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png", {
      maxZoom: 19, attribution: "&copy; OpenStreetMap"
    }).addTo(map);

    // Esri Sat (sem key, ok p/ demo). Se falhar por rede, continua no OSM.
    const esriSat = L.tileLayer(
      "https://server.arcgisonline.com/ArcGIS/rest/services/World_Imagery/MapServer/tile/{z}/{y}/{x}",
      { maxZoom: 19, attribution: "Tiles &copy; Esri" }
    );

    let isSatellite = false;
    const btnMapMode = document.getElementById("btnMapMode");
    btnMapMode.addEventListener("click", ()=>{
      if(!isSatellite){
        map.removeLayer(osm);
        esriSat.addTo(map);
        isSatellite = true;
        btnMapMode.textContent = "🗺️ Mapa";
      }else{
        map.removeLayer(esriSat);
        osm.addTo(map);
        isSatellite = false;
        btnMapMode.textContent = "🛰 Satélite";
      }
    });

    const markersLayer = L.layerGroup().addTo(map);

    // ===== GPS =====
    let userPos = null;
    let userLayer = null;
    let watchId = null;

    function drawUserPin(lat, lng, accuracyMeters){
      if(userLayer){ map.removeLayer(userLayer); userLayer = null; }
      const radius = Math.min(Math.max(accuracyMeters || 70, 40), 160);
      const halo = L.circle([lat, lng], { radius, color:"#60a5fa", fillColor:"#60a5fa", fillOpacity:0.15, weight:1 });
      const dot = L.circleMarker([lat, lng], { radius:7, color:"#1d4ed8", fillColor:"#3b82f6", fillOpacity:1, weight:2 });
      userLayer = L.layerGroup([halo, dot]).addTo(map);
    }

    function focusOnMe(){
      if(location.protocol === "file:"){
        document.getElementById("bannerFile").style.display = "block";
      }
      if(!navigator.geolocation){
        alert("Geolocalização não disponível neste navegador.");
        return;
      }
      navigator.geolocation.getCurrentPosition(
        (pos) => {
          userPos = { lat: pos.coords.latitude, lng: pos.coords.longitude };
          drawUserPin(userPos.lat, userPos.lng, pos.coords.accuracy);
          map.setView([userPos.lat, userPos.lng], 15);

          if(watchId == null){
            watchId = navigator.geolocation.watchPosition(
              (p) => {
                userPos = { lat: p.coords.latitude, lng: p.coords.longitude };
                drawUserPin(userPos.lat, userPos.lng, p.coords.accuracy);
              },
              () => {},
              { enableHighAccuracy:true, maximumAge:15000, timeout:10000 }
            );
          }
          applyFilters(false);
        },
        (err) => {
          console.log("GPS erro:", err);
          alert("Não foi possível acessar sua localização. Verifique a permissão do navegador.");
        },
        { enableHighAccuracy:true, timeout:8000, maximumAge:15000 }
      );
    }
    document.getElementById("btnEu").addEventListener("click", focusOnMe);

    // ===== DRAWER =====
    const overlay = document.getElementById("overlay");
    const drawer = document.getElementById("drawer");
    let isDrawerOpen = false;

    function openDrawer(){
      isDrawerOpen = true;
      overlay.classList.add("open");
      drawer.classList.add("open");
      drawer.setAttribute("aria-hidden","false");
    }
    function closeDrawer(){
      isDrawerOpen = false;
      overlay.classList.remove("open");
      drawer.classList.remove("open");
      drawer.setAttribute("aria-hidden","true");
    }
    function toggleDrawer(){ isDrawerOpen ? closeDrawer() : openDrawer(); }

    document.getElementById("btnFiltros").addEventListener("click", toggleDrawer);
    overlay.addEventListener("click", closeDrawer);
    window.addEventListener("keydown",(e)=>{ if(e.key==="Escape"){ closeDrawer(); closeModal(); } });

    // ===== MODAL DETALHE =====
    const modalOverlay = document.getElementById("modalOverlay");
    const modal = document.getElementById("modal");
    const modalTitle = document.getElementById("modalTitle");
    const modalBody = document.getElementById("modalBody");
    const modalGrid = document.getElementById("modalGrid");
    const modalActions = document.getElementById("modalActions");
    document.getElementById("modalClose").addEventListener("click", closeModal);
    modalOverlay.addEventListener("click", closeModal);

    function openModal(bloco){
      modalTitle.textContent = bloco.name;

      const dist = userPos ? haversineKm(userPos.lat,userPos.lng,bloco.location.lat,bloco.location.lng) : null;
      modalBody.innerHTML = `
        📍 ${escapeHtml(bloco.street)} — ${escapeHtml(bloco.region)}<br/>
        ⏰ ${escapeHtml(bloco.started_at || "--:--")}<br/>
        👥 ${formatNum(bloco.nearby_people)} próximos
        ${dist!=null ? `<br/>📏 ${dist.toFixed(1)} km de você` : ``}
      `;

      const statusLabel = statusBadgeInfo(bloco.status).text;
      const crowdLabel = crowdBadgeInfo(bloco.crowd_level).text;

      modalGrid.innerHTML = `
        <div class="miniCard"><b>Status</b>${escapeHtml(statusLabel)}</div>
        <div class="miniCard"><b>Lotação</b>${escapeHtml(crowdLabel)}</div>
        <div class="miniCard"><b>Região</b>${escapeHtml(bloco.region)}</div>
        <div class="miniCard"><b>Estilo (fase 2)</b>${escapeHtml((bloco.genres||[]).join(", "))}</div>
      `;

      const dest = `${bloco.location.lat},${bloco.location.lng}`;
      const gmapsWalk = `https://www.google.com/maps/dir/?api=1&destination=${encodeURIComponent(dest)}&travelmode=walking`;
      const gmapsDrive = `https://www.google.com/maps/dir/?api=1&destination=${encodeURIComponent(dest)}&travelmode=driving`;
      const waze = `https://waze.com/ul?ll=${encodeURIComponent(dest)}&navigate=yes`;
      const uber = `https://m.uber.com/ul/?action=setPickup&dropoff[latitude]=${encodeURIComponent(bloco.location.lat)}&dropoff[longitude]=${encodeURIComponent(bloco.location.lng)}&dropoff[nickname]=${encodeURIComponent(bloco.name)}`;
      const ninenine = `https://99app.com/`;

      modalActions.innerHTML = `
        <button class="primary" type="button" id="modalFocus">Ver no mapa</button>
        <a class="primary" href="${gmapsWalk}" target="_blank" rel="noopener">Google Maps (a pé)</a>
        <a href="${waze}" target="_blank" rel="noopener">Waze</a>
        <a href="${uber}" target="_blank" rel="noopener">Uber</a>
        <a href="${ninenine}" target="_blank" rel="noopener">99</a>
      `;
      document.getElementById("modalFocus").addEventListener("click", ()=>{
        closeModal();
        map.setView([bloco.location.lat, bloco.location.lng], 16);
      });

      modalOverlay.classList.add("open");
      modal.classList.add("open");
    }

    function closeModal(){
      modalOverlay.classList.remove("open");
      modal.classList.remove("open");
    }

    // ===== FILTROS + BUSCA =====
    const elQ = document.getElementById("q");
    const elRegion = document.getElementById("region");
    const elRadius = document.getElementById("radius");
    const elList = document.getElementById("list");
    const elSubtitle = document.getElementById("subtitle");

    let selectedStatus = "";
    let currentFiltered = [...BLOCOS];

    // popular regiões
    const regions = Array.from(new Set(BLOCOS.map(b=>b.region))).sort((a,b)=>a.localeCompare(b,"pt-BR"));
    regions.forEach(r=>{
      const opt = document.createElement("option");
      opt.value = r; opt.textContent = r;
      elRegion.appendChild(opt);
    });

    document.getElementById("statusChips").addEventListener("click",(e)=>{
      const chip = e.target.closest(".chip");
      if(!chip) return;
      selectedStatus = chip.dataset.status || "";
      document.querySelectorAll("#statusChips .chip").forEach(c=>c.classList.remove("active"));
      chip.classList.add("active");
    });

    document.getElementById("apply").addEventListener("click", ()=>{
      applyFilters(true);
      closeDrawer();
    });

    document.getElementById("clear").addEventListener("click", ()=>{
      selectedStatus = "";
      document.querySelectorAll("#statusChips .chip").forEach(c=>c.classList.remove("active"));
      document.querySelector('#statusChips .chip[data-status=""]').classList.add("active");
      elRadius.value = "3";
      elRegion.value = "";
      elQ.value = "";
      applyFilters(true);
    });

    elQ.addEventListener("input", ()=>applyFilters(false));
    elQ.addEventListener("keydown",(e)=>{ if(e.key==="Enter") applyFilters(false); });

    function applyFilters(shouldFitBounds){
      const q = (elQ.value || "").trim().toLowerCase();
      const region = elRegion.value;
      const radiusKm = elRadius.value ? Number(elRadius.value) : null;

      currentFiltered = BLOCOS.filter(b=>{
        if(q && !b.name.toLowerCase().includes(q)) return false;
        if(region && b.region !== region) return false;
        if(selectedStatus && b.status !== selectedStatus) return false;

        if(radiusKm != null && userPos){
          const d = haversineKm(userPos.lat, userPos.lng, b.location.lat, b.location.lng);
          if(d > radiusKm) return false;
        }
        return true;
      });

      if(userPos){
        currentFiltered.sort((a,b)=>
          haversineKm(userPos.lat, userPos.lng, a.location.lat, a.location.lng) -
          haversineKm(userPos.lat, userPos.lng, b.location.lat, b.location.lng)
        );
        elSubtitle.textContent = "Ordenado por distância";
      } else {
        elSubtitle.textContent = "Ordenação padrão (GPS não disponível)";
      }

      renderMap(currentFiltered, shouldFitBounds);
      renderList(currentFiltered);
    }

    // ===== RENDER =====
    function statusColor(status){
      if(status==="rolando") return "#00ff7f";
      if(status==="terminando") return "#ffd24d";
      if(status==="encerrado") return "#ff4d4d";
      return "#9a9a9a";
    }
    function statusBadgeInfo(status){
      if(status==="rolando") return { cls:"green", text:"Ao vivo (GPS)" };
      if(status==="terminando") return { cls:"yellow", text:"Terminando" };
      if(status==="encerrado") return { cls:"red", text:"Encerrado" };
      return { cls:"gray", text:"Programado" };
    }
    function crowdBadgeInfo(level){
      if(level==="alto") return { cls:"orange", text:"Alta" };
      if(level==="medio") return { cls:"yellow", text:"Média" };
      return { cls:"gray", text:"Baixa" };
    }

    function renderMap(blocos, shouldFitBounds){
      markersLayer.clearLayers();

      blocos.forEach(b=>{
        const col = statusColor(b.status);
        const marker = L.circleMarker([b.location.lat, b.location.lng], {
          radius: 9, color: col, fillColor: col, fillOpacity: 0.95, weight: 0
        }).addTo(markersLayer);

        marker.on("click", ()=>{
          openModal(b);
        });

        marker.bindTooltip(b.name, { direction:"top", offset:[0,-8], opacity:0.9 });
      });

      if(shouldFitBounds && blocos.length){
        const bounds = L.latLngBounds(blocos.map(b=>[b.location.lat,b.location.lng]));
        map.fitBounds(bounds.pad(0.25));
      }
    }

    function renderList(blocos){
      elList.innerHTML = "";

      if(!blocos.length){
        const div = document.createElement("div");
        div.className = "card";
        div.style.cursor = "default";
        div.innerHTML = `
          <div class="left">
            <div class="titleRow"><span class="pin programado"></span><div class="title">Nenhum bloco encontrado</div></div>
            <div class="meta"><div>Tente limpar filtros ou buscar outro nome.</div></div>
          </div>
        `;
        elList.appendChild(div);
        return;
      }

      blocos.forEach(b=>{
        const dist = userPos ? haversineKm(userPos.lat,userPos.lng,b.location.lat,b.location.lng) : null;
        const s = statusBadgeInfo(b.status);
        const c = crowdBadgeInfo(b.crowd_level);

        const div = document.createElement("div");
        div.className = "card";
        div.innerHTML = `
          <div class="left">
            <div class="titleRow">
              <span class="pin ${b.status}"></span>
              <div class="title">${escapeHtml(b.name)}</div>
            </div>
            <div class="meta">
              <div>📍 ${escapeHtml(b.street)} — ${escapeHtml(b.region)}</div>
              <div>⏰ ${escapeHtml(b.started_at || "--:--")} • ${dist != null ? `📏 ${dist.toFixed(1)} km • ` : ""}👥 ${formatNum(b.nearby_people)} próximos</div>
            </div>
            <div class="actionsRow">
              <button class="btnSmall primary" type="button" data-action="details">VER DETALHES</button>
              <button class="btnSmall" type="button" data-action="focus">VER NO MAPA</button>
            </div>
          </div>
          <div class="badges">
            <div class="badge ${s.cls}">${s.text}${b.started_at ? ` • desde ${escapeHtml(b.started_at)}` : ""}</div>
            <div class="badge ${c.cls}">Lotação: ${c.text}</div>
          </div>
        `;

        div.addEventListener("click", ()=>openModal(b));
        div.querySelector('[data-action="details"]').addEventListener("click",(e)=>{ e.stopPropagation(); openModal(b); });
        div.querySelector('[data-action="focus"]').addEventListener("click",(e)=>{ e.stopPropagation(); map.setView([b.location.lat,b.location.lng],16); });

        elList.appendChild(div);
      });
    }

    // ===== INIT =====
    if(location.protocol === "file:"){
      document.getElementById("bannerFile").style.display = "block";
    }
    renderMap(BLOCOS, true);
    renderList(BLOCOS);

    // ===== HELPERS =====
    function formatNum(n){
      try{ return Number(n).toLocaleString("pt-BR"); }catch(e){ return String(n); }
    }
    function escapeHtml(str){
      return String(str)
        .replaceAll("&","&amp;")
        .replaceAll("<","&lt;")
        .replaceAll(">","&gt;")
        .replaceAll('"',"&quot;")
        .replaceAll("'","&#039;");
    }
    function haversineKm(lat1, lon1, lat2, lon2){
      const R=6371;
      const toRad = x => x*Math.PI/180;
      const dLat=toRad(lat2-lat1);
      const dLon=toRad(lon2-lon1);
      const a=Math.sin(dLat/2)**2 + Math.cos(toRad(lat1))*Math.cos(toRad(lat2))*Math.sin(dLon/2)**2;
      return 2*R*Math.atan2(Math.sqrt(a),Math.sqrt(1-a));
    }
  </script>
</body>
</html>
