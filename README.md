# UNISEFE-WEB-CAD-2D
<!doctype html>
<html lang="it">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>Unisefe CAD</title>
<style>
:root{
  --topbar-h:0px;
  --toolbar-h:44px;
  --panel-w:320px;
  --border:#d9d9d9;
  --bg:#f3f3f3;
  --surface:#ffffff;
  --text:#111111;
  --muted:#666666;
  --radius:8px;
  --icon:20px;
  --control:32px;
  --gap:8px;
}
*{box-sizing:border-box}
html,body{width:100%;height:100%;margin:0}
body{
  font-family:system-ui,-apple-system,BlinkMacSystemFont,"Segoe UI",sans-serif;
  color:var(--text);
  background:var(--bg);
  overflow:hidden;
}
button,input,select,textarea{font:inherit}
button{color:inherit}

.app{
  width:100vw;
  height:100vh;
  display:grid;
  grid-template-rows:var(--toolbar-h) 1fr;
  background:var(--bg);
}

.topbar{
  display:grid;
  grid-template-columns:auto 1fr auto;
  align-items:center;
  gap:12px;
  padding:0 12px;
  background:var(--surface);
  border-bottom:1px solid var(--border);
}
.brand{
  font-weight:700;
  letter-spacing:.02em;
  white-space:nowrap;
}
.mode-tabs{
  display:flex;
  align-items:center;
  justify-content:center;
  gap:4px;
  min-width:0;
}
.mode-tab{
  width:36px;
  height:32px;
  padding:0;
  display:grid;
  place-items:center;
  border:1px solid transparent;
  border-radius:var(--radius);
  background:transparent;
  cursor:pointer;
}
.mode-tab svg{
  width:20px;
  height:20px;
  stroke:currentColor;
  fill:none;
  stroke-width:1.8;
  stroke-linecap:round;
  stroke-linejoin:round;
}
.mode-tab:hover{background:#f2f2f2}
.mode-tab[aria-selected="true"]{
  background:#111;
  color:#fff;
}
.top-actions{
  display:flex;
  align-items:center;
  gap:4px;
}

.toolbar{
  display:flex;
  align-items:center;
  gap:var(--gap);
  padding:0 10px;
  background:var(--surface);
  border-bottom:1px solid var(--border);
  overflow:hidden;
}
.tool-group{
  display:flex;
  align-items:center;
  gap:4px;
}
.tool-separator{
  width:1px;
  height:24px;
  background:var(--border);
  flex:0 0 auto;
}
.icon-btn{
  width:var(--control);
  height:var(--control);
  padding:0;
  display:grid;
  place-items:center;
  border:1px solid transparent;
  border-radius:var(--radius);
  background:transparent;
  cursor:pointer;
  flex:0 0 auto;
}
.icon-btn:hover{background:#f1f1f1;border-color:#e5e5e5}
.icon-btn svg{
  width:var(--icon);
  height:var(--icon);
  stroke:currentColor;
  fill:none;
  stroke-width:1.8;
  stroke-linecap:round;
  stroke-linejoin:round;
}

.workspace{
  min-height:0;
  display:grid;
  grid-template-columns:minmax(0,1fr) var(--panel-w);
  background:var(--bg);
}


.stage{
  min-width:0;
  min-height:0;
  padding:16px;
  overflow:auto;
  display:grid;
  place-items:start center;
  background:#e9e9e9;
}
.canvas-frame{
  width:min(1200px,100%);
  min-height:calc(100vh - var(--topbar-h) - var(--toolbar-h) - 32px);
  background:#fff;
  border:1px solid #d6d6d6;
  box-shadow:0 2px 8px rgba(0,0,0,.06);
  position:relative;
  overflow:hidden;
}
.canvas-placeholder{
  min-height:700px;
  display:grid;
  place-items:center;
  color:#999;
  text-align:center;
  padding:40px;
}

.rightpanel{
  min-width:0;
  background:var(--surface);
  border-left:1px solid var(--border);
  display:grid;
  grid-template-rows:auto 1fr;
}
.panel-head{
  height:44px;
  display:flex;
  align-items:center;
  justify-content:space-between;
  gap:8px;
  padding:0 10px 0 14px;
  border-bottom:1px solid var(--border);
}
.panel-title{
  font-size:14px;
  font-weight:650;
}
.panel-body{
  min-height:0;
  overflow:auto;
  padding:12px;
}
.panel-section{
  border-bottom:1px solid #ececec;
  padding:0 0 12px;
  margin:0 0 12px;
}
.panel-section:last-child{border-bottom:0}
.panel-section h3{
  margin:0 0 8px;
  font-size:12px;
  text-transform:uppercase;
  letter-spacing:.06em;
  color:var(--muted);
}
.field{
  display:grid;
  grid-template-columns:90px 1fr;
  align-items:center;
  gap:8px;
  min-height:34px;
  font-size:13px;
}
.field input,
.field select{
  width:100%;
  min-width:0;
  height:30px;
  border:1px solid var(--border);
  border-radius:6px;
  padding:0 8px;
  background:#fff;
}


.document-surface{
  display:flex;
  justify-content:center;
  align-items:flex-start;
  padding:32px;
  background:#dedede;
}
.document-page{
  width:min(794px,100%);
  min-height:1123px;
  background:#fff;
  padding:76px 82px;
  outline:none;
  color:#111;
  font-size:16px;
  line-height:1.6;
  box-shadow:0 2px 12px rgba(0,0,0,.08);
}
.document-page h1{
  margin:0 0 24px;
  font-size:32px;
  line-height:1.2;
}
.document-page p{margin:0 0 1em}
.document-page:focus{box-shadow:0 0 0 1px #cfcfcf,0 2px 12px rgba(0,0,0,.08)}


.sheet-surface{
  width:100%;
  height:100%;
  min-height:100%;
  background:#fff;
  overflow:auto;
  position:relative;
}
.sheet-wrap{
  min-width:100%;
  min-height:100%;
  background:#fff;
  padding:0 0 40px;
}
.sheet-grid{
  display:grid;
  grid-template-columns:46px repeat(8,minmax(110px,1fr));
  grid-auto-rows:32px;
  border-top:1px solid #dfe3e8;
  border-left:1px solid #dfe3e8;
  min-width:930px;
  width:100%;
}
.sheet-cell,
.sheet-head,
.sheet-rowhead{
  border-right:1px solid #e2e5e9;
  border-bottom:1px solid #e2e5e9;
  min-width:0;
}
.sheet-head,
.sheet-rowhead{
  display:flex;
  align-items:center;
  justify-content:center;
  background:#f7f8fa;
  font-size:12px;
  font-weight:600;
  color:#5b6470;
  user-select:none;
}
.sheet-head,
.sheet-rowhead{cursor:pointer}
.sheet-head.is-selected,
.sheet-rowhead.is-selected{
  background:#e9eaec;
  color:#111;
  box-shadow:inset 0 0 0 1px #111;
}

.sheet-head{
  position:sticky;
  top:34px;
  z-index:3;
}
.sheet-rowhead{
  position:sticky;
  left:0;
  z-index:2;
}
.sheet-cell{
  padding:5px 8px;
  outline:none;
  background:#fff;
  font-size:13px;
  line-height:21px;
  white-space:nowrap;
  overflow:hidden;
}
.sheet-cell:hover{
  background:#fafbfc;
}
.sheet-cell.is-merged-master{
  position:relative;
  z-index:2;
  overflow:hidden;
  background:#fff;
}
.sheet-cell.is-merged-hidden{
  visibility:hidden;
  pointer-events:none;
}

.sheet-cell:focus,
.sheet-cell.is-active{
  position:relative;
  z-index:1;
  box-shadow:inset 0 0 0 2px #111;
  background:#fff;
}
.sheet-cell.is-selected{
  background:#e9edf2;
  box-shadow:inset 0 0 0 1px #6d7680;
}
.sheet-cell.is-selected.is-active{
  box-shadow:inset 0 0 0 2px #111;
}

.sheet-corner{cursor:pointer}
.sheet-corner.is-selected{background:#e9eaec;box-shadow:inset 0 0 0 1px #111}
.sheet-cell.format-border-all{border-color:#111}
.sheet-cell.format-border-none{border-color:transparent}

.sheet-formula{
  height:34px;
  display:grid;
  grid-template-columns:64px 1fr;
  position:sticky;
  top:0;
  z-index:5;
  border-bottom:1px solid #dfe3e8;
  background:#fff;
}
.sheet-namebox,
.sheet-formulabox{
  height:33px;
  border:0;
  border-right:1px solid #dfe3e8;
  padding:0 10px;
  outline:none;
  background:#fff;
  font-size:13px;
}
.sheet-namebox{
  text-align:center;
  font-weight:600;
  color:#3e4650;
  background:#fafafa;
}
.sheet-formulabox{
  border-right:0;
}
.sheet-formulabox:focus{
  box-shadow:inset 0 0 0 1px #111;
}


.cad-surface{position:absolute;inset:0;background:#fff;overflow:hidden}
#cad-canvas{display:block;width:100%;height:100%;touch-action:none;cursor:crosshair;background:#fff}
.cad-hud{position:absolute;left:10px;bottom:10px;display:flex;gap:6px;pointer-events:none;flex-wrap:wrap}
.cad-chip{background:rgba(255,255,255,.94);border:1px solid var(--border);border-radius:6px;padding:5px 8px;font-size:11px;color:#555}
#toolbar-cad{overflow-x:auto;min-width:0}
#toolbar-cad .icon-btn{font-size:11px;font-weight:650}
.icon-btn.active{background:#111;color:#fff;border-color:#111}
.cad-panel-actions{display:grid;grid-template-columns:repeat(2,minmax(0,1fr));gap:6px}
.cad-panel-actions button{height:32px;border:1px solid var(--border);background:#fff;border-radius:6px;cursor:pointer}
.cad-panel-actions button:hover,.cad-panel-actions button.active{background:#111;color:#fff}
riki-space{display:none}

.hidden{display:none!important}

@media (max-width:900px){
  :root{--panel-w:280px}
}
@media (max-width:720px){
  .workspace{grid-template-columns:minmax(0,1fr)}
  .rightpanel{
    position:fixed;
    top:calc(var(--topbar-h) + var(--toolbar-h));
    right:0;
    bottom:0;
    width:min(var(--panel-w),88vw);
    z-index:20;
    box-shadow:-8px 0 24px rgba(0,0,0,.12);
  }
}

#print-layer{display:none}
@media print{
  @page{margin:12mm}
  body *{visibility:hidden!important}
  #print-layer,#print-layer *{visibility:visible!important}
  #print-layer{display:block!important;position:absolute!important;inset:0!important;width:100%!important;min-height:100%!important;background:#fff!important;color:#111!important;overflow:visible!important}
  #print-layer .print-document{width:100%!important;min-height:auto!important;box-shadow:none!important;border:0!important;margin:0!important}
  #print-layer .print-sheet-table{border-collapse:collapse;width:auto;max-width:100%;font:12px system-ui,sans-serif}
  #print-layer .print-sheet-table td{min-width:80px;height:28px;padding:4px 6px;border:1px solid #cfd3d8;vertical-align:middle;white-space:nowrap}
  #print-layer .print-sheet-window{position:relative;overflow:hidden;background:#fff}
  #print-layer .print-sheet-window-inner{position:absolute;transform-origin:top left}
  #print-layer .print-cad-image{display:block;max-width:100%;max-height:calc(100vh - 24mm);margin:0 auto;object-fit:contain}
}





/* WordPress: right panel only — fixed header, scrollable body */
.rightpanel{
  display:flex !important;
  flex-direction:column !important;
  overflow:hidden !important;
}
.rightpanel .panel-head{
  flex:0 0 auto !important;
}
.rightpanel .panel-body{
  flex:1 1 auto !important;
  min-height:0 !important;
  overflow-y:auto !important;
  overflow-x:hidden !important;
  -webkit-overflow-scrolling:touch;
}


.topbar{display:none!important}
.mode-tabs{display:none!important}


/* Unisefe responsive layer 1.0.3 */
html,body,.app{width:100%;height:100vh;height:100dvh;max-width:100%;overflow:hidden}
.app{min-width:0}
.toolbar{
  min-width:0;
  overflow-x:auto;
  overflow-y:hidden;
  -webkit-overflow-scrolling:touch;
  scrollbar-width:thin;
  overscroll-behavior-x:contain;
}
.toolbar>.tool-group{flex:0 0 auto}
.rightpanel.hidden{display:none!important}
.stage{overscroll-behavior:contain}

@media (max-width:900px){
  :root{--panel-w:280px;--gap:6px}
  .toolbar{padding-inline:8px}
  .stage{padding:10px}
  .document-surface{padding:20px}
  .document-page{padding:52px 48px}
}

@media (max-width:720px){
  :root{--toolbar-h:42px;--control:34px;--icon:19px}
  .toolbar{gap:5px;padding-inline:6px}
  .tool-group{gap:2px}
  .tool-separator{height:22px}
  .workspace{position:relative;grid-template-columns:minmax(0,1fr);min-width:0}
  .stage{padding:6px;min-width:0}
  .canvas-frame{width:100%;min-height:calc(100dvh - var(--toolbar-h) - 12px)}
  .document-surface{padding:10px}
  .document-page{
    width:100%;
    min-height:calc(100dvh - var(--toolbar-h) - 32px);
    padding:34px 24px;
    box-shadow:0 1px 5px rgba(0,0,0,.08);
  }
  .document-page h1{font-size:27px;margin-bottom:18px}
  .sheet-grid{grid-template-columns:42px repeat(8,minmax(96px,1fr));min-width:810px}
  .rightpanel{
    position:absolute!important;
    left:0!important;
    right:0!important;
    top:auto!important;
    bottom:0!important;
    width:100%!important;
    max-width:none!important;
    height:min(44dvh,390px)!important;
    border-left:0!important;
    border-top:1px solid var(--border)!important;
    box-shadow:0 -8px 24px rgba(0,0,0,.12)!important;
    z-index:30!important;
  }
  .rightpanel .panel-head{height:42px;min-height:42px}
  .rightpanel .panel-body{padding:10px 12px calc(12px + env(safe-area-inset-bottom))}
  .field{grid-template-columns:82px minmax(0,1fr)}
  .cad-hud{left:6px;right:6px;bottom:6px}
}

@media (max-width:480px){
  :root{--toolbar-h:40px;--control:32px;--icon:18px;--gap:4px}
  .toolbar{padding-inline:4px}
  .icon-btn{border-radius:6px}
  .stage{padding:4px}
  .document-surface{padding:6px}
  .document-page{padding:26px 18px;font-size:15px;line-height:1.55}
  .document-page h1{font-size:24px}
  .rightpanel{height:min(48dvh,360px)!important}
  .panel-section{margin-bottom:10px;padding-bottom:10px}
  .field{grid-template-columns:74px minmax(0,1fr);gap:6px;font-size:12px}
  .field input,.field select{height:32px}
  .cad-panel-actions{grid-template-columns:1fr 1fr}
  .cad-chip{font-size:10px;padding:4px 6px}
}

@media (max-width:360px){
  .document-page{padding:22px 14px}
  .field{grid-template-columns:68px minmax(0,1fr)}
}

</style>
</head>
<body>
<div class="app">

  <header class="topbar">

    <nav class="mode-tabs" aria-label="Applicazioni">
      <button class="mode-tab" aria-selected="true" data-mode="document" title="Document" aria-label="Document">
        <svg viewBox="0 0 24 24"><path d="M6 3h9l3 3v15H6z"/><path d="M15 3v4h4"/><path d="M9 11h6M9 15h6"/></svg>
      </button>
      <button class="mode-tab" aria-selected="false" data-mode="sheet" title="Sheet" aria-label="Sheet">
        <svg viewBox="0 0 24 24"><rect x="4" y="4" width="16" height="16" rx="2"/><path d="M4 10h16M4 15h16M10 4v16M15 4v16"/></svg>
      </button>
      <button class="mode-tab" aria-selected="false" data-mode="cad" title="CAD" aria-label="CAD">
        <svg viewBox="0 0 24 24"><path d="M4 19 12 5l8 14z"/><path d="M8 16h8"/><circle cx="12" cy="10" r="1.5"/></svg>
      </button>
    </nav>

    <div class="top-actions"></div>
  </header>

  <div class="toolbar">
    <div class="tool-group">
      <button class="icon-btn" title="Undo" aria-label="Undo">
        <svg viewBox="0 0 24 24"><path d="M9 7 4 12l5 5"/><path d="M4 12h9a7 7 0 0 1 7 7"/></svg>
      </button>
      <button class="icon-btn" title="Redo" aria-label="Redo">
        <svg viewBox="0 0 24 24"><path d="m15 7 5 5-5 5"/><path d="M20 12h-9a7 7 0 0 0-7 7"/></svg>
      </button>
    </div>
    <div class="tool-separator"></div>
<div class="tool-group" id="toolbar-context">
      <button class="icon-btn doc-tool" data-cmd="bold" title="Bold" aria-label="Bold">
        <svg viewBox="0 0 24 24"><path d="M8 5h5a4 4 0 0 1 0 8H8z"/><path d="M8 13h6a3 3 0 0 1 0 6H8z"/></svg>
      </button>
      <button class="icon-btn doc-tool" data-cmd="italic" title="Italic" aria-label="Italic">
        <svg viewBox="0 0 24 24"><path d="M10 5h7M7 19h7M14 5 10 19"/></svg>
      </button>
      <button class="icon-btn doc-tool" data-cmd="underline" title="Underline" aria-label="Underline">
        <svg viewBox="0 0 24 24"><path d="M8 5v6a4 4 0 0 0 8 0V5M6 20h12"/></svg>
      </button>
      <div class="tool-separator"></div>
      <button class="icon-btn doc-tool" data-cmd="justifyLeft" title="Align left" aria-label="Align left">
        <svg viewBox="0 0 24 24"><path d="M5 6h14M5 10h10M5 14h14M5 18h9"/></svg>
      </button>
      <button class="icon-btn doc-tool" data-cmd="justifyCenter" title="Align center" aria-label="Align center">
        <svg viewBox="0 0 24 24"><path d="M5 6h14M7 10h10M5 14h14M8 18h8"/></svg>
      </button>
      <button class="icon-btn doc-tool" data-cmd="justifyRight" title="Align right" aria-label="Align right">
        <svg viewBox="0 0 24 24"><path d="M5 6h14M9 10h10M5 14h14M10 18h9"/></svg>
      </button>
      <div class="tool-separator"></div>
      <button class="icon-btn doc-tool" data-cmd="insertUnorderedList" title="Bulleted list" aria-label="Bulleted list">
        <svg viewBox="0 0 24 24"><circle cx="5" cy="7" r="1"/><circle cx="5" cy="12" r="1"/><circle cx="5" cy="17" r="1"/><path d="M9 7h10M9 12h10M9 17h10"/></svg>
      </button>
      <button class="icon-btn doc-tool" data-cmd="insertOrderedList" title="Numbered list" aria-label="Numbered list">
        <svg viewBox="0 0 24 24"><path d="M4 6h2v3M4 9h3M4 13h3l-3 4h3"/><path d="M10 7h10M10 12h10M10 17h10"/></svg>
      </button>
      <div class="tool-separator"></div>
      <button class="icon-btn doc-print" id="doc-print" title="Print / Save PDF" aria-label="Print / Save PDF">
        <svg viewBox="0 0 24 24"><path d="M7 9V4h10v5"/><rect x="5" y="14" width="14" height="6"/><path d="M5 16H3v-6h18v6h-2"/><path d="M17 12h.01"/></svg>
      </button>
    </div>
    <div class="tool-group hidden" id="toolbar-sheet">
      <button class="icon-btn sheet-tool" data-action="bold" title="Bold cell" aria-label="Bold cell">
        <svg viewBox="0 0 24 24"><path d="M8 5h5a4 4 0 0 1 0 8H8z"/><path d="M8 13h6a3 3 0 0 1 0 6H8z"/></svg>
      </button>
      <button class="icon-btn sheet-tool" data-action="italic" title="Italic" aria-label="Italic">
        <svg viewBox="0 0 24 24"><path d="M10 5h7M7 19h7M14 5 10 19"/></svg>
      </button>
      <button class="icon-btn sheet-tool" data-action="underline" title="Underline" aria-label="Underline">
        <svg viewBox="0 0 24 24"><path d="M8 5v6a4 4 0 0 0 8 0V5M6 20h12"/></svg>
      </button>
      <button class="icon-btn sheet-tool" data-action="sum" title="Auto sum" aria-label="Auto sum">
        <svg viewBox="0 0 24 24"><path d="M17 5H8l6 7-6 7h9"/></svg>
      </button>
      <button class="icon-btn sheet-tool" data-action="clear" title="Clear cell" aria-label="Clear cell">
        <svg viewBox="0 0 24 24"><path d="m5 16 8-8 6 6-5 5H8z"/><path d="M13 8 9 4"/></svg>
      </button>
      <button class="icon-btn sheet-tool" data-action="merge" title="Merge cells" aria-label="Merge cells">
        <svg viewBox="0 0 24 24"><rect x="4" y="5" width="16" height="14" rx="1"/><path d="M9 5v14M15 5v14"/><path d="m7 12 3-3M7 12l3 3M17 12l-3-3M17 12l-3 3"/></svg>
      </button>
      <button class="icon-btn sheet-tool" data-action="split" title="Split cells" aria-label="Split cells">
        <svg viewBox="0 0 24 24"><rect x="4" y="5" width="16" height="14" rx="1"/><path d="M12 5v14"/><path d="m10 9-3 3 3 3M14 9l3 3-3 3"/></svg>
      </button>
      <button class="icon-btn sheet-tool" data-action="border-all" title="All borders" aria-label="All borders">
        <svg viewBox="0 0 24 24"><rect x="4" y="4" width="16" height="16"/><path d="M12 4v16M4 12h16"/></svg>
      </button>
      <button class="icon-btn sheet-tool" data-action="border-none" title="No borders" aria-label="No borders">
        <svg viewBox="0 0 24 24"><rect x="5" y="5" width="14" height="14"/><path d="m4 20 16-16"/></svg>
      </button>
      <div class="tool-separator"></div>
      <button class="icon-btn sheet-print" id="sheet-print" title="Print / Save PDF" aria-label="Print / Save PDF">
        <svg viewBox="0 0 24 24"><path d="M7 9V4h10v5"/><rect x="5" y="14" width="14" height="6"/><path d="M5 16H3v-6h18v6h-2"/><path d="M17 12h.01"/></svg>
      </button>
    </div>
    <div class="tool-group hidden" id="toolbar-cad">
      <button class="icon-btn" data-cad-name="select" data-cad-kind="tool" title="Select" aria-label="Select">
        <svg viewBox="0 0 24 24"><path d="M6 4l9 8-5 1 3 6-2 1-3-6-4 4z"/></svg>
      </button>
      <button class="icon-btn" data-cad-name="line" data-cad-kind="tool" title="Line" aria-label="Line">
        <svg viewBox="0 0 24 24"><path d="M5 19 19 5"/><circle cx="5" cy="19" r="1.5"/><circle cx="19" cy="5" r="1.5"/></svg>
      </button>
      <button class="icon-btn" data-cad-name="rect" data-cad-kind="tool" title="Rectangle" aria-label="Rectangle">
        <svg viewBox="0 0 24 24"><rect x="5" y="6" width="14" height="12"/></svg>
      </button>
      <button class="icon-btn" data-cad-name="circle" data-cad-kind="tool" title="Circle" aria-label="Circle">
        <svg viewBox="0 0 24 24"><circle cx="12" cy="12" r="7"/></svg>
      </button>
      <button class="icon-btn" data-cad-name="arc" data-cad-kind="tool" title="Arc" aria-label="Arc">
        <svg viewBox="0 0 24 24"><path d="M5 16a8 8 0 0 1 14 0"/><circle cx="5" cy="16" r="1.25"/><circle cx="19" cy="16" r="1.25"/></svg>
      </button>
      <button class="icon-btn" data-cad-name="dim" data-cad-kind="tool" title="Dimension" aria-label="Dimension">
        <svg viewBox="0 0 24 24"><path d="M5 12h14"/><path d="m8 9-3 3 3 3M16 9l3 3-3 3"/><path d="M5 7v10M19 7v10"/></svg>
      </button>
      <button class="icon-btn" data-cad-name="text" data-cad-kind="tool" title="Text" aria-label="Text">
        <svg viewBox="0 0 24 24"><path d="M7 19 12 5l5 14M9 14h6"/></svg>
      </button>
      <div class="tool-separator"></div>
      <button class="icon-btn cad-print" id="cad-print" title="Print / Save PDF" aria-label="Print / Save PDF">
        <svg viewBox="0 0 24 24"><path d="M7 9V4h10v5"/><rect x="5" y="14" width="14" height="6"/><path d="M5 16H3v-6h18v6h-2"/><path d="M17 12h.01"/></svg>
      </button>
    </div>
  </div>

  <main class="workspace">
    <section class="stage">
      <div class="canvas-frame document-surface" id="app-surface">
        <article id="document-editor" class="document-page" contenteditable="true" spellcheck="true" aria-label="Document editor">
          <h1>Untitled document</h1>
          <p>Start writing here...</p>
        </article>

        <div id="sheet-editor" class="sheet-surface hidden" aria-label="Sheet editor">
          <div class="sheet-formula">
            <input id="sheet-namebox" class="sheet-namebox" value="A1" readonly>
            <input id="sheet-formulabox" class="sheet-formulabox" placeholder="Formula or value">
          </div>
          <div class="sheet-wrap">
            <div class="sheet-grid" id="sheet-grid">
              <div class="sheet-head sheet-corner" id="sheet-select-all" title="Select all" aria-label="Select all"></div>
              <div class="sheet-head">A</div><div class="sheet-head">B</div><div class="sheet-head">C</div><div class="sheet-head">D</div>
              <div class="sheet-head">E</div><div class="sheet-head">F</div><div class="sheet-head">G</div><div class="sheet-head">H</div>

              <div class="sheet-rowhead">1</div>
              <div class="sheet-cell" contenteditable="true" data-cell="A1"></div><div class="sheet-cell" contenteditable="true" data-cell="B1"></div><div class="sheet-cell" contenteditable="true" data-cell="C1"></div><div class="sheet-cell" contenteditable="true" data-cell="D1"></div>
              <div class="sheet-cell" contenteditable="true" data-cell="E1"></div><div class="sheet-cell" contenteditable="true" data-cell="F1"></div><div class="sheet-cell" contenteditable="true" data-cell="G1"></div><div class="sheet-cell" contenteditable="true" data-cell="H1"></div>

              <div class="sheet-rowhead">2</div>
              <div class="sheet-cell" contenteditable="true" data-cell="A2"></div><div class="sheet-cell" contenteditable="true" data-cell="B2"></div><div class="sheet-cell" contenteditable="true" data-cell="C2"></div><div class="sheet-cell" contenteditable="true" data-cell="D2"></div>
              <div class="sheet-cell" contenteditable="true" data-cell="E2"></div><div class="sheet-cell" contenteditable="true" data-cell="F2"></div><div class="sheet-cell" contenteditable="true" data-cell="G2"></div><div class="sheet-cell" contenteditable="true" data-cell="H2"></div>

              <div class="sheet-rowhead">3</div>
              <div class="sheet-cell" contenteditable="true" data-cell="A3"></div><div class="sheet-cell" contenteditable="true" data-cell="B3"></div><div class="sheet-cell" contenteditable="true" data-cell="C3"></div><div class="sheet-cell" contenteditable="true" data-cell="D3"></div>
              <div class="sheet-cell" contenteditable="true" data-cell="E3"></div><div class="sheet-cell" contenteditable="true" data-cell="F3"></div><div class="sheet-cell" contenteditable="true" data-cell="G3"></div><div class="sheet-cell" contenteditable="true" data-cell="H3"></div>

              <div class="sheet-rowhead">4</div>
              <div class="sheet-cell" contenteditable="true" data-cell="A4"></div><div class="sheet-cell" contenteditable="true" data-cell="B4"></div><div class="sheet-cell" contenteditable="true" data-cell="C4"></div><div class="sheet-cell" contenteditable="true" data-cell="D4"></div>
              <div class="sheet-cell" contenteditable="true" data-cell="E4"></div><div class="sheet-cell" contenteditable="true" data-cell="F4"></div><div class="sheet-cell" contenteditable="true" data-cell="G4"></div><div class="sheet-cell" contenteditable="true" data-cell="H4"></div>

              <div class="sheet-rowhead">5</div>
              <div class="sheet-cell" contenteditable="true" data-cell="A5"></div><div class="sheet-cell" contenteditable="true" data-cell="B5"></div><div class="sheet-cell" contenteditable="true" data-cell="C5"></div><div class="sheet-cell" contenteditable="true" data-cell="D5"></div>
              <div class="sheet-cell" contenteditable="true" data-cell="E5"></div><div class="sheet-cell" contenteditable="true" data-cell="F5"></div><div class="sheet-cell" contenteditable="true" data-cell="G5"></div><div class="sheet-cell" contenteditable="true" data-cell="H5"></div>
            </div>
          </div>
        </div>

        <div id="cad-editor" class="cad-surface hidden" aria-label="CAD editor">
          <canvas id="cad-canvas" tabindex="0"></canvas>
          <div class="cad-hud">
            <div class="cad-chip" id="cad-coords">x 0 · y 0</div>
            <div class="cad-chip" id="cad-command">LINE · pick first point</div>
            <div class="cad-chip" id="cad-selection">no selection</div>
            <div class="cad-chip" id="cad-count">0 entities</div>
          </div>
        </div>
      </div>
    </section>

    <aside class="rightpanel" id="rightpanel">
      <div class="panel-head">
        <div class="panel-title">Document</div>
        <button class="icon-btn" title="Close panel" aria-label="Close panel" id="panel-close">
          <svg viewBox="0 0 24 24"><path d="m6 6 12 12M18 6 6 18"/></svg>
        </button>
      </div>
      <div class="panel-body">
        <div id="panel-document">
          <section class="panel-section">
            <h3>General</h3>
            <label class="field"><span>Name</span><input value="Untitled document"></label>
            <label class="field"><span>Type</span><select><option>Document</option></select></label>
          </section>
          <section class="panel-section">
            <h3>Page</h3>
            <label class="field"><span>Width</span><input value="210 mm"></label>
            <label class="field"><span>Height</span><input value="297 mm"></label>
            <label class="field"><span>Margins</span><input value="22 mm"></label>
          </section>
          <section class="panel-section">
            <h3>Text</h3>
            <label class="field"><span>Font</span><input value="System"></label>
            <label class="field"><span>Size</span><input value="16 px"></label>
          </section>
        </div>

        <div id="panel-sheet" class="hidden">
          <section class="panel-section">
            <h3>Selected cell</h3>
            <label class="field"><span>Address</span><input id="sheet-panel-address" value="A1" readonly></label>
            <label class="field"><span>Value</span><input id="sheet-panel-value" value=""></label>
          </section>
          <section class="panel-section">
            <h3>Cell format</h3>
            <label class="field"><span>Type</span><select id="sheet-panel-type"><option>General</option><option>Number</option><option>Percent</option><option>Currency</option><option>Text</option></select></label>
            <label class="field"><span>Align</span><select id="sheet-panel-align"><option>Left</option><option>Center</option><option>Right</option></select></label>
            <label class="field"><span>Borders</span><select id="sheet-panel-border"><option value="grid">Grid</option><option value="all">All</option><option value="none">None</option></select></label>
            <label class="field"><span>Fill</span><input id="sheet-fill-color" type="color" value="#ffffff"></label>
            <label class="field"><span>Text</span><input id="sheet-text-color" type="color" value="#111111"></label>
          </section>
          <section class="panel-section">
            <h3>Print / PDF</h3>
            <label class="field"><span>Area</span><select id="sheet-print-area"><option value="selection">Selected cells</option><option value="window">Window</option><option value="all">Whole sheet</option></select></label>
          </section>
          <section class="panel-section">
            <h3>Worksheet</h3>
            <label class="field"><span>Rows</span><input value="5" readonly></label>
            <label class="field"><span>Columns</span><input value="8" readonly></label>
            <label class="field"><span>Col width</span><input id="sheet-col-width" type="number" min="50" max="500" step="5" value="120"></label>
            <label class="field"><span>Row height</span><input id="sheet-row-height" type="number" min="20" max="200" step="2" value="32"></label>
          </section>
        </div>
        <div id="panel-cad" class="hidden">
          <section class="panel-section">
            <h3>Modify</h3>
            <div class="cad-panel-actions">
              <button type="button" data-cad-name="copy" data-cad-kind="tool">Copy</button>
              <button type="button" data-cad-name="move" data-cad-kind="tool">Move</button>
              <button type="button" data-cad-name="offset" data-cad-kind="tool">Offset</button>
              <button type="button" data-cad-name="mirror" data-cad-kind="tool">Mirror</button>
              <button type="button" data-cad-name="delete" data-cad-kind="action">Delete</button>
              <button type="button" data-cad-name="fit" data-cad-kind="action">Fit</button>
            </div>
          </section>
          <section class="panel-section">
            <h3>View</h3>
            <label class="field"><span>Snap</span><input id="cad-snap" value="1"></label>
            <label class="field"><span>Text</span><input id="cad-text-size" value="16"></label>
          </section>
          <section class="panel-section">
            <h3>Print / PDF</h3>
            <label class="field"><span>Area</span><select id="cad-print-area"><option value="selection">Selection</option><option value="window">Window</option><option value="all">Whole drawing</option></select></label>
          </section>
          <section class="panel-section">
            <h3>Project</h3>
            <div class="cad-panel-actions">
              <button data-cad-name="open" data-cad-kind="action">Open</button>
              <button data-cad-name="save" data-cad-kind="action">Save</button>
            </div>
          </section>
        </div>
      </div>
    </aside>
  </main>
</div>
<div id="print-layer" aria-hidden="true"></div>
<riki-space id="cad-riki-space" name="RIKI_CAD" version="cad2d-v1-stable" canonical="true" continuity="same-space" state="total" relation="simultaneous">
  <riki-byte name="CONSTITUTION"><riki-value>1</riki-value><riki-bit>1</riki-bit></riki-byte>
  <riki-byte name="SPACE"><riki-value>1</riki-value><riki-bit>1</riki-bit></riki-byte>
  <riki-byte name="CAD"><riki-value>1</riki-value><riki-bit>1</riki-bit></riki-byte>
  <riki-byte name="TOOL"><riki-value>line</riki-value><riki-bit>1</riki-bit></riki-byte>
  <riki-byte name="SNAP"><riki-value>10</riki-value><riki-bit>1</riki-bit></riki-byte>
  <riki-byte name="GRID"><riki-value>10</riki-value><riki-bit>1</riki-bit></riki-byte>
  <riki-byte name="VIEW_X"><riki-value>0</riki-value><riki-bit>1</riki-bit></riki-byte>
  <riki-byte name="VIEW_Y"><riki-value>0</riki-value><riki-bit>1</riki-bit></riki-byte>
  <riki-byte name="VIEW_SCALE"><riki-value>1</riki-value><riki-bit>1</riki-bit></riki-byte>
  <riki-byte name="TEXT_SIZE"><riki-value>16</riki-value><riki-bit>1</riki-bit></riki-byte>

  <riki-region name="DRAWING" permanent="true"></riki-region>

  <riki-region name="INTERFACE" permanent="true">
    <riki-relation kind="tool" name="select" label="Select"></riki-relation>
    <riki-relation kind="tool" name="line" label="Line"></riki-relation>
    <riki-relation kind="tool" name="rect" label="Rect"></riki-relation>
    <riki-relation kind="tool" name="circle" label="Circle"></riki-relation>
    <riki-relation kind="tool" name="arc" label="Arc"></riki-relation>
    <riki-relation kind="tool" name="dim" label="Dim"></riki-relation>
    <riki-relation kind="tool" name="text" label="Text"></riki-relation>
    <riki-relation kind="tool" name="copy" label="Copy"></riki-relation>
    <riki-relation kind="tool" name="move" label="Move"></riki-relation>
    <riki-relation kind="tool" name="offset" label="Offset"></riki-relation>
    <riki-relation kind="tool" name="mirror" label="Mirror"></riki-relation>
    <riki-relation kind="action" name="undo" label="Undo"></riki-relation>
    <riki-relation kind="action" name="delete" label="Delete"></riki-relation>
    <riki-relation kind="action" name="fit" label="Fit"></riki-relation>
    <riki-relation kind="action" name="save" label="Save"></riki-relation>
    <riki-relation kind="action" name="open" label="Open"></riki-relation>
    <riki-relation kind="action" name="text-down" label="A−"></riki-relation>
    <riki-relation kind="action" name="text-up" label="A+"></riki-relation>
  </riki-region>
</riki-space>
<input id="cad-openProject" type="file" accept=".riki,.json,application/json,text/html" hidden>

<script>
(() => {
  "use strict";

  const PRINT = (() => {
    const layer=document.getElementById("print-layer");
    function clear(){if(layer){layer.innerHTML="";layer.removeAttribute("data-mode")}}
    function open(content,mode){
      if(!layer)return;
      clear();
      if(typeof content==="string")layer.innerHTML=content; else if(content)layer.append(content);
      layer.dataset.mode=mode||"";
      layer.setAttribute("aria-hidden","false");
      const cleanup=()=>{layer.setAttribute("aria-hidden","true");clear();window.removeEventListener("afterprint",cleanup)};
      window.addEventListener("afterprint",cleanup);
      requestAnimationFrame(()=>requestAnimationFrame(()=>window.print()));
    }
    return Object.freeze({open,clear});
  })();

  const CORE = (() => {
    const SPACE = {
      NOME: "RIKI_OFFICE",
      BYTE: "RIKI_OFFICE",
      BIT: 1,
      ACTIVE_APP: "document",
      REGIONS: Object.create(null)
    };

    function register(name, module) {
      if (SPACE.REGIONS[name]) throw new Error("Duplicate RIKI region: " + name);
      SPACE.REGIONS[name] = module;
      validate();
    }

    function validate() {
      SPACE.BIT = Object.values(SPACE.REGIONS).every(m => !m || m.BIT === 1) ? 1 : 0;
      document.body.dataset.rikiBit = String(SPACE.BIT);
      return SPACE.BIT;
    }

    function activate(name) {
      SPACE.ACTIVE_APP = name;
      document.body.dataset.mode = name;
      Object.entries(SPACE.REGIONS).forEach(([key, module]) => {
        if (module && typeof module.activate === "function") {
          module.activate(key === name);
        }
      });
      validate();
    }

    return Object.freeze({ SPACE, register, validate, activate });
  })();

  const UI = (() => {
    const tabs = [...document.querySelectorAll(".mode-tab")];
    const panel = document.getElementById("rightpanel");
    const panelTitle = panel?.querySelector(".panel-title");
    const frame = document.getElementById("app-surface");

    function title(text) {
      if (panelTitle) panelTitle.textContent = text;
    }

    function select(name) {
      tabs.forEach(t => t.setAttribute("aria-selected", String(t.dataset.mode === name)));
    }

    function frameMode(name) {
      if (!frame) return;
      frame.classList.toggle("document-surface", name === "document");
      frame.style.padding = (name === "sheet" || name === "cad") ? "0" : "";
      frame.style.background = (name === "sheet" || name === "cad") ? "#fff" : "";
    }

    tabs.forEach(tab => {
      tab.addEventListener("click", () => {
        select(tab.dataset.mode);
        frameMode(tab.dataset.mode);
        CORE.activate(tab.dataset.mode);
      });
    });

    document.getElementById("panel-close")?.addEventListener("click", () => {
      panel?.classList.toggle("hidden");
    });

    return Object.freeze({ title, select, frameMode });
  })();

  const DOCUMENT = (() => {
    const editor = document.getElementById("document-editor");
    const toolbar = document.getElementById("toolbar-context");
    const panel = document.getElementById("panel-document");

    const state = {
      NOME: "DOCUMENT",
      BYTE: "DOCUMENT",
      VALORE: editor?.innerHTML || "",
      BIT: editor ? 1 : 0,
      CATENE: ["DOCUMENT_TEXT", "DOCUMENT_TITLE"]
    };

    function sync() {
      if (!editor) return;
      state.VALORE = editor.innerHTML;
      state.BIT = 1;
      CORE.validate();
    }

    editor?.addEventListener("input", sync);

    document.querySelectorAll(".doc-tool").forEach(btn => {
      btn.addEventListener("mousedown", e => {
        if (CORE.SPACE.ACTIVE_APP !== "document") return;
        e.preventDefault();
        editor?.focus();
        document.execCommand(btn.dataset.cmd, false, null);
        sync();
      });
    });

    document.getElementById("doc-print")?.addEventListener("click",()=>{
      if(CORE.SPACE.ACTIVE_APP!=="document"||!editor)return;
      const clone=editor.cloneNode(true);
      clone.removeAttribute("contenteditable");
      clone.classList.add("print-document");
      PRINT.open(clone,"document");
    });

    function activate(on) {
      editor?.classList.toggle("hidden", !on);
      toolbar?.classList.toggle("hidden", !on);
      panel?.classList.toggle("hidden", !on);
      if (on) UI.title("Document · BIT " + state.BIT);
    }

    return Object.freeze({ ...state, activate, sync });
  })();

  const SHEET = (() => {
    const root = document.getElementById("sheet-editor");
    const toolbar = document.getElementById("toolbar-sheet");
    const panel = document.getElementById("panel-sheet");
    const formula = document.getElementById("sheet-formulabox");
    const namebox = document.getElementById("sheet-namebox");
    const panelAddress = document.getElementById("sheet-panel-address");
    const panelValue = document.getElementById("sheet-panel-value");
    const colWidthInput = document.getElementById("sheet-col-width");
    const rowHeightInput = document.getElementById("sheet-row-height");
    const fillColorInput = document.getElementById("sheet-fill-color");
    const textColorInput = document.getElementById("sheet-text-color");
    const typeInput = document.getElementById("sheet-panel-type");
    const alignInput = document.getElementById("sheet-panel-align");
    const borderInput = document.getElementById("sheet-panel-border");
    const selectAllCorner = document.getElementById("sheet-select-all");
    const printAreaInput = document.getElementById("sheet-print-area");
    const cells = [...document.querySelectorAll(".sheet-cell")];
    const columnHeads = [...document.querySelectorAll(".sheet-head")].filter(h => /^[A-H]$/.test(h.textContent.trim()));
    const rowHeads = [...document.querySelectorAll(".sheet-rowhead")];

    const values = Object.create(null);
    const columnWidths = Object.create(null);
    const rowHeights = Object.create(null);
    const selectedColumns = new Set();
    const selectedRows = new Set();
    const selectedCells = new Set();
    const cellFill = Object.create(null);
    const cellTextColor = Object.create(null);
    const cellFontWeight = Object.create(null);
    const cellFontStyle = Object.create(null);
    const cellTextDecoration = Object.create(null);
    const cellAlign = Object.create(null);
    const cellType = Object.create(null);
    const cellBorderMode = Object.create(null);
    let anchorCell = "A1";
    let dragSelecting = false;
    let dragAnchor = "A1";
    let headerSelectionActive = false;
    const mergedRanges = new Map();

    const state = {
      NOME: "SHEET",
      BYTE: "SHEET",
      VALORE: values,
      BIT: root && cells.length ? 1 : 0,
      SELECTION: "A1",
      FORMULA_CELL: null,
      FORMULA_BUFFER: "",
      CATENE: ["SHEET_CELLS", "SHEET_SELECTION"]
    };

    function rawValue(addr) {
      return values[addr] ?? "";
    }

    function numericValue(addr, stack) {
      const raw = rawValue(addr);
      if (typeof raw === "number") return raw;
      const s = String(raw).trim();

      if (s.startsWith("=")) {
        return evaluateFormula(s, stack || new Set([addr]));
      }

      const n = Number(s.replace(",", "."));
      return Number.isFinite(n) ? n : 0;
    }

    function evaluateFormula(formulaText, stack) {
      const source = String(formulaText || "").trim();
      if (!source.startsWith("=")) return source;

      let expr = source.slice(1).toUpperCase();
      if (!expr.trim()) return "=";

      // Basic range functions: SUM / AVERAGE / MIN / MAX.
      expr = expr.replace(/\b(SUM|AVERAGE|MIN|MAX)\(([A-H][1-5]):([A-H][1-5])\)/g,
        (_, fn, a1, a2) => {
          const p1 = addrParts(a1), p2 = addrParts(a2);
          if (!p1 || !p2) return "0";
          const vals = [];
          const c1 = Math.min(p1.colIndex, p2.colIndex);
          const c2 = Math.max(p1.colIndex, p2.colIndex);
          const r1 = Math.min(p1.row, p2.row);
          const r2 = Math.max(p1.row, p2.row);
          for (let r=r1; r<=r2; r++) {
            for (let c=c1; c<=c2; c++) {
              vals.push(numericValue(addrFrom(c,r), new Set(stack || [])));
            }
          }
          if (!vals.length) return "0";
          if (fn === "SUM") return String(vals.reduce((a,b)=>a+b,0));
          if (fn === "AVERAGE") return String(vals.reduce((a,b)=>a+b,0)/vals.length);
          if (fn === "MIN") return String(Math.min(...vals));
          if (fn === "MAX") return String(Math.max(...vals));
          return "0";
        }
      );

      expr = expr.replace(/\b([A-H][1-5])\b/g, (_, ref) => {
        const guard = stack || new Set();
        if (guard.has(ref)) return "0";
        const next = new Set(guard);
        next.add(ref);
        return String(numericValue(ref, next));
      });

      if (!/^[0-9+\-*/().\s]+$/.test(expr)) return "#ERROR";

      try {
        const result = Function('"use strict";return (' + expr + ')')();
        return Number.isFinite(result) ? result : "#ERROR";
      } catch {
        return "#ERROR";
      }
    }

    function formatDisplay(addr, rawDisplay) {
      const mode = cellType[addr] || "General";
      const s = String(rawDisplay ?? "");
      if (mode === "Text") return s;

      const n = Number(s);
      if (!Number.isFinite(n)) return s;

      if (mode === "Number") return n.toLocaleString(undefined, {maximumFractionDigits: 2});
      if (mode === "Percent") return (n * 100).toLocaleString(undefined, {maximumFractionDigits: 2}) + "%";
      if (mode === "Currency") return n.toLocaleString(undefined, {style:"currency", currency:"EUR"});
      return s;
    }

    function displayValue(addr) {
      const raw = rawValue(addr);
      const s = String(raw ?? "");

      // While a formula is being edited, keep the raw expression visible.
      if (state.FORMULA_CELL === addr) return s;

      // A bare "=" is incomplete, not an error.
      if (s === "=") return s;

      const shown = s.startsWith("=")
        ? String(evaluateFormula(s, new Set([addr])))
        : s;

      return formatDisplay(addr, shown);
    }

    function addrParts(addr) {
      const m = String(addr || "").match(/^([A-H])([1-5])$/);
      if (!m) return null;
      return { col:m[1], row:Number(m[2]), colIndex:m[1].charCodeAt(0)-64 };
    }

    function addrFrom(colIndex, row) {
      return String.fromCharCode(64 + colIndex) + row;
    }

    function placeSheetGrid() {
      const grid = document.getElementById("sheet-grid");
      if (!grid) return;

      // Corner + column headers.
      const allHeads = [...grid.querySelectorAll(".sheet-head")];
      if (allHeads[0]) {
        allHeads[0].style.gridColumn = "1";
        allHeads[0].style.gridRow = "1";
      }

      columnHeads.forEach((head, i) => {
        head.style.gridColumn = String(i + 2);
        head.style.gridRow = "1";
      });

      // Row headers.
      rowHeads.forEach((head, i) => {
        head.style.gridColumn = "1";
        head.style.gridRow = String(i + 2);
      });

      // Cells.
      cells.forEach(cell => {
        const p = addrParts(cell.dataset.cell);
        if (!p) return;
        cell.style.gridColumn = String(p.colIndex + 1);
        cell.style.gridRow = String(p.row + 1);
      });
    }

    function currentFillTargets() {
      if (selectedCells.size) return [...selectedCells];

      if (selectedColumns.size) {
        const out = [];
        [...selectedColumns].forEach(col => {
          for (let r = 1; r <= 5; r++) out.push(col + r);
        });
        return out;
      }

      if (selectedRows.size) {
        const out = [];
        [...selectedRows].forEach(row => {
          for (let c = 1; c <= 8; c++) out.push(addrFrom(c, row));
        });
        return out;
      }

      return [state.SELECTION];
    }

    function currentRectSelection() {
      if (selectedCells.size > 1) {
        const pts = [...selectedCells].map(addrParts).filter(Boolean);
        if (pts.length) {
          return {
            c1: Math.min(...pts.map(p => p.colIndex)),
            c2: Math.max(...pts.map(p => p.colIndex)),
            r1: Math.min(...pts.map(p => p.row)),
            r2: Math.max(...pts.map(p => p.row))
          };
        }
      }

      if (selectedColumns.size && selectedRows.size) {
        const cols = [...selectedColumns].map(c => c.charCodeAt(0)-64).sort((a,b)=>a-b);
        const rows = [...selectedRows].sort((a,b)=>a-b);
        return {
          c1: cols[0], c2: cols[cols.length-1],
          r1: rows[0], r2: rows[rows.length-1]
        };
      }

      if (selectedColumns.size) {
        const cols = [...selectedColumns].map(c => c.charCodeAt(0)-64).sort((a,b)=>a-b);
        const p = addrParts(state.SELECTION);
        return { c1:cols[0], c2:cols[cols.length-1], r1:p.row, r2:p.row };
      }

      if (selectedRows.size) {
        const rows = [...selectedRows].sort((a,b)=>a-b);
        const p = addrParts(state.SELECTION);
        return { c1:p.colIndex, c2:p.colIndex, r1:rows[0], r2:rows[rows.length-1] };
      }

      return null;
    }

    function mergeCells() {
      const rect = currentRectSelection();
      if (!rect) return;
      if (rect.c1 === rect.c2 && rect.r1 === rect.r2) return;

      const master = addrFrom(rect.c1, rect.r1);
      const members = [];

      for (let r = rect.r1; r <= rect.r2; r++) {
        for (let c = rect.c1; c <= rect.c2; c++) {
          const addr = addrFrom(c, r);
          if (addr !== master) members.push(addr);
        }
      }

      mergedRanges.set(master, {
        master,
        members,
        c1:rect.c1, c2:rect.c2, r1:rect.r1, r2:rect.r2
      });

      selectedCells.clear();
      selectedCells.add(master);
      anchorCell = master;
      state.SELECTION = master;
      renderAllCells();
      renderSelection();
    }

    function splitCells() {
      const current = state.SELECTION;
      let master = null;

      if (mergedRanges.has(current)) {
        master = current;
      } else {
        for (const [key, range] of mergedRanges) {
          if (range.members.includes(current)) {
            master = key;
            break;
          }
        }
      }

      if (!master) return;
      mergedRanges.delete(master);
      selectedCells.clear();
      selectedCells.add(master);
      anchorCell = master;
      state.SELECTION = master;
      renderAllCells();
      renderSelection();
    }

    function selectedColumn() {
      return String(state.SELECTION || "A1").match(/^[A-H]/)?.[0] || "A";
    }

    function selectedRow() {
      return Number(String(state.SELECTION || "A1").match(/\d+$/)?.[0] || 1);
    }

    function activeColumns() {
      return selectedColumns.size ? [...selectedColumns] : [selectedColumn()];
    }

    function activeRows() {
      return selectedRows.size ? [...selectedRows] : [selectedRow()];
    }

    function renderHeaderSelection() {
      columnHeads.forEach(h => h.classList.toggle("is-selected", selectedColumns.has(h.textContent.trim())));
      rowHeads.forEach(h => h.classList.toggle("is-selected", selectedRows.has(Number(h.textContent.trim()))));
    }

    function applyColumnWidth(col, width) {
      const index = col.charCodeAt(0) - 64; // A=1
      const grid = document.getElementById("sheet-grid");
      if (!grid) return;

      columnWidths[col] = width;

      const cols = ["46px"];
      for (let i = 1; i <= 8; i++) {
        const letter = String.fromCharCode(64 + i);
        cols.push((columnWidths[letter] || 120) + "px");
      }
      grid.style.gridTemplateColumns = cols.join(" ");
    }

    function applyRowHeight(row, height) {
      rowHeights[row] = height;

      const grid = document.getElementById("sheet-grid");
      if (!grid) return;

      const rows = ["32px"];
      for (let r = 1; r <= 5; r++) {
        rows.push((rowHeights[r] || 32) + "px");
      }
      grid.style.gridTemplateRows = rows.join(" ");
    }

    function selectCellRange(a, b) {
      const pa = addrParts(a);
      const pb = addrParts(b);
      if (!pa || !pb) return;

      selectedCells.clear();

      const c1 = Math.min(pa.colIndex, pb.colIndex);
      const c2 = Math.max(pa.colIndex, pb.colIndex);
      const r1 = Math.min(pa.row, pb.row);
      const r2 = Math.max(pa.row, pb.row);

      for (let r = r1; r <= r2; r++) {
        for (let c = c1; c <= c2; c++) {
          selectedCells.add(addrFrom(c, r));
        }
      }
    }

    function renderSelection() {
      const raw = rawValue(state.SELECTION);
      if (namebox) namebox.value = state.SELECTION;
      if (formula && document.activeElement !== formula) formula.value = raw;
      if (panelAddress) panelAddress.value = state.SELECTION;
      if (panelValue && document.activeElement !== panelValue) panelValue.value = raw;

      const cols = activeColumns();
      const rows = activeRows();

      if (colWidthInput && document.activeElement !== colWidthInput) {
        const vals = cols.map(c => columnWidths[c] || 120);
        colWidthInput.value = vals.every(v => v === vals[0]) ? vals[0] : "";
        colWidthInput.placeholder = vals.every(v => v === vals[0]) ? "" : "mixed";
      }

      if (rowHeightInput && document.activeElement !== rowHeightInput) {
        const vals = rows.map(r => rowHeights[r] || 32);
        rowHeightInput.value = vals.every(v => v === vals[0]) ? vals[0] : "";
        rowHeightInput.placeholder = vals.every(v => v === vals[0]) ? "" : "mixed";
      }

      renderHeaderSelection();

      if (fillColorInput && document.activeElement !== fillColorInput) {
        const targets = currentFillTargets();
        const colors = targets.map(a => cellFill[a] || "#ffffff");
        fillColorInput.value = colors.length && colors.every(c => c === colors[0]) ? colors[0] : "#ffffff";
      }

      if (textColorInput && document.activeElement !== textColorInput) {
        const targets = currentFillTargets();
        const colors = targets.map(a => cellTextColor[a] || "#111111");
        textColorInput.value = colors.length && colors.every(c => c === colors[0]) ? colors[0] : "#111111";
      }

      const fmtTargets = currentFillTargets();

      if (alignInput && document.activeElement !== alignInput) {
        const vals = fmtTargets.map(a => cellAlign[a] || "Left");
        alignInput.value = vals.every(v => v === vals[0]) ? vals[0] : "Left";
      }

      if (typeInput && document.activeElement !== typeInput) {
        const vals = fmtTargets.map(a => cellType[a] || "General");
        typeInput.value = vals.every(v => v === vals[0]) ? vals[0] : "General";
      }

      if (borderInput && document.activeElement !== borderInput) {
        const vals = fmtTargets.map(a => cellBorderMode[a] || "grid");
        borderInput.value = vals.every(v => v === vals[0]) ? vals[0] : "grid";
      }

      if (selectAllCorner) {
        selectAllCorner.classList.toggle("is-selected", selectedCells.size === cells.length);
      }

      cells.forEach(cell => {
        cell.classList.toggle("is-active", !headerSelectionActive && cell.dataset.cell === state.SELECTION);
        cell.classList.toggle("is-selected", !headerSelectionActive && selectedCells.has(cell.dataset.cell));
      });
    }

    function renderAllCells() {
      placeSheetGrid();

      cells.forEach(cell => {
        cell.classList.remove("is-merged-master","is-merged-hidden");
        cell.style.visibility = "";

        const p = addrParts(cell.dataset.cell);
        if (p) {
          cell.style.gridColumn = String(p.colIndex + 1);
          cell.style.gridRow = String(p.row + 1);
        }
      });

      for (const [master, range] of mergedRanges) {
        const masterCell = document.querySelector('.sheet-cell[data-cell="' + master + '"]');
        if (!masterCell) continue;

        masterCell.classList.add("is-merged-master");

        // +1 because grid column 1 is the row-header column.
        masterCell.style.gridColumn =
          String(range.c1 + 1) + " / " + String(range.c2 + 2);

        // +1 because grid row 1 is the column-header row.
        masterCell.style.gridRow =
          String(range.r1 + 1) + " / " + String(range.r2 + 2);

        range.members.forEach(addr => {
          const cell = document.querySelector('.sheet-cell[data-cell="' + addr + '"]');
          if (cell) cell.classList.add("is-merged-hidden");
        });
      }

      cells.forEach(cell => {
        const addr = cell.dataset.cell;
        cell.style.backgroundColor = cellFill[addr] || "";
        cell.style.color = cellTextColor[addr] || "";
        cell.style.fontWeight = cellFontWeight[addr] || "";
        cell.style.fontStyle = cellFontStyle[addr] || "";
        cell.style.textDecoration = cellTextDecoration[addr] || "";
        cell.style.textAlign = (cellAlign[addr] || "Left").toLowerCase();
        cell.classList.toggle("format-border-all", cellBorderMode[addr] === "all");
        cell.classList.toggle("format-border-none", cellBorderMode[addr] === "none");

        // Never rewrite the cell currently being edited:
        // doing so resets the caret to the beginning and reverses typed text.
        if (document.activeElement === cell) return;

        cell.textContent = displayValue(addr);
      });
    }

    function setCell(addr, value) {
      values[addr] = String(value ?? "");
      state.SELECTION = addr;
      renderAllCells();
      renderSelection();
      CORE.validate();
    }

    cells.forEach(cell => {
      cell.addEventListener("mousedown", e => {
        if (CORE.SPACE.ACTIVE_APP !== "sheet") return;

        const addr = cell.dataset.cell;
        headerSelectionActive = false;

        // Formula reference pick has priority.
        if (
          state.FORMULA_CELL &&
          state.FORMULA_CELL !== addr &&
          String(state.FORMULA_BUFFER || "").startsWith("=")
        ) {
          e.preventDefault();

          state.FORMULA_BUFFER += addr;
          values[state.FORMULA_CELL] = state.FORMULA_BUFFER;

          const origin = document.querySelector(
            '.sheet-cell[data-cell="' + state.FORMULA_CELL + '"]'
          );

          if (origin) {
            origin.textContent = state.FORMULA_BUFFER;
            origin.focus();

            const range = document.createRange();
            range.selectNodeContents(origin);
            range.collapse(false);
            const sel = window.getSelection();
            sel.removeAllRanges();
            sel.addRange(range);
          }

          if (formula) formula.value = state.FORMULA_BUFFER;
          if (panelValue) panelValue.value = state.FORMULA_BUFFER;
          state.SELECTION = state.FORMULA_CELL;
          renderSelection();
          return;
        }

        selectedColumns.clear();
        selectedRows.clear();

        // Shift extends from the existing anchor.
        if (e.shiftKey) {
          e.preventDefault();
          selectCellRange(anchorCell || state.SELECTION, addr);
          state.SELECTION = addr;
          renderSelection();
          return;
        }

        // Ctrl/Cmd toggles one cell without losing the others.
        if (e.ctrlKey || e.metaKey) {
          e.preventDefault();
          if (selectedCells.has(addr)) selectedCells.delete(addr);
          else selectedCells.add(addr);

          if (!selectedCells.size) selectedCells.add(addr);

          state.SELECTION = addr;
          anchorCell = addr;
          renderSelection();
          return;
        }

        // Normal click starts a spreadsheet-style drag selection.
        selectedCells.clear();
        selectedCells.add(addr);
        state.SELECTION = addr;
        anchorCell = addr;
        dragAnchor = addr;
        dragSelecting = true;
        renderSelection();
      });

      cell.addEventListener("mouseenter", e => {
        if (CORE.SPACE.ACTIVE_APP !== "sheet") return;
        if (!dragSelecting || !(e.buttons & 1)) return;

        e.preventDefault();
        selectCellRange(dragAnchor, cell.dataset.cell);
        state.SELECTION = cell.dataset.cell;
        renderSelection();
      });

      cell.addEventListener("focus", () => {
        if (CORE.SPACE.ACTIVE_APP !== "sheet") return;
        state.SELECTION = cell.dataset.cell;
        const raw = rawValue(cell.dataset.cell);
        if (String(raw).startsWith("=")) {
          cell.textContent = raw;
          state.FORMULA_CELL = cell.dataset.cell;
          state.FORMULA_BUFFER = raw;
        }
        renderSelection();
      });
      cell.addEventListener("blur", () => {
        if (CORE.SPACE.ACTIVE_APP !== "sheet") return;
        cell.textContent = displayValue(cell.dataset.cell);
      });



      cell.addEventListener("input", () => {
        if (CORE.SPACE.ACTIVE_APP !== "sheet") return;

        const value = cell.textContent || "";
        setCell(cell.dataset.cell, value);

        if (value.startsWith("=")) {
          state.FORMULA_CELL = cell.dataset.cell;
          state.FORMULA_BUFFER = value;
        } else if (state.FORMULA_CELL === cell.dataset.cell) {
          state.FORMULA_CELL = null;
          state.FORMULA_BUFFER = "";
        }
      });

      cell.addEventListener("keydown", e => {
        if (CORE.SPACE.ACTIVE_APP !== "sheet") return;

        if (e.key === "Enter") {
          e.preventDefault();
          const value = String(cell.textContent || "").replace(/\n+/g, "");
          values[cell.dataset.cell] = value;
          state.SELECTION = cell.dataset.cell;
          state.FORMULA_CELL = null;
          state.FORMULA_BUFFER = "";
          renderAllCells();
          renderSelection();
          CORE.validate();
          cell.blur();
          return;
        }

        if (e.key === "Escape") {
          e.preventDefault();
          state.FORMULA_CELL = null;
          state.FORMULA_BUFFER = "";
          cell.blur();
          renderSelection();
        }
      });
    });

    window.addEventListener("mouseup", () => {
      dragSelecting = false;
    });

    formula?.addEventListener("input", () => {
      if (CORE.SPACE.ACTIVE_APP !== "sheet") return;
      const value = formula.value || "";
      setCell(state.SELECTION, value);

      if (value.startsWith("=")) {
        state.FORMULA_CELL = state.SELECTION;
        state.FORMULA_BUFFER = value;
      } else {
        state.FORMULA_CELL = null;
        state.FORMULA_BUFFER = "";
      }
    });
    formula?.addEventListener("keydown", e => {
      if (CORE.SPACE.ACTIVE_APP !== "sheet") return;
      if (e.key === "Enter") {
        e.preventDefault();
        values[state.SELECTION] = formula.value || "";
        state.FORMULA_CELL = null;
        state.FORMULA_BUFFER = "";
        renderAllCells();
        renderSelection();
        CORE.validate();
        formula.blur();
      }
      if (e.key === "Escape") {
        e.preventDefault();
        state.FORMULA_CELL = null;
        state.FORMULA_BUFFER = "";
        formula.blur();
        renderSelection();
      }
    });

    panelValue?.addEventListener("change", () => setCell(state.SELECTION, panelValue.value));

    selectAllCorner?.addEventListener("click", () => {
      if (CORE.SPACE.ACTIVE_APP !== "sheet") return;
      headerSelectionActive = false;
      selectedColumns.clear();
      selectedRows.clear();
      selectedCells.clear();
      cells.forEach(cell => selectedCells.add(cell.dataset.cell));
      state.SELECTION = "A1";
      anchorCell = "A1";
      renderSelection();
    });

    columnHeads.forEach(head => {
      head.addEventListener("click", e => {
        if (CORE.SPACE.ACTIVE_APP !== "sheet") return;
        const col = head.textContent.trim();

        headerSelectionActive = true;
        selectedCells.clear();

        if (!e.ctrlKey && !e.metaKey) {
          selectedColumns.clear();
          selectedRows.clear();
        }

        if (selectedColumns.has(col)) selectedColumns.delete(col);
        else selectedColumns.add(col);

        renderSelection();
      });
    });

    rowHeads.forEach(head => {
      head.addEventListener("click", e => {
        if (CORE.SPACE.ACTIVE_APP !== "sheet") return;
        const row = Number(head.textContent.trim());

        headerSelectionActive = true;
        selectedCells.clear();

        if (!e.ctrlKey && !e.metaKey) {
          selectedRows.clear();
          selectedColumns.clear();
        }

        if (selectedRows.has(row)) selectedRows.delete(row);
        else selectedRows.add(row);

        renderSelection();
      });
    });

    cells.forEach(cell => {
      cell.addEventListener("focus", () => {
        headerSelectionActive = false;
        if (selectedColumns.size || selectedRows.size) {
          selectedColumns.clear();
          selectedRows.clear();
          renderHeaderSelection();
        }
      });
    });

    alignInput?.addEventListener("change", () => {
      if (CORE.SPACE.ACTIVE_APP !== "sheet") return;
      currentFillTargets().forEach(addr => cellAlign[addr] = alignInput.value);
      renderAllCells();
      renderSelection();
    });

    typeInput?.addEventListener("change", () => {
      if (CORE.SPACE.ACTIVE_APP !== "sheet") return;
      currentFillTargets().forEach(addr => cellType[addr] = typeInput.value);
      renderAllCells();
      renderSelection();
    });

    borderInput?.addEventListener("change", () => {
      if (CORE.SPACE.ACTIVE_APP !== "sheet") return;
      currentFillTargets().forEach(addr => cellBorderMode[addr] = borderInput.value);
      renderAllCells();
      renderSelection();
    });

    fillColorInput?.addEventListener("input", () => {
      if (CORE.SPACE.ACTIVE_APP !== "sheet") return;
      const color = fillColorInput.value || "#ffffff";
      currentFillTargets().forEach(addr => {
        cellFill[addr] = color;
      });
      renderAllCells();
      renderSelection();
    });

    textColorInput?.addEventListener("input", () => {
      if (CORE.SPACE.ACTIVE_APP !== "sheet") return;
      const color = textColorInput.value || "#111111";
      currentFillTargets().forEach(addr => {
        cellTextColor[addr] = color;
      });
      renderAllCells();
      renderSelection();
    });

    colWidthInput?.addEventListener("change", () => {
      if (CORE.SPACE.ACTIVE_APP !== "sheet") return;
      const width = Math.max(50, Math.min(500, Number(colWidthInput.value) || 120));
      activeColumns().forEach(col => applyColumnWidth(col, width));
      colWidthInput.value = width;
      renderSelection();
    });

    rowHeightInput?.addEventListener("change", () => {
      if (CORE.SPACE.ACTIVE_APP !== "sheet") return;
      const height = Math.max(20, Math.min(200, Number(rowHeightInput.value) || 32));
      activeRows().forEach(row => applyRowHeight(row, height));
      rowHeightInput.value = height;
      renderSelection();
    });

    function selectionRectAddresses() {
      const rect = currentRectSelection();
      if (!rect) return [[state.SELECTION]];

      const rows = [];
      for (let r=rect.r1; r<=rect.r2; r++) {
        const row = [];
        for (let c=rect.c1; c<=rect.c2; c++) row.push(addrFrom(c,r));
        rows.push(row);
      }
      return rows;
    }

    function selectionToTSV() {
      return selectionRectAddresses()
        .map(row => row.map(addr => String(rawValue(addr))).join("\t"))
        .join("\n");
    }

    function pasteTSV(tsv) {
      const rows = String(tsv || "").replace(/\r/g,"").split("\n");
      const start = addrParts(state.SELECTION);
      if (!start) return;

      rows.forEach((line, ri) => {
        if (start.row + ri > 5) return;
        line.split("\t").forEach((val, ci) => {
          if (start.colIndex + ci > 8) return;
          values[addrFrom(start.colIndex + ci, start.row + ri)] = val;
        });
      });

      renderAllCells();
      renderSelection();
    }

    document.querySelectorAll(".sheet-tool").forEach(btn => {
      btn.addEventListener("click", () => {
        if (CORE.SPACE.ACTIVE_APP !== "sheet") return;
        const cell = document.querySelector('.sheet-cell[data-cell="' + state.SELECTION + '"]');
        if (!cell) return;

        if (btn.dataset.action === "clear") {
          currentFillTargets().forEach(addr => values[addr] = "");
          renderAllCells();
          renderSelection();
          return;
        }
        if (btn.dataset.action === "merge") {
          mergeCells();
          return;
        }
        if (btn.dataset.action === "split") {
          splitCells();
          return;
        }
        if (btn.dataset.action === "bold") {
          const targets = currentFillTargets();
          const on = targets.some(a => cellFontWeight[a] !== "700");
          targets.forEach(a => cellFontWeight[a] = on ? "700" : "");
          renderAllCells();
          return;
        }

        if (btn.dataset.action === "italic") {
          const targets = currentFillTargets();
          const on = targets.some(a => cellFontStyle[a] !== "italic");
          targets.forEach(a => cellFontStyle[a] = on ? "italic" : "");
          renderAllCells();
          return;
        }

        if (btn.dataset.action === "underline") {
          const targets = currentFillTargets();
          const on = targets.some(a => cellTextDecoration[a] !== "underline");
          targets.forEach(a => cellTextDecoration[a] = on ? "underline" : "");
          renderAllCells();
          return;
        }

        if (btn.dataset.action === "border-all") {
          currentFillTargets().forEach(a => cellBorderMode[a] = "all");
          renderAllCells();
          renderSelection();
          return;
        }

        if (btn.dataset.action === "border-none") {
          currentFillTargets().forEach(a => cellBorderMode[a] = "none");
          renderAllCells();
          renderSelection();
          return;
        }

        if (btn.dataset.action === "sum") {
          const rect = currentRectSelection();
          if (rect && (rect.c1 !== rect.c2 || rect.r1 !== rect.r2)) {
            const a = addrFrom(rect.c1, rect.r1);
            const b = addrFrom(rect.c2, rect.r2);
            values[state.SELECTION] = "=SUM(" + a + ":" + b + ")";
            renderAllCells();
            renderSelection();
            return;
          }

          const p = addrParts(state.SELECTION);
          let total = 0;
          for (let r=1; r<p.row; r++) {
            total += numericValue(addrFrom(p.colIndex, r), new Set());
          }
          values[state.SELECTION] = String(total);
          renderAllCells();
          renderSelection();
          return;
        }
      });
    });

    function printSelectionTable(){
      let rect=currentRectSelection();
      if(!rect){const p=addrParts(state.SELECTION);rect={c1:p.colIndex,c2:p.colIndex,r1:p.row,r2:p.row}}
      const table=document.createElement("table");table.className="print-sheet-table";
      for(let r=rect.r1;r<=rect.r2;r++){
        const tr=document.createElement("tr");
        for(let c=rect.c1;c<=rect.c2;c++){
          const addr=addrFrom(c,r);
          let covered=false;
          for(const range of mergedRanges.values()){if(range.members.includes(addr)){covered=true;break}}
          if(covered)continue;
          const td=document.createElement("td");
          td.textContent=displayValue(addr);
          const source=document.querySelector('.sheet-cell[data-cell="'+addr+'"]');
          if(source){
            const cs=getComputedStyle(source);
            td.style.backgroundColor=cs.backgroundColor;td.style.color=cs.color;td.style.fontWeight=cs.fontWeight;
            td.style.fontStyle=cs.fontStyle;td.style.textDecoration=cs.textDecoration;td.style.textAlign=cs.textAlign;
            td.style.borderColor=cs.borderColor;
          }
          const merge=mergedRanges.get(addr);
          if(merge){td.colSpan=Math.max(1,merge.c2-merge.c1+1);td.rowSpan=Math.max(1,merge.r2-merge.r1+1)}
          tr.append(td);
        }
        table.append(tr);
      }
      return table;
    }

    function printSheetWindow(){
      const wrap=document.createElement("div");wrap.className="print-sheet-window";
      wrap.style.width=Math.max(320,root.clientWidth)+"px";wrap.style.height=Math.max(240,root.clientHeight)+"px";
      const inner=document.createElement("div");inner.className="print-sheet-window-inner";
      const clone=root.cloneNode(true);clone.classList.remove("hidden");clone.style.width=root.scrollWidth+"px";clone.style.height=root.scrollHeight+"px";clone.style.overflow="visible";
      clone.querySelectorAll(".sheet-formula").forEach(el=>el.remove());
      inner.style.left=(-root.scrollLeft)+"px";inner.style.top=(-root.scrollTop)+"px";inner.append(clone);wrap.append(inner);return wrap;
    }

    document.getElementById("sheet-print")?.addEventListener("click",()=>{
      if(CORE.SPACE.ACTIVE_APP!=="sheet"||!root)return;
      const mode=printAreaInput?.value||"selection";
      if(mode==="selection"){PRINT.open(printSelectionTable(),"sheet-selection");return}
      if(mode==="window"){PRINT.open(printSheetWindow(),"sheet-window");return}
      const clone=root.cloneNode(true);clone.classList.remove("hidden");clone.style.height="auto";clone.style.overflow="visible";
      clone.querySelectorAll(".sheet-formula").forEach(el=>el.remove());
      PRINT.open(clone,"sheet-all");
    });

    window.addEventListener("keydown", async e => {
      if (CORE.SPACE.ACTIVE_APP !== "sheet") return;

      const active = document.activeElement;
      const editingCell = active && active.classList && active.classList.contains("sheet-cell");
      const editingFormula = active === formula;

      if ((e.ctrlKey || e.metaKey) && e.key.toLowerCase() === "c" && !editingCell && !editingFormula) {
        e.preventDefault();
        try { await navigator.clipboard.writeText(selectionToTSV()); } catch {}
        return;
      }

      if ((e.ctrlKey || e.metaKey) && e.key.toLowerCase() === "v" && !editingCell && !editingFormula) {
        e.preventDefault();
        try {
          const t = await navigator.clipboard.readText();
          pasteTSV(t);
        } catch {}
        return;
      }

      if ((e.key === "Delete" || e.key === "Backspace") && !editingCell && !editingFormula) {
        e.preventDefault();
        currentFillTargets().forEach(addr => values[addr] = "");
        renderAllCells();
        renderSelection();
      }
    });

    function activate(on) {
      if (on && !selectedCells.size) selectedCells.add(state.SELECTION);
      root?.classList.toggle("hidden", !on);
      toolbar?.classList.toggle("hidden", !on);
      panel?.classList.toggle("hidden", !on);
      if (on) {
        UI.title("Sheet · BIT " + state.BIT);
        placeSheetGrid();
        renderAllCells();
        renderSelection();
      }
    }

    return Object.freeze({ ...state, activate, setCell });
  })();

  const CAD = (() => {
    const root = document.getElementById("cad-editor");
    const toolbar = document.getElementById("toolbar-cad");
    const panel = document.getElementById("panel-cad");
    const space = document.getElementById("cad-riki-space");

    const state = {
      NOME: "CAD",
      BYTE: "CAD",
      BIT: root && space ? 1 : 0,
      CATENE: ["CAD_DRAWING", "CAD_TOOL", "CAD_VIEW"]
    };

    function activate(on) {
      root?.classList.toggle("hidden", !on);
      toolbar?.classList.toggle("hidden", !on);
      panel?.classList.toggle("hidden", !on);

      if (on) {
        UI.title("CAD · BIT " + state.BIT);
        // CAD engine is kept completely separate and receives only a resize wake-up.
        requestAnimationFrame(() => window.dispatchEvent(new Event("resize")));
      }
    }

    return Object.freeze({ ...state, activate });
  })();

  CORE.register("document", DOCUMENT);
  CORE.register("sheet", SHEET);
  CORE.register("cad", CAD);

  UI.select("cad");
  UI.frameMode("cad");
  CORE.activate("cad");

  Object.defineProperty(window, "RIKI_OFFICE", {
    value: CORE.SPACE,
    writable: false,
    configurable: false
  });
})();
</script><script>
(()=>{
'use strict';
const space=document.querySelector('#cad-riki-space');
const drawing=space.querySelector('riki-region[name="DRAWING"]');
const ui=space.querySelector('riki-region[name="INTERFACE"]');
const canvas=document.querySelector('#cad-canvas'),ctx=canvas.getContext('2d');
const toolbar=document.querySelector('#toolbar-cad'),coords=document.querySelector('#cad-coords'),command=document.querySelector('#cad-command'),selectionText=document.querySelector('#cad-selection'),count=document.querySelector('#cad-count');
const openProject=document.querySelector('#cad-openProject');
const printArea=document.querySelector('#cad-print-area');

const dpr=()=>Math.max(1,window.devicePixelRatio||1);
const byte=n=>space.querySelector(`riki-byte[name="${n}"] riki-value`);
const get=n=>byte(n)?.textContent??'';
const set=(n,v)=>{const e=byte(n);if(e)e.textContent=String(v)};
const num=n=>Number(get(n))||0;
let seq=0, selected=null, draft=null, modify=null, pan=null, history=[],cmdInput={stage:'idle',buffer:'',v1:null},lastPointerWorld=null;


function projectState(){
  const bytes={};
  for(const b of space.querySelectorAll(':scope > riki-byte')){
    const n=b.getAttribute('name'),v=b.querySelector(':scope > riki-value');
    if(n&&v)bytes[n]=v.textContent;
  }
  return {format:'RIKI-CAD-2D',version:1,bytes,drawing:drawing.innerHTML};
}
function buildSelfHtml(){
  const clone=document.documentElement.cloneNode(true);
  clone.querySelectorAll('#toolbar-cad button').forEach(b=>b.remove());
  const cc=clone.querySelector('#cad-canvas');
  if(cc){cc.removeAttribute('width');cc.removeAttribute('height')}
  const sd=clone.querySelector('#saveDialog');
  if(sd)sd.style.display='none';
  const sn=clone.querySelector('#saveName');
  if(sn)sn.value='RIKI-CAD-2D.html';
  return '<!doctype html>\n'+clone.outerHTML;
}

async function saveProject(){
  const now=new Date(),pad=n=>String(n).padStart(2,'0');
  const name=`RIKI-CAD-2D-${now.getFullYear()}${pad(now.getMonth()+1)}${pad(now.getDate())}-${pad(now.getHours())}${pad(now.getMinutes())}.html`;

  if(typeof window.showSaveFilePicker!=='function'){
    command.textContent='SAVE · open this HTML directly in Chrome/Edge on Desktop';
    return;
  }

  try{
    const handle=await window.showSaveFilePicker({
      suggestedName:name,
      types:[{
        description:'RIKI CAD 2D HTML',
        accept:{'text/html':['.html']}
      }]
    });

    const html=buildSelfHtml();
    const writable=await handle.createWritable();
    await writable.write(new Blob([html],{type:'text/html;charset=utf-8'}));
    await writable.close();

    command.textContent='SAVE · new RIKI HTML saved on PC';
  }catch(err){
    if(err && err.name==='AbortError'){
      command.textContent='SAVE · cancelled';
    }else{
      command.textContent='SAVE · browser blocked native Save As';
      console.error(err);
    }
  }
}
function restoreProject(data){
  if(!data||data.format!=='RIKI-CAD-2D'||typeof data.drawing!=='string')throw new Error('Invalid RIKI project');
  if(data.bytes&&typeof data.bytes==='object')for(const [n,v] of Object.entries(data.bytes))if(byte(n))set(n,v);
  drawing.innerHTML=data.drawing;selected=null;draft=null;modify=null;history=[];resetCommandInput();
  let m=0;for(const e of drawing.querySelectorAll('[name]')){const q=(e.getAttribute('name')||'').match(/^[PR](\d+)$/);if(q)m=Math.max(m,Number(q[1]))}seq=m;
  syncToolbar();render();command.textContent='OPEN · project loaded';
}
function openProjectFile(file){
  if(!file)return;const reader=new FileReader();reader.onload=()=>{try{restoreProject(JSON.parse(String(reader.result)))}catch(err){command.textContent='OPEN · invalid project'}};reader.readAsText(file);
}
openProject.addEventListener('change',()=>{openProjectFile(openProject.files?.[0]);openProject.value=''});

function resetCommandInput(){cmdInput={stage:'idle',buffer:'',v1:null};updateCommand()}
function updateCommand(){
  const tool=get('TOOL');
  if(tool==='line'){
    if(!draft){command.textContent='LINE · pick first point';return}
    command.textContent=`LINE · length ${cmdInput.buffer||'…'} · Enter · or length<angle`;
    return
  }
  if(tool==='rect'){
    if(!draft){command.textContent='RECT · pick first corner';return}
    if(cmdInput.stage==='height'){command.textContent=`RECT · height ${cmdInput.buffer||'…'} · Enter`;return}
    command.textContent=`RECT · opposite corner or width${cmdInput.buffer?' '+cmdInput.buffer:''}`;return
  }
  if(tool==='circle'){
    if(!draft){command.textContent='CIRCLE · pick center';return}
    command.textContent=`CIRCLE · point on circumference or radius${cmdInput.buffer?' '+cmdInput.buffer:''}`;return
  }
  if(tool==='arc'){
    if(!draft){command.textContent='ARC · pick center';return}
    if(cmdInput.stage==='radius'){command.textContent=`ARC · radius or start point${cmdInput.buffer?' '+cmdInput.buffer:''}`;return}
    if(cmdInput.stage==='startAngle'){command.textContent=`ARC · start angle ${cmdInput.buffer||'…'}° · Enter`;return}
    if(cmdInput.stage==='endAngle'){command.textContent=`ARC · end angle ${cmdInput.buffer||'…'}° · Enter`;return}
    command.textContent='ARC · pick end point on arc';return
  }
  if(tool==='dim'){
    if(!draft){command.textContent='DIM · pick first point';return}
    if(draft.stage===1){command.textContent='DIM · pick second point';return}
    command.textContent='DIM · choose distance with mouse · click';return
  }
  if(tool==='text'){
    if(!draft){command.textContent='TEXT · pick insertion point';return}
    command.textContent=`TEXT · ${cmdInput.buffer||'type text'} · Enter`;return
  }
  if(['copy','move','offset','mirror'].includes(tool)){
    const T=tool.toUpperCase();
    if(!selected){command.textContent=`${T} · select entity`;return}
    if(tool==='mirror'){
      if(!modify||!modify.axisA){command.textContent='MIRROR · pick first point of axis';return}
      command.textContent=`MIRROR · second axis point or angle${cmdInput.buffer?' '+cmdInput.buffer+'°':''} · Enter`;return
    }
    command.textContent=(tool==='move'||tool==='copy')?`${T} · click destination`:tool==='offset'?`${T} · click offset side/distance`:`${T}`;return
  }
  command.textContent=tool.toUpperCase();
}

function lineAngle(a,b){return Math.atan2(b.y-a.y,b.x-a.x)*180/Math.PI}
function endpointFromPolar(a,len,deg){const r=deg*Math.PI/180;return{x:a.x+len*Math.cos(r),y:a.y+len*Math.sin(r)}}
function commitDraft(d){
  if(!d){draft=null;resetCommandInput();render();return}
  if(d.kind==='arc'){
    if(!d.b||!d.c||Math.hypot(d.b.x-d.a.x,d.b.y-d.a.y)<1e-9){draft=null;resetCommandInput();render();return}
    saveHistory();const a=createPoint(d.a),b=createPoint(d.b),c=createPoint(d.c);const rel=createRelation('arc',a,b,c);selected=rel.getAttribute('name');draft=null;resetCommandInput();render();return
  }
  if(Math.hypot(d.b.x-d.a.x,d.b.y-d.a.y)<1e-9){draft=null;resetCommandInput();render();return}
  saveHistory();const a=createPoint(d.a),b=createPoint(d.b);const rel=createRelation(d.kind,a,b);selected=rel.getAttribute('name');draft=null;resetCommandInput();render();
}
function parseLinePair(text){
  const t=text.trim().replace(',', '.');
  let m=t.match(/^([+-]?(?:\d+(?:\.\d*)?|\.\d+))\s*(?:<|@|\s)\s*([+-]?(?:\d+(?:\.\d*)?|\.\d+))$/);
  return m?{length:+m[1],angle:+m[2]}:null;
}

function point(name){return drawing.querySelector(`:scope > riki-point[name="${name}"]`)}
function pxy(name){const p=point(name);return p?{x:+p.getAttribute('x'),y:+p.getAttribute('y')}:null}
function relations(){return [...drawing.querySelectorAll(':scope > riki-relation')]}
function points(){return [...drawing.querySelectorAll(':scope > riki-point')]}
function worldToScreen(p){const s=num('VIEW_SCALE')||1;return{x:(p.x-num('VIEW_X'))*s+canvas.clientWidth/2,y:canvas.clientHeight/2-(p.y-num('VIEW_Y'))*s}}
function screenToWorld(p){const s=num('VIEW_SCALE')||1;return{x:(p.x-canvas.clientWidth/2)/s+num('VIEW_X'),y:(canvas.clientHeight/2-p.y)/s+num('VIEW_Y')}}
let guideState={x:null,y:null,point:null};

function magneticCandidates(){
  const out=[];

  for(const p of points()){
    out.push({
      x:+p.getAttribute('x'),
      y:+p.getAttribute('y'),
      kind:'point'
    });
  }

  for(const r of relations()){
    const d=relData(r);
    if(!d)continue;

    if(d.kind==='line'||d.kind==='rect'){
      out.push({
        x:(d.a.x+d.b.x)/2,
        y:(d.a.y+d.b.y)/2,
        kind:'mid'
      });
    }

    if(d.kind==='circle'||d.kind==='arc'){
      out.push({
        x:d.a.x,
        y:d.a.y,
        kind:'center'
      });
    }
  }

  return out;
}

function snap(p){
  if(num('SNAP')===0){
    guideState={x:null,y:null,point:null};
    return p;
  }

  const scale=num('VIEW_SCALE')||1;
  const tol=10/scale;
  let out={x:p.x,y:p.y};

  guideState={x:null,y:null,point:null};

  let best=null,bestD=Infinity;
  for(const c of magneticCandidates()){
    const d=Math.hypot(p.x-c.x,p.y-c.y);
    if(d<bestD&&d<=tol){
      best=c;
      bestD=d;
    }
  }

  if(best){
    out={x:best.x,y:best.y};
    guideState.point=best;
    guideState.x=best.x;
    guideState.y=best.y;
    return out;
  }

  // Dynamic orthogonal guides from the active construction anchor.
  let anchor=null;
  if(draft&&draft.a)anchor=draft.a;
  else if(modify&&modify.axisA)anchor=modify.axisA;

  if(anchor){
    if(Math.abs(p.x-anchor.x)<=tol){
      out.x=anchor.x;
      guideState.x=anchor.x;
    }
    if(Math.abs(p.y-anchor.y)<=tol){
      out.y=anchor.y;
      guideState.y=anchor.y;
    }
  }

  // Magnetic alignment with existing points even without landing directly on them.
  for(const c of magneticCandidates()){
    if(guideState.x===null&&Math.abs(p.x-c.x)<=tol){
      out.x=c.x;
      guideState.x=c.x;
      break;
    }
  }
  for(const c of magneticCandidates()){
    if(guideState.y===null&&Math.abs(p.y-c.y)<=tol){
      out.y=c.y;
      guideState.y=c.y;
      break;
    }
  }

  return out;
}
function next(prefix){seq++;return prefix+seq}
function createPoint(p){const e=document.createElement('riki-point');e.setAttribute('name',next('P'));e.setAttribute('x',p.x);e.setAttribute('y',p.y);e.setAttribute('permanent','true');drawing.append(e);return e.getAttribute('name')}
function createRelation(kind,a,b,c=null){const e=document.createElement('riki-relation');e.setAttribute('name',next('R'));e.setAttribute('kind',kind);e.setAttribute('a',a);e.setAttribute('b',b);if(c)e.setAttribute('c',c);e.setAttribute('permanent','true');drawing.append(e);return e}
function createTextRelation(a,text){const e=document.createElement('riki-relation');e.setAttribute('name',next('R'));e.setAttribute('kind','text');e.setAttribute('a',a);e.setAttribute('text',text);e.setAttribute('permanent','true');drawing.append(e);return e}
function relData(r){
  if(!r)return null;const k=r.getAttribute('kind'),a=pxy(r.getAttribute('a')),b=pxy(r.getAttribute('b')),c=pxy(r.getAttribute('c'));
  return a&&b?{kind:k,a,b,c}:null
}
function relCenter(r){
  const d=relData(r);if(!d)return{x:0,y:0};
  if(d.kind==='circle'||d.kind==='arc')return d.a;
  return{x:(d.a.x+d.b.x)/2,y:(d.a.y+d.b.y)/2}
}
function makeEntity(d){
  const a=createPoint(d.a),b=createPoint(d.b),c=d.c?createPoint(d.c):null;
  return createRelation(d.kind,a,b,c)
}
function cloneShift(r,dx,dy){
  const d=relData(r);if(!d)return null;
  return makeEntity({kind:d.kind,a:{x:d.a.x+dx,y:d.a.y+dy},b:{x:d.b.x+dx,y:d.b.y+dy},c:d.c?{x:d.c.x+dx,y:d.c.y+dy}:null})
}
function moveRelation(r,dx,dy){
  if(!r)return;for(const key of ['a','b','c']){const n=r.getAttribute(key),p=n&&point(n);if(p){p.setAttribute('x',+p.getAttribute('x')+dx);p.setAttribute('y',+p.getAttribute('y')+dy)}}
}
function sideVector(r,w){const c=relCenter(r),dx=w.x-c.x,dy=w.y-c.y,l=Math.hypot(dx,dy)||1;return{x:dx/l,y:dy/l}}
function offsetEntity(r,w,distance){
  const d=relData(r);if(!d||!(distance>0))return null;
  if(d.kind==='line'){
    const vx=d.b.x-d.a.x,vy=d.b.y-d.a.y,L=Math.hypot(vx,vy);if(!L)return null;
    let nx=-vy/L,ny=vx/L;const mx=(d.a.x+d.b.x)/2,my=(d.a.y+d.b.y)/2;if((w.x-mx)*nx+(w.y-my)*ny<0){nx=-nx;ny=-ny}
    return makeEntity({kind:'line',a:{x:d.a.x+nx*distance,y:d.a.y+ny*distance},b:{x:d.b.x+nx*distance,y:d.b.y+ny*distance}})
  }
  if(d.kind==='rect'){
    const minx=Math.min(d.a.x,d.b.x),maxx=Math.max(d.a.x,d.b.x),miny=Math.min(d.a.y,d.b.y),maxy=Math.max(d.a.y,d.b.y);
    const outside=w.x<minx||w.x>maxx||w.y<miny||w.y>maxy,sgn=outside?1:-1;
    const nminx=minx-sgn*distance,nmaxx=maxx+sgn*distance,nminy=miny-sgn*distance,nmaxy=maxy+sgn*distance;
    if(nmaxx<=nminx||nmaxy<=nminy)return null;
    return makeEntity({kind:'rect',a:{x:nminx,y:nminy},b:{x:nmaxx,y:nmaxy}})
  }
  if(d.kind==='circle'||d.kind==='arc'){
    const r0=Math.hypot(d.b.x-d.a.x,d.b.y-d.a.y),rw=Math.hypot(w.x-d.a.x,w.y-d.a.y),sgn=rw>=r0?1:-1,r1=r0+sgn*distance;if(r1<=1e-9)return null;
    const scale=r1/r0,b={x:d.a.x+(d.b.x-d.a.x)*scale,y:d.a.y+(d.b.y-d.a.y)*scale};
    const c=d.c?{x:d.a.x+(d.c.x-d.a.x)*scale,y:d.a.y+(d.c.y-d.a.y)*scale}:null;
    return makeEntity({kind:d.kind,a:d.a,b,c})
  }
  return null
}
function reflectPoint(p,a,b){const vx=b.x-a.x,vy=b.y-a.y,L2=vx*vx+vy*vy;if(!L2)return p;const t=((p.x-a.x)*vx+(p.y-a.y)*vy)/L2,q={x:a.x+t*vx,y:a.y+t*vy};return{x:2*q.x-p.x,y:2*q.y-p.y}}
function mirrorEntity(r,a,b){const d=relData(r);if(!d)return null;return makeEntity({kind:d.kind,a:reflectPoint(d.a,a,b),b:reflectPoint(d.b,a,b),c:d.c?reflectPoint(d.c,a,b):null})}
function beginModify(tool){
  draft=null;cmdInput={stage:'distance',buffer:'',v1:null};
  modify={tool,hover:null,axisA:null,axisB:null};
  if(tool==='mirror')cmdInput.stage='axis';
  updateCommand();render()
}
function finishModify(){modify=null;cmdInput={stage:'idle',buffer:'',v1:null};updateCommand();render()}
function applyLinearModify(tool,w,dist){
  const r=selected&&drawing.querySelector(`:scope > riki-relation[name="${selected}"]`);if(!r||!(dist>0))return;
  saveHistory();let out=null;
  if(tool==='offset')out=offsetEntity(r,w,dist);
  else{const v=sideVector(r,w),dx=v.x*dist,dy=v.y*dist;if(tool==='copy')out=cloneShift(r,dx,dy);else if(tool==='move'){moveRelation(r,dx,dy);out=r}}
  if(out)selected=out.getAttribute('name');finishModify()
}
function saveHistory(){history.push(drawing.innerHTML);if(history.length>100)history.shift()}
function undo(){if(!history.length)return;drawing.innerHTML=history.pop();selected=null;render()}
function del(){if(!selected)return;saveHistory();const rel=drawing.querySelector(`:scope > riki-relation[name="${selected}"]`);if(rel){const used=[rel.getAttribute('a'),rel.getAttribute('b'),rel.getAttribute('c')];rel.remove();for(const n of used){if(n&&!relations().some(r=>r.getAttribute('a')===n||r.getAttribute('b')===n||r.getAttribute('c')===n))point(n)?.remove()}}selected=null;render()}

function activateCadControl(name,kind){
  if(kind==='tool'){
    set('TOOL',name);draft=null;modify=null;
    if(!['copy','move','offset','mirror'].includes(name))selected=null;
    resetCommandInput();
    if(['copy','move','offset','mirror'].includes(name)&&selected)beginModify(name);
    syncToolbar();render();return;
  }
  if(name==='undo')undo();
  else if(name==='delete')del();
  else if(name==='fit')fit();
  else if(name==='save')saveProject();
  else if(name==='open')openProject.click();
  else if(name==='text-down'){set('TEXT_SIZE',Math.max(8,num('TEXT_SIZE')-2));render();}
  else if(name==='text-up'){set('TEXT_SIZE',Math.min(72,num('TEXT_SIZE')+2));render();}
}
function runCadControl(b){
  const name=b.dataset.cadName||b.dataset.name;
  const kind=b.dataset.cadKind||b.dataset.kind;
  if(!name)return;
  if(kind==='tool'){
    set('TOOL',name);
    draft=null;modify=null;
    if(!['copy','move','offset','mirror'].includes(name))selected=null;
    resetCommandInput();
    if(['copy','move','offset','mirror'].includes(name)&&selected)beginModify(name);
    syncToolbar();render();
    return;
  }
  if(name==='undo')undo();
  else if(name==='delete')del();
  else if(name==='fit')fit();
  else if(name==='save')saveProject();
  else if(name==='open')openProject.click();
  else if(name==='text-down'){set('TEXT_SIZE',Math.max(8,num('TEXT_SIZE')-2));render();}
  else if(name==='text-up'){set('TEXT_SIZE',Math.min(72,num('TEXT_SIZE')+2));render();}
}
function buildToolbar(){
  document.querySelectorAll('[data-cad-name]').forEach(b=>{
    b.addEventListener('click',()=>runCadControl(b));
  });
  syncToolbar();
}
function syncToolbar(){
  document.querySelectorAll('[data-cad-kind="tool"]').forEach(b=>b.classList.toggle('active',b.dataset.cadName===get('TOOL')));
  updateCommand();
}

function resize(){const r=canvas.getBoundingClientRect(),q=dpr();canvas.width=Math.round(r.width*q);canvas.height=Math.round(r.height*q);ctx.setTransform(q,0,0,q,0,0);render()}
function drawGuides(){
  ctx.save();
  ctx.lineWidth=1;
  ctx.setLineDash([6,6]);
  ctx.strokeStyle='#9aa3ad';

  if(guideState.x!==null){
    const p=worldToScreen({x:guideState.x,y:0});
    ctx.beginPath();
    ctx.moveTo(p.x,0);
    ctx.lineTo(p.x,canvas.clientHeight);
    ctx.stroke();
  }

  if(guideState.y!==null){
    const p=worldToScreen({x:0,y:guideState.y});
    ctx.beginPath();
    ctx.moveTo(0,p.y);
    ctx.lineTo(canvas.clientWidth,p.y);
    ctx.stroke();
  }

  ctx.setLineDash([]);

  if(guideState.point){
    const p=worldToScreen(guideState.point);
    ctx.strokeStyle='#111';
    ctx.lineWidth=1.5;
    ctx.beginPath();
    ctx.arc(p.x,p.y,5,0,Math.PI*2);
    ctx.stroke();
  }

  ctx.restore();
}

function arcWorldPoints(center,start,end){
  if(!center||!start||!end)return [];
  const r=Math.hypot(start.x-center.x,start.y-center.y);
  if(!Number.isFinite(r)||r<=1e-9)return [];
  let a0=Math.atan2(start.y-center.y,start.x-center.x);
  let a1=Math.atan2(end.y-center.y,end.x-center.x);
  let sweep=a1-a0;
  const tau=Math.PI*2;
  while(sweep<0)sweep+=tau;
  while(sweep>=tau)sweep-=tau;
  if(sweep<=1e-7)return [];
  const steps=Math.max(24,Math.ceil(sweep*32));
  const out=[];
  for(let i=0;i<=steps;i++){
    const a=a0+sweep*(i/steps);
    out.push({x:center.x+r*Math.cos(a),y:center.y+r*Math.sin(a)});
  }
  return out;
}
function drawArcWorld(center,start,end){
  const pts=arcWorldPoints(center,start,end);
  if(!pts.length)return;
  const p0=worldToScreen(pts[0]);
  ctx.moveTo(p0.x,p0.y);
  for(let i=1;i<pts.length;i++){
    const p=worldToScreen(pts[i]);
    ctx.lineTo(p.x,p.y);
  }
}
function drawArrow(p,dir,size){const n={x:-dir.y,y:dir.x};ctx.beginPath();ctx.moveTo(p.x,p.y);ctx.lineTo(p.x-dir.x*size+n.x*size*.45,p.y-dir.y*size+n.y*size*.45);ctx.moveTo(p.x,p.y);ctx.lineTo(p.x-dir.x*size-n.x*size*.45,p.y-dir.y*size-n.y*size*.45);ctx.stroke()}
function dimGeometry(a,b,c){const vx=b.x-a.x,vy=b.y-a.y,L=Math.hypot(vx,vy);if(!L)return null;const u={x:vx/L,y:vy/L},n={x:-u.y,y:u.x};const mid={x:(a.x+b.x)/2,y:(a.y+b.y)/2};const off=(c.x-mid.x)*n.x+(c.y-mid.y)*n.y;return{L,u,n,off,qa:{x:a.x+n.x*off,y:a.y+n.y*off},qb:{x:b.x+n.x*off,y:b.y+n.y*off}}}
function drawRel(r,highlight=false){const k=r.getAttribute('kind'),a=pxy(r.getAttribute('a'));if(!a)return;const size=num('TEXT_SIZE')||16;ctx.save();ctx.strokeStyle=highlight?'#111111':'#444444';ctx.fillStyle=highlight?'#111111':'#222222';ctx.lineWidth=highlight?2.6:1.6;
  if(k==='text'){const A=worldToScreen(a);ctx.font=`${size}px system-ui,sans-serif`;ctx.textBaseline='alphabetic';ctx.fillText(r.getAttribute('text')||'',A.x,A.y);ctx.restore();return}
  const b=pxy(r.getAttribute('b'));if(!b){ctx.restore();return}const A=worldToScreen(a),B=worldToScreen(b);ctx.beginPath();
  if(k==='line'){ctx.moveTo(A.x,A.y);ctx.lineTo(B.x,B.y)}
  else if(k==='rect'){ctx.rect(Math.min(A.x,B.x),Math.min(A.y,B.y),Math.abs(B.x-A.x),Math.abs(B.y-A.y))}
  else if(k==='circle'){const rad=Math.hypot(B.x-A.x,B.y-A.y);ctx.arc(A.x,A.y,rad,0,Math.PI*2)}
  else if(k==='arc'){drawArcWorld(a,b,pxy(r.getAttribute('c')))}
  else if(k==='dim'){const c=pxy(r.getAttribute('c')),g=c&&dimGeometry(a,b,c);if(g){ctx.lineWidth=highlight?1.2:0.8;const QA=worldToScreen(g.qa),QB=worldToScreen(g.qb),sc=num('VIEW_SCALE')||1,ext=Math.max(5,6/sc),ea=worldToScreen({x:g.qa.x+g.n.x*Math.sign(g.off||1)*ext,y:g.qa.y+g.n.y*Math.sign(g.off||1)*ext}),eb=worldToScreen({x:g.qb.x+g.n.x*Math.sign(g.off||1)*ext,y:g.qb.y+g.n.y*Math.sign(g.off||1)*ext});ctx.moveTo(A.x,A.y);ctx.lineTo(ea.x,ea.y);ctx.moveTo(B.x,B.y);ctx.lineTo(eb.x,eb.y);ctx.moveTo(QA.x,QA.y);ctx.lineTo(QB.x,QB.y);ctx.stroke();const ds={x:(QB.x-QA.x),y:(QB.y-QA.y)},dl=Math.hypot(ds.x,ds.y)||1,du={x:ds.x/dl,y:ds.y/dl};drawArrow(QA,{x:-du.x,y:-du.y},8);drawArrow(QB,du,8);const M={x:(QA.x+QB.x)/2,y:(QA.y+QB.y)/2};ctx.font=`${size}px system-ui,sans-serif`;ctx.textAlign='center';ctx.textBaseline='bottom';ctx.save();ctx.translate(M.x,M.y-4);let ang=Math.atan2(QB.y-QA.y,QB.x-QA.x);if(ang>Math.PI/2||ang<-Math.PI/2)ang+=Math.PI;ctx.rotate(ang);ctx.fillText(formatMeasure(g.L),0,0);ctx.restore();ctx.restore();return}}
  ctx.stroke();ctx.restore()}
function formatMeasure(v){const s=Math.abs(v-Math.round(v))<1e-8?String(Math.round(v)):v.toFixed(2).replace(/0+$/,'').replace(/\.$/,'');return s}

function drawDraft(){if(!draft||!draft.a)return;const A=worldToScreen(draft.a);ctx.save();ctx.setLineDash([6,5]);ctx.strokeStyle='#777777';ctx.lineWidth=1.3;ctx.beginPath();if(draft.kind==='line'&&draft.b){const B=worldToScreen(draft.b);ctx.moveTo(A.x,A.y);ctx.lineTo(B.x,B.y)}else if(draft.kind==='rect'&&draft.b){const B=worldToScreen(draft.b);ctx.rect(Math.min(A.x,B.x),Math.min(A.y,B.y),Math.abs(B.x-A.x),Math.abs(B.y-A.y))}else if(draft.kind==='circle'&&draft.b){const B=worldToScreen(draft.b);ctx.arc(A.x,A.y,Math.hypot(B.x-A.x,B.y-A.y),0,Math.PI*2)}else if(draft.kind==='dim'){ctx.lineWidth=0.8;if(draft.b){const B=worldToScreen(draft.b);if(draft.c){const g=dimGeometry(draft.a,draft.b,draft.c);if(g){const QA=worldToScreen(g.qa),QB=worldToScreen(g.qb);ctx.moveTo(A.x,A.y);ctx.lineTo(QA.x,QA.y);ctx.moveTo(B.x,B.y);ctx.lineTo(QB.x,QB.y);ctx.moveTo(QA.x,QA.y);ctx.lineTo(QB.x,QB.y)}}else{ctx.moveTo(A.x,A.y);ctx.lineTo(B.x,B.y)}}}else if(draft.kind==='text'){ctx.font=`${num('TEXT_SIZE')||16}px system-ui,sans-serif`;ctx.fillStyle='#777777';ctx.setLineDash([]);ctx.fillText(cmdInput.buffer||'Text',A.x,A.y)}else if(draft.kind==='arc'){
  ctx.moveTo(A.x-4,A.y);ctx.lineTo(A.x+4,A.y);ctx.moveTo(A.x,A.y-4);ctx.lineTo(A.x,A.y+4);
  if(draft.b){
    const B=worldToScreen(draft.b);
    if(draft.c){drawArcWorld(draft.a,draft.b,draft.c)}
    else{ctx.moveTo(A.x,A.y);ctx.lineTo(B.x,B.y)}
  }
}ctx.stroke();ctx.restore()}
function drawModifyPreview(){
  if(!modify||!selected)return;const r=drawing.querySelector(`:scope > riki-relation[name="${selected}"]`);if(!r)return;
  ctx.save();ctx.setLineDash([5,5]);ctx.strokeStyle='#111111';ctx.lineWidth=1.4;
  if(modify.tool==='mirror'&&modify.axisA){const a=worldToScreen(modify.axisA),b=worldToScreen(modify.axisB||modify.hover||modify.axisA);ctx.beginPath();ctx.moveTo(a.x,a.y);ctx.lineTo(b.x,b.y);ctx.stroke()}
  else if(modify.hover){const c=worldToScreen(relCenter(r)),h=worldToScreen(modify.hover);ctx.beginPath();ctx.moveTo(c.x,c.y);ctx.lineTo(h.x,h.y);ctx.stroke()}
  ctx.restore()
}
function render(){ctx.clearRect(0,0,canvas.clientWidth,canvas.clientHeight);for(const r of relations())drawRel(r,r.getAttribute('name')===selected);drawGuides();drawDraft();drawModifyPreview();count.textContent=`${relations().length} ${relations().length===1?'entity':'entities'}`;selectionText.textContent=selected||'no selection'}

function distSeg(p,a,b){const dx=b.x-a.x,dy=b.y-a.y,l=dx*dx+dy*dy;if(!l)return Math.hypot(p.x-a.x,p.y-a.y);let t=((p.x-a.x)*dx+(p.y-a.y)*dy)/l;t=Math.max(0,Math.min(1,t));return Math.hypot(p.x-(a.x+t*dx),p.y-(a.y+t*dy))}
function hit(w){const tol=8/(num('VIEW_SCALE')||1);let best=null,bd=Infinity;for(const r of relations()){const k=r.getAttribute('kind'),a=pxy(r.getAttribute('a'));if(!a)continue;let d=Infinity;if(k==='text'){d=Math.hypot(w.x-a.x,w.y-a.y)}else{const b=pxy(r.getAttribute('b'));if(!b)continue;if(k==='line')d=distSeg(w,a,b);if(k==='rect'){const x1=Math.min(a.x,b.x),x2=Math.max(a.x,b.x),y1=Math.min(a.y,b.y),y2=Math.max(a.y,b.y);d=Math.min(distSeg(w,{x:x1,y:y1},{x:x2,y:y1}),distSeg(w,{x:x2,y:y1},{x:x2,y:y2}),distSeg(w,{x:x2,y:y2},{x:x1,y:y2}),distSeg(w,{x:x1,y:y2},{x:x1,y:y1}))}if(k==='circle')d=Math.abs(Math.hypot(w.x-a.x,w.y-a.y)-Math.hypot(b.x-a.x,b.y-a.y));if(k==='arc'){const c=pxy(r.getAttribute('c'));if(c){const rad=Math.hypot(b.x-a.x,b.y-a.y),ang=Math.atan2(w.y-a.y,w.x-a.x),sa=Math.atan2(b.y-a.y,b.x-a.x),ea=Math.atan2(c.y-a.y,c.x-a.x),twopi=Math.PI*2,norm=x=>(x%twopi+twopi)%twopi,span=norm(ea-sa),pos=norm(ang-sa);d=pos<=span+0.02?Math.abs(Math.hypot(w.x-a.x,w.y-a.y)-rad):Infinity}}if(k==='dim'){const c=pxy(r.getAttribute('c')),g=c&&dimGeometry(a,b,c);if(g)d=Math.min(distSeg(w,g.qa,g.qb),distSeg(w,a,g.qa),distSeg(w,b,g.qb))}}
if(d<bd){bd=d;best=r}}return bd<=tol?best:null}
function eventPoint(e){const r=canvas.getBoundingClientRect();return{x:e.clientX-r.left,y:e.clientY-r.top}}
canvas.addEventListener('pointerdown',e=>{canvas.focus({preventScroll:true});canvas.setPointerCapture(e.pointerId);const sp=eventPoint(e),w=snap(screenToWorld(sp));if(e.button===1||e.button===2||e.altKey||e.shiftKey){pan={sp,x:num('VIEW_X'),y:num('VIEW_Y')};return}const tool=get('TOOL');if(tool==='select'){const h=hit(w);selected=h?.getAttribute('name')||null;render();return}if(['copy','move','offset','mirror'].includes(tool)){
  if(!selected){const h=hit(w);selected=h?.getAttribute('name')||null;if(selected)beginModify(tool);else render();return}
  if(!modify)beginModify(tool);
  if(tool==='mirror'){
    if(!modify.axisA){modify.axisA=w;modify.axisB=w;cmdInput={stage:'mirrorAngle',buffer:'',v1:null};updateCommand();render();return}
    if(Math.hypot(w.x-modify.axisA.x,w.y-modify.axisA.y)>1e-9){saveHistory();const r=drawing.querySelector(`:scope > riki-relation[name="${selected}"]`),out=mirrorEntity(r,modify.axisA,w);if(out)selected=out.getAttribute('name');finishModify()}return
  }
  modify.hover=w;
  const r=drawing.querySelector(`:scope > riki-relation[name="${selected}"]`);
  if(!r){finishModify();return}
  if(tool==='move'||tool==='copy'){
    const c=relCenter(r),dx=w.x-c.x,dy=w.y-c.y;
    if(Math.hypot(dx,dy)>1e-9){
      saveHistory();
      let out=null;
      if(tool==='copy')out=cloneShift(r,dx,dy);
      else{moveRelation(r,dx,dy);out=r}
      if(out)selected=out.getAttribute('name');
      finishModify();
    }
    return
  }
  if(tool==='offset'){
    const d=relData(r);let dist=0;
    if(d){
      if(d.kind==='line')dist=distSeg(w,d.a,d.b);
      else if(d.kind==='circle'||d.kind==='arc')dist=Math.abs(Math.hypot(w.x-d.a.x,w.y-d.a.y)-Math.hypot(d.b.x-d.a.x,d.b.y-d.a.y));
      else if(d.kind==='rect'){
        const x1=Math.min(d.a.x,d.b.x),x2=Math.max(d.a.x,d.b.x),y1=Math.min(d.a.y,d.b.y),y2=Math.max(d.a.y,d.b.y);
        dist=Math.min(distSeg(w,{x:x1,y:y1},{x:x2,y:y1}),distSeg(w,{x:x2,y:y1},{x:x2,y:y2}),distSeg(w,{x:x2,y:y2},{x:x1,y:y2}),distSeg(w,{x:x1,y:y2},{x:x1,y:y1}));
      }
    }
    if(dist>1e-9){saveHistory();const out=offsetEntity(r,w,dist);if(out)selected=out.getAttribute('name');finishModify()}
    return
  }
  updateCommand();render();return
}if(tool==='dim'){
  if(!draft){draft={kind:'dim',a:w,b:null,c:null,stage:1};cmdInput={stage:'second',buffer:'',v1:null};updateCommand();render();return}
  if(draft.stage===1){if(Math.hypot(w.x-draft.a.x,w.y-draft.a.y)>1e-9){draft.b=w;draft.stage=2;cmdInput.stage='offset';updateCommand();render()}return}
  if(draft.stage===2){draft.c=w;saveHistory();const a=createPoint(draft.a),b=createPoint(draft.b),c=createPoint(draft.c);const rel=createRelation('dim',a,b,c);selected=rel.getAttribute('name');draft=null;resetCommandInput();render();return}
}if(tool==='text'){
  if(!draft){draft={kind:'text',a:w};cmdInput={stage:'text',buffer:'',v1:null};updateCommand();render()}return
}if(tool==='line'){
  if(!draft){
    draft={kind:'line',a:w,b:w};
    lastPointerWorld=w;
    cmdInput={stage:'length',buffer:'',v1:null};
    updateCommand();
    render();
  }else{
    draft.b=w;
    commitDraft(draft);
  }
  return
}if(tool==='rect'){if(!draft){draft={kind:'rect',a:w,b:w};cmdInput={stage:'width',buffer:'',v1:null};updateCommand();render()}else{draft.b=w;commitDraft(draft)}return}if(tool==='circle'){if(!draft){draft={kind:'circle',a:w,b:w};cmdInput={stage:'radius',buffer:'',v1:null};updateCommand();render()}else{draft.b=w;commitDraft(draft)}return}if(tool==='arc'){
  if(!draft){
    draft={kind:'arc',a:w,b:null,c:null,stage:1};
    cmdInput={stage:'radius',buffer:'',v1:null,v2:null};
    updateCommand();render();return
  }
  if(draft.stage===1){
    draft.b=w;
    draft.stage=2;
    cmdInput.stage='endPoint';
    cmdInput.v1=Math.hypot(w.x-draft.a.x,w.y-draft.a.y);
    cmdInput.v2=lineAngle(draft.a,w);
    updateCommand();render();return
  }
  if(draft.stage===2){
    draft.c=w;
    commitDraft(draft);return
  }
}});
canvas.addEventListener('pointermove',e=>{const sp=eventPoint(e),raw=screenToWorld(sp),w=snap(raw);lastPointerWorld=w;coords.textContent=`x ${w.x.toFixed(2)} · y ${w.y.toFixed(2)}`;if(pan){const s=num('VIEW_SCALE')||1;set('VIEW_X',pan.x-(sp.x-pan.sp.x)/s);set('VIEW_Y',pan.y+(sp.y-pan.sp.y)/s);render();return}if(modify&&selected){modify.hover=w;if(modify.tool==='mirror'&&modify.axisA)modify.axisB=w;render();return}if(draft){if(draft.kind==='dim'){if(draft.stage===1)draft.b=w;else if(draft.stage===2)draft.c=w;}else if(draft.kind==='text'){}else if(draft.kind==='arc'){
  if(draft.stage===1)draft.b=w;
  else if(draft.stage===2)draft.c=w;
  if(cmdInput.stage==='startAngle'&&cmdInput.v1!=null&&cmdInput.buffer){const a=cadNumber(cmdInput.buffer);if(Number.isFinite(a))draft.b=endpointFromPolar(draft.a,cmdInput.v1,a)}
  if(cmdInput.stage==='endAngle'&&cmdInput.v1!=null&&cmdInput.buffer){const a=cadNumber(cmdInput.buffer);if(Number.isFinite(a))draft.c=endpointFromPolar(draft.a,cmdInput.v1,a)}
}else if(draft.kind==='line'){
  const pair=parseLinePair(cmdInput.buffer);

  if(pair&&pair.length>0&&Number.isFinite(pair.angle)){
    draft.b=endpointFromPolar(draft.a,pair.length,pair.angle);
  }else if(cmdInput.buffer){
    const len=cadNumber(cmdInput.buffer);
    const target=lastPointerWorld||w;
    const deg=lineAngle(draft.a,target);

    if(Number.isFinite(len)&&len>0){
      draft.b=endpointFromPolar(draft.a,len,deg);
    }else{
      draft.b=w;
    }
  }else{
    draft.b=w;
  }
}else if(draft.kind==='rect'&&cmdInput.v1!=null){const h=cmdInput.stage==='height'&&cmdInput.buffer?cadNumber(cmdInput.buffer):(w.y-draft.a.y);draft.b={x:draft.a.x+cmdInput.v1,y:draft.a.y+(Number.isFinite(h)?h:0)}}else if(draft.kind==='circle'&&cmdInput.buffer){const r=cadNumber(cmdInput.buffer);draft.b=Number.isFinite(r)&&r>0?{x:draft.a.x+r,y:draft.a.y}:w}else draft.b=w;render()}});
canvas.addEventListener('pointerup',e=>{if(pan){pan=null;return}});
canvas.addEventListener('wheel',e=>{e.preventDefault();const sp=eventPoint(e),before=screenToWorld(sp),old=num('VIEW_SCALE')||1,ns=Math.max(.02,Math.min(100,old*Math.exp(-e.deltaY*.001)));set('VIEW_SCALE',ns);const after=screenToWorld(sp);set('VIEW_X',num('VIEW_X')+(before.x-after.x));set('VIEW_Y',num('VIEW_Y')+(before.y-after.y));render()},{passive:false});
canvas.addEventListener('pointerleave',()=>{guideState={x:null,y:null,point:null};render()});
canvas.addEventListener('contextmenu',e=>e.preventDefault());
function cadEventInEditable(e){
  const t=e.target;
  if(!t)return false;
  return !!(
    t.closest?.('input,textarea,select,[contenteditable="true"]') ||
    t.isContentEditable
  );
}

function appendCadNumericKey(key){
  let k=key;
  if(k===',')k='.';

  if(/^[0-9]$/.test(k)){
    cmdInput.buffer+=k;
    return true;
  }

  if(k==='.'){
    if(cmdInput.buffer.includes('.'))return false;
    if(cmdInput.buffer===''||cmdInput.buffer==='+'||cmdInput.buffer==='-'){
      cmdInput.buffer+='0.';
    }else{
      cmdInput.buffer+='.';
    }
    return true;
  }

  if(k==='+'||k==='-'){
    if(cmdInput.buffer===''){
      cmdInput.buffer=k;
      return true;
    }
    return false;
  }

  return false;
}

function cadNumber(text){
  const s=String(text??'').trim().replace(',','.');
  if(!s||s==='+'||s==='-'||s==='.'||s==='+.'||s==='-.')return NaN;
  const n=Number(s);
  return Number.isFinite(n)?n:NaN;
}

window.addEventListener('keydown',e=>{if(document.body.dataset.mode!=='cad')return;
  // Never let CAD shortcuts/command input steal keystrokes from real form fields.
  if(cadEventInEditable(e))return;
  if((e.ctrlKey||e.metaKey)&&e.key.toLowerCase()==='s'){e.preventDefault();saveProject();return}
  if((e.ctrlKey||e.metaKey)&&e.key.toLowerCase()==='o'){e.preventDefault();openProject.click();return}
  if((e.ctrlKey||e.metaKey)&&e.key.toLowerCase()==='z'){e.preventDefault();undo();return}
  const tool=get('TOOL');
  if(['copy','move','offset','mirror'].includes(tool)&&selected){
    if(!modify)beginModify(tool);
    if(e.key==='Escape'){e.preventDefault();finishModify();selected=null;render();return}
    if(e.key==='Backspace'){e.preventDefault();cmdInput.buffer=cmdInput.buffer.slice(0,-1);updateCommand();render();return}
    if(/^[0-9.,+-]$/.test(e.key)){e.preventDefault();if(appendCadNumericKey(e.key)){updateCommand();render()}return}
    if(e.key==='Enter'){
      e.preventDefault();
      if(tool==='mirror'){
        if(!modify.axisA)return;
        const deg=cadNumber(cmdInput.buffer),r=drawing.querySelector(`:scope > riki-relation[name="${selected}"]`);
        if(Number.isFinite(deg)){const b=endpointFromPolar(modify.axisA,100,deg);saveHistory();const out=mirrorEntity(r,modify.axisA,b);if(out)selected=out.getAttribute('name');finishModify()}
      }else{
        const d=cadNumber(cmdInput.buffer),w=modify.hover||relCenter(drawing.querySelector(`:scope > riki-relation[name="${selected}"]`));
        if(Number.isFinite(d)&&d>0)applyLinearModify(tool,w,d)
      }
      return
    }
  }
  if(tool==='text'&&draft&&draft.kind==='text'){
    if(e.key==='Escape'){e.preventDefault();draft=null;resetCommandInput();render();return}
    if(e.key==='Backspace'){
      e.preventDefault();
      cmdInput.buffer=cmdInput.buffer.slice(0,-1);

      if(tool==='line'){
        const pair=parseLinePair(cmdInput.buffer);
        if(pair&&pair.length>0&&Number.isFinite(pair.angle)){
          draft.b=endpointFromPolar(draft.a,pair.length,pair.angle);
        }else{
          const len=cadNumber(cmdInput.buffer);
          const target=lastPointerWorld||draft.b||draft.a;
          const deg=lineAngle(draft.a,target);
          if(Number.isFinite(len)&&len>0&&Number.isFinite(deg)){
            draft.b=endpointFromPolar(draft.a,len,deg);
          }else if(lastPointerWorld){
            draft.b=lastPointerWorld;
          }
        }
      }

      updateCommand();
      render();
      return;
    }
    if(e.key==='Enter'){e.preventDefault();const t=cmdInput.buffer.trim();if(t){saveHistory();const a=createPoint(draft.a),rel=createTextRelation(a,t);selected=rel.getAttribute('name')}draft=null;resetCommandInput();render();return}
    if(e.key.length===1&&!e.ctrlKey&&!e.metaKey&&!e.altKey){e.preventDefault();cmdInput.buffer+=e.key;updateCommand();render();return}
  }
  if(tool==='dim'&&draft&&e.key==='Escape'){e.preventDefault();draft=null;resetCommandInput();render();return}
  if(draft&&['line','rect','circle','arc'].includes(tool)){
    if(e.key==='Escape'){e.preventDefault();draft=null;resetCommandInput();render();return}
    if(e.key==='Backspace'){e.preventDefault();cmdInput.buffer=cmdInput.buffer.slice(0,-1);updateCommand();render();return}
    if(/^[0-9.,+-]$/.test(e.key)){
      e.preventDefault();

      if(tool==='line' && (cmdInput.buffer.includes('<') || cmdInput.buffer.includes('@'))){
        let k=e.key===','?'.':e.key;
        if(/^[0-9]$/.test(k)){
          cmdInput.buffer+=k;
        }else if(k==='.' && !cmdInput.buffer.split(/[<@]/).pop().includes('.')){
          cmdInput.buffer+=k;
        }else if((k==='+'||k==='-') && /[<@]$/.test(cmdInput.buffer)){
          cmdInput.buffer+=k;
        }
        updateCommand();
        render();
        return;
      }

      if(appendCadNumericKey(e.key)){
        // Update LINE geometry immediately, even if the mouse does not move.
        if(tool==='line'){
          const len=cadNumber(cmdInput.buffer);
          const target=lastPointerWorld||draft.b||draft.a;
          const deg=lineAngle(draft.a,target);
          if(Number.isFinite(len)&&len>0&&Number.isFinite(deg)){
            draft.b=endpointFromPolar(draft.a,len,deg);
          }
        }
        updateCommand();
        render();
      }
      return;
    }
    if(tool==='line'){
      // Direct polar entry, e.g. 100<45 or 100@45.
      const pair=parseLinePair(cmdInput.buffer);

      if(e.key==='Enter'){
        e.preventDefault();

        if(pair&&pair.length>0&&Number.isFinite(pair.angle)){
          draft.b=endpointFromPolar(draft.a,pair.length,pair.angle);
          commitDraft(draft);
          return;
        }

        const len=cadNumber(cmdInput.buffer);
        if(Number.isFinite(len)&&len>0){
          const target=lastPointerWorld||draft.b||draft.a;
          let deg=lineAngle(draft.a,target);
          if(!Number.isFinite(deg))deg=0;
          draft.b=endpointFromPolar(draft.a,len,deg);
          commitDraft(draft);
        }
        return;
      }

      // Allow separator for direct polar entry inside the same buffer.
      if((e.key==='<'||e.key==='@') && !cmdInput.buffer.includes('<') && !cmdInput.buffer.includes('@')){
        e.preventDefault();
        const len=cadNumber(cmdInput.buffer);
        if(Number.isFinite(len)&&len>0){
          cmdInput.buffer += e.key;
          updateCommand();
          render();
        }
        return;
      }
    }
    if(tool==='rect'&&e.key==='Enter'){
      e.preventDefault();
      if(cmdInput.stage==='width'){
        const v=cadNumber(cmdInput.buffer);
        if(Number.isFinite(v)&&v!==0){cmdInput.v1=v;cmdInput.buffer='';cmdInput.stage='height';updateCommand();render()}
      }else{
        const h=cadNumber(cmdInput.buffer);
        if(cmdInput.v1!==null&&Number.isFinite(h)&&h!==0){draft.b={x:draft.a.x+cmdInput.v1,y:draft.a.y+h};commitDraft(draft)}
      }
      return
    }
    if(tool==='circle'&&e.key==='Enter'){
      e.preventDefault();const r=cadNumber(cmdInput.buffer);
      if(Number.isFinite(r)&&r>0){draft.b={x:draft.a.x+r,y:draft.a.y};commitDraft(draft)}
      return
    }
    if(tool==='arc'){
      if(e.key==='Enter'){
        e.preventDefault();
        if(cmdInput.stage==='radius'){
          const r=cadNumber(cmdInput.buffer);
          if(Number.isFinite(r)&&r>0){cmdInput.v1=r;cmdInput.buffer='';cmdInput.stage='startAngle';updateCommand();render()}
        }else if(cmdInput.stage==='startAngle'){
          const a=cadNumber(cmdInput.buffer);
          if(cmdInput.v1>0&&Number.isFinite(a)){cmdInput.v2=a;draft.b=endpointFromPolar(draft.a,cmdInput.v1,a);cmdInput.buffer='';cmdInput.stage='endAngle';updateCommand();render()}
        }else if(cmdInput.stage==='endAngle'){
          const a=cadNumber(cmdInput.buffer);
          if(cmdInput.v1>0&&Number.isFinite(a)){draft.c=endpointFromPolar(draft.a,cmdInput.v1,a);commitDraft(draft)}
        }
        return
      }
    }

  }
  if(e.key==='Delete'||e.key==='Backspace'){
    if(selected){
      e.preventDefault();
      del();
    }
  }
  if(e.key==='Escape'){
    e.preventDefault();
    draft=null;modify=null;selected=null;resetCommandInput();render();
  }
});
function cadCanvasData(){render();return canvas.toDataURL('image/png')}

function cadSelectionBoundsCss(){
  if(!selected)return null;
  const rel=drawing.querySelector(`:scope > riki-relation[name="${selected}"]`);if(!rel)return null;
  const d=relData(rel),kind=rel.getAttribute('kind');let pts=[];
  if(kind==='text'){const a=pxy(rel.getAttribute('a'));if(a)pts=[a]}
  else if(d){
    pts=[d.a,d.b];if(d.c)pts.push(d.c);
    if(kind==='circle'||kind==='arc'){const rad=Math.hypot(d.b.x-d.a.x,d.b.y-d.a.y);pts.push({x:d.a.x-rad,y:d.a.y-rad},{x:d.a.x+rad,y:d.a.y+rad})}
    if(kind==='rect')pts.push({x:d.a.x,y:d.b.y},{x:d.b.x,y:d.a.y});
  }
  if(!pts.length)return null;
  const sp=pts.map(worldToScreen),xs=sp.map(p=>p.x),ys=sp.map(p=>p.y),pad=24;
  const x1=Math.max(0,Math.min(...xs)-pad),y1=Math.max(0,Math.min(...ys)-pad);
  const x2=Math.min(canvas.clientWidth,Math.max(...xs)+pad),y2=Math.min(canvas.clientHeight,Math.max(...ys)+pad);
  return{x:x1,y:y1,w:Math.max(1,x2-x1),h:Math.max(1,y2-y1)};
}

function cropCadCanvas(bounds){
  if(!bounds)return cadCanvasData();
  const q=dpr(),x=Math.max(0,Math.round(bounds.x*q)),y=Math.max(0,Math.round(bounds.y*q)),w=Math.max(1,Math.round(bounds.w*q)),h=Math.max(1,Math.round(bounds.h*q));
  const out=document.createElement('canvas');out.width=w;out.height=h;const ox=out.getContext('2d');ox.fillStyle='#fff';ox.fillRect(0,0,w,h);ox.drawImage(canvas,x,y,w,h,0,0,w,h);return out.toDataURL('image/png');
}

function printCadImage(dataUrl,mode){
  const img=document.createElement('img');img.className='print-cad-image';img.alt='CAD print';img.src=dataUrl;
  const layer=document.getElementById('print-layer');if(!layer)return;
  layer.innerHTML='';layer.dataset.mode=mode||'cad';layer.setAttribute('aria-hidden','false');layer.append(img);
  const cleanup=()=>{layer.setAttribute('aria-hidden','true');layer.innerHTML='';window.removeEventListener('afterprint',cleanup)};
  window.addEventListener('afterprint',cleanup);img.onload=()=>requestAnimationFrame(()=>window.print());
}

document.getElementById('cad-print')?.addEventListener('click',()=>{
  const mode=printArea?.value||'window';
  if(mode==='selection'){if(!selected){command.textContent='PRINT · select an entity first';return}render();printCadImage(cropCadCanvas(cadSelectionBoundsCss()),'cad-selection');return}
  if(mode==='window'){render();printCadImage(cadCanvasData(),'cad-window');return}
  const vx=get('VIEW_X'),vy=get('VIEW_Y'),vs=get('VIEW_SCALE');fit();
  requestAnimationFrame(()=>{render();const data=cadCanvasData();set('VIEW_X',vx);set('VIEW_Y',vy);set('VIEW_SCALE',vs);render();printCadImage(data,'cad-all')});
});

function fit(){const ps=points();if(!ps.length){set('VIEW_X',0);set('VIEW_Y',0);set('VIEW_SCALE',1);render();return}const xs=ps.map(p=>+p.getAttribute('x')),ys=ps.map(p=>+p.getAttribute('y'));const minx=Math.min(...xs),maxx=Math.max(...xs),miny=Math.min(...ys),maxy=Math.max(...ys);set('VIEW_X',(minx+maxx)/2);set('VIEW_Y',(miny+maxy)/2);const w=Math.max(1,maxx-minx),h=Math.max(1,maxy-miny);set('VIEW_SCALE',Math.max(.02,Math.min(100,.8*Math.min(canvas.clientWidth/w,canvas.clientHeight/h))));render()}

function syncSequenceFromSpace(){
  let m=0;
  for(const e of drawing.querySelectorAll('[name]')){
    const q=(e.getAttribute('name')||'').match(/^[PR](\d+)$/);
    if(q)m=Math.max(m,Number(q[1]));
  }
  seq=m;
}
syncSequenceFromSpace();buildToolbar();window.addEventListener('resize',resize);resize();window.RIKI_CAD={resize,render,fit,undo,tool:n=>{set('TOOL',n);syncToolbar();render();},count:()=>relations().length};
})();
</script>
<script>
(()=>{
 const s=document.querySelector('#cad-riki-space');
 const val=n=>s.querySelector(`riki-byte[name="${n}"] riki-value`);
 const bind=(id,n)=>{const el=document.getElementById(id); if(!el)return; el.addEventListener('change',()=>{const v=val(n);if(v)v.textContent=el.value;window.RIKI_CAD?.render();});};
 bind('cad-snap','SNAP');bind('cad-text-size','TEXT_SIZE');
})();
</script>

</body>
</html>
