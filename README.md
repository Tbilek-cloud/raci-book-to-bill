[book_to_bill_raci (3).html](https://github.com/user-attachments/files/26098580/book_to_bill_raci.3.html)
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>Book to Bill – RACI</title>
<style>
*{box-sizing:border-box;margin:0;padding:0}
body{font-family:Arial,sans-serif;font-size:13px;background:#f4f5f7;color:#172b4d;min-height:100vh;display:flex;flex-direction:column}
.topbar{background:#0052cc;color:#fff;padding:10px 20px;display:flex;align-items:center;justify-content:space-between;position:sticky;top:0;z-index:50;flex-shrink:0}
.brand{font-weight:700;font-size:15px;letter-spacing:.2px}
.topbar-right{display:flex;align-items:center;gap:8px}
.dot{width:8px;height:8px;border-radius:50%;background:#ffab00;display:none;margin-right:2px;flex-shrink:0}
.tbtn{border:none;border-radius:4px;padding:6px 13px;font-size:12px;font-weight:700;cursor:pointer;display:flex;align-items:center;gap:5px;transition:background .15s}
.tbtn-save{background:#36b37e;color:#fff}.tbtn-save:hover{background:#2da06e}.tbtn-save:disabled{background:#6b778c;cursor:not-allowed}
.tbtn-log{background:rgba(255,255,255,.15);color:#fff;border:1px solid rgba(255,255,255,.3)}.tbtn-log:hover{background:rgba(255,255,255,.28)}
.tbtn-notes{background:#6554c0;color:#fff;border:none}.tbtn-notes:hover{background:#5243aa}
.tabs{background:#fff;border-bottom:2px solid #dfe1e6;padding:0 20px;display:flex;flex-shrink:0}
.tab{padding:10px 18px;font-size:12px;font-weight:600;color:#6b778c;cursor:pointer;border-bottom:3px solid transparent;margin-bottom:-2px;transition:color .12s,border-color .12s}
.tab:hover{color:#0052cc}.tab.active{color:#0052cc;border-bottom-color:#0052cc}
.tab.notes-tab.active{color:#6554c0;border-bottom-color:#6554c0}
.toolbar{background:#fff;border-bottom:1px solid #dfe1e6;padding:9px 20px;display:flex;gap:12px;align-items:center;flex-wrap:wrap;flex-shrink:0}
.toolbar label{font-size:11px;color:#6b778c;font-weight:600}
.toolbar select{font-size:12px;padding:5px 8px;border:1.5px solid #dfe1e6;border-radius:4px;background:#fff;color:#172b4d;outline:none}
.toolbar select:focus{border-color:#0052cc}
.edit-hint{font-size:11px;color:#6b778c;font-style:italic}
.panel{display:none;flex:1;overflow-y:auto}.panel.active{display:block}
.content{padding:16px 20px}
.page-title{font-size:15px;font-weight:700;margin-bottom:2px}
.page-sub{font-size:11px;color:#6b778c;margin-bottom:12px}
.legend{display:flex;gap:8px;flex-wrap:wrap;margin-bottom:12px;align-items:center}
.leg{display:flex;align-items:center;gap:4px;font-size:11px;color:#6b778c}
.badge{display:inline-flex;align-items:center;justify-content:center;width:26px;height:26px;border-radius:4px;font-weight:700;font-size:10px;user-select:none;transition:transform .1s,opacity .15s;cursor:pointer;flex-shrink:0}
.badge:hover{transform:scale(1.15);box-shadow:0 0 0 2px #0052cc55}
.badge.off{opacity:.15;transform:scale(.88)}.badge.off:hover{opacity:.35;transform:scale(1.05)}
.r{background:#c0dd97;color:#27500a}.a{background:#b5d4f4;color:#0c447c}
.c{background:#fac775;color:#633806}.i{background:#d3d1c7;color:#444441}
.ra{background:#9fe1cb;color:#085041}
.empty{color:#bbb;font-size:14px;cursor:pointer;padding:3px 6px;border-radius:4px;transition:background .1s}.empty:hover{background:#f0f4ff}
table{width:100%;border-collapse:collapse;table-layout:fixed}
th,td{border:1px solid #dfe1e6;padding:5px 6px;vertical-align:middle;text-align:center}
th{font-weight:700;font-size:9px;background:#f4f5f7;color:#6b778c;text-transform:uppercase;letter-spacing:.3px;line-height:1.3}
th.proc-h{text-align:left;width:18%}
td.step{text-align:left;font-size:11px;color:#172b4d;padding-left:16px;line-height:1.4}
.section-row td{background:#ebecf0;font-weight:700;font-size:11px;text-align:left;color:#172b4d;text-transform:uppercase;letter-spacing:.3px;padding:7px 10px}
.sys-header{font-size:10px;font-weight:700;color:#0052cc !important}
.reg-header{font-size:9px;color:#0052cc !important;font-weight:400}
tr:hover td:not(.section-row td){background:#f0f4ff}
.section-row:hover td{background:#e4e6eb}
/* BP NOTES */
.notes-panel{padding:20px;max-width:1100px}
.notes-header{display:flex;align-items:center;justify-content:space-between;margin-bottom:6px;flex-wrap:wrap;gap:10px}
.notes-title{font-size:15px;font-weight:700;color:#172b4d}
.notes-subtitle{font-size:12px;color:#6b778c;margin-bottom:20px;line-height:1.6;background:#f0ebff;border-left:3px solid #6554c0;padding:10px 14px;border-radius:0 6px 6px 0}
.notes-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(320px,1fr));gap:16px;margin-bottom:24px}
.note-card{background:#fff;border:1px solid #dfe1e6;border-radius:8px;overflow:hidden;transition:box-shadow .15s}
.note-card:hover{box-shadow:0 2px 12px rgba(0,0,0,.1)}
.note-card-head{background:#6554c0;color:#fff;padding:10px 14px;display:flex;align-items:center;justify-content:space-between}
.note-card-head .section-lbl{font-size:11px;font-weight:700;letter-spacing:.3px}
.note-card-head .note-meta{font-size:10px;opacity:.8}
.note-card-body{padding:14px}
.note-card-body textarea{width:100%;border:1.5px solid #dfe1e6;border-radius:4px;padding:8px 10px;font-size:12px;font-family:Arial,sans-serif;resize:vertical;min-height:90px;outline:none;color:#172b4d;line-height:1.6;transition:border .15s}
.note-card-body textarea:focus{border-color:#6554c0}
.note-card-body textarea::placeholder{color:#aaa}
.note-card-footer{padding:8px 14px 12px;display:flex;align-items:center;justify-content:space-between;gap:8px;border-top:1px solid #f0f0f0;margin-top:8px}
.note-saved-ts{font-size:10px;color:#6b778c;font-style:italic}
.btn-save-note{background:#6554c0;color:#fff;border:none;border-radius:4px;padding:5px 14px;font-size:11px;font-weight:700;cursor:pointer;transition:background .15s}
.btn-save-note:hover{background:#5243aa}
.btn-save-note:disabled{background:#b3aad8;cursor:not-allowed}
.note-dot{width:7px;height:7px;border-radius:50%;background:#ffab00;display:none;margin-left:6px;flex-shrink:0}
.all-notes-section{margin-top:24px}
.all-notes-title{font-size:13px;font-weight:700;color:#172b4d;margin-bottom:12px;display:flex;align-items:center;gap:8px}
.all-notes-search{font-size:12px;padding:6px 10px;border:1.5px solid #dfe1e6;border-radius:4px;outline:none;width:220px;margin-left:auto}
.all-notes-search:focus{border-color:#6554c0}
.note-entry{background:#fff;border:1px solid #dfe1e6;border-radius:6px;padding:12px 16px;margin-bottom:10px}
.note-entry-head{display:flex;align-items:center;justify-content:space-between;margin-bottom:6px;flex-wrap:wrap;gap:6px}
.note-entry-section{font-size:11px;font-weight:700;color:#6554c0;background:#f0ebff;padding:2px 8px;border-radius:10px}
.note-entry-meta{font-size:10px;color:#6b778c}
.note-entry-text{font-size:12px;color:#172b4d;line-height:1.6;white-space:pre-wrap}
.no-notes{text-align:center;color:#6b778c;padding:30px 0;font-size:13px}
/* AUDIT LOG */
.log-panel{padding:20px}
.log-header{display:flex;align-items:center;justify-content:space-between;margin-bottom:14px;flex-wrap:wrap;gap:10px}
.log-title{font-size:15px;font-weight:700}
.log-controls{display:flex;gap:8px;align-items:center;flex-wrap:wrap}
.log-search{font-size:12px;padding:6px 10px;border:1.5px solid #dfe1e6;border-radius:4px;outline:none;width:190px}.log-search:focus{border-color:#0052cc}
.btn-csv{background:#0052cc;color:#fff;border:none;border-radius:4px;padding:6px 12px;font-size:12px;font-weight:700;cursor:pointer}.btn-csv:hover{background:#0065ff}
.btn-clear{background:#fff;color:#de350b;border:1px solid #de350b;border-radius:4px;padding:6px 10px;font-size:12px;font-weight:600;cursor:pointer}.btn-clear:hover{background:#ffebe6}
.log-empty{text-align:center;color:#6b778c;padding:40px 0;font-size:13px}
.log-table{width:100%;border-collapse:collapse;font-size:12px}
.log-table th{background:#f4f5f7;text-align:left;padding:8px 10px;font-size:10px;font-weight:700;text-transform:uppercase;letter-spacing:.4px;color:#6b778c;border-bottom:2px solid #dfe1e6;position:sticky;top:0}
.log-table td{padding:8px 10px;border-bottom:1px solid #f0f0f0;vertical-align:top}
.log-table tr:hover td{background:#f8f9ff}
.val-old{color:#de350b;font-weight:600}.val-new{color:#006644;font-weight:600}
.arrow{color:#6b778c;margin:0 4px}
.inactive-tag{background:#f4f5f7;color:#6b778c;font-size:10px;padding:1px 5px;border-radius:4px;margin-left:3px}
.ts{color:#6b778c;font-size:11px;white-space:nowrap}
.stats-bar{display:flex;gap:10px;margin-bottom:14px;flex-wrap:wrap}
.stat{background:#fff;border:1px solid #dfe1e6;border-radius:6px;padding:8px 14px;text-align:center}
.stat-n{font-size:20px;font-weight:700;color:#0052cc}.stat-l{font-size:10px;color:#6b778c;text-transform:uppercase;letter-spacing:.4px}
.log-type-note{background:#f0ebff;color:#5243aa;font-size:10px;padding:1px 7px;border-radius:8px;font-weight:700;margin-left:4px}
.log-type-raci{background:#deebff;color:#0052cc;font-size:10px;padding:1px 7px;border-radius:8px;font-weight:700;margin-left:4px}
/* POPUP */
.popup{display:none;position:fixed;z-index:200;background:#fff;border-radius:8px;box-shadow:0 4px 24px rgba(0,0,0,.22);width:240px;overflow:hidden}
.popup.open{display:block}
.popup-head{background:#0052cc;color:#fff;padding:9px 12px;font-weight:700;font-size:12px;display:flex;justify-content:space-between;align-items:center}
.popup-head button{background:none;border:none;color:#fff;font-size:17px;cursor:pointer;line-height:1}
.popup-body{padding:10px 12px}
.icon-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:6px;margin-bottom:8px}
.icon-opt{display:flex;flex-direction:column;align-items:center;gap:3px;cursor:pointer;padding:5px 3px;border-radius:5px;border:2px solid transparent;transition:border .12s}
.icon-opt:hover{border-color:#0052cc55}.icon-opt.selected{border-color:#0052cc;background:#f0f4ff}
.icon-opt .lbl{font-size:8px;color:#6b778c;text-align:center}
.off-row{display:flex;align-items:center;gap:7px;font-size:11px;color:#172b4d;padding:7px 0;border-top:1px solid #f0f0f0;margin-top:2px;cursor:pointer}
.off-row input[type=checkbox]{width:14px;height:14px;cursor:pointer;accent-color:#0052cc}
.popup-footer{display:flex;gap:5px;padding:8px 12px;border-top:1px solid #f0f0f0;background:#f4f5f7}
.btn-apply{background:#0052cc;color:#fff;border:none;border-radius:4px;padding:5px 12px;font-size:11px;font-weight:700;cursor:pointer;flex:1}.btn-apply:hover{background:#0065ff}
.btn-cancel2{background:#fff;color:#172b4d;border:1px solid #dfe1e6;border-radius:4px;padding:5px 9px;font-size:11px;cursor:pointer}.btn-cancel2:hover{background:#ebecf0}
/* MODALS */
.modal-bg{display:none;position:fixed;inset:0;background:rgba(0,0,0,.5);z-index:300;align-items:center;justify-content:center}
.modal-bg.open{display:flex}
.modal{background:#fff;border-radius:8px;box-shadow:0 6px 30px rgba(0,0,0,.2);width:380px;overflow:hidden}
.modal-head{background:#0052cc;color:#fff;padding:14px 18px;font-weight:700;font-size:14px;display:flex;justify-content:space-between;align-items:center}
.modal-head.purple{background:#6554c0}
.modal-head button{background:none;border:none;color:#fff;font-size:18px;cursor:pointer}
.modal-body{padding:18px}
.info-box{font-size:12px;color:#6b778c;margin-bottom:12px;line-height:1.6;background:#f4f5f7;padding:10px 12px;border-radius:6px;border-left:3px solid #0052cc}
.info-box.purple{border-left-color:#6554c0;background:#f0ebff}
.modal-body label{display:block;font-size:11px;font-weight:600;color:#6b778c;text-transform:uppercase;letter-spacing:.5px;margin-bottom:4px;margin-top:10px}
.modal-body input{width:100%;border:1.5px solid #dfe1e6;border-radius:4px;padding:8px 10px;font-size:13px;outline:none}
.modal-body input:focus{border-color:#0052cc}
.login-err{color:#de350b;font-size:12px;margin-top:6px;display:none}
.modal-footer{display:flex;gap:8px;padding:14px 18px;border-top:1px solid #f0f0f0;background:#f4f5f7;justify-content:flex-end}
.btn-confirm{background:#36b37e;color:#fff;border:none;border-radius:4px;padding:8px 18px;font-size:13px;font-weight:700;cursor:pointer}.btn-confirm:hover{background:#2da06e}
.btn-confirm.purple{background:#6554c0}.btn-confirm.purple:hover{background:#5243aa}
.btn-discard{background:#fff;color:#de350b;border:1px solid #de350b;border-radius:4px;padding:8px 12px;font-size:13px;cursor:pointer}.btn-discard:hover{background:#ffebe6}
.success-banner{display:none;padding:12px 14px;border-radius:6px;font-size:13px;font-weight:700;text-align:center}
.success-banner.green{background:#e3fcef;border:1px solid #abf5d1;color:#006644}
.success-banner.purple{background:#f0ebff;border:1px solid #c0b6f2;color:#403294}
.users-hint{font-size:11px;color:#6b778c;margin-top:12px;border-top:1px solid #f0f0f0;padding-top:10px;line-height:1.8}
.users-hint b{color:#172b4d}
.rpill{display:inline-block;padding:1px 6px;border-radius:8px;font-size:10px;font-weight:600}
.p-cbm{background:#e3fcef;color:#006644}.p-fbp{background:#deebff;color:#0052cc}.p-adm{background:#fff0b3;color:#974f0c}
</style>
</head>
<body>

<div class="topbar">
  <div class="brand">Keyloop · Book to Bill RACI</div>
  <div class="topbar-right">
    <div class="dot" id="changesDot" title="Unsaved RACI changes"></div>
    <button class="tbtn tbtn-notes" onclick="switchTab('notes')">&#128221; BP Notes</button>
    <button class="tbtn tbtn-log" onclick="switchTab('log')">&#128203; Audit Log</button>
    <button class="tbtn tbtn-save" id="btnSave" onclick="openSaveModal()" disabled>&#128190; Save changes</button>
  </div>
</div>

<div class="tabs">
  <div class="tab active" id="tab-raci" onclick="switchTab('raci')">RACI Table</div>
  <div class="tab notes-tab" id="tab-notes" onclick="switchTab('notes')">&#128221; BP Notes <span id="notesDot" class="note-dot"></span></div>
  <div class="tab" id="tab-log" onclick="switchTab('log')">Audit Log <span id="logCount" style="background:#0052cc;color:#fff;border-radius:8px;padding:1px 7px;font-size:10px;margin-left:4px;display:none">0</span></div>
</div>

<div class="toolbar" id="raciToolbar">
  <label>Region / System:</label>
  <select id="sysFilter" onchange="filterTable()">
    <option value="all">All regions</option>
    <option value="kf">UKI — Keyforce / NetSuite</option>
    <option value="rq">Canada — Rapid / QuickBooks</option>
    <option value="css">RoW — CSS / Navision</option>
    <option value="se">Canada — Serti / Billing</option>
  </select>
  <label style="margin-left:8px">Stakeholder:</label>
  <select id="stakeFilter" onchange="filterTable()">
    <option value="all">All stakeholders</option>
    <option value="0">Sales</option>
    <option value="1">Billing / CBM</option>
    <option value="2">PS – Professional Services</option>
    <option value="3">Collections</option>
    <option value="4">Cash &amp; Bank</option>
    <option value="5">CE – Customer Enablement / Warehouse</option>
    <option value="6">FBP – Finance Business Partner</option>
  </select>
  <span class="edit-hint">Click any badge to edit · Save requires sign-in</span>
</div>

<div class="panel active" id="panel-raci">
  <div class="content">
    <div class="page-title">Book to Bill — RACI by system &amp; region</div>
    <div class="page-sub">FBP = Finance Business Partner &nbsp;|&nbsp; CBM = Contract &amp; Billing Management &nbsp;|&nbsp; PS = Professional Services &nbsp;|&nbsp; CE = Customer Enablement</div>
    <div class="legend">
      <div class="leg"><span class="badge r" style="cursor:default">R</span>Responsible</div>
      <div class="leg"><span class="badge a" style="cursor:default">A</span>Accountable</div>
      <div class="leg"><span class="badge c" style="cursor:default">C</span>Consulted</div>
      <div class="leg"><span class="badge i" style="cursor:default">I</span>Informed</div>
      <div class="leg"><span class="badge ra" style="cursor:default">R/A</span>Resp. &amp; Accountable</div>
    </div>
    <div style="overflow-x:auto">
    <table id="raciTable">
    <colgroup>
      <col style="width:18%">
      <col style="width:4.1%"><col style="width:4.1%"><col style="width:4.1%"><col style="width:4.1%"><col style="width:4.1%"><col style="width:4.1%"><col style="width:4.1%">
      <col style="width:4.1%"><col style="width:4.1%"><col style="width:4.1%"><col style="width:4.1%"><col style="width:4.1%"><col style="width:4.1%"><col style="width:4.1%">
      <col style="width:4.1%"><col style="width:4.1%"><col style="width:4.1%"><col style="width:4.1%"><col style="width:4.1%"><col style="width:4.1%"><col style="width:4.1%">
      <col style="width:4.1%"><col style="width:4.1%"><col style="width:4.1%"><col style="width:4.1%"><col style="width:4.1%"><col style="width:4.1%"><col style="width:4.1%">
    </colgroup>
    <thead>
    <tr>
      <th class="proc-h" rowspan="3">Process step</th>
      <th colspan="7" class="sys-header">Keyforce – NetSuite</th>
      <th colspan="7" class="sys-header">Rapid – QuickBooks</th>
      <th colspan="7" class="sys-header">CSS – Navision</th>
      <th colspan="7" class="sys-header">Serti – Billing</th>
    </tr>
    <tr>
      <th colspan="7" class="reg-header">UKI</th>
      <th colspan="7" class="reg-header">Canada</th>
      <th colspan="7" class="reg-header">Rest of World</th>
      <th colspan="7" class="reg-header">Canada</th>
    </tr>
    <tr>
      <th>Sales</th><th>Billing/CBM</th><th>PS</th><th>Collections</th><th>Cash&amp;Bank</th><th>CE/WH</th><th>FBP</th>
      <th>Sales</th><th>Billing/CBM</th><th>PS</th><th>Collections</th><th>Cash&amp;Bank</th><th>CE/WH</th><th>FBP</th>
      <th>Sales</th><th>Billing/CBM</th><th>PS</th><th>Collections</th><th>Cash&amp;Bank</th><th>CE/WH</th><th>FBP</th>
      <th>Sales</th><th>Billing/CBM</th><th>PS</th><th>Collections</th><th>Cash&amp;Bank</th><th>CE/WH</th><th>FBP</th>
    </tr>
    </thead>
    <tbody id="tableBody"></tbody>
    </table>
    </div>
  </div>
</div>

<!-- BP NOTES PANEL -->
<div class="panel" id="panel-notes">
  <div class="notes-panel">
    <div class="notes-header"><div class="notes-title">&#128221; Business Partner Notes</div></div>
    <div class="notes-subtitle">This space is for Finance Business Partners (FBPs) to record observations, decisions, open questions or commentary on each process section. Notes are saved with your sign-in and appear in the Audit Log.</div>
    <div class="notes-grid" id="notesGrid"></div>
    <div class="all-notes-section">
      <div class="all-notes-title">All saved notes <input class="all-notes-search" id="notesSearch" placeholder="Search notes..." oninput="renderAllNotes()"></div>
      <div id="allNotesContent"></div>
    </div>
  </div>
</div>

<!-- AUDIT LOG PANEL -->
<div class="panel" id="panel-log">
  <div class="log-panel">
    <div class="log-header">
      <div class="log-title">&#128203; Audit Log</div>
      <div class="log-controls">
        <input class="log-search" id="logSearch" placeholder="Search logs..." oninput="renderLog()">
        <button class="btn-csv" onclick="exportCSV()">&#8595; Export CSV</button>
        <button class="btn-clear" onclick="clearLog()">Clear log</button>
      </div>
    </div>
    <div class="stats-bar" id="statsBar"></div>
    <div id="logContent"></div>
  </div>
</div>

<!-- CELL POPUP -->
<div class="popup" id="cellPopup">
  <div class="popup-head">Edit cell <button onclick="closePopup()">×</button></div>
  <div class="popup-body">
    <div class="icon-grid" id="iconGrid"></div>
    <label class="off-row"><input type="checkbox" id="chkOff"> Mark as inactive (dimmed)</label>
  </div>
  <div class="popup-footer">
    <button class="btn-cancel2" onclick="closePopup()">Cancel</button>
    <button class="btn-apply" onclick="applyCell()">Apply</button>
  </div>
</div>

<!-- RACI SAVE MODAL -->
<div class="modal-bg" id="saveModal">
  <div class="modal">
    <div class="modal-head">Confirm &amp; save RACI changes <button onclick="closeSaveModal()">×</button></div>
    <div class="modal-body">
      <div class="success-banner green" id="successBanner">✓ RACI changes saved &amp; logged!</div>
      <div id="loginSection">
        <div class="info-box">Sign in to confirm your RACI edits. Your username will be recorded in the audit log.</div>
        <div class="login-err" id="loginErr">Invalid username or password.</div>
        <label>Username</label><input type="text" id="uname" placeholder="e.g. cbm.uki" autocomplete="off">
        <label>Password</label><input type="password" id="pwd" placeholder="••••••••">
        <div class="users-hint"><b>Demo accounts</b><br>cbm.uki / cbm.canada / cbm.row <span class="rpill p-cbm">CBM</span> — pass123<br>fbp.uki / fbp.canada / fbp.row <span class="rpill p-fbp">FBP</span> — pass123<br>admin <span class="rpill p-adm">Admin</span> — admin123</div>
      </div>
    </div>
    <div class="modal-footer" id="modalFooter">
      <button class="btn-discard" onclick="discardChanges()">Discard changes</button>
      <button class="btn-confirm" onclick="doSaveLogin()">Sign in &amp; save</button>
    </div>
  </div>
</div>

<!-- NOTE SAVE MODAL -->
<div class="modal-bg" id="noteModal">
  <div class="modal">
    <div class="modal-head purple">Save BP Note <button onclick="closeNoteModal()">×</button></div>
    <div class="modal-body">
      <div class="success-banner purple" id="noteSuccessBanner">✓ Note saved &amp; logged!</div>
      <div id="noteLoginSection">
        <div class="info-box purple">Sign in as a Finance Business Partner to save this note. Your name and timestamp will be recorded.</div>
        <div class="login-err" id="noteLoginErr">Invalid username or password.</div>
        <label>Username</label><input type="text" id="noteUname" placeholder="e.g. fbp.uki" autocomplete="off">
        <label>Password</label><input type="password" id="notePwd" placeholder="••••••••">
      </div>
    </div>
    <div class="modal-footer" id="noteModalFooter">
      <button class="btn-discard" onclick="closeNoteModal()">Cancel</button>
      <button class="btn-confirm purple" onclick="doNoteSaveLogin()">Sign in &amp; save note</button>
    </div>
  </div>
</div>

<script>
// ── CONFIG ────────────────────────────────────────────────────────────────────
var APPS_SCRIPT_URL='YOUR_APPS_SCRIPT_URL_HERE';

// ── USERS ─────────────────────────────────────────────────────────────────────
var USERS={
  'cbm.uki':   {pass:'pass123',label:'CBM – UKI',   role:'cbm'},
  'cbm.canada':{pass:'pass123',label:'CBM – Canada',role:'cbm'},
  'cbm.row':   {pass:'pass123',label:'CBM – RoW',   role:'cbm'},
  'fbp.uki':   {pass:'pass123',label:'FBP – UKI',   role:'fbp'},
  'fbp.canada':{pass:'pass123',label:'FBP – Canada',role:'fbp'},
  'fbp.row':   {pass:'pass123',label:'FBP – RoW',   role:'fbp'},
  'admin':     {pass:'admin123',label:'Admin',       role:'admin'}
};

var ICONS=[
  {val:'R',  cls:'r',  label:'Responsible'},
  {val:'A',  cls:'a',  label:'Accountable'},
  {val:'C',  cls:'c',  label:'Consulted'},
  {val:'I',  cls:'i',  label:'Informed'},
  {val:'R/A',cls:'ra', label:'R & Accountable'},
  {val:'—',  cls:'',   label:'None'},
];

var SYS_KEYS=['kf','rq','css','se'];
var SYS_LABELS={kf:'Keyforce–NetSuite (UKI)',rq:'Rapid–QuickBooks (Canada)',css:'CSS–Navision (RoW)',se:'Serti–Billing (Canada)'};
var STAKE_LABELS=['Sales','Billing/CBM','PS','Collections','Cash & Bank','CE/Warehouse','FBP'];
function colLabel(ci){return SYS_LABELS[SYS_KEYS[Math.floor(ci/7)]]+' / '+STAKE_LABELS[ci%7];}

// ── DATA (Anna's corrections applied) ─────────────────────────────────────────
// Cols per system: [Sales, Billing/CBM, PS, Collections, Cash&Bank, CE/WH, FBP]
var D='—';
var SECTIONS=[

  // ── 1. CATALOGUE & PRODUCT MANAGEMENT ────────────────────────────────────
  // Anna: Catalogue team (not billing) maintains catalogue in NS & NAV.
  // Billing only does Annual Price Increase (moved to section 10).
  {title:'1. Catalogue & Product Management',rows:[
    ['New product / SKU setup & activation in source system','all',
      'C','—','—','—','—','—','A',  'C','—','—','—','—','—','A',  'C','—','—','—','—','—','A',  'C','—','—','—','—','—','A'],
    // ^ Catalogue team (CE/WH col used as proxy) owns this, not Billing
    ['Catalogue maintenance: item attributes, rev rec & billing fields','all',
      '—','I','—','—','—','R/A','A',  '—','I','—','—','—','R/A','A',  '—','I','—','—','—','R/A','A',  '—','I','—','—','—','R/A','A'],
    ['Pricing maintenance & rate card update','all',
      'C','—','—','—','—','—','R/A',  'C','R','—','—','—','—','A',  'C','—','—','—','—','—','R/A',  'C','—','—','—','—','—','R/A'],
    ['Item sync: Salesforce → Boomi → NetSuite','kf',
      '—','I','—','—','—','R','—',  D,D,D,D,D,D,D,  D,D,D,D,D,D,D,  D,D,D,D,D,D,D],
  ]},

  // ── 2. CUSTOMER MASTER DATA MANAGEMENT ───────────────────────────────────
  {title:'2. Customer Master Data Management',rows:[
    ['New customer creation (credit check, VAT, mandatory fields)','all',
      'C','R','—','—','—','C','A',  'C','R','—','—','—','C','A',  'C','R','—','—','—','C','A',  'C','R','—','—','—','C','A'],
    ['Customer master data amendments (address, billing entity)','all',
      '—','R/A','—','—','—','C','I',  '—','R/A','—','—','—','C','I',  '—','R/A','—','—','—','C','I',  '—','R/A','—','—','—','C','I'],
    ['Customer sync: Salesforce → Boomi → NetSuite','kf',
      '—','I','—','—','—','R','—',  D,D,D,D,D,D,D,  D,D,D,D,D,D,D,  D,D,D,D,D,D,D],
    ['Credit check & sanctions review','all',
      'C','R','—','—','—','—','A',  'C','R','—','—','—','—','A',  'C','R','—','—','—','—','A',  'C','R','—','—','—','—','A'],
  ]},

  // ── 3. QUOTE TO ORDER ─────────────────────────────────────────────────────
  // Anna: Billing team does NOT approve discounts. Only validates quote/order (system vs signed PDF).
  // In CSS/NAV: Oracle CPQ quote "Accepted by customer" → Billing validates values vs PDF, can only update PO number.
  // In KF/NS: Billing validates sales orders only, does NOT approve quotes or discounts.
  // PS project container: created automatically in NS by order activation; in NAV by "Accepted by CDK" status.
  {title:'3. Quote to Order',rows:[
    ['Quote validation: discount & commercial approval','all',
      'R','—','—','—','—','—','A',  'R','—','—','—','—','—','A',  'R','—','—','—','—','—','A',  'R','—','—','—','—','—','A'],
    // ^ Billing removed from discount approval per Anna
    ['Quote/order validation: system values vs signed PDF (Billing team)','all',
      '—','R','—','—','—','—','I',  '—','R','—','—','—','—','I',  '—','R','—','—','—','—','I',  '—','R','—','—','—','—','I'],
    // ^ Billing validates system vs PDF only; PO number update only in CSS/NAV
    ['Purchase Order number update on order (CSS/NAV)','css',
      D,D,D,D,D,D,D,  D,D,D,D,D,D,D,  '—','R','—','—','—','—','I',  D,D,D,D,D,D,D],
    ['PS involvement matrix check at quoting stage','all',
      'C','—','R/A','—','—','—','C',  'C','—','R/A','—','—','—','C',  'C','—','R/A','—','—','—','C',  'C','—','R/A','—','—','—','C'],
    // PS project container auto-created on order activation (NS) / "Accepted by CDK" status (NAV)
    ['Order activation → auto PS project & subscription creation (NS)','kf',
      '—','—','—','—','—','—','I',  D,D,D,D,D,D,D,  D,D,D,D,D,D,D,  D,D,D,D,D,D,D],
    ['"Accepted by CDK" status → auto Sales Contract (Project) creation (NAV)','css',
      D,D,D,D,D,D,D,  D,D,D,D,D,D,D,  '—','—','—','—','—','—','I',  D,D,D,D,D,D,D],
    ['Billing case creation & pick-up in Salesforce (Rapid/Canada)','rq',
      D,D,D,D,D,D,D,  '—','R/A','—','—','—','—','I',  D,D,D,D,D,D,D,  D,D,D,D,D,D,D],
  ]},

  // ── 4. PS – PROJECT & MILESTONE MANAGEMENT ────────────────────────────────
  // Anna: PS project container auto-created (see section 3).
  // T&M rating done by Warehouse/CE team, not CBM. CBM only does corrections.
  // Billing milestone: PS triggers OT (automatic); CBM runs recurring billing runs.
  {title:'4. PS – Project & Milestone Management',rows:[
    ['Fixed-fee vs T&M contract type identification at quote','all',
      'C','C','R','—','—','—','A',  'C','C','R','—','—','—','A',  'C','C','R','—','—','—','A',  'C','C','R','—','—','—','A'],
    ['Sub-milestone creation & hour tracking','all',
      '—','—','R/A','—','—','—','I',  '—','—','R/A','—','—','—','I',  '—','—','R/A','—','—','—','I',  '—','—','R/A','—','—','—','I'],
    // T&M rating: CE/Warehouse team finalises; CBM only corrects if needed
    ['T&M billing finalisation (CE/Warehouse team)','all',
      '—','C','—','—','—','R','I',  '—','C','—','—','—','R','I',  '—','C','—','—','—','R','I',  '—','C','—','—','—','R','I'],
    ['T&M billing corrections (CBM, if required)','all',
      '—','R','—','—','—','—','I',  '—','R','—','—','—','—','I',  '—','R','—','—','—','—','I',  '—','R','—','—','—','—','I'],
    // OT milestone invoice: triggered automatically by PS milestone completion
    ['OT/Consultancy invoice: auto-triggered on milestone completion (PS)','all',
      '—','—','R','—','—','—','I',  '—','—','R','—','—','—','I',  '—','—','R','—','—','—','I',  '—','—','R','—','—','—','I'],
    // Recurring element billed by CBM in billing runs
    ['Recurring element billing runs (CBM)','all',
      '—','R/A','—','—','—','—','I',  '—','R/A','—','—','—','—','I',  '—','R/A','—','—','—','—','I',  '—','R/A','—','—','—','—','I'],
    ['PS fixed-fee: control total hours ≤ contracted maximum','all',
      '—','C','R','—','—','—','A',  '—','C','R','—','—','—','A',  '—','C','R','—','—','—','A',  '—','C','R','—','—','—','A'],
    ['KeyedIn ↔ NetSuite milestone data sync','kf',
      '—','—','R','—','—','—','I',  D,D,D,D,D,D,D,  D,D,D,D,D,D,D,  D,D,D,D,D,D,D],
  ]},

  // ── 5. ORDER TO FULFILMENT & BACKLOG ─────────────────────────────────────
  // Anna: No Backlog Recurring Review in NS; exists only in NAV; FBPs not involved.
  // "Deletion" not available in NS/NAV for billing. Backlog management is done by PS.
  {title:'5. Order to Fulfilment & Backlog',rows:[
    // Backlog recurring review: NAV only, PS/CBM, FBP not involved
    ['Backlog recurring review (NAV only — not applicable in NS)','css',
      D,D,D,D,D,D,D,  D,D,D,D,D,D,D,  '—','R','C','—','—','—','—',  D,D,D,D,D,D,D],
    // Backlog management (amendments/admin deletions by PS)
    ['Backlog order amendments & admin deletions (managed by PS)','all',
      'C','—','R/A','—','—','—','I',  'C','—','R/A','—','—','—','I',  'C','—','R/A','—','—','—','I',  'C','—','R/A','—','—','—','I'],
    ['Hardware fulfilment (serialised & non-serialised) — Warehouse','all',
      '—','—','—','—','—','R','A',  '—','—','—','—','—','R','A',  '—','—','—','—','—','R','A',  '—','—','—','—','—','R','A'],
    ['HaaS installation milestone → billing start trigger','all',
      '—','R','C','—','—','—','I',  '—','R','C','—','—','—','I',  '—','R','C','—','—','—','I',  '—','R','C','—','—','—','I'],
    ['Volume report extraction & billing spreadsheet (Rapid only)','rq',
      D,D,D,D,D,D,D,  '—','R/A','—','—','—','—','I',  D,D,D,D,D,D,D,  D,D,D,D,D,D,D],
  ]},

  // ── 6. INVOICE & BILLING GENERATION ──────────────────────────────────────
  // Anna: No SaaS/HaaS split in NS — Recurring and Transactional (Usage) billing by CBM.
  // Sales Order (HW) billing by Warehouse. OT/Consultancy auto on milestone.
  // PS items invoiced automatically in both NS & NAV on milestone completion.
  // FBPs NOT informed every time invoice dispatched.
  // Pro forma: does NOT exist in NS; manual actual Proforma done for PO request purposes only.
  // OT & Hardware by Warehouse or auto on milestone.
  {title:'6. Invoice & Billing Generation',rows:[
    // Recurring billing: CBM triggers billing runs in NS & NAV
    ['Recurring billing runs — CBM triggers (NS & NAV)','kf',
      '—','R/A','—','—','—','—','—',  D,D,D,D,D,D,D,  D,D,D,D,D,D,D,  D,D,D,D,D,D,D],
    ['Recurring billing runs — CBM triggers (NAV)','css',
      D,D,D,D,D,D,D,  D,D,D,D,D,D,D,  '—','R/A','—','—','—','—','—',  D,D,D,D,D,D,D],
    ['Recurring invoices in QuickBooks (Rapid)','rq',
      D,D,D,D,D,D,D,  '—','R/A','—','—','—','—','—',  D,D,D,D,D,D,D,  D,D,D,D,D,D,D],
    ['Recurring invoices in Serti (Canada)','se',
      D,D,D,D,D,D,D,  D,D,D,D,D,D,D,  D,D,D,D,D,D,D,  '—','R/A','—','—','—','—','—'],
    // Transactional/Usage billing: CBM triggers in NS
    ['Transactional / usage billing (CBM triggers in NS)','kf',
      '—','R/A','—','—','—','—','—',  D,D,D,D,D,D,D,  D,D,D,D,D,D,D,  D,D,D,D,D,D,D],
    // Sales Order / Hardware billing: Warehouse team
    ['Sales order / hardware invoice (Warehouse team)','all',
      '—','—','—','—','—','R','I',  '—','—','—','—','—','R','I',  '—','—','—','—','—','R','I',  '—','—','—','—','—','R','I'],
    // OT/Consultancy/PS: auto on milestone completion in both NS & NAV
    ['OT / PS invoice: auto-generated on milestone completion','all',
      '—','—','R','—','—','—','—',  '—','—','R','—','—','—','—',  '—','—','R','—','—','—','—',  '—','—','R','—','—','—','—'],
    ['Invoice consolidation (multi-subscription, bill-to grouping)','all',
      '—','R/A','—','—','—','—','—',  '—','R/A','—','—','—','—','—',  '—','R/A','—','—','—','—','—',  '—','R/A','—','—','—','—','—'],
    // Pro forma: does NOT exist in NS; manual only for PO request
    ['Pro forma invoice (manual, PO request only — NOT in NS)','css',
      D,D,D,D,D,D,D,  D,D,D,D,D,D,D,  '—','R/A','—','—','—','—','—',  D,D,D,D,D,D,D],
    // Invoice delivery: FBP not informed routinely
    ['Invoice delivery (email / portal / paper)','all',
      '—','R/A','—','—','—','C','—',  '—','R/A','—','—','—','C','—',  '—','R/A','—','—','—','C','—',  '—','R/A','—','—','—','C','—'],
    ['E-invoicing & tax compliance (VAT, e-reporting)','all',
      '—','R','—','—','—','—','A',  '—','R','—','—','—','—','A',  '—','R','—','—','—','—','A',  '—','R','—','—','—','—','A'],
    ['Usage/consumption billing (SMS, print)','all',
      '—','R','C','—','—','—','A',  '—','R','C','—','—','—','A',  '—','R','C','—','—','—','A',  '—','R','C','—','—','—','A'],
  ]},

  // ── 7. CREDIT MEMOS & BILLING CORRECTIONS ────────────────────────────────
  {title:'7. Credit Memos & Billing Corrections',rows:[
    ['Credit memo request & initiation (reason code, supporting doc)','all',
      '—','R','—','—','—','—','A',  '—','R','—','—','—','—','A',  '—','R','—','—','—','—','A',  '—','R','—','—','—','—','A'],
    ['Credit memo approval (tiered by value & reason)','all',
      '—','—','—','—','—','—','A',  '—','—','—','—','—','—','A',  '—','—','—','—','—','—','A',  '—','—','—','—','—','—','A'],
    ['Invoice correction & rebilling (credit rebuild → recharge)','all',
      '—','R','—','—','—','—','A',  '—','R','—','—','—','—','A',  '—','R','—','—','—','—','A',  '—','R','—','—','—','—','A'],
    ['Duplicate invoice prevention & detection','all',
      '—','R/A','—','—','—','—','I',  '—','R/A','—','—','—','—','I',  '—','R/A','—','—','—','—','I',  '—','R/A','—','—','—','—','I'],
  ]},

  // ── 8. REVENUE RECOGNITION ────────────────────────────────────────────────
  // Anna: Revenue release & reconciliation in NAV done by Billing (CBM).
  // Reconciliation is a separate report reconciling NAV, HYP & DWH.
  // Contract cost capitalisation & amortisation: not really applicable.
  {title:'8. Revenue Recognition',rows:[
    ['Revenue plan creation & release – IFRS + local GAAP (NS ZAB)','kf',
      '—','I','—','—','—','—','R/A',  D,D,D,D,D,D,D,  D,D,D,D,D,D,D,  D,D,D,D,D,D,D],
    // NAV: Billing (CBM) does revenue release; reconciliation vs HYP & DWH is separate
    ['Revenue release in NAV (CBM) + reconciliation vs HYP & DWH','css',
      D,D,D,D,D,D,D,  D,D,D,D,D,D,D,  '—','R','—','—','—','—','A',  D,D,D,D,D,D,D],
    ['PS rev rec: ratable (linked to SaaS) vs point-in-time','all',
      '—','C','C','—','—','—','R/A',  '—','C','C','—','—','—','R/A',  '—','C','C','—','—','—','R/A',  '—','C','C','—','—','—','R/A'],
    ['Revenue reconciliation & period-end close','all',
      '—','C','—','—','—','—','R/A',  '—','C','—','—','—','—','R/A',  '—','C','—','—','—','—','R/A',  '—','C','—','—','—','—','R/A'],
    ['Dual-book rev rec: IFRS vs management book','all',
      '—','I','—','—','—','—','R/A',  '—','I','—','—','—','—','R/A',  '—','I','—','—','—','—','R/A',  '—','I','—','—','—','—','R/A'],
  ]},

  // ── 9. ACCOUNTS RECEIVABLE & CASH APPLICATION ─────────────────────────────
  {title:'9. Accounts Receivable & Cash Application',rows:[
    ['Payment receipt & application (direct debit / bank transfer)','all',
      '—','C','—','C','R','—','A',  '—','C','—','C','R','—','A',  '—','C','—','C','R','—','A',  '—','C','—','C','R','—','A'],
    ['Automated payment matching (exact → auto-apply)','all',
      '—','—','—','C','R/A','—','I',  '—','—','—','C','R/A','—','I',  '—','—','—','C','R/A','—','I',  '—','—','—','C','R/A','—','I'],
    ['Unapplied / unallocated cash management & month-end','all',
      '—','—','—','C','R/A','—','I',  '—','—','—','C','R/A','—','I',  '—','—','—','C','R/A','—','I',  '—','—','—','C','R/A','—','I'],
    ['Dunning letter workflow (tiered reminders)','all',
      '—','—','—','R/A','—','—','A',  '—','—','—','R/A','—','—','A',  '—','—','—','R/A','—','—','A',  '—','—','—','R/A','—','—','A'],
    ['Collections escalation (sales, CE, finance alignment)','all',
      'C','—','—','R','—','C','A',  'C','—','—','R','—','C','A',  'C','—','—','R','—','C','A',  'C','—','—','R','—','C','A'],
    ['Dispute management (contract-related)','all',
      'C','R','—','C','—','C','C',  'C','R','—','C','—','C','C',  'C','R','—','C','—','C','C',  'C','R','—','C','—','C','C'],
    ['Bad debt provision review & write-off approval','all',
      '—','—','—','C','—','—','R/A',  '—','—','—','C','—','—','R/A',  '—','—','—','C','—','—','R/A',  '—','—','—','C','—','—','R/A'],
    ['Customer refund / reimbursement approval','all',
      '—','C','—','—','C','—','A',  '—','C','—','—','C','—','A',  '—','C','—','—','C','—','A',  '—','C','—','—','C','—','A'],
    ['Intercompany billing & netting','all',
      '—','C','—','—','C','—','R/A',  '—','C','—','—','C','—','R/A',  '—','C','—','—','C','—','R/A',  '—','C','—','—','C','—','R/A'],
  ]},

  // ── 10. SERVICE CONTRACT / SUBSCRIPTION / ASSET MANAGEMENT ───────────────
  // Anna: All points adjusted to Service Contract / Subscription / Asset.
  // Cancellations in NS: approved by FBP, processed (R) by CBM.
  // Subscription amendments: CBM performs cancellations, qty reductions, site changes.
  // Co-term: not amendable.
  // Annual Price Increase: CBM performs adjustment in NAV & SF/NS + provides contact details.
  // Comms: Marketing. Calculations/% uplift agreed by Finance/Sales/Legal — CBM not involved.
  {title:'10. Service Contract / Subscription / Asset Management',rows:[
    ['Service contract / subscription creation & maintenance','all',
      'C','R/A','—','—','—','C','I',  'C','R/A','—','—','—','C','I',  'C','R/A','—','—','—','C','I',  'C','R/A','—','—','—','C','I'],
    // Cancellations: FBP approves (NS), CBM processes (R in both)
    ['Subscription / asset cancellation — FBP approves, CBM processes','all',
      '—','R','—','—','—','—','A',  '—','R','—','—','—','—','A',  '—','R','—','—','—','—','A',  '—','R','—','—','—','—','A'],
    // Qty reductions & site changes: CBM performs
    ['Quantity reductions (downsell) & site changes — CBM','all',
      'I','R','—','—','—','—','I',  'I','R','—','—','—','—','I',  'I','R','—','—','—','—','I',  'I','R','—','—','—','—','I'],
    // Evergreen & term renewals
    ['Evergreen & term-based renewal processing','all',
      'R','C','—','—','—','—','I',  'R','C','—','—','—','—','I',  'R','C','—','—','—','—','I',  'R','C','—','—','—','—','I'],
    // Annual Price Increase: CBM adjusts ERP & provides contacts; Marketing comms; Finance/Sales/Legal agree %
    ['Annual Price Increase: uplift % agreed by Finance / Sales / Legal','all',
      'C','—','—','—','—','—','R/A',  'C','—','—','—','—','—','R/A',  'C','—','—','—','—','—','R/A',  'C','—','—','—','—','—','R/A'],
    ['Annual Price Increase: ERP price adjustment (CBM) & contact data','all',
      '—','R','—','—','—','—','I',  '—','R','—','—','—','—','I',  '—','R','—','—','—','—','I',  '—','R','—','—','—','—','I'],
    ['Annual Price Increase: customer communications (Marketing)','all',
      '—','C','—','—','—','R','I',  '—','C','—','—','—','R','I',  '—','C','—','—','—','R','I',  '—','C','—','—','—','R','I'],
  ]},

  // ── 11. CUSTOMER ENABLEMENT (CE) ─────────────────────────────────────────
  {title:'11. Customer Enablement (CE)',rows:[
    ['Case creation & routing (billing/contract disputes)','all',
      'C','C','—','C','—','R/A','I',  'C','C','—','C','—','R/A','I',  'C','C','—','C','—','R/A','I',  'C','C','—','C','—','R/A','I'],
    ['Case management, escalation & SLA tracking','all',
      'C','C','—','C','—','R/A','I',  'C','C','—','C','—','R/A','I',  'C','C','—','C','—','R/A','I',  'C','C','—','C','—','R/A','I'],
    ['Customer portal: invoice & statement self-service','all',
      '—','I','—','—','—','R/A','I',  '—','I','—','—','—','R/A','I',  '—','I','—','—','—','R/A','I',  '—','I','—','—','—','R/A','I'],
    ['Entitlements, SLAs & incident management','all',
      '—','—','—','—','—','R/A','I',  '—','—','—','—','—','R/A','I',  '—','—','—','—','—','R/A','I',  '—','—','—','—','—','R/A','I'],
    ['Customer onboarding post go-live','all',
      'C','C','R','—','—','R','A',  'C','C','R','—','—','R','A',  'C','C','R','—','—','R','A',  'C','C','R','—','—','R','A'],
  ]},

  // ── 12. REPORTING & GOVERNANCE ────────────────────────────────────────────
  {title:'12. Reporting & Governance',rows:[
    ['AR ageing, DSO & collections reporting','all',
      '—','R','—','C','C','—','A',  '—','R','—','C','C','—','A',  '—','R','—','C','C','—','A',  '—','R','—','C','C','—','A'],
    ['ARR / ACV / TCV bookings & revenue reporting','all',
      'C','C','—','—','—','—','R/A',  'C','C','—','—','—','—','R/A',  'C','C','—','—','—','—','R/A',  'C','C','—','—','—','—','R/A'],
    ['Win/loss & conversion loss reporting','all',
      'C','R','—','—','—','—','A',  'C','R','—','—','—','—','A',  'C','R','—','—','—','—','A',  'C','R','—','—','—','—','A'],
    ['PS backlog & milestone completion reporting','all',
      '—','C','R','—','—','—','A',  '—','C','R','—','—','—','A',  '—','C','R','—','—','—','A',  '—','C','R','—','—','—','A'],
    ['Usage cap / commitment tracking','all',
      '—','R','C','—','—','—','A',  '—','R','C','—','—','—','A',  '—','R','C','—','—','—','A',  '—','R','C','—','—','—','A'],
    ['NAV / HYP / DWH reconciliation report (revenue)','css',
      D,D,D,D,D,D,D,  D,D,D,D,D,D,D,  '—','R','—','—','—','—','A',  D,D,D,D,D,D,D],
    ['SOX compliance & audit support','all',
      '—','C','—','—','—','—','R/A',  '—','C','—','—','—','—','R/A',  '—','C','—','—','—','—','R/A',  '—','C','—','—','—','—','R/A'],
    ['Data quality monitoring & audit trail','all',
      '—','R','—','—','—','—','A',  '—','R','—','—','—','—','A',  '—','R','—','—','—','—','A',  '—','R','—','—','—','—','A'],
  ]},
];

// ── STATE ─────────────────────────────────────────────────────────────────────
var state=[];
var pendingEdits=[];
var auditLog=[];
var hasChanges=false;
var notes=[];

function buildState(){
  state=[];var ri=0;
  SECTIONS.forEach(function(sec){
    sec.rows.forEach(function(row){
      state[ri]=[];
      for(var ci=0;ci<28;ci++) state[ri][ci]={val:row[ci+2],off:false};
      ri++;
    });
  });
}

function markChanged(){
  hasChanges=true;
  document.getElementById('changesDot').style.display='block';
  document.getElementById('btnSave').disabled=false;
}

function switchTab(t){
  ['raci','notes','log'].forEach(function(id){
    document.getElementById('tab-'+id).classList.toggle('active',id===t);
    document.getElementById('panel-'+id).classList.toggle('active',id===t);
  });
  document.getElementById('raciToolbar').style.display=t==='raci'?'flex':'none';
  if(t==='notes'){buildNotesGrid();renderAllNotes();}
  if(t==='log') renderLog();
}

function getStepLabel(ri){
  var idx=0,lbl='';
  SECTIONS.forEach(function(sec){sec.rows.forEach(function(r){if(idx===ri)lbl=r[0];idx++;});});
  return lbl;
}

function buildTable(){
  var tb=document.getElementById('tableBody');tb.innerHTML='';var ri=0;
  SECTIONS.forEach(function(sec){
    var sr=document.createElement('tr');sr.className='section-row';sr.dataset.sec='1';
    sr.innerHTML='<td colspan="29">'+sec.title+'</td>';
    tb.appendChild(sr);
    sec.rows.forEach(function(row){
      var tr=document.createElement('tr');tr.dataset.sys=row[1];
      var html='<td class="step">'+row[0]+'</td>';
      for(var ci=0;ci<28;ci++) html+='<td id="c_'+ri+'_'+ci+'">'+cellHtml(ri,ci)+'</td>';
      tr.innerHTML=html;tb.appendChild(tr);ri++;
    });
  });
}

function cellHtml(ri,ci){
  var s=state[ri][ci];
  if(s.val==='—') return '<span class="empty" data-cell onclick="openCell('+ri+','+ci+',this)" title="Click to assign">—</span>';
  var cls=s.val==='R/A'?'ra':s.val.toLowerCase();
  return '<span class="badge '+cls+(s.off?' off':'')+'" data-cell onclick="openCell('+ri+','+ci+',this)" title="Click to edit">'+s.val+'</span>';
}

function refreshCell(ri,ci){
  var el=document.getElementById('c_'+ri+'_'+ci);
  if(el) el.innerHTML=cellHtml(ri,ci);
}

function filterTable(){
  var sv=document.getElementById('sysFilter').value;
  var stv=document.getElementById('stakeFilter').value;
  document.querySelectorAll('#raciTable tr').forEach(function(tr){
    var cells=tr.children;
    for(var i=1;i<cells.length;i++){
      var sb=Math.floor((i-1)/7),sk=(i-1)%7,key=SYS_KEYS[sb];
      cells[i].style.display=(sv==='all'||key===sv)&&(stv==='all'||sk===parseInt(stv))?'':'none';
    }
  });
  document.querySelectorAll('#tableBody tr:not([data-sec])').forEach(function(r){
    r.style.display=(sv==='all'||r.dataset.sys===sv||r.dataset.sys==='all')?'':'none';
  });
  document.querySelectorAll('#tableBody tr[data-sec]').forEach(function(s){
    var next=s.nextElementSibling,vis=false;
    while(next&&!next.dataset.sec){if(next.style.display!=='none')vis=true;next=next.nextElementSibling;}
    s.style.display=vis?'':'none';
  });
}

// ── CELL POPUP ────────────────────────────────────────────────────────────────
var editRi=-1,editCi=-1,editSelVal='',editOff=false,popupOpen=false;

function openCell(ri,ci,anchor){
  editRi=ri;editCi=ci;
  var s=state[ri][ci];editSelVal=s.val;editOff=s.off;
  var grid=document.getElementById('iconGrid');grid.innerHTML='';
  ICONS.forEach(function(ic){
    var d=document.createElement('div');
    d.className='icon-opt'+(ic.val===editSelVal?' selected':'');
    d.onclick=function(){document.querySelectorAll('.icon-opt').forEach(function(x){x.classList.remove('selected');});d.classList.add('selected');editSelVal=ic.val;};
    d.innerHTML=ic.val==='—'
      ?'<span style="font-size:16px;color:#bbb">—</span><span class="lbl">None</span>'
      :'<span class="badge '+ic.cls+'" style="cursor:default;width:28px;height:28px;font-size:10px">'+ic.val+'</span><span class="lbl">'+ic.label+'</span>';
    grid.appendChild(d);
  });
  document.getElementById('chkOff').checked=editOff;
  var popup=document.getElementById('cellPopup');popup.classList.add('open');
  var rect=anchor.getBoundingClientRect();
  var left=rect.left+window.scrollX,top=rect.bottom+window.scrollY+6,pw=240,ph=280;
  if(left+pw>window.innerWidth-10) left=window.innerWidth-pw-10;
  if(top+ph>window.scrollY+window.innerHeight-10) top=rect.top+window.scrollY-ph-6;
  popup.style.left=Math.max(6,left)+'px';popup.style.top=Math.max(6,top)+'px';
  popupOpen=true;
}

function closePopup(){document.getElementById('cellPopup').classList.remove('open');popupOpen=false;editRi=-1;editCi=-1;}

function applyCell(){
  if(editRi<0) return;
  var s=state[editRi][editCi];
  var newOff=document.getElementById('chkOff').checked;
  if(s.val!==editSelVal||s.off!==newOff){
    pendingEdits.push({ri:editRi,ci:editCi,stepLabel:getStepLabel(editRi),col:colLabel(editCi),oldVal:s.val,oldOff:s.off,newVal:editSelVal,newOff:newOff});
    state[editRi][editCi]={val:editSelVal,off:newOff};
    refreshCell(editRi,editCi);markChanged();
  }
  closePopup();
}

document.addEventListener('click',function(e){
  if(!popupOpen) return;
  if(!document.getElementById('cellPopup').contains(e.target)&&!e.target.closest('[data-cell]')) closePopup();
});

// ── RACI SAVE ────────────────────────────────────────────────────────────────
function openSaveModal(){
  document.getElementById('loginErr').style.display='none';
  document.getElementById('successBanner').style.display='none';
  document.getElementById('loginSection').style.display='block';
  document.getElementById('modalFooter').style.display='flex';
  document.getElementById('uname').value='';document.getElementById('pwd').value='';
  document.getElementById('saveModal').classList.add('open');
}
function closeSaveModal(){document.getElementById('saveModal').classList.remove('open');}

function doSaveLogin(){
  var u=document.getElementById('uname').value.trim().toLowerCase();
  var p=document.getElementById('pwd').value;
  if(USERS[u]&&USERS[u].pass===p){
    document.getElementById('loginErr').style.display='none';
    var ts=nowTs();
    var newEntries=pendingEdits.map(function(e){
      return {type:'raci',ts:ts,user:u,userLabel:USERS[u].label,stepLabel:e.stepLabel,col:e.col,oldVal:e.oldVal,oldOff:e.oldOff,newVal:e.newVal,newOff:e.newOff};
    });
    newEntries.forEach(function(e){auditLog.unshift(e);});
    pendingEdits=[];hasChanges=false;
    document.getElementById('changesDot').style.display='none';
    document.getElementById('btnSave').disabled=true;
    updateLogCount();
    document.getElementById('loginSection').style.display='none';
    document.getElementById('modalFooter').style.display='none';
    document.getElementById('successBanner').style.display='block';
    syncToSheets(newEntries);
    setTimeout(closeSaveModal,2000);
  } else {document.getElementById('loginErr').style.display='block';}
}

function discardChanges(){
  pendingEdits.forEach(function(e){state[e.ri][e.ci]={val:e.oldVal,off:e.oldOff};refreshCell(e.ri,e.ci);});
  pendingEdits=[];hasChanges=false;
  document.getElementById('changesDot').style.display='none';
  document.getElementById('btnSave').disabled=true;
  closeSaveModal();
}

document.getElementById('pwd').addEventListener('keydown',function(e){if(e.key==='Enter')doSaveLogin();});
document.getElementById('uname').addEventListener('keydown',function(e){if(e.key==='Enter')doSaveLogin();});

// ── BP NOTES ──────────────────────────────────────────────────────────────────
var pendingNoteIdx=-1;

function buildNotesGrid(){
  var grid=document.getElementById('notesGrid');grid.innerHTML='';
  SECTIONS.forEach(function(sec,idx){
    var n=notes[idx]||{};
    var card=document.createElement('div');card.className='note-card';
    var savedMeta=n.savedTs?'Last saved: '+n.savedTs+' by '+n.savedLabel:'No note saved yet';
    card.innerHTML=
      '<div class="note-card-head">'+
        '<span class="section-lbl">'+sec.title+'</span>'+
        '<span class="note-meta" id="note-meta-'+idx+'">'+savedMeta+'</span>'+
      '</div>'+
      '<div class="note-card-body">'+
        '<textarea id="note-ta-'+idx+'" placeholder="Add your BP notes, observations, decisions or open questions here…" oninput="noteDirty('+idx+')">'+escHtml(n.text||'')+'</textarea>'+
        '<div class="note-card-footer">'+
          '<span class="note-saved-ts" id="note-st-'+idx+'"></span>'+
          '<div style="display:flex;align-items:center;gap:6px">'+
            '<span class="note-dot" id="note-dot-'+idx+'"></span>'+
            '<button class="btn-save-note" id="note-btn-'+idx+'" onclick="openNoteModal('+idx+')" disabled>Save note</button>'+
          '</div>'+
        '</div>'+
      '</div>';
    grid.appendChild(card);
  });
}

function noteDirty(idx){
  document.getElementById('note-dot-'+idx).style.display='block';
  document.getElementById('note-btn-'+idx).disabled=false;
  document.getElementById('notesDot').style.display='block';
}

function openNoteModal(idx){
  pendingNoteIdx=idx;
  document.getElementById('noteLoginErr').style.display='none';
  document.getElementById('noteSuccessBanner').style.display='none';
  document.getElementById('noteLoginSection').style.display='block';
  document.getElementById('noteModalFooter').style.display='flex';
  document.getElementById('noteUname').value='';document.getElementById('notePwd').value='';
  document.getElementById('noteModal').classList.add('open');
}
function closeNoteModal(){document.getElementById('noteModal').classList.remove('open');pendingNoteIdx=-1;}

function doNoteSaveLogin(){
  var u=document.getElementById('noteUname').value.trim().toLowerCase();
  var p=document.getElementById('notePwd').value;
  if(USERS[u]&&USERS[u].pass===p){
    document.getElementById('noteLoginErr').style.display='none';
    var idx=pendingNoteIdx;
    var text=document.getElementById('note-ta-'+idx).value.trim();
    var ts=nowTs();
    notes[idx]={text:text,savedBy:u,savedLabel:USERS[u].label,savedTs:ts};
    document.getElementById('note-meta-'+idx).textContent='Last saved: '+ts+' by '+USERS[u].label;
    document.getElementById('note-dot-'+idx).style.display='none';
    document.getElementById('note-btn-'+idx).disabled=true;
    var entry={type:'note',ts:ts,user:u,userLabel:USERS[u].label,stepLabel:SECTIONS[idx].title,col:'BP Notes',oldVal:'',oldOff:false,newVal:text,newOff:false};
    auditLog.unshift(entry);updateLogCount();
    syncToSheets([entry]);
    var anyDirty=false;
    SECTIONS.forEach(function(_,i){if(document.getElementById('note-dot-'+i)&&document.getElementById('note-dot-'+i).style.display==='block') anyDirty=true;});
    document.getElementById('notesDot').style.display=anyDirty?'block':'none';
    document.getElementById('noteLoginSection').style.display='none';
    document.getElementById('noteModalFooter').style.display='none';
    document.getElementById('noteSuccessBanner').style.display='block';
    renderAllNotes();
    setTimeout(closeNoteModal,1800);
  } else {document.getElementById('noteLoginErr').style.display='block';}
}

document.getElementById('notePwd').addEventListener('keydown',function(e){if(e.key==='Enter')doNoteSaveLogin();});
document.getElementById('noteUname').addEventListener('keydown',function(e){if(e.key==='Enter')doNoteSaveLogin();});

function renderAllNotes(){
  var q=(document.getElementById('notesSearch').value||'').toLowerCase();
  var el=document.getElementById('allNotesContent');
  var entries=[];
  SECTIONS.forEach(function(sec,idx){
    var n=notes[idx];
    if(n&&n.text&&(!q||(n.text+sec.title+n.savedLabel).toLowerCase().includes(q))) entries.push({title:sec.title,n:n});
  });
  if(!entries.length){
    el.innerHTML='<div class="no-notes">'+(Object.keys(notes).length?'No notes match your search.':'No notes saved yet. Write in a section card above and save it.')+'</div>';return;
  }
  el.innerHTML=entries.map(function(e){
    return '<div class="note-entry">'+
      '<div class="note-entry-head"><span class="note-entry-section">'+e.title+'</span><span class="note-entry-meta">'+e.n.savedTs+' · '+e.n.savedLabel+'</span></div>'+
      '<div class="note-entry-text">'+escHtml(e.n.text)+'</div></div>';
  }).join('');
}

// ── AUDIT LOG ─────────────────────────────────────────────────────────────────
function updateLogCount(){
  var cnt=document.getElementById('logCount');
  cnt.textContent=auditLog.length;cnt.style.display=auditLog.length?'inline-block':'none';
}

function renderLog(){
  var q=(document.getElementById('logSearch').value||'').toLowerCase();
  var filtered=auditLog.filter(function(e){
    return !q||(e.user+e.stepLabel+e.col+e.ts+(e.newVal||'')).toLowerCase().includes(q);
  });
  var users={};auditLog.forEach(function(e){users[e.user]=(users[e.user]||0)+1;});
  var topUser=Object.keys(users).sort(function(a,b){return users[b]-users[a];})[0]||'—';
  var noteCount=auditLog.filter(function(e){return e.type==='note';}).length;
  var raciCount=auditLog.filter(function(e){return e.type==='raci';}).length;
  document.getElementById('statsBar').innerHTML=
    stat(raciCount,'RACI changes')+stat(noteCount,'BP notes')+stat(Object.keys(users).length,'Contributors')+stat(topUser,'Most active');
  var el=document.getElementById('logContent');
  if(!filtered.length){
    el.innerHTML='<div class="log-empty">'+(auditLog.length?'No entries match your search.':'No changes or notes saved yet.')+'</div>';return;
  }
  var rows=filtered.map(function(e){
    var typePill=e.type==='note'?'<span class="log-type-note">BP Note</span>':'<span class="log-type-raci">RACI</span>';
    var changeCell=e.type==='note'
      ?'<span style="font-size:11px;color:#172b4d;white-space:pre-wrap">'+escHtml((e.newVal||'').slice(0,120)+(e.newVal&&e.newVal.length>120?'…':''))+'</span>'
      :'<span class="val-old">'+(e.oldVal||'—')+(e.oldOff?' <span class="inactive-tag">inactive</span>':'')+'</span><span class="arrow">→</span><span class="val-new">'+(e.newVal||'—')+(e.newOff?' <span class="inactive-tag">inactive</span>':'')+'</span>';
    return '<tr><td class="ts">'+e.ts+'</td><td><strong>'+e.user+'</strong><br><span style="font-size:10px;color:#6b778c">'+e.userLabel+'</span></td><td>'+typePill+'<br>'+e.stepLabel+'</td><td style="font-size:11px">'+e.col+'</td><td>'+changeCell+'</td></tr>';
  }).join('');
  el.innerHTML='<table class="log-table"><thead><tr><th>Timestamp</th><th>User</th><th>Type / Section</th><th>Column</th><th>Change / Note</th></tr></thead><tbody>'+rows+'</tbody></table>';
}

function stat(val,lbl){return '<div class="stat"><div class="stat-n">'+val+'</div><div class="stat-l">'+lbl+'</div></div>';}

function exportCSV(){
  if(!auditLog.length){alert('No log entries to export.');return;}
  var rows=[['Type','Timestamp','User','User Label','Section / Step','Column','Old Value','Old Active','New Value']];
  auditLog.forEach(function(e){rows.push([e.type||'raci',e.ts,e.user,e.userLabel,e.stepLabel,e.col,e.oldVal||'',e.oldOff?'Inactive':'Active',e.newVal||'']);});
  var csv=rows.map(function(r){return r.map(function(c){return '"'+String(c).replace(/"/g,'""')+'"';}).join(',');}).join('\n');
  var a=document.createElement('a');
  a.href='data:text/csv;charset=utf-8,'+encodeURIComponent(csv);
  a.download='RACI_AuditLog_'+new Date().toISOString().slice(0,10)+'.csv';a.click();
}

function clearLog(){
  if(!auditLog.length) return;
  if(!confirm('Clear the entire audit log? This cannot be undone.')) return;
  auditLog=[];updateLogCount();renderLog();
}

function syncToSheets(entries){
  if(!APPS_SCRIPT_URL||APPS_SCRIPT_URL==='YOUR_APPS_SCRIPT_URL_HERE') return;
  fetch(APPS_SCRIPT_URL,{method:'POST',body:JSON.stringify({entries:entries})}).catch(function(){});
}

function loadAuditLogFromSheets(){
  if(!APPS_SCRIPT_URL||APPS_SCRIPT_URL==='YOUR_APPS_SCRIPT_URL_HERE') return;
  fetch(APPS_SCRIPT_URL).then(function(r){return r.json();}).then(function(data){
    if(data.status==='ok'&&data.entries.length){
      auditLog=data.entries.reverse().map(function(e){
        return {type:e['Type']||'raci',ts:e['Timestamp'],user:e['User'],userLabel:e['User Label'],stepLabel:e['Process Step'],col:e['Column'],oldVal:e['Old Value'],oldOff:e['Old Active']==='Inactive',newVal:e['New Value'],newOff:e['New Active']==='Inactive'};
      });
      updateLogCount();
    }
  }).catch(function(){});
}

function nowTs(){return new Date().toLocaleString('en-GB',{day:'2-digit',month:'short',year:'numeric',hour:'2-digit',minute:'2-digit',second:'2-digit'});}
function escHtml(s){return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');}

buildState();buildTable();filterTable();loadAuditLogFromSheets();
</script>
</body>
</html>
