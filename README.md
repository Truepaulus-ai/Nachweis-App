[index.html](https://github.com/user-attachments/files/34595650/index.html)
<!doctype html>
<html lang="de" dir="ltr">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Nachweis-App – Konzeptstudie Jobcenter Wiesbaden</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Source+Sans+3:wght@400;600;700;800&display=swap">
<style>
/* Mobile-first: eine Spalte (max. 430px), blaue Kopfzone mit Sichtumschalter, Inhalt, feste Tab-Leiste unten. */
/* Farbwelt orientiert an Prototyp v1 (Blau/Gold, Source Sans 3) – ohne Wappen, Logo oder Wortmarke.
   Kontraste geprüft auf WCAG AA; Text-Blau im Dunkelmodus als eigenes Token (--brand-ink). */
:root{
  --brand:#00489b; --brand-strong:#0b2a55; --brand-soft:#e3ecf8; --brand-ink:#00489b;
  --accent:#f2b705; --on-accent:#0b2a55; --accent-soft:#fff3cc; --accent-ink:#6b4500;
  --bg:#eef2f8; --surface:#ffffff; --fg:#0d2346; --muted:#52627c; --line:#c9d3e3;
  --open:#7a4a00; --open-bg:#fff0d1;
  --recv:#1c4c8c; --recv-bg:#e2ecfa;
  --ok:#17663a; --ok-bg:#dff1e6;
  --bad:#9e2a1e; --bad-bg:#fbe4e0;
  --staff:#2f3747; --staff-soft:#e6e9f0;
  --shadow:0 1px 2px rgba(13,35,70,.06),0 6px 18px rgba(13,35,70,.07);
  --font:"Source Sans 3","Segoe UI",system-ui,-apple-system,Roboto,"Noto Sans","Noto Sans Arabic","Geeza Pro",Tahoma,Arial,sans-serif;
  color-scheme:light;
}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){
  --brand:#1f5fbf; --brand-strong:#06162e; --brand-soft:#14284a; --brand-ink:#8fb8ff;
  --accent:#f2b705; --on-accent:#0b2a55; --accent-soft:#3a2f0b; --accent-ink:#ffd66b;
  --bg:#0a1424; --surface:#121f35; --fg:#e8eef8; --muted:#a3b2c9; --line:#2a3b58;
  --open:#ffcf7a; --open-bg:#3a2b0e; --recv:#9cc3ff; --recv-bg:#15294a;
  --ok:#7fd9a2; --ok-bg:#123522; --bad:#ffa597; --bad-bg:#43180f;
  --staff:#262d3d; --staff-soft:#1a2030;
  --shadow:0 1px 2px rgba(0,0,0,.4),0 6px 18px rgba(0,0,0,.3); color-scheme:dark}}
:root[data-theme="dark"]{
  --brand:#1f5fbf; --brand-strong:#06162e; --brand-soft:#14284a; --brand-ink:#8fb8ff;
  --accent:#f2b705; --on-accent:#0b2a55; --accent-soft:#3a2f0b; --accent-ink:#ffd66b;
  --bg:#0a1424; --surface:#121f35; --fg:#e8eef8; --muted:#a3b2c9; --line:#2a3b58;
  --open:#ffcf7a; --open-bg:#3a2b0e; --recv:#9cc3ff; --recv-bg:#15294a;
  --ok:#7fd9a2; --ok-bg:#123522; --bad:#ffa597; --bad-bg:#43180f;
  --staff:#262d3d; --staff-soft:#1a2030;
  --shadow:0 1px 2px rgba(0,0,0,.4),0 6px 18px rgba(0,0,0,.3); color-scheme:dark}

*{box-sizing:border-box}
html,body{margin:0;min-height:100%}
body{background:var(--bg);color:var(--fg);font-family:var(--font);font-size:17px;line-height:1.45;-webkit-text-size-adjust:100%}
button,input,select,textarea{font:inherit;color:inherit}
button{cursor:pointer}
:focus-visible{outline:3px solid var(--accent);outline-offset:2px;border-radius:6px}
h1,h2,h3{margin:0;line-height:1.2;text-wrap:balance}
h1{font-size:1.55rem;font-weight:800}
h2{font-size:1.15rem;font-weight:800}
h3{font-size:1.02rem;font-weight:700}
p{margin:0}
.sr{position:absolute!important;width:1px;height:1px;overflow:hidden;clip:rect(0 0 0 0);white-space:nowrap}
[hidden]{display:none!important}

.shell{max-width:430px;margin:0 auto;min-height:100vh;background:var(--bg);position:relative;padding-bottom:calc(86px + env(safe-area-inset-bottom,0px))}
.shell.nonav{padding-bottom:24px}
.pad{padding-inline:max(16px,env(safe-area-inset-left,0px)) max(16px,env(safe-area-inset-right,0px))}

/* Kopf */
.top{position:sticky;top:0;z-index:6;background:var(--brand);color:#fff;border-radius:0 0 22px 22px;padding-bottom:2px}
.top.staff{background:var(--staff)}
.topbar{display:flex;align-items:center;gap:10px;padding-block:10px}
.mark{width:36px;height:36px;border-radius:10px;background:#fff;display:grid;place-items:center;flex:none}
.brandtx{display:flex;flex-direction:column;min-width:0;flex:1}
.brandtx b{font-size:1rem;line-height:1.1}
.brandtx small{font-size:.75rem;opacity:.85}
.langsel{position:relative;display:flex;align-items:center}
.langsel select{appearance:none;-webkit-appearance:none;background:rgba(255,255,255,.15);border:1.5px solid rgba(255,255,255,.5);color:#fff;border-radius:10px;min-height:44px;padding-block:0;padding-inline:34px 10px;font-weight:700;font-size:.9rem}
.langsel select option{color:#172326;background:#fff}
.langsel svg{position:absolute;inset-inline-start:9px;pointer-events:none}
.proto{background:var(--brand-strong);color:#dce6f5;font-size:.8rem;line-height:1.3;padding-block:5px;text-align:center}
.top.staff .proto{background:#1d2330}
.roles{display:grid;grid-template-columns:1fr 1fr;gap:4px;background:rgba(0,0,0,.2);border-radius:12px;padding:4px;margin-block:0 10px}
.roles button{border:0;background:transparent;color:#fff;min-height:40px;border-radius:9px;font-weight:700;font-size:.88rem;display:flex;align-items:center;justify-content:center;gap:6px}
.roles button[aria-pressed="true"]{background:#fff;color:var(--brand-strong)}
.top.staff .roles button[aria-pressed="true"]{color:var(--staff)}

main{display:flex;flex-direction:column;gap:18px;padding-block:18px 8px}
.head{display:flex;flex-direction:column;gap:4px}
.sender{display:flex;align-items:center;gap:8px;font-weight:700;color:var(--brand-ink);font-size:.95rem}
.head p{color:var(--muted)}
.head h1:focus{outline:none}
.backbtn{align-self:flex-start;display:inline-flex;align-items:center;gap:6px;border:0;background:none;color:var(--brand-ink);font-weight:700;min-height:44px;padding:0}
[dir="rtl"] .flip{transform:scaleX(-1)}

.card{background:var(--surface);border:1px solid var(--line);border-radius:16px;padding:16px;display:flex;flex-direction:column;gap:12px}
.btn{display:flex;align-items:center;justify-content:center;gap:8px;min-height:52px;border-radius:12px;font-weight:800;font-size:1rem;padding:10px 16px;border:0;text-align:center;width:100%}
.btn-p{background:var(--brand);color:#fff}
.btn-s{background:var(--surface);color:var(--fg);border:1.5px solid var(--line)}
.btn-a{background:var(--accent);color:var(--on-accent)}
.btn-d{background:var(--brand-strong);color:#fff}
.btn-staff{background:var(--staff);color:#fff}
.btn:disabled{opacity:.45;cursor:not-allowed}
.row{display:flex;gap:10px}
.row>*{flex:1;min-width:0}
.grid2{display:grid;grid-template-columns:1fr 1fr;gap:10px}
.grid3{display:grid;grid-template-columns:repeat(3,1fr);gap:8px}
.muted{color:var(--muted)}
.small{font-size:.88rem}

/* Status-Chips: Farbe + Symbol + Text */
.chip{display:inline-flex;align-items:center;gap:5px;border-radius:999px;padding:3px 10px 3px 8px;font-size:.84rem;font-weight:800;white-space:nowrap;align-self:flex-start}
.c-open{background:var(--open-bg);color:var(--open)}
.c-received{background:var(--recv-bg);color:var(--recv)}
.c-checked{background:var(--ok-bg);color:var(--ok)}
.c-resubmit{background:var(--bad-bg);color:var(--bad)}

/* Erinnerungsbanner */
.remind{background:var(--accent);border-radius:20px;padding:18px;display:flex;flex-direction:column;gap:10px;color:var(--on-accent)}
.remind-top{display:flex;gap:12px;align-items:flex-start}
.remind .ic{width:48px;height:48px;border-radius:14px;background:var(--brand-strong);color:var(--accent);display:grid;place-items:center;flex:none}
.remind h2{font-size:1.2rem}
.remind .due{font-weight:700;color:var(--on-accent)}
.cd{font-variant-numeric:tabular-nums;font-weight:800;background:#fff;color:#0d2346;border-radius:10px;padding:8px 12px;display:flex;align-items:center;gap:8px}
.remind ul{margin:0;padding-inline-start:20px;font-weight:600}

/* Vorgang */
.case-title{display:flex;justify-content:space-between;gap:10px;align-items:flex-start}
.steps{display:grid;grid-template-columns:repeat(4,1fr);gap:4px;list-style:none;margin:0;padding:0}
.steps li{display:flex;flex-direction:column;gap:6px;font-size:.78rem;font-weight:700;color:var(--muted);text-align:center}
.steps li::before{content:"";height:6px;border-radius:99px;background:var(--line)}
.steps li.done::before{background:var(--brand)}
.steps li.now{color:var(--fg)}
.steps li.now::before{background:var(--accent)}
.sentence{background:var(--brand-soft);border-radius:12px;padding:12px;font-weight:600}

/* Analoger Weg */
.analog{background:var(--surface);border:2px dashed var(--brand);border-radius:16px;padding:16px;display:flex;flex-direction:column;gap:10px}
.analog h2{color:var(--brand-ink)}
.kv{display:grid;grid-template-columns:auto 1fr;gap:4px 12px;margin:0;font-size:.95rem}
.kv dt{color:var(--muted)} .kv dd{margin:0;font-weight:700;min-width:0;overflow-wrap:anywhere}

/* Checkliste */
.list{display:flex;flex-direction:column;gap:12px}
.proof{background:var(--surface);border:1px solid var(--line);border-radius:16px;padding:14px;display:flex;flex-direction:column;gap:10px}
.proof.need{border:2px solid var(--accent)}
.proof.need.bad{border-color:var(--bad)}
.proof-h{display:flex;gap:12px;align-items:flex-start}
.proof-h .tx{flex:1;min-width:0;display:flex;flex-direction:column;gap:4px}
.proof-h p{color:var(--muted);font-size:.95rem}
.why{border:0;background:none;color:var(--brand-ink);font-weight:700;display:inline-flex;align-items:center;gap:6px;min-height:44px;padding:0;text-align:start}
.whybox{background:var(--bg);border-radius:10px;padding:10px 12px;font-size:.95rem;display:flex;flex-direction:column;gap:6px}
.thumbs{display:flex;gap:8px;overflow-x:auto;padding-bottom:2px}
.thumbs img{width:54px;height:72px;object-fit:cover;border-radius:6px;border:1px solid var(--line);flex:none;background:#fff}
.sec-label{font-size:.82rem;font-weight:800;letter-spacing:.06em;text-transform:uppercase;color:var(--muted)}
[lang="ar"] .sec-label{letter-spacing:0}

/* Upload */
.shot{position:relative;border-radius:14px;overflow:hidden;background:#20302f;aspect-ratio:3/4;max-width:100%;max-height:52vh;margin-inline:auto;width:100%;display:grid;place-items:center}
.shot img{width:100%;height:100%;object-fit:contain}
.shot.bad{outline:4px solid var(--bad)}
.shot.blurfx img{filter:blur(5px)}
.shot .ph{color:#cfe0df;text-align:center;padding:20px;display:flex;flex-direction:column;align-items:center;gap:10px}
.spin{width:36px;height:36px;border-radius:50%;border:4px solid rgba(255,255,255,.3);border-top-color:#fff;animation:spin .8s linear infinite}
@keyframes spin{to{transform:rotate(360deg)}}
.fb{border-radius:12px;padding:12px 14px;display:flex;gap:10px;align-items:flex-start;font-weight:700}
.fb-bad{background:var(--bad-bg);color:var(--bad)}
.fb-ok{background:var(--ok-bg);color:var(--ok)}
.pages{display:flex;gap:10px;overflow-x:auto;padding-block:4px}
.pg{flex:none;width:76px;display:flex;flex-direction:column;gap:4px;align-items:center;font-size:.78rem;font-weight:700}
.pg img{width:76px;height:100px;object-fit:cover;border-radius:8px;border:2px solid var(--ok);background:#fff}
.pg button{border:0;background:var(--bg);border-radius:8px;min-height:36px;min-width:44px;display:grid;place-items:center;color:var(--bad)}
.src{display:grid;grid-template-columns:repeat(3,1fr);gap:8px}
.src .btn{flex-direction:column;gap:4px;min-height:78px;font-size:.88rem;padding:8px}
.note{display:flex;gap:8px;align-items:flex-start;font-size:.85rem;color:var(--muted)}

/* Prüfansicht & Bestätigung */
.check{display:flex;gap:12px;align-items:flex-start;background:var(--surface);border:2px solid var(--line);border-radius:14px;padding:14px;cursor:pointer;font-weight:700}
.check input{width:26px;height:26px;flex:none;accent-color:var(--brand);margin:0}
.big-ok{width:76px;height:76px;border-radius:50%;background:var(--ok-bg);color:var(--ok);display:grid;place-items:center;margin-inline:auto}
.center{text-align:center}

/* Postfach */
.thread{display:flex;gap:12px;align-items:flex-start;background:var(--surface);border:1px solid var(--line);border-radius:14px;padding:14px;text-align:start;width:100%}
.thread.unread{border:2px solid var(--brand)}
.thread .tx{flex:1;min-width:0;display:flex;flex-direction:column;gap:4px}
.thread time{font-size:.82rem;color:var(--muted);white-space:nowrap}
.casechip{font-size:.76rem;font-weight:800;color:var(--brand-ink);background:var(--brand-soft);border-radius:6px;padding:2px 8px;align-self:flex-start}
.newchip{font-size:.76rem;font-weight:800;color:#fff;background:var(--brand);border-radius:6px;padding:2px 8px}
.bubbles{display:flex;flex-direction:column;gap:10px}
.bubble{max-width:88%;border-radius:14px;padding:10px 12px;display:flex;flex-direction:column;gap:4px}
.bubble.office{background:var(--surface);border:1px solid var(--line);align-self:flex-start}
.bubble.you{background:var(--brand);color:#fff;align-self:flex-end}
.bubble small{font-size:.76rem;opacity:.8;font-weight:700}
textarea{width:100%;min-height:96px;border-radius:12px;border:1.5px solid var(--line);background:var(--surface);padding:10px 12px;resize:vertical}
label.lbl{font-weight:700;display:block;margin-bottom:6px}
input.inp{width:100%;min-height:52px;border-radius:12px;border:1.5px solid var(--line);background:var(--surface);padding:0 14px}

/* Mehr */
.menu{display:flex;flex-direction:column;gap:10px}
.menu button{display:flex;align-items:center;gap:12px;background:var(--surface);border:1px solid var(--line);border-radius:14px;min-height:60px;padding:10px 14px;text-align:start;font-weight:700}
.menu button .tx{flex:1}
.optbadge{font-size:.74rem;font-weight:800;color:var(--accent-ink);background:var(--accent-soft);border:1.5px solid var(--accent);border-radius:6px;padding:1px 7px}

/* Vermögen */
.opt-banner{display:flex;gap:10px;align-items:flex-start;background:var(--accent-soft);border:2px solid var(--accent);border-radius:14px;padding:12px;font-weight:700;color:var(--fg)}
.yn{display:grid;grid-template-columns:1fr 1fr;gap:10px}
.yn button{min-height:60px;border-radius:12px;border:2px solid var(--line);background:var(--surface);font-weight:800;font-size:1.05rem}
.yn button[aria-pressed="true"]{border-color:var(--brand);background:var(--brand-soft);color:var(--fg)}
.stepper{display:flex;align-items:center;gap:12px}
.stepper button{width:52px;height:52px;border-radius:12px;border:1.5px solid var(--line);background:var(--surface);font-size:1.4rem;font-weight:800}
.stepper output{font-size:1.4rem;font-weight:800;min-width:2ch;text-align:center;font-variant-numeric:tabular-nums}
.bar{height:8px;background:var(--line);border-radius:99px;overflow:hidden}
.bar i{display:block;height:100%;background:var(--brand)}
.warn{display:flex;gap:10px;align-items:flex-start;border-radius:12px;padding:12px;font-weight:700}
.warn.w{background:var(--open-bg);color:var(--open)}
.warn.i{background:var(--recv-bg);color:var(--recv)}
.warn.o{background:var(--ok-bg);color:var(--ok)}

/* Sachbearbeitung */
.staffinfo{background:var(--staff-soft);border-inline-start:5px solid var(--staff);border-radius:12px;padding:12px 14px;font-weight:700}
.sproof{background:var(--surface);border:1px solid var(--line);border-radius:14px;padding:14px;display:flex;flex-direction:column;gap:10px}
.meta{font-size:.84rem;color:var(--muted);display:flex;gap:6px;align-items:flex-start}
.meta svg{flex:none;margin-top:2px}
.meta span{min-width:0}
.radios{display:flex;flex-direction:column;gap:8px}
.radios label{display:flex;gap:10px;align-items:center;min-height:44px;border:1.5px solid var(--line);border-radius:10px;padding:0 12px;font-weight:700}
.radios input{width:22px;height:22px;accent-color:var(--staff)}

/* Tab-Leiste */
.nav{position:fixed;bottom:0;left:50%;transform:translateX(-50%);width:100%;max-width:430px;z-index:6;background:var(--surface);border-top:1px solid var(--line);padding-bottom:env(safe-area-inset-bottom,0px);display:grid;grid-template-columns:repeat(4,1fr)}
.nav button{border:0;background:none;min-height:64px;display:flex;flex-direction:column;align-items:center;justify-content:center;gap:2px;font-size:.78rem;font-weight:700;color:var(--muted);position:relative}
.nav button[aria-current="page"]{color:var(--brand-ink)}
.nav button[aria-current="page"]::before{content:"";position:absolute;top:0;inset-inline:22%;height:3px;border-radius:0 0 3px 3px;background:var(--brand)}
.badge{position:absolute;top:7px;inset-inline-start:calc(50% + 6px);background:var(--bad);color:#fff;border-radius:99px;font-size:.7rem;min-width:19px;height:19px;display:grid;place-items:center;padding:0 5px}

/* Push-Simulation & Toast */
.push{position:fixed;top:calc(8px + env(safe-area-inset-top,0px));left:50%;transform:translateX(-50%);width:calc(100% - 20px);max-width:410px;z-index:30;background:rgba(250,252,252,.97);color:#172326;border-radius:18px;box-shadow:0 10px 30px rgba(0,0,0,.25);padding:12px;display:flex;gap:10px;align-items:flex-start;animation:drop .35s ease;border:1px solid #d6dfe0}
.push .mark{background:var(--brand);width:38px;height:38px}
.push .tx{flex:1;min-width:0;display:flex;flex-direction:column;gap:2px;text-align:start;background:none;border:0;padding:0}
.push small{font-size:.74rem;color:#4f5f63;font-weight:700}
.push b{font-size:.95rem}
.push span{font-size:.9rem}
.push .x{border:0;background:#e8eeee;border-radius:50%;width:36px;height:36px;display:grid;place-items:center;flex:none;color:#172326}
@keyframes drop{from{transform:translate(-50%,-120%)}to{transform:translate(-50%,0)}}
.toast{position:fixed;bottom:calc(96px + env(safe-area-inset-bottom,0px));left:50%;transform:translateX(-50%);background:var(--fg);color:var(--bg);font-weight:700;border-radius:12px;padding:12px 16px;z-index:31;max-width:calc(100% - 32px);text-align:center}
@media (prefers-reduced-motion:reduce){*{animation:none!important;transition:none!important}}
@media (min-width:600px){body{background:var(--line)} .shell{box-shadow:0 0 0 1px var(--line),0 10px 40px rgba(0,0,0,.12)}}
</style>
</head>
<body>
<div id="app"></div>
<div id="push" aria-live="polite"></div>
<div id="toast" aria-live="polite"></div>
<input type="file" id="inCam" accept="image/*" capture="environment" hidden>
<input type="file" id="inFile" accept="image/*" hidden>

<script>
(function(){
"use strict";

/* ===================== Sprachen ===================== */
const LANGS = {
  de:{name:"Deutsch", loc:"de-DE", dir:"ltr"},
  en:{name:"English", loc:"en-GB", dir:"ltr"},
  ar:{name:"العربية", loc:"ar-u-nu-latn", dir:"rtl"},
  uk:{name:"Українська", loc:"uk-UA", dir:"ltr"}
};

const T = {
de:{
  app:"Nachweis-App", appSub:"Konzeptstudie Jobcenter Wiesbaden", sender:"Kommunales Jobcenter – Konzeptstudie",
  proto:"Prototyp im Rahmen eines studentischen Erfahrungsberichts – keine offizielle Anwendung der Landeshauptstadt Wiesbaden",
  lang:"Sprache wählen", viewClient:"Meine Sicht", viewStaff:"Sachbearbeitung", viewSwitch:"Ansicht wechseln",
  loginTitle:"Anmelden", loginLead:"Mit Ihrem Nutzerkonto sehen Sie, welche Nachweise noch fehlen.",
  user:"Benutzername", pass:"Passwort", loginBtn:"Anmelden",
  loginNote:"Nur simuliert. Es werden keine Daten geprüft oder gespeichert.",
  noAccount:"Noch kein Konto? In der echten App können Sie sich hier registrieren.",
  navHome:"Start", navProofs:"Nachweise", navMail:"Postfach", navMore:"Mehr",
  hello:"Hallo, {name}!", caseTitle:"Weiterbewilligungsantrag 2026", caseNo:"Vorgang {no}",
  missing1:"1 Nachweis fehlt", missingN:"{n} Nachweise fehlen",
  dueIn:"Frist in {d} Tagen", dueOn:"Frist: {date}", cd:"Noch {d} Tage · {h} Std. · {m} Min.",
  uploadNow:"Jetzt hochladen", toChecklist:"Zur Checkliste",
  st_open:"offen", st_received:"eingegangen", st_checked:"geprüft", st_resubmit:"bitte erneut einreichen",
  case_incomplete:"unvollständig", case_review:"vollständig – Antrag wird geprüft", case_done:"geprüft – Bescheid folgt",
  sent_missing1:"Es fehlt noch 1 Nachweis. Sobald er da ist, prüfen wir Ihren Antrag. Erst danach kann gezahlt werden.",
  sent_missingN:"Es fehlen noch {n} Nachweise. Sobald alle da sind, prüfen wir Ihren Antrag. Erst danach kann gezahlt werden.",
  sent_review:"Alle Nachweise sind da. Wir prüfen jetzt Ihren Antrag. Sie müssen gerade nichts tun.",
  sent_done:"Alle Nachweise sind geprüft. Sie bekommen bald Ihren Bescheid.",
  step1:"Antrag", step2:"Nachweise", step3:"Prüfung", step4:"Bescheid", stepsLabel:"Bearbeitungsstand",
  analogTitle:"Lieber persönlich oder per Post? Das geht weiterhin.",
  analogText:"Sie können Unterlagen auch abgeben oder schicken. Die App ist freiwillig.",
  phone:"Telefon", phoneVal:"0000 000000 (Platzhalter)", address:"Adresse",
  addressVal:"Musterstraße 1, 00000 Musterstadt (Platzhalter)", hoursL:"Zeiten", hours:"Mo–Fr 8–12 Uhr (Platzhalter)",
  copy:"Nummer kopieren", copied:"Nummer kopiert",
  checklistTitle:"Ihre Nachweise", checklistLead:"Diese Nachweise braucht Ihre Sachbearbeitung für Ihren Antrag.",
  todo:"Noch zu erledigen", doneH:"Erledigt", why:"Warum brauchen wir das?",
  addPhoto:"Foto aufnehmen", addAgain:"Erneut einreichen", pages1:"1 Seite", pagesN:"{n} Seiten",
  receivedOn:"eingegangen am {date}", setBy:"Liste von Ihrer Sachbearbeitung",
  uploadTitle:"Nachweis hochladen", camera:"Kamera", file:"Datei", demoPhoto:"Demo-Foto",
  tips:"Tipp: Blatt flach hinlegen, gutes Licht, alle 4 Ecken im Bild.",
  shotEmpty:"Noch kein Foto. Wählen Sie unten Kamera, Datei oder Demo-Foto.",
  checking:"Foto wird geprüft …", okPage:"Gut lesbar. Seite gespeichert.",
  badBlur:"Foto unscharf – bitte erneut aufnehmen.", badCut:"Seite abgeschnitten – bitte erneut aufnehmen.",
  retake:"Erneut aufnehmen", removePage:"Seite {n} entfernen", page:"Seite {n}", pagesDone:"Ihre Seiten",
  toReview:"Weiter zur Prüfung", addMore:"Weitere Seite? Einfach noch ein Foto aufnehmen.",
  simNote:"Simulation: Die Prüfung der Fotos ist nur angedeutet. Nichts wird gesendet.", back:"Zurück",
  reviewTitle:"Bitte prüfen Sie Ihre Angaben", rCase:"Vorgang", rProof:"Nachweis", rPages:"Seiten", rFrom:"Von",
  reviewCheck:"Alle Seiten sind vollständig und gut lesbar.", edit:"Ändern", send:"Jetzt absenden",
  confTitle:"Eingegangen", confLead:"Danke! Ihr Nachweis ist bei uns angekommen.",
  receipt:"Eingangsbestätigung", receiptNo:"Nummer", receiptTime:"Zeitpunkt", copyTitle:"Kopie Ihrer Unterlagen",
  confMail:"Die Bestätigung liegt auch in Ihrem Postfach.", confLaw:"Bestätigung mit Übersicht der Unterlagen (§ 36a Abs. 2b SGB I)",
  toHome:"Zur Startseite", nowStatus:"So geht es weiter",
  mailTitle:"Postfach", mailLead:"Nachrichten zu Ihrem Vorgang", newBadge:"Neu", unread:"ungelesen",
  replyLabel:"Ihre Antwort", replyPh:"Schreiben Sie hier …", sendMsg:"Senden", you:"Sie", office:"Ihr Jobcenter",
  msgSent:"Nachricht gesendet", goUpload:"Nachweis jetzt hochladen", emptyReply:"Bitte schreiben Sie zuerst eine Nachricht.",
  moreTitle:"Mehr", assetHelp:"Ausfüllhilfe Anlage Vermögen", optional:"Optional", privacy:"Datenschutz",
  analog:"Persönlich oder per Post", logout:"Abmelden", staffView:"Sicht der Sachbearbeitung", account:"Angemeldet als {u}",
  privacyTitle:"Datenschutz – kurz erklärt",
  p1:"Ihre Angaben sind Sozialdaten. Sie sind besonders geschützt.", p2:"Wir fragen nur, was für Ihren Antrag nötig ist.",
  p3:"Die App macht keine automatischen Datenabgleiche.", p4:"Kein Tracking. Keine Werbung.",
  p5:"Sie dürfen jederzeit fragen, welche Daten wir haben.", p6:"In diesem Prototyp wird nichts gespeichert oder gesendet.",
  pLaw:"Grundlagen: Sozialgeheimnis (§ 35 SGB I), Sozialdatenschutz (§§ 67 ff. SGB X), Art. 5 und 15 DSGVO.",
  assetLead:"Kurze Fragen helfen Ihnen beim Formular.", assetOptNote:"Optional und freiwillig. Ersetzt nicht das Formular „Anlage Vermögen“.",
  q1:"Haben Sie ein oder mehrere Konten?", q1why:"Auch ein Girokonto zählt. So sehen wir, welche Kontoauszüge nötig sind.",
  q1n:"Wie viele Konten?", q2:"Haben Sie Bargeld oder Wertsachen zu Hause?", q2why:"Zum Beispiel Schmuck oder Goldmünzen. Das zählt zum Vermögen.",
  q3:"Haben Sie ein Auto?", q3why:"Ein Auto kann zum Vermögen zählen. Oft dürfen Sie es behalten.",
  q4:"Haben Sie eine Lebens- oder Rentenversicherung?", q4why:"Der aktuelle Wert der Versicherung kann wichtig sein.",
  whyAsk:"Warum fragen wir das?", yes:"Ja", no:"Nein", next:"Weiter", qOf:"Frage {i} von {n}",
  plausTitle:"Prüfung Ihrer Angaben", warnNoKa:"Sie haben {n} Konto/Konten angegeben, aber noch keine Kontoauszüge hochgeladen.",
  warnPerAccount:"Bitte laden Sie für jedes Konto Auszüge hoch ({n} Konten).", warnNoAccount:"Fast alle Menschen haben ein Girokonto. Bitte prüfen Sie Ihre Angabe.",
  hintIns:"Bitte legen Sie den aktuellen Wert der Versicherung bei.", allPlausible:"Ihre Angaben passen zusammen.", restart:"Neu beginnen",
  staffTitle:"Eingang Leistungssachbearbeitung", staffLead:"Simulation: So kommen die Nachweise bei der Sachbearbeitung an.",
  staffInfo:"Jeder Nachweis kommt schon dem Vorgang und der Anforderung zugeordnet an. Kein Scannen, kein Zuordnen.",
  client:"Person", deadline:"Frist", markChecked:"Geprüft", request:"Erneut anfordern", reason:"Grund",
  r_blur:"Nicht lesbar", r_page:"Seite fehlt", r_period:"Falscher Zeitraum", sendRequest:"Anfordern und benachrichtigen",
  viaApp:"über App · automatisch zugeordnet", notYet:"Noch nicht eingegangen", remind:"Erinnerung senden", reminded:"Erinnerung gesendet",
  cancel:"Abbrechen", staffSet:"Status gesetzt: {s}", staffBack:"Zur Kundensicht wechseln",
  m1Subj:"Ihr Antrag ist da", m1Body:"Wir haben Ihren Weiterbewilligungsantrag erhalten. In der App sehen Sie, welche Nachweise noch fehlen.",
  m2Subj:"Lohnabrechnung März fehlt noch", m2Body:"Danke für die Kontoauszüge. Uns fehlt noch Ihre Lohnabrechnung für März. Bitte laden Sie sie in der App hoch.",
  mRecSubj:"Eingangsbestätigung: {proof}", mRecBody:"Eingegangen am {time}. Nummer: {no}. Seiten: {n}.",
  mResSubj:"Bitte erneut einreichen: {proof}", mResBody:"Grund: {reason}. Bitte laden Sie den Nachweis noch einmal hoch.",
  mRemSubj:"Erinnerung: {proof}", mRemBody:"Bitte laden Sie diesen Nachweis bis {date} hoch.",
  autoReply:"Danke, Ihre Nachricht ist angekommen. Wir melden uns.",
  pushRemTitle:"Erinnerung: Frist in {d} Tagen", pushRemBody:"Noch offen: {list}. Bitte bis {date} hochladen.",
  pushMsgTitle:"Neue Nachricht vom Jobcenter", appNow:"Nachweis-App · jetzt", close:"Schließen", and:" und ",
  pushHint:"Simulierte Push-Benachrichtigung"
},
en:{
  app:"Proof App", appSub:"Concept study Jobcenter Wiesbaden", sender:"Municipal job centre – concept study",
  proto:"Prototype for a student field report – not an official application of the City of Wiesbaden",
  lang:"Choose language", viewClient:"My view", viewStaff:"Caseworker", viewSwitch:"Switch view",
  loginTitle:"Sign in", loginLead:"With your user account you can see which documents are still missing.",
  user:"Username", pass:"Password", loginBtn:"Sign in",
  loginNote:"Simulated only. No data is checked or stored.",
  noAccount:"No account yet? In the real app you could register here.",
  navHome:"Home", navProofs:"Documents", navMail:"Inbox", navMore:"More",
  hello:"Hello, {name}!", caseTitle:"Application to continue benefits 2026", caseNo:"Case {no}",
  missing1:"1 document missing", missingN:"{n} documents missing",
  dueIn:"Deadline in {d} days", dueOn:"Deadline: {date}", cd:"{d} days · {h} h · {m} min left",
  uploadNow:"Upload now", toChecklist:"Open checklist",
  st_open:"open", st_received:"received", st_checked:"checked", st_resubmit:"please resubmit",
  case_incomplete:"incomplete", case_review:"complete – application is being checked", case_done:"checked – decision follows",
  sent_missing1:"1 document is still missing. Once we have it, we will check your application. Only then can we pay.",
  sent_missingN:"{n} documents are still missing. Once we have all of them, we will check your application. Only then can we pay.",
  sent_review:"We have all documents. We are now checking your application. You do not need to do anything right now.",
  sent_done:"All documents are checked. You will get your decision soon.",
  step1:"Application", step2:"Documents", step3:"Check", step4:"Decision", stepsLabel:"Progress",
  analogTitle:"Prefer to come in person or send it by post? You still can.",
  analogText:"You can also hand in or post your documents. Using the app is voluntary.",
  phone:"Phone", phoneVal:"0000 000000 (placeholder)", address:"Address",
  addressVal:"Sample Street 1, 00000 Sample Town (placeholder)", hoursL:"Hours", hours:"Mon–Fri 8 am–12 pm (placeholder)",
  copy:"Copy number", copied:"Number copied",
  checklistTitle:"Your documents", checklistLead:"Your caseworker needs these documents for your application.",
  todo:"Still to do", doneH:"Done", why:"Why do we need this?",
  addPhoto:"Take photo", addAgain:"Submit again", pages1:"1 page", pagesN:"{n} pages",
  receivedOn:"received on {date}", setBy:"List from your caseworker",
  uploadTitle:"Upload document", camera:"Camera", file:"File", demoPhoto:"Demo photo",
  tips:"Tip: lay the page flat, use good light, keep all 4 corners in the picture.",
  shotEmpty:"No photo yet. Choose camera, file or demo photo below.",
  checking:"Checking photo …", okPage:"Easy to read. Page saved.",
  badBlur:"Photo is blurry – please take it again.", badCut:"Page is cut off – please take it again.",
  retake:"Take again", removePage:"Remove page {n}", page:"Page {n}", pagesDone:"Your pages",
  toReview:"Continue to review", addMore:"Another page? Just take one more photo.",
  simNote:"Simulation: the photo check is only imitated. Nothing is sent.", back:"Back",
  reviewTitle:"Please check your details", rCase:"Case", rProof:"Document", rPages:"Pages", rFrom:"From",
  reviewCheck:"All pages are complete and easy to read.", edit:"Change", send:"Send now",
  confTitle:"Received", confLead:"Thank you! Your document has arrived.",
  receipt:"Confirmation of receipt", receiptNo:"Number", receiptTime:"Time", copyTitle:"Copy of your documents",
  confMail:"You will also find this confirmation in your inbox.", confLaw:"Confirmation with overview of documents (§ 36a (2b) SGB I)",
  toHome:"Back to home", nowStatus:"What happens next",
  mailTitle:"Inbox", mailLead:"Messages about your case", newBadge:"New", unread:"unread",
  replyLabel:"Your reply", replyPh:"Write here …", sendMsg:"Send", you:"You", office:"Your job centre",
  msgSent:"Message sent", goUpload:"Upload document now", emptyReply:"Please write a message first.",
  moreTitle:"More", assetHelp:"Help with the assets form", optional:"Optional", privacy:"Data protection",
  analog:"In person or by post", logout:"Sign out", staffView:"Caseworker view", account:"Signed in as {u}",
  privacyTitle:"Data protection – in brief",
  p1:"Your details are social data. They are specially protected.", p2:"We only ask for what your application needs.",
  p3:"The app does not run any automatic data matching.", p4:"No tracking. No advertising.",
  p5:"You can always ask which data we hold.", p6:"In this prototype nothing is stored or sent.",
  pLaw:"Legal basis: social secrecy (§ 35 SGB I), social data protection (§§ 67 ff. SGB X), Art. 5 and 15 GDPR.",
  assetLead:"Short questions help you with the form.", assetOptNote:"Optional and voluntary. Does not replace the official assets form.",
  q1:"Do you have one or more bank accounts?", q1why:"A current account counts too. This shows us which bank statements we need.",
  q1n:"How many accounts?", q2:"Do you keep cash or valuables at home?", q2why:"For example jewellery or gold coins. These count as assets.",
  q3:"Do you have a car?", q3why:"A car can count as an asset. Often you may keep it.",
  q4:"Do you have a life or pension insurance?", q4why:"The current value of the insurance can matter.",
  whyAsk:"Why do we ask?", yes:"Yes", no:"No", next:"Next", qOf:"Question {i} of {n}",
  plausTitle:"Checking your answers", warnNoKa:"You entered {n} account(s) but have not uploaded any bank statements yet.",
  warnPerAccount:"Please upload statements for each account ({n} accounts).", warnNoAccount:"Almost everyone has a current account. Please check your answer.",
  hintIns:"Please add the current value of the insurance.", allPlausible:"Your answers fit together.", restart:"Start again",
  staffTitle:"Caseworker inbox", staffLead:"Simulation: this is how documents reach the caseworker.",
  staffInfo:"Each document already arrives linked to the case and the request. No scanning, no sorting.",
  client:"Person", deadline:"Deadline", markChecked:"Checked", request:"Request again", reason:"Reason",
  r_blur:"Not readable", r_page:"Page missing", r_period:"Wrong period", sendRequest:"Request and notify",
  viaApp:"via app · linked automatically", notYet:"Not received yet", remind:"Send reminder", reminded:"Reminder sent",
  cancel:"Cancel", staffSet:"Status set: {s}", staffBack:"Switch to customer view",
  m1Subj:"We received your application", m1Body:"We have received your application to continue benefits. The app shows which documents are still missing.",
  m2Subj:"March payslip still missing", m2Body:"Thank you for the bank statements. We still need your payslip for March. Please upload it in the app.",
  mRecSubj:"Confirmation of receipt: {proof}", mRecBody:"Received on {time}. Number: {no}. Pages: {n}.",
  mResSubj:"Please resubmit: {proof}", mResBody:"Reason: {reason}. Please upload the document again.",
  mRemSubj:"Reminder: {proof}", mRemBody:"Please upload this document by {date}.",
  autoReply:"Thank you, your message has arrived. We will get back to you.",
  pushRemTitle:"Reminder: deadline in {d} days", pushRemBody:"Still open: {list}. Please upload by {date}.",
  pushMsgTitle:"New message from the job centre", appNow:"Proof App · now", close:"Close", and:" and ",
  pushHint:"Simulated push notification"
},
ar:{
  app:"تطبيق المستندات", appSub:"دراسة مفهوم – جوب سنتر فيسبادن", sender:"مركز العمل البلدي – دراسة مفهوم",
  proto:"نموذج أولي ضمن تقرير خبرة طلابي – ليس تطبيقًا رسميًا لمدينة فيسبادن",
  lang:"اختر اللغة", viewClient:"عرضي", viewStaff:"الموظف المختص", viewSwitch:"تغيير العرض",
  loginTitle:"تسجيل الدخول", loginLead:"من خلال حسابك ترى المستندات التي ما زالت ناقصة.",
  user:"اسم المستخدم", pass:"كلمة المرور", loginBtn:"تسجيل الدخول",
  loginNote:"محاكاة فقط. لا يتم فحص أو حفظ أي بيانات.",
  noAccount:"ليس لديك حساب؟ في التطبيق الحقيقي يمكنك التسجيل هنا.",
  navHome:"الرئيسية", navProofs:"المستندات", navMail:"البريد", navMore:"المزيد",
  hello:"مرحبًا، {name}!", caseTitle:"طلب استمرار المساعدة 2026", caseNo:"رقم الملف {no}",
  missing1:"مستند واحد ناقص", missingN:"المستندات الناقصة: {n}",
  dueIn:"الموعد النهائي بعد {d} أيام", dueOn:"الموعد النهائي: {date}", cd:"متبقٍ: {d} أيام · {h} ساعة · {m} دقيقة",
  uploadNow:"ارفع الآن", toChecklist:"إلى قائمة المستندات",
  st_open:"ناقص", st_received:"تم الاستلام", st_checked:"تم التدقيق", st_resubmit:"يرجى الإرسال مرة أخرى",
  case_incomplete:"غير مكتمل", case_review:"مكتمل – يتم تدقيق الطلب", case_done:"تم التدقيق – القرار قادم",
  sent_missing1:"ما زال مستند واحد ناقصًا. عندما يصلنا سندقق طلبك. بعد ذلك فقط يمكن الدفع.",
  sent_missingN:"ما زالت هناك مستندات ناقصة: {n}. عندما تصلنا كلها سندقق طلبك. بعد ذلك فقط يمكن الدفع.",
  sent_review:"وصلتنا كل المستندات. نحن ندقق طلبك الآن. لا تحتاج إلى فعل شيء الآن.",
  sent_done:"تم تدقيق كل المستندات. ستحصل قريبًا على القرار.",
  step1:"الطلب", step2:"المستندات", step3:"التدقيق", step4:"القرار", stepsLabel:"مرحلة المعالجة",
  analogTitle:"تفضل الحضور شخصيًا أو الإرسال بالبريد؟ هذا ما زال ممكنًا.",
  analogText:"يمكنك أيضًا تسليم المستندات أو إرسالها بالبريد. استخدام التطبيق اختياري.",
  phone:"الهاتف", phoneVal:"0000 000000 (مثال)", address:"العنوان",
  addressVal:"Musterstraße 1, 00000 Musterstadt (مثال)", hoursL:"الأوقات", hours:"الإثنين–الجمعة 8–12 (مثال)",
  copy:"نسخ الرقم", copied:"تم نسخ الرقم",
  checklistTitle:"مستنداتك", checklistLead:"يحتاج الموظف المختص إلى هذه المستندات لطلبك.",
  todo:"ما زال مطلوبًا", doneH:"تم", why:"لماذا نحتاج هذا؟",
  addPhoto:"التقط صورة", addAgain:"أرسل مرة أخرى", pages1:"صفحة واحدة", pagesN:"عدد الصفحات: {n}",
  receivedOn:"تم الاستلام في {date}", setBy:"القائمة من الموظف المختص",
  uploadTitle:"رفع مستند", camera:"الكاميرا", file:"ملف", demoPhoto:"صورة تجريبية",
  tips:"نصيحة: ضع الورقة مسطحة، وإضاءة جيدة، والزوايا الأربع داخل الصورة.",
  shotEmpty:"لا توجد صورة بعد. اختر الكاميرا أو ملفًا أو صورة تجريبية.",
  checking:"يتم فحص الصورة …", okPage:"واضحة. تم حفظ الصفحة.",
  badBlur:"الصورة غير واضحة – يرجى التصوير مرة أخرى.", badCut:"الصفحة مقطوعة – يرجى التصوير مرة أخرى.",
  retake:"صوّر مرة أخرى", removePage:"احذف الصفحة {n}", page:"صفحة {n}", pagesDone:"صفحاتك",
  toReview:"متابعة إلى المراجعة", addMore:"صفحة أخرى؟ التقط صورة أخرى فقط.",
  simNote:"محاكاة: فحص الصور شكلي فقط. لا يتم إرسال أي شيء.", back:"رجوع",
  reviewTitle:"يرجى مراجعة بياناتك", rCase:"الملف", rProof:"المستند", rPages:"الصفحات", rFrom:"من",
  reviewCheck:"كل الصفحات كاملة وواضحة.", edit:"تعديل", send:"أرسل الآن",
  confTitle:"تم الاستلام", confLead:"شكرًا! وصلنا مستندك.",
  receipt:"تأكيد الاستلام", receiptNo:"الرقم", receiptTime:"الوقت", copyTitle:"نسخة من مستنداتك",
  confMail:"تجد هذا التأكيد أيضًا في بريدك.", confLaw:"تأكيد مع نظرة عامة على المستندات (§ 36a Abs. 2b SGB I)",
  toHome:"إلى الصفحة الرئيسية", nowStatus:"ماذا يحدث بعد ذلك",
  mailTitle:"البريد", mailLead:"رسائل حول ملفك", newBadge:"جديد", unread:"غير مقروءة",
  replyLabel:"ردك", replyPh:"اكتب هنا …", sendMsg:"إرسال", you:"أنت", office:"مركز العمل",
  msgSent:"تم إرسال الرسالة", goUpload:"ارفع المستند الآن", emptyReply:"يرجى كتابة رسالة أولًا.",
  moreTitle:"المزيد", assetHelp:"مساعدة في ملحق الممتلكات", optional:"اختياري", privacy:"حماية البيانات",
  analog:"شخصيًا أو بالبريد", logout:"تسجيل الخروج", staffView:"عرض الموظف المختص", account:"مسجل باسم {u}",
  privacyTitle:"حماية البيانات – باختصار",
  p1:"بياناتك بيانات اجتماعية. وهي محمية بشكل خاص.", p2:"نسأل فقط عما يحتاجه طلبك.",
  p3:"التطبيق لا يقوم بأي مقارنة آلية للبيانات.", p4:"لا تتبع. لا إعلانات.",
  p5:"يمكنك دائمًا أن تسأل عن البيانات التي لدينا.", p6:"في هذا النموذج لا يتم حفظ أو إرسال أي شيء.",
  pLaw:"الأساس القانوني: السرية الاجتماعية (§ 35 SGB I)، حماية البيانات الاجتماعية (§§ 67 ff. SGB X)، المادتان 5 و15 من اللائحة العامة لحماية البيانات.",
  assetLead:"أسئلة قصيرة تساعدك في ملء النموذج.", assetOptNote:"اختياري وطوعي. لا يحل محل نموذج الممتلكات الرسمي.",
  q1:"هل لديك حساب بنكي أو أكثر؟", q1why:"الحساب الجاري يُحسب أيضًا. هكذا نعرف أي كشوف حساب نحتاج.",
  q1n:"كم عدد الحسابات؟", q2:"هل لديك نقود أو أشياء ثمينة في البيت؟", q2why:"مثل المجوهرات أو العملات الذهبية. هذا يُحسب من الممتلكات.",
  q3:"هل لديك سيارة؟", q3why:"قد تُحسب السيارة من الممتلكات. غالبًا يمكنك الاحتفاظ بها.",
  q4:"هل لديك تأمين على الحياة أو تأمين تقاعدي؟", q4why:"القيمة الحالية للتأمين قد تكون مهمة.",
  whyAsk:"لماذا نسأل؟", yes:"نعم", no:"لا", next:"التالي", qOf:"السؤال {i} من {n}",
  plausTitle:"فحص إجاباتك", warnNoKa:"ذكرت عدد الحسابات: {n}، لكنك لم ترفع أي كشف حساب بعد.",
  warnPerAccount:"يرجى رفع كشوف لكل حساب (عدد الحسابات: {n}).", warnNoAccount:"لدى معظم الناس حساب جارٍ. يرجى التحقق من إجابتك.",
  hintIns:"يرجى إرفاق القيمة الحالية للتأمين.", allPlausible:"إجاباتك متوافقة.", restart:"ابدأ من جديد",
  staffTitle:"صندوق الوارد لدى الموظف المختص", staffLead:"محاكاة: هكذا تصل المستندات إلى الموظف.",
  staffInfo:"يصل كل مستند مرتبطًا مسبقًا بالملف وبالطلب. لا مسح ضوئي ولا فرز.",
  client:"الشخص", deadline:"الموعد النهائي", markChecked:"تم التدقيق", request:"اطلب مرة أخرى", reason:"السبب",
  r_blur:"غير مقروء", r_page:"صفحة ناقصة", r_period:"فترة خاطئة", sendRequest:"اطلب وأرسل إشعارًا",
  viaApp:"عبر التطبيق · رُبط تلقائيًا", notYet:"لم يصل بعد", remind:"أرسل تذكيرًا", reminded:"تم إرسال التذكير",
  cancel:"إلغاء", staffSet:"تم تعيين الحالة: {s}", staffBack:"الانتقال إلى عرض العميل",
  m1Subj:"وصلنا طلبك", m1Body:"استلمنا طلب استمرار المساعدة. في التطبيق ترى المستندات التي ما زالت ناقصة.",
  m2Subj:"كشف راتب شهر مارس ما زال ناقصًا", m2Body:"شكرًا على كشوف الحساب. ما زلنا نحتاج كشف راتبك لشهر مارس. يرجى رفعه في التطبيق.",
  mRecSubj:"تأكيد الاستلام: {proof}", mRecBody:"تم الاستلام في {time}. الرقم: {no}. الصفحات: {n}.",
  mResSubj:"يرجى الإرسال مرة أخرى: {proof}", mResBody:"السبب: {reason}. يرجى رفع المستند مرة أخرى.",
  mRemSubj:"تذكير: {proof}", mRemBody:"يرجى رفع هذا المستند قبل {date}.",
  autoReply:"شكرًا، وصلتنا رسالتك. سنرد عليك.",
  pushRemTitle:"تذكير: الموعد النهائي بعد {d} أيام", pushRemBody:"ما زال ناقصًا: {list}. يرجى الرفع قبل {date}.",
  pushMsgTitle:"رسالة جديدة من مركز العمل", appNow:"تطبيق المستندات · الآن", close:"إغلاق", and:" و",
  pushHint:"إشعار تجريبي"
},
uk:{
  app:"Застосунок документів", appSub:"Концепт-дослідження Jobcenter Wiesbaden", sender:"Муніципальний джобцентр – концепт-дослідження",
  proto:"Прототип у межах студентського звіту про практику – не офіційний застосунок міста Вісбаден",
  lang:"Оберіть мову", viewClient:"Мій вигляд", viewStaff:"Працівник", viewSwitch:"Змінити вигляд",
  loginTitle:"Вхід", loginLead:"У своєму акаунті ви бачите, яких документів ще бракує.",
  user:"Ім’я користувача", pass:"Пароль", loginBtn:"Увійти",
  loginNote:"Лише симуляція. Дані не перевіряються і не зберігаються.",
  noAccount:"Ще немає акаунта? У справжньому застосунку тут можна зареєструватися.",
  navHome:"Головна", navProofs:"Документи", navMail:"Пошта", navMore:"Більше",
  hello:"Вітаємо, {name}!", caseTitle:"Заява на продовження виплат 2026", caseNo:"Справа {no}",
  missing1:"Бракує 1 документа", missingN:"Бракує документів: {n}",
  dueIn:"Строк через {d} днів", dueOn:"Строк: {date}", cd:"Залишилось: {d} дн. · {h} год · {m} хв",
  uploadNow:"Завантажити зараз", toChecklist:"До списку",
  st_open:"не подано", st_received:"отримано", st_checked:"перевірено", st_resubmit:"подайте повторно",
  case_incomplete:"неповна", case_review:"повна – заява перевіряється", case_done:"перевірено – рішення буде",
  sent_missing1:"Бракує ще 1 документа. Коли він надійде, ми перевіримо вашу заяву. Лише після цього можлива виплата.",
  sent_missingN:"Бракує ще документів: {n}. Коли надійдуть усі, ми перевіримо вашу заяву. Лише після цього можлива виплата.",
  sent_review:"Усі документи надійшли. Зараз ми перевіряємо вашу заяву. Вам нічого не потрібно робити.",
  sent_done:"Усі документи перевірено. Незабаром ви отримаєте рішення.",
  step1:"Заява", step2:"Документи", step3:"Перевірка", step4:"Рішення", stepsLabel:"Стан обробки",
  analogTitle:"Бажаєте особисто або поштою? Це й далі можливо.",
  analogText:"Ви можете також принести або надіслати документи. Застосунок – добровільний.",
  phone:"Телефон", phoneVal:"0000 000000 (приклад)", address:"Адреса",
  addressVal:"Musterstraße 1, 00000 Musterstadt (приклад)", hoursL:"Години", hours:"Пн–Пт 8–12 (приклад)",
  copy:"Копіювати номер", copied:"Номер скопійовано",
  checklistTitle:"Ваші документи", checklistLead:"Ці документи потрібні працівникові для вашої заяви.",
  todo:"Ще потрібно", doneH:"Готово", why:"Навіщо це потрібно?",
  addPhoto:"Сфотографувати", addAgain:"Подати повторно", pages1:"1 сторінка", pagesN:"Сторінок: {n}",
  receivedOn:"отримано {date}", setBy:"Список від вашого працівника",
  uploadTitle:"Завантажити документ", camera:"Камера", file:"Файл", demoPhoto:"Демо-фото",
  tips:"Порада: покладіть аркуш рівно, добре освітлення, усі 4 кути в кадрі.",
  shotEmpty:"Ще немає фото. Оберіть камеру, файл або демо-фото.",
  checking:"Фото перевіряється …", okPage:"Добре читається. Сторінку збережено.",
  badBlur:"Фото нечітке – будь ласка, сфотографуйте ще раз.", badCut:"Сторінку обрізано – будь ласка, сфотографуйте ще раз.",
  retake:"Сфотографувати ще раз", removePage:"Видалити сторінку {n}", page:"Сторінка {n}", pagesDone:"Ваші сторінки",
  toReview:"Далі до перевірки", addMore:"Ще сторінка? Просто зробіть ще одне фото.",
  simNote:"Симуляція: перевірка фото лише імітується. Нічого не надсилається.", back:"Назад",
  reviewTitle:"Будь ласка, перевірте дані", rCase:"Справа", rProof:"Документ", rPages:"Сторінки", rFrom:"Від",
  reviewCheck:"Усі сторінки повні й добре читаються.", edit:"Змінити", send:"Надіслати",
  confTitle:"Отримано", confLead:"Дякуємо! Ваш документ надійшов.",
  receipt:"Підтвердження отримання", receiptNo:"Номер", receiptTime:"Час", copyTitle:"Копія ваших документів",
  confMail:"Це підтвердження є також у вашій пошті.", confLaw:"Підтвердження з переліком документів (§ 36a Abs. 2b SGB I)",
  toHome:"На головну", nowStatus:"Що далі",
  mailTitle:"Пошта", mailLead:"Повідомлення щодо вашої справи", newBadge:"Нове", unread:"непрочитане",
  replyLabel:"Ваша відповідь", replyPh:"Пишіть тут …", sendMsg:"Надіслати", you:"Ви", office:"Ваш джобцентр",
  msgSent:"Повідомлення надіслано", goUpload:"Завантажити документ зараз", emptyReply:"Спочатку напишіть повідомлення.",
  moreTitle:"Більше", assetHelp:"Допомога з додатком про майно", optional:"Необов’язково", privacy:"Захист даних",
  analog:"Особисто або поштою", logout:"Вийти", staffView:"Вигляд працівника", account:"Ви увійшли як {u}",
  privacyTitle:"Захист даних – коротко",
  p1:"Ваші дані – соціальні дані. Вони особливо захищені.", p2:"Ми запитуємо лише те, що потрібно для заяви.",
  p3:"Застосунок не здійснює автоматичних звірок даних.", p4:"Без стеження. Без реклами.",
  p5:"Ви завжди можете запитати, які дані ми маємо.", p6:"У цьому прототипі нічого не зберігається і не надсилається.",
  pLaw:"Підстави: соціальна таємниця (§ 35 SGB I), захист соціальних даних (§§ 67 ff. SGB X), ст. 5 і 15 GDPR.",
  assetLead:"Короткі запитання допоможуть із формуляром.", assetOptNote:"Необов’язково й добровільно. Не замінює офіційний формуляр про майно.",
  q1:"У вас є один або кілька банківських рахунків?", q1why:"Поточний рахунок теж рахується. Так ми бачимо, які виписки потрібні.",
  q1n:"Скільки рахунків?", q2:"У вас є готівка або цінності вдома?", q2why:"Наприклад, прикраси чи золоті монети. Це належить до майна.",
  q3:"У вас є автомобіль?", q3why:"Автомобіль може належати до майна. Часто його можна залишити.",
  q4:"У вас є страхування життя або пенсійне страхування?", q4why:"Поточна вартість страховки може бути важливою.",
  whyAsk:"Чому ми питаємо?", yes:"Так", no:"Ні", next:"Далі", qOf:"Питання {i} з {n}",
  plausTitle:"Перевірка ваших відповідей", warnNoKa:"Ви вказали рахунків: {n}, але ще не завантажили виписки.",
  warnPerAccount:"Будь ласка, завантажте виписки для кожного рахунку (рахунків: {n}).", warnNoAccount:"Майже кожна людина має поточний рахунок. Перевірте відповідь.",
  hintIns:"Будь ласка, додайте поточну вартість страховки.", allPlausible:"Ваші відповіді узгоджуються.", restart:"Почати знову",
  staffTitle:"Вхідні працівника", staffLead:"Симуляція: так документи надходять до працівника.",
  staffInfo:"Кожен документ одразу надходить прив’язаним до справи і запиту. Без сканування, без сортування.",
  client:"Особа", deadline:"Строк", markChecked:"Перевірено", request:"Запросити повторно", reason:"Причина",
  r_blur:"Нечитабельно", r_page:"Бракує сторінки", r_period:"Неправильний період", sendRequest:"Запросити й повідомити",
  viaApp:"через застосунок · прив’язано автоматично", notYet:"Ще не надійшло", remind:"Надіслати нагадування", reminded:"Нагадування надіслано",
  cancel:"Скасувати", staffSet:"Статус встановлено: {s}", staffBack:"До вигляду клієнта",
  m1Subj:"Вашу заяву отримано", m1Body:"Ми отримали вашу заяву на продовження виплат. У застосунку видно, яких документів ще бракує.",
  m2Subj:"Бракує розрахункового листа за березень", m2Body:"Дякуємо за виписки. Нам ще потрібен ваш розрахунковий лист за березень. Будь ласка, завантажте його в застосунку.",
  mRecSubj:"Підтвердження отримання: {proof}", mRecBody:"Отримано {time}. Номер: {no}. Сторінок: {n}.",
  mResSubj:"Подайте повторно: {proof}", mResBody:"Причина: {reason}. Будь ласка, завантажте документ ще раз.",
  mRemSubj:"Нагадування: {proof}", mRemBody:"Будь ласка, завантажте цей документ до {date}.",
  autoReply:"Дякуємо, ваше повідомлення надійшло. Ми відповімо.",
  pushRemTitle:"Нагадування: строк через {d} днів", pushRemBody:"Ще не подано: {list}. Завантажте до {date}.",
  pushMsgTitle:"Нове повідомлення від джобцентру", appNow:"Застосунок документів · зараз", close:"Закрити", and:" і ",
  pushHint:"Симульоване push-сповіщення"
}};

/* ===================== Beispieldaten (fiktiv) ===================== */
const CLIENT = {name:"Alex Beispiel", user:"demo.nutzer", caseNo:"WBA-2026-0815", bg:"BG 000-DEMO"};
const now0 = new Date();
const today0 = new Date(now0.getFullYear(), now0.getMonth(), now0.getDate());
const DEADLINE = new Date(today0.getTime() + 5*864e5 + (23*3600+59*60)*1000);
const ago = d => new Date(now0.getTime() - d*864e5);

const PROOF_TEXT = {
  wba:{title:{de:"Weiterbewilligungsantrag (Hauptantrag)",en:"Main application form",ar:"استمارة الطلب الرئيسية",uk:"Основна форма заяви"},
       what:{de:"Das ausgefüllte und unterschriebene Formular.",en:"The completed and signed form.",ar:"الاستمارة معبأة وموقعة.",uk:"Заповнена й підписана форма."},
       why:{de:"Ohne Antrag können wir nicht weiter zahlen.",en:"Without the application we cannot continue paying.",ar:"بدون الطلب لا يمكننا الاستمرار في الدفع.",uk:"Без заяви ми не можемо продовжити виплати."}},
  id:{title:{de:"Personalausweis",en:"Identity card",ar:"بطاقة الهوية",uk:"Посвідчення особи"},
       what:{de:"Vorder- und Rückseite.",en:"Front and back.",ar:"الوجه الأمامي والخلفي.",uk:"Лицьовий і зворотний бік."},
       why:{de:"Damit wir sicher wissen, dass Sie es sind.",en:"So we know for sure that it is you.",ar:"لنتأكد أنك أنت صاحب الطلب.",uk:"Щоб ми точно знали, що це ви."}},
  rent:{title:{de:"Mietbescheinigung",en:"Rent certificate",ar:"شهادة الإيجار",uk:"Довідка про оренду"},
       what:{de:"Vom Vermieter ausgefüllt.",en:"Filled in by your landlord.",ar:"يعبئها المؤجر.",uk:"Заповнює орендодавець."},
       why:{de:"Damit wir Ihre Miete richtig berechnen.",en:"So we can calculate your rent correctly.",ar:"لنحسب الإيجار بشكل صحيح.",uk:"Щоб правильно розрахувати вашу оренду."}},
  hi:{title:{de:"Nachweis Krankenversicherung",en:"Health insurance proof",ar:"إثبات التأمين الصحي",uk:"Підтвердження медичного страхування"},
       what:{de:"Schreiben Ihrer Krankenkasse über Ihre Mitgliedschaft.",en:"Letter from your health insurer about your membership.",ar:"رسالة من شركة التأمين الصحي عن عضويتك.",uk:"Лист вашої лікарняної каси про членство."},
       why:{de:"Damit Sie weiter versichert sind.",en:"So that you stay insured.",ar:"لكي تبقى مؤمَّنًا.",uk:"Щоб ви й далі були застраховані."}},
  ka:{title:{de:"Kontoauszüge der letzten 3 Monate",en:"Bank statements, last 3 months",ar:"كشوف الحساب لآخر 3 أشهر",uk:"Банківські виписки за 3 місяці"},
       what:{de:"Alle Seiten, alle Konten.",en:"All pages, all accounts.",ar:"كل الصفحات، كل الحسابات.",uk:"Усі сторінки, усі рахунки."},
       why:{de:"So sehen wir Ihr Einkommen und das Geld auf Ihren Konten.",en:"This shows us your income and the money in your accounts.",ar:"هكذا نرى دخلك والمال في حساباتك.",uk:"Так ми бачимо ваш дохід і гроші на рахунках."},
       note:{de:"Sie dürfen bei bestimmten Ausgaben den Empfänger schwärzen, z. B. Spenden an eine Partei. Der Betrag muss lesbar bleiben.",
             en:"For certain payments you may black out the recipient, e.g. donations to a party. The amount must stay readable.",
             ar:"يمكنك إخفاء اسم المستفيد في بعض المدفوعات، مثل التبرع لحزب. يجب أن يبقى المبلغ مقروءًا.",
             uk:"Для деяких витрат можна зафарбувати отримувача, напр. внески партії. Сума має залишатися видимою."}},
  pay:{title:{de:"Lohnabrechnung März",en:"Payslip for March",ar:"كشف راتب شهر مارس",uk:"Розрахунковий лист за березень"},
       what:{de:"Die Abrechnung von Ihrem Arbeitgeber.",en:"The payslip from your employer.",ar:"كشف الراتب من صاحب العمل.",uk:"Розрахунковий лист від роботодавця."},
       why:{de:"Ihr Lohn wird angerechnet. Dafür brauchen wir den genauen Betrag.",en:"Your wages are taken into account. We need the exact amount.",ar:"يُحتسب راتبك. لذلك نحتاج المبلغ الدقيق.",uk:"Ваша зарплата враховується. Нам потрібна точна сума."}}
};

const S = {
  lang:"de", role:"client", screen:"login", loggedIn:false,
  proofs:[
    {id:"wba", status:"checked", files:[]},
    {id:"id", status:"checked", files:[]},
    {id:"rent", status:"checked", files:[]},
    {id:"hi", status:"received", files:[]},
    {id:"ka", status:"open", files:[]},
    {id:"pay", status:"open", files:[]}
  ],
  threads:[
    {id:"t1", read:true, at:+ago(3), subj:["m1Subj"], msgs:[{from:"office", key:"m1Body", at:+ago(3)}]}
  ],
  open:{}, up:null, attempts:{}, reviewOk:false, receipt:null, threadId:null, lastSrc:"demo",
  asset:{step:0, accounts:null, count:1, cash:null, car:null, ins:null},
  staffReq:null, staffReason:"r_blur", reminded:{}, pendingPush:[], flags:{}
};

/* ===================== Hilfsfunktionen ===================== */
const $ = s => document.querySelector(s);
const esc = s => String(s).replace(/[&<>"']/g, c => ({"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;","'":"&#39;"}[c]));
function t(k, p){
  let s = (T[S.lang] && T[S.lang][k]) ?? T.de[k] ?? k;
  if(p) for(const x in p) s = s.split("{"+x+"}").join(p[x]);
  return s;
}
const L = o => o ? (o[S.lang] || o.de) : "";
const loc = () => LANGS[S.lang].loc;
const fDate = d => new Date(d).toLocaleDateString(loc(), {day:"2-digit", month:"2-digit", year:"numeric"});
const fTime = d => new Date(d).toLocaleString(loc(), {day:"2-digit", month:"2-digit", year:"numeric", hour:"2-digit", minute:"2-digit"});
const proof = id => S.proofs.find(p => p.id === id);
const ptitle = id => L(PROOF_TEXT[id].title);
const missing = () => S.proofs.filter(p => p.status === "open" || p.status === "resubmit");
const pagesTxt = n => n === 1 ? t("pages1") : t("pagesN", {n});
const daysLeft = () => Math.round((new Date(DEADLINE.getFullYear(), DEADLINE.getMonth(), DEADLINE.getDate()) - today0) / 864e5);
function caseState(){
  const m = missing().length;
  if(m) return {key:"incomplete", n:m};
  if(S.proofs.some(p => p.status === "received")) return {key:"review", n:0};
  return {key:"done", n:0};
}
function caseSentence(){
  const c = caseState();
  if(c.key === "incomplete") return c.n === 1 ? t("sent_missing1") : t("sent_missingN", {n:c.n});
  return c.key === "review" ? t("sent_review") : t("sent_done");
}
function cdText(){
  let ms = Math.max(0, DEADLINE - new Date());
  const d = Math.floor(ms/864e5); ms -= d*864e5;
  const h = Math.floor(ms/36e5); ms -= h*36e5;
  const m = Math.floor(ms/6e4);
  return t("cd", {d, h, m});
}
function listJoin(arr){
  if(arr.length < 2) return arr.join("");
  return arr.slice(0,-1).join(", ") + t("and") + arr[arr.length-1];
}
function msgParams(p){
  if(!p) return {};
  const o = Object.assign({}, p);
  if(p.proof) o.proof = ptitle(p.proof);
  if(p.reason) o.reason = t(p.reason);
  if(p.date) o.date = fDate(p.date);
  if(p.time) o.time = fTime(p.time);
  return o;
}
const subjOf = th => t(th.subj[0], msgParams(th.subj[1]));
function preview(th){ const m = th.msgs[th.msgs.length-1]; const s = m.text ?? t(m.key, msgParams(m.p)); return s.length > 80 ? s.slice(0,80) + "…" : s; }

/* ===================== Symbole ===================== */
const I = {
  logo:'<svg width="22" height="22" viewBox="0 0 24 24" aria-hidden="true"><path d="M6 2.5h8l5 5V20a1.5 1.5 0 0 1-1.5 1.5h-11A1.5 1.5 0 0 1 5 20V4a1.5 1.5 0 0 1 1-1.5z" fill="#00489b"/><path d="M8.5 13.5l2.5 2.5 5-5.5" fill="none" stroke="#f2b705" stroke-width="2.4" stroke-linecap="round" stroke-linejoin="round"/></svg>',
  logoW:'<svg width="22" height="22" viewBox="0 0 24 24" aria-hidden="true"><path d="M6 2.5h8l5 5V20a1.5 1.5 0 0 1-1.5 1.5h-11A1.5 1.5 0 0 1 5 20V4a1.5 1.5 0 0 1 1-1.5z" fill="#fff"/><path d="M8.5 13.5l2.5 2.5 5-5.5" fill="none" stroke="#f2b705" stroke-width="2.4" stroke-linecap="round" stroke-linejoin="round"/></svg>',
  globe:'<svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="#fff" stroke-width="2" aria-hidden="true"><circle cx="12" cy="12" r="9"/><path d="M3 12h18M12 3c2.5 3 2.5 15 0 18M12 3c-2.5 3-2.5 15 0 18"/></svg>',
  home:'<svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linejoin="round" aria-hidden="true"><path d="M3 11l9-7 9 7v9a1 1 0 0 1-1 1h-5v-6H9v6H4a1 1 0 0 1-1-1z"/></svg>',
  list:'<svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><path d="M9 6h11M9 12h11M9 18h11M4 6l1 1 2-2M4 12l1 1 2-2M4 18l1 1 2-2"/></svg>',
  mail:'<svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linejoin="round" aria-hidden="true"><rect x="3" y="5" width="18" height="14" rx="2"/><path d="M3 7l9 6 9-6"/></svg>',
  more:'<svg width="24" height="24" viewBox="0 0 24 24" fill="currentColor" aria-hidden="true"><circle cx="5" cy="12" r="2"/><circle cx="12" cy="12" r="2"/><circle cx="19" cy="12" r="2"/></svg>',
  user:'<svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" aria-hidden="true"><circle cx="12" cy="8" r="4"/><path d="M4 21c0-4 3.6-7 8-7s8 3 8 7"/></svg>',
  desk:'<svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linejoin="round" aria-hidden="true"><rect x="3" y="4" width="18" height="12" rx="1.5"/><path d="M8 20h8M12 16v4"/></svg>',
  cam:'<svg width="26" height="26" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linejoin="round" aria-hidden="true"><path d="M4 8h3l2-3h6l2 3h3v11H4z"/><circle cx="12" cy="13" r="3.5"/></svg>',
  file:'<svg width="26" height="26" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><path d="M12 15V4M7 9l5-5 5 5M4 15v4a1 1 0 0 0 1 1h14a1 1 0 0 0 1-1v-4"/></svg>',
  demo:'<svg width="26" height="26" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linejoin="round" aria-hidden="true"><path d="M6 3h9l4 4v14H6z"/><path d="M9 11h7M9 15h7M9 7h3"/></svg>',
  clock:'<svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" aria-hidden="true"><circle cx="12" cy="12" r="9"/><path d="M12 7v5l3 2"/></svg>',
  bell:'<svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><path d="M6 8a6 6 0 1 1 12 0c0 7 3 9 3 9H3s3-2 3-9"/><path d="M10.3 21a1.94 1.94 0 0 0 3.4 0"/></svg>',
  back:'<svg class="flip" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.6" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><path d="M15 5l-7 7 7 7"/></svg>',
  chev:'<svg class="flip" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.4" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><path d="M9 5l7 7-7 7"/></svg>',
  down:'<svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.6" stroke-linecap="round" aria-hidden="true"><path d="M6 9l6 6 6-6"/></svg>',
  x:'<svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.6" stroke-linecap="round" aria-hidden="true"><path d="M6 6l12 12M18 6L6 18"/></svg>',
  trash:'<svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" aria-hidden="true"><path d="M4 7h16M10 11v6M14 11v6M6 7l1 13h10l1-13M9 7V4h6v3"/></svg>',
  phone:'<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linejoin="round" aria-hidden="true"><path d="M5 3h4l2 5-2.5 1.5a11 11 0 0 0 6 6L16 13l5 2v4a2 2 0 0 1-2 2A16 16 0 0 1 3 5a2 2 0 0 1 2-2"/></svg>',
  shield:'<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linejoin="round" aria-hidden="true"><path d="M12 3l8 3v6c0 5-3.5 8-8 9-4.5-1-8-4-8-9V6z"/></svg>',
  coins:'<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" aria-hidden="true"><ellipse cx="9" cy="7" rx="6" ry="3"/><path d="M3 7v4c0 1.7 2.7 3 6 3s6-1.3 6-3V7M9 14v3c0 1.7 2.7 3 6 3s6-1.3 6-3v-4c0-1.6-2.4-2.9-5.4-3"/></svg>',
  out:'<svg class="flip" width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><path d="M14 4h5v16h-5M10 8l-4 4 4 4M6 12h10"/></svg>',
  info:'<svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" style="flex:none" aria-hidden="true"><circle cx="12" cy="12" r="9"/><path d="M12 11v6M12 7.5v.01"/></svg>',
  warn:'<svg width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" stroke-linecap="round" stroke-linejoin="round" style="flex:none" aria-hidden="true"><path d="M12 3l10 18H2z"/><path d="M12 10v5M12 18v.01"/></svg>',
  logoSmall:'<svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linejoin="round" aria-hidden="true"><path d="M3 21h18M5 21V10l7-5 7 5v11M9 21v-6h6v6"/></svg>',
  okBig:'<svg width="40" height="40" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.6" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><path d="M5 12.5l4.5 4.5L19 7.5"/></svg>'
};
const SICON = {
  open:'<svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.8" stroke-dasharray="3.2 3" aria-hidden="true"><circle cx="12" cy="12" r="9"/></svg>',
  received:'<svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.8" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><path d="M4 13h4l2 3h4l2-3h4M4 13l3-8h10l3 8v6H4z"/></svg>',
  checked:'<svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="3.2" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><path d="M5 12.5l4.5 4.5L19 7.5"/></svg>',
  resubmit:'<svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.8" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true"><path d="M4 12a8 8 0 1 0 2.5-5.8M4 4v4h4"/></svg>'
};
const chip = st => `<span class="chip c-${st}">${SICON[st]}<span><span class="sr">Status: </span>${t("st_"+st)}</span></span>`;

/* ===================== Demo-Dokumente (Canvas, fiktiv) ===================== */
function makeDoc(id, variant, pageNo){
  const c = document.createElement("canvas"); c.width = 600; c.height = 800;
  const g = c.getContext("2d");
  g.fillStyle = "#3a4a49"; g.fillRect(0,0,600,800);
  g.save();
  if(variant === "blur"){ g.filter = "blur(5px)"; g.translate(300,400); g.rotate(-0.05); g.translate(-300,-400); }
  g.fillStyle = "#ffffff"; g.fillRect(28,28,544,744);
  g.fillStyle = "#00489b"; g.fillRect(28,28,544,10);
  g.fillStyle = "#172326"; g.font = "bold 28px sans-serif";
  const heads = {ka:"Kontoauszug · Beispielbank", pay:"Entgeltabrechnung März", wba:"Weiterbewilligungsantrag", id:"Ausweis (Muster)", rent:"Mietbescheinigung", hi:"Mitgliedsbescheinigung"};
  g.fillText(heads[id] || "Dokument", 56, 90);
  g.font = "18px sans-serif"; g.fillStyle = "#4f5f63";
  g.fillText("MUSTER – fiktive Daten · Seite " + (pageNo||1), 56, 122);
  if(id === "ka"){
    const rows = [["01.","Gehalt Musterfirma GmbH","+1.240,00"],["03.","Miete","-520,00"],["05.","Strom Stadtwerke (fiktiv)","-48,00"],["09.","Supermarkt","-63,17"],["12.","Mobilfunk","-15,99"],["15.","Überweisung","-30,00"],["21.","Apotheke","-8,40"],["28.","Kontoführung","-4,50"]];
    g.font = "17px sans-serif";
    rows.forEach((r,i) => { const y = 180 + i*46; g.fillStyle = i%2 ? "#ffffff" : "#eef3f3"; g.fillRect(56, y-26, 488, 40); g.fillStyle = "#172326"; g.fillText(r[0], 66, y); g.fillText(r[1], 120, y); g.textAlign = "right"; g.fillText(r[2], 534, y); g.textAlign = "left"; });
    g.font = "bold 19px sans-serif"; g.fillText("Kontostand: 512,94 EUR", 56, 600);
  } else if(id === "pay"){
    const rows = [["Bruttolohn","1.580,00"],["Lohnsteuer","-42,10"],["Sozialversicherung","-331,02"],["Nettolohn","1.206,88"]];
    g.font = "19px sans-serif";
    rows.forEach((r,i) => { const y = 200 + i*56; g.fillStyle = "#172326"; g.fillText(r[0], 66, y); g.textAlign = "right"; g.fillText(r[1]+" EUR", 534, y); g.textAlign = "left"; g.fillStyle = "#cfd8da"; g.fillRect(56, y+16, 488, 2); });
    g.fillStyle = "#4f5f63"; g.font = "17px sans-serif"; g.fillText("Arbeitgeber: Musterfirma GmbH (fiktiv)", 66, 470);
  } else {
    g.fillStyle = "#cfd8da";
    for(let i = 0; i < 12; i++) g.fillRect(56, 170 + i*38, 260 + ((i*83) % 220), 12);
  }
  g.strokeStyle = "#00489b"; g.lineWidth = 3; g.strokeRect(56, 680, 190, 52);
  g.restore();
  return c.toDataURL("image/jpeg", 0.78);
}
S.proofs.forEach(p => { if(p.status !== "open") p.files.push({pages:[makeDoc(p.id,null,1)], at:+ago(4), no:"EB-"+(1000+Math.floor(Math.random()*8999))}); });

/* ===================== Bausteine ===================== */
function header(){
  const staff = S.role === "staff";
  const langOpts = Object.keys(LANGS).map(k => `<option value="${k}" ${k===S.lang?"selected":""} lang="${k}">${LANGS[k].name}</option>`).join("");
  return `<header class="top ${staff?"staff":""}">
    <div class="proto pad" role="note">${t("proto")}</div>
    <div class="pad">
      <div class="topbar">
        <span class="mark">${I.logo}</span>
        <span class="brandtx"><b>${t("app")}</b><small>${t("appSub")}</small></span>
        <label class="langsel">${I.globe}<span class="sr">${t("lang")}</span>
          <select id="langSel" aria-label="${t("lang")}">${langOpts}</select></label>
      </div>
      ${S.loggedIn ? `<div class="roles" role="group" aria-label="${t("viewSwitch")}">
        <button data-act="role" data-v="client" aria-pressed="${!staff}">${I.user}${t("viewClient")}</button>
        <button data-act="role" data-v="staff" aria-pressed="${staff}">${I.desk}${t("viewStaff")}</button>
      </div>` : ""}
    </div></header>`;
}
function nav(){
  const unread = S.threads.filter(x => !x.read).length;
  const cur = {home:"home", checklist:"checklist", upload:"checklist", review:"checklist", confirm:"checklist", mail:"mail", thread:"mail", more:"more", privacy:"more", analog:"more", asset:"more"}[S.screen];
  const b = (id, ic, label, extra="") => `<button data-act="go" data-v="${id}" ${cur===id?'aria-current="page"':""}>${ic}<span>${label}</span>${extra}</button>`;
  return `<nav class="nav" aria-label="Navigation">
    ${b("home", I.home, t("navHome"))}
    ${b("checklist", I.list, t("navProofs"), missing().length ? `<span class="badge" aria-label="${missing().length}">${missing().length}</span>` : "")}
    ${b("mail", I.mail, t("navMail"), unread ? `<span class="badge"><span aria-hidden="true">${unread}</span><span class="sr">${unread} ${t("unread")}</span></span>` : "")}
    ${b("more", I.more, t("navMore"))}
  </nav>`;
}
const head = (title, lead, back) => `<div class="head">
  ${back ? `<button class="backbtn" data-act="go" data-v="${back}">${I.back}${t("back")}</button>` : ""}
  <h1 tabindex="-1" id="h1">${title}</h1>${lead ? `<p>${lead}</p>` : ""}</div>`;

function analogBox(){
  return `<section class="analog" aria-labelledby="anH">
    <h2 id="anH">${t("analogTitle")}</h2>
    <p>${t("analogText")}</p>
    <dl class="kv"><dt>${t("phone")}</dt><dd><span id="phoneNo">${t("phoneVal")}</span></dd>
      <dt>${t("address")}</dt><dd>${t("addressVal")}</dd><dt>${t("hoursL")}</dt><dd>${t("hours")}</dd></dl>
    <button class="btn btn-s" data-act="copyPhone">${I.phone}${t("copy")}</button>
  </section>`;
}

/* ===================== Screens Kundensicht ===================== */
function scrLogin(){
  return `<main class="pad" id="main">
    <p class="sender">${I.logoSmall}<span>${t("sender")}</span></p>
    ${head(t("loginTitle"), t("loginLead"))}
    <form class="card" id="loginForm" novalidate>
      <div><label class="lbl" for="lUser">${t("user")}</label><input class="inp" id="lUser" autocomplete="off" value="${CLIENT.user}"></div>
      <div><label class="lbl" for="lPass">${t("pass")}</label><input class="inp" id="lPass" type="password" autocomplete="off" value="demo1234"></div>
      <button class="btn btn-p" type="submit" data-test="login">${t("loginBtn")}</button>
      <p class="note">${I.info}<span>${t("loginNote")}</span></p>
    </form>
    <p class="small muted">${t("noAccount")}</p>
    ${analogBox()}
  </main>`;
}

function reminderBanner(){
  const m = missing();
  if(!m.length) return "";
  return `<section class="remind" aria-labelledby="remH" role="region">
    <div class="remind-top"><span class="ic">${I.bell}</span>
      <div><h2 id="remH">${m.length===1 ? t("missing1") : t("missingN",{n:m.length})}</h2>
      <p class="due">${t("dueIn",{d:daysLeft()})} · ${fDate(DEADLINE)}</p></div></div>
    <ul>${m.map(p => `<li>${esc(ptitle(p.id))}</li>`).join("")}</ul>
    <div class="cd" aria-live="off">${I.clock}<span id="cd">${cdText()}</span></div>
    <button class="btn btn-d" data-act="upload" data-v="${m[0].id}" data-test="remUpload">${t("uploadNow")}</button>
  </section>`;
}
function caseCard(){
  const c = caseState();
  const stepNow = c.key === "incomplete" ? 1 : c.key === "review" ? 2 : 3;
  const chipCls = c.key === "incomplete" ? "c-open" : c.key === "review" ? "c-received" : "c-checked";
  const chipIc = c.key === "incomplete" ? SICON.open : c.key === "review" ? SICON.received : SICON.checked;
  const steps = [t("step1"), t("step2"), t("step3"), t("step4")].map((s,i) =>
    `<li class="${i<stepNow?"done":i===stepNow?"now":""}" ${i===stepNow?'aria-current="step"':""}>${s}</li>`).join("");
  return `<section class="card" aria-labelledby="caseH">
    <div class="case-title"><div><h2 id="caseH">${t("caseTitle")}</h2><p class="small muted">${t("caseNo",{no:CLIENT.caseNo})}</p></div></div>
    <span class="chip ${chipCls}" id="caseStatus">${chipIc}<span><span class="sr">Status: </span>${t("case_"+c.key)}</span></span>
    <ol class="steps" aria-label="${t("stepsLabel")}">${steps}</ol>
    <p class="sentence" id="caseSentence">${caseSentence()}</p>
    <button class="btn btn-s" data-act="go" data-v="checklist">${t("toChecklist")}${I.chev}</button>
  </section>`;
}
function scrHome(){
  return `<main class="pad" id="main">
    ${head(t("hello",{name:"Alex"}))}
    ${reminderBanner()}
    ${caseCard()}
    ${analogBox()}
  </main>`;
}

function proofCard(p){
  const tx = PROOF_TEXT[p.id], need = p.status === "open" || p.status === "resubmit";
  const last = p.files[p.files.length-1];
  const isOpen = !!S.open[p.id];
  return `<article class="proof ${need?"need":""} ${p.status==="resubmit"?"bad":""}" aria-labelledby="ph-${p.id}">
    <div class="proof-h"><div class="tx">
      <h3 id="ph-${p.id}">${esc(L(tx.title))}</h3>
      <p>${esc(L(tx.what))}</p>
      ${chip(p.status)}
    </div></div>
    <button class="why" data-act="why" data-v="${p.id}" aria-expanded="${isOpen}" aria-controls="why-${p.id}">${I.info}${t("why")}${I.down}</button>
    <div class="whybox" id="why-${p.id}" ${isOpen?"":"hidden"}><p>${esc(L(tx.why))}</p>${tx.note?`<p><b>${esc(L(tx.note))}</b></p>`:""}</div>
    ${last ? `<div class="meta">${t("receivedOn",{date:fDate(last.at)})} · ${pagesTxt(last.pages.length)}</div>
      <div class="thumbs">${last.pages.map((s,i)=>`<img src="${s}" alt="${esc(L(tx.title))}, ${t("page",{n:i+1})}">`).join("")}</div>` : ""}
    ${need ? `<button class="btn btn-p" data-act="upload" data-v="${p.id}" data-test="up-${p.id}">${I.cam}${p.status==="resubmit"?t("addAgain"):t("addPhoto")}</button>` : ""}
  </article>`;
}
function scrChecklist(){
  const need = S.proofs.filter(p => p.status==="open"||p.status==="resubmit");
  const done = S.proofs.filter(p => !(p.status==="open"||p.status==="resubmit"));
  return `<main class="pad" id="main">
    ${head(t("checklistTitle"), t("checklistLead"))}
    <div class="card" style="gap:6px"><b>${t("caseTitle")}</b><span class="small muted">${t("caseNo",{no:CLIENT.caseNo})} · ${t("dueOn",{date:fDate(DEADLINE)})}</span>
      <span class="small muted">${t("setBy")}</span></div>
    ${need.length ? `<h2 class="sec-label">${t("todo")} (${need.length})</h2><div class="list">${need.map(proofCard).join("")}</div>` : `<p class="sentence">${caseSentence()}</p>`}
    <h2 class="sec-label">${t("doneH")} (${done.length})</h2><div class="list">${done.map(proofCard).join("")}</div>
  </main>`;
}

function scrUpload(){
  const u = S.up, tx = PROOF_TEXT[u.proofId];
  let shot;
  if(u.checking) shot = `<div class="shot"><div class="ph"><span class="spin"></span><span>${t("checking")}</span></div></div>`;
  else if(u.bad) shot = `<div class="shot bad ${u.bad.cssBlur?"blurfx":""}"><img src="${u.bad.src}" alt="${t("badBlur")}"></div>`;
  else if(u.pages.length) shot = `<div class="shot"><img src="${u.pages[u.pages.length-1]}" alt="${t("page",{n:u.pages.length})}"></div>`;
  else shot = `<div class="shot"><div class="ph">${I.cam}<span>${t("shotEmpty")}</span></div></div>`;
  const fb = u.bad ? `<div class="fb fb-bad" role="alert" id="fbBad">${I.warn}<span>${t(u.bad.reason)}</span></div>
      <button class="btn btn-a" data-act="retake" data-test="retake">${I.cam}${t("retake")}</button>`
    : (!u.checking && u.pages.length ? `<div class="fb fb-ok" role="status">${SICON.checked}<span>${t("okPage")}</span></div>` : "");
  const src = u.bad || u.checking ? "" : `<div class="src">
      <button class="btn btn-s" data-act="cam">${I.cam}${t("camera")}</button>
      <button class="btn btn-s" data-act="file">${I.file}${t("file")}</button>
      <button class="btn btn-s" data-act="demo" data-test="demo">${I.demo}${t("demoPhoto")}</button></div>`;
  return `<main class="pad" id="main">
    ${head(esc(L(tx.title)), esc(L(tx.what)), "checklist")}
    ${shot}
    ${fb}
    ${src}
    ${!u.bad && !u.checking && !u.pages.length ? `<p class="note">${I.info}<span>${t("tips")}</span></p>` : ""}
    ${u.pages.length ? `<section aria-labelledby="pgH" style="display:flex;flex-direction:column;gap:8px">
      <h2 class="sec-label" id="pgH">${t("pagesDone")} (${u.pages.length})</h2>
      <div class="pages">${u.pages.map((s,i)=>`<div class="pg"><img src="${s}" alt="${t("page",{n:i+1})}"><span>${t("page",{n:i+1})}</span>
        <button data-act="rmPage" data-v="${i}" aria-label="${t("removePage",{n:i+1})}">${I.trash}</button></div>`).join("")}</div>
      ${!u.bad && !u.checking ? `<p class="small muted">${t("addMore")}</p>` : ""}</section>` : ""}
    <button class="btn btn-p" data-act="toReview" data-test="toReview" ${u.pages.length && !u.bad && !u.checking ? "" : "disabled"}>${t("toReview")}${I.chev}</button>
    <p class="note">${I.info}<span>${t("simNote")}</span></p>
  </main>`;
}

function scrReview(){
  const u = S.up;
  return `<main class="pad" id="main">
    ${head(t("reviewTitle"), "", "upload")}
    <section class="card">
      <dl class="kv"><dt>${t("rCase")}</dt><dd>${t("caseTitle")}<br><span class="muted small">${CLIENT.caseNo}</span></dd>
        <dt>${t("rProof")}</dt><dd>${esc(ptitle(u.proofId))}</dd>
        <dt>${t("rPages")}</dt><dd>${u.pages.length}</dd>
        <dt>${t("rFrom")}</dt><dd>${CLIENT.user}</dd></dl>
      <div class="thumbs">${u.pages.map((s,i)=>`<img src="${s}" alt="${t("page",{n:i+1})}">`).join("")}</div>
      <button class="btn btn-s" data-act="go" data-v="upload">${t("edit")}</button>
    </section>
    <label class="check" for="revOk"><input type="checkbox" id="revOk" ${S.reviewOk?"checked":""}><span>${t("reviewCheck")}</span></label>
    <button class="btn btn-p" data-act="submit" data-test="submit" ${S.reviewOk?"":"disabled"}>${t("send")}</button>
  </main>`;
}

function scrConfirm(){
  const r = S.receipt;
  return `<main class="pad" id="main">
    <div class="big-ok">${I.okBig}</div>
    <div class="head center"><h1 tabindex="-1" id="h1">${t("confTitle")}</h1><p>${t("confLead")}</p></div>
    <section class="card" aria-labelledby="rcH">
      <h2 id="rcH">${t("receipt")}</h2>
      <dl class="kv"><dt>${t("receiptNo")}</dt><dd>${r.no}</dd><dt>${t("receiptTime")}</dt><dd>${fTime(r.at)}</dd>
        <dt>${t("rCase")}</dt><dd>${t("caseTitle")}</dd><dt>${t("rProof")}</dt><dd>${esc(ptitle(r.proofId))}</dd>
        <dt>Status</dt><dd>${chip("received")}</dd></dl>
      <h3>${t("copyTitle")}</h3>
      <div class="thumbs">${r.pages.map((s,i)=>`<img src="${s}" alt="${t("page",{n:i+1})}">`).join("")}</div>
      <p class="small muted">${t("confLaw")}</p>
      <p class="note">${I.mail}<span>${t("confMail")}</span></p>
    </section>
    <section class="card" aria-labelledby="nxH"><h2 id="nxH">${t("nowStatus")}</h2>
      <p class="sentence" id="confSentence">${caseSentence()}</p></section>
    <button class="btn btn-p" data-act="go" data-v="home" data-test="toHome">${t("toHome")}</button>
  </main>`;
}

function scrMail(){
  const list = S.threads.slice().sort((a,b) => b.at - a.at);
  return `<main class="pad" id="main">
    ${head(t("mailTitle"), t("mailLead"))}
    <div class="list">${list.map(th => `<button class="thread ${th.read?"":"unread"}" data-act="thread" data-v="${th.id}" data-test="th-${th.id}">
      <span class="tx"><span class="casechip">${t("caseTitle")}</span><b>${esc(subjOf(th))}</b>
      <span class="small muted">${esc(preview(th))}</span></span>
      <span style="display:flex;flex-direction:column;align-items:flex-end;gap:6px"><time>${fDate(th.at)}</time>${th.read?"":`<span class="newchip">${t("newBadge")}</span>`}</span>
    </button>`).join("")}</div>
  </main>`;
}
function scrThread(){
  const th = S.threads.find(x => x.id === S.threadId);
  const action = th.action && proof(th.action) && (proof(th.action).status === "open" || proof(th.action).status === "resubmit");
  return `<main class="pad" id="main">
    ${head(esc(subjOf(th)), `<span class="casechip">${t("caseTitle")} · ${CLIENT.caseNo}</span>`, "mail")}
    <div class="bubbles">${th.msgs.map(m => `<div class="bubble ${m.from}"><small>${m.from==="you"?t("you"):t("sender")} · ${fTime(m.at)}</small>
      <span>${esc(m.text ?? t(m.key, msgParams(m.p)))}</span></div>`).join("")}</div>
    ${action ? `<button class="btn btn-p" data-act="upload" data-v="${th.action}" data-test="threadUpload">${I.cam}${t("goUpload")}</button>` : ""}
    <form id="replyForm" class="card" novalidate>
      <label class="lbl" for="replyText">${t("replyLabel")}</label>
      <textarea id="replyText" placeholder="${t("replyPh")}"></textarea>
      <button class="btn btn-s" type="submit">${t("sendMsg")}</button>
    </form>
  </main>`;
}

function scrMore(){
  const it = (act, v, ic, label, extra="") => `<button data-act="${act}" data-v="${v}">${ic}<span class="tx">${label}</span>${extra}${I.chev}</button>`;
  return `<main class="pad" id="main">
    ${head(t("moreTitle"), t("account",{u:CLIENT.user}))}
    <div class="menu">
      ${it("go","asset",I.coins,t("assetHelp"),`<span class="optbadge">${t("optional")}</span>`)}
      ${it("go","privacy",I.shield,t("privacy"))}
      ${it("go","analog",I.phone,t("analog"))}
      ${it("role","staff",I.desk,t("staffView"))}
      ${it("logout","",I.out,t("logout"))}
    </div>
  </main>`;
}
function scrPrivacy(){
  return `<main class="pad" id="main">
    ${head(t("privacyTitle"), "", "more")}
    <section class="card"><ul style="margin:0;padding-inline-start:20px;display:flex;flex-direction:column;gap:8px">
      ${["p1","p2","p3","p4","p5","p6"].map(k=>`<li>${t(k)}</li>`).join("")}</ul>
      <p class="small muted">${t("pLaw")}</p></section>
  </main>`;
}
function scrAnalog(){
  return `<main class="pad" id="main">${head(t("analog"), "", "more")}${analogBox()}</main>`;
}

function scrAsset(){
  const a = S.asset, N = 4;
  const qs = [["q1","q1why","accounts"],["q2","q2why","cash"],["q3","q3why","car"],["q4","q4why","ins"]];
  let body;
  if(a.step < N){
    const [q, why, key] = qs[a.step];
    const val = a[key];
    body = `<div class="bar" aria-hidden="true"><i style="width:${(a.step)/N*100}%"></i></div>
      <p class="small muted">${t("qOf",{i:a.step+1,n:N})}</p>
      <section class="card" aria-labelledby="qH"><h2 id="qH">${t(q)}</h2>
        <div class="yn" role="group" aria-labelledby="qH">
          <button data-act="ans" data-v="yes" aria-pressed="${val===true}">${t("yes")}</button>
          <button data-act="ans" data-v="no" aria-pressed="${val===false}">${t("no")}</button></div>
        ${key==="accounts" && val===true ? `<div><p class="lbl" id="cntL">${t("q1n")}</p><div class="stepper" role="group" aria-labelledby="cntL">
          <button data-act="cnt" data-v="-1" aria-label="-1">−</button><output aria-live="polite">${a.count}</output><button data-act="cnt" data-v="1" aria-label="+1">+</button></div></div>` : ""}
        <div class="whybox"><b>${t("whyAsk")}</b><p>${t(why)}</p></div>
      </section>
      <div class="row">${a.step>0?`<button class="btn btn-s" data-act="aStep" data-v="-1">${t("back")}</button>`:""}
        <button class="btn btn-p" data-act="aStep" data-v="1" ${val===null?"disabled":""}>${t("next")}</button></div>`;
  } else {
    const ka = proof("ka"), kaPages = ka.files.reduce((s,f)=>s+f.pages.length,0);
    const w = [];
    if(a.accounts === false) w.push(["w", t("warnNoAccount")]);
    if(a.accounts && (ka.status==="open"||ka.status==="resubmit")) w.push(["w", t("warnNoKa",{n:a.count}), true]);
    else if(a.accounts && a.count > 1 && kaPages < a.count) w.push(["w", t("warnPerAccount",{n:a.count})]);
    if(a.ins) w.push(["i", t("hintIns")]);
    if(!w.length) w.push(["o", t("allPlausible")]);
    body = `<section class="card" aria-labelledby="plH"><h2 id="plH">${t("plausTitle")}</h2>
      ${w.map(x=>`<div class="warn ${x[0]}" role="${x[0]==="w"?"alert":"status"}">${x[0]==="o"?SICON.checked:x[0]==="w"?I.warn:I.info}<span>${x[1]}</span></div>
        ${x[2]?`<button class="btn btn-p" data-act="upload" data-v="ka">${I.cam}${t("uploadNow")}</button>`:""}`).join("")}
      </section>
      <button class="btn btn-s" data-act="aReset">${t("restart")}</button>`;
  }
  return `<main class="pad" id="main">
    ${head(t("assetHelp"), t("assetLead"), "more")}
    <div class="opt-banner" role="note"><span class="optbadge">${t("optional")}</span><span>${t("assetOptNote")}</span></div>
    ${body}
  </main>`;
}

/* ===================== Sicht Sachbearbeitung ===================== */
function scrStaff(){
  const c = caseState();
  const rows = S.proofs.map(p => {
    const last = p.files[p.files.length-1];
    const req = S.staffReq === p.id;
    let actions = "";
    if(p.status === "received"){
      actions = req ? `<fieldset class="radios" style="border:0;padding:0;margin:0"><legend class="lbl">${t("reason")}</legend>
          ${["r_blur","r_page","r_period"].map(r=>`<label><input type="radio" name="reason" value="${r}" ${S.staffReason===r?"checked":""}>${t(r)}</label>`).join("")}</fieldset>
          <div class="row"><button class="btn btn-s" data-act="sCancel">${t("cancel")}</button><button class="btn btn-staff" data-act="sSend" data-v="${p.id}">${t("sendRequest")}</button></div>`
        : `<div class="row"><button class="btn btn-staff" data-act="sOk" data-v="${p.id}" data-test="sOk-${p.id}">${SICON.checked}${t("markChecked")}</button>
           <button class="btn btn-s" data-act="sReq" data-v="${p.id}">${SICON.resubmit}${t("request")}</button></div>`;
    } else if(p.status === "open" || p.status === "resubmit"){
      actions = `<button class="btn btn-s" data-act="sRemind" data-v="${p.id}" ${S.reminded[p.id]?"disabled":""}>${I.bell}${S.reminded[p.id]?t("reminded"):t("remind")}</button>`;
    }
    return `<article class="sproof" aria-labelledby="sp-${p.id}">
      <div style="display:flex;justify-content:space-between;gap:8px;align-items:flex-start;flex-wrap:wrap"><h3 id="sp-${p.id}">${esc(ptitle(p.id))}</h3>${chip(p.status)}</div>
      ${last && p.status !== "open" ? `<div class="meta">${SICON.received}<span>${fTime(last.at)} · ${pagesTxt(last.pages.length)} · ${t("viaApp")} · ${last.no}</span></div>
        <div class="thumbs">${last.pages.map((s,i)=>`<img src="${s}" alt="${esc(ptitle(p.id))}, ${t("page",{n:i+1})}">`).join("")}</div>`
        : `<div class="meta">${t("notYet")}</div>`}
      ${actions}
    </article>`;
  }).join("");
  return `<main class="pad" id="main">
    ${head(t("staffTitle"), t("staffLead"))}
    <div class="staffinfo">${t("staffInfo")}</div>
    <section class="card"><h2>${t("caseTitle")}</h2>
      <dl class="kv"><dt>${t("rCase")}</dt><dd>${CLIENT.caseNo} · ${CLIENT.bg}</dd><dt>${t("client")}</dt><dd>${CLIENT.name}</dd>
        <dt>${t("deadline")}</dt><dd>${fDate(DEADLINE)}</dd><dt>Status</dt><dd>${t("case_"+c.key)}</dd></dl></section>
    <div class="list">${rows}</div>
    <button class="btn btn-p" data-act="role" data-v="client">${I.user}${t("staffBack")}</button>
  </main>`;
}

/* ===================== Rendern ===================== */
let lastScreenKey = "";
function render(){
  const el = $("#app");
  let body;
  if(!S.loggedIn) body = scrLogin();
  else if(S.role === "staff") body = scrStaff();
  else body = ({home:scrHome, checklist:scrChecklist, upload:scrUpload, review:scrReview, confirm:scrConfirm, mail:scrMail, thread:scrThread, more:scrMore, privacy:scrPrivacy, analog:scrAnalog, asset:scrAsset}[S.screen] || scrHome)();
  const showNav = S.loggedIn && S.role === "client";
  el.innerHTML = `<div class="shell ${showNav?"":"nonav"}">${header()}${body}</div>${showNav?nav():""}`;
  const key = S.role + S.screen + S.threadId;
  if(key !== lastScreenKey){ window.scrollTo(0,0); const h = $("#h1"); if(h && lastScreenKey) h.focus({preventScroll:true}); lastScreenKey = key; }
  renderPush();
}
function setLang(l){
  S.lang = l;
  document.documentElement.lang = l;
  document.documentElement.dir = LANGS[l].dir;
  document.title = t("app") + " – " + t("appSub");
  render();
}
function go(screen){ S.screen = screen; render(); }

/* Push-Benachrichtigung (simuliert) */
let pushTimer;
function showPush(p){ S.push = p; renderPush(); clearTimeout(pushTimer); pushTimer = setTimeout(()=>{ S.push = null; renderPush(); }, 9000); }
function renderPush(){
  const box = $("#push");
  if(!S.push){ box.innerHTML = ""; return; }
  box.innerHTML = `<div class="push" role="status" aria-label="${t("pushHint")}">
    <span class="mark">${I.logoW}</span>
    <button class="tx" data-act="pushOpen" data-test="push"><small>${t("appNow")}</small><b>${esc(S.push.title())}</b><span>${esc(S.push.body())}</span></button>
    <button class="x" data-act="pushClose" aria-label="${t("close")}">${I.x}</button></div>`;
}
let toastTimer;
function toast(msg){ $("#toast").innerHTML = `<div class="toast">${esc(msg)}</div>`; clearTimeout(toastTimer); toastTimer = setTimeout(()=>{$("#toast").innerHTML="";}, 2600); }

function reminderPush(){
  const m = missing();
  if(!m.length) return;
  showPush({
    title:() => t("pushRemTitle",{d:daysLeft()}),
    body:() => t("pushRemBody",{list:listJoin(missing().map(p=>ptitle(p.id))), date:fDate(DEADLINE)}),
    go:() => { S.role="client"; go("checklist"); }
  });
}

/* Upload-Logik */
function startUpload(id){ S.up = {proofId:id, pages:[], bad:null, checking:false}; S.reviewOk = false; go("upload"); }
function addImage(src, fromDemo){
  const u = S.up; u.checking = true; render();
  setTimeout(() => {
    S.attempts[u.proofId] = (S.attempts[u.proofId] || 0) + 1;
    u.checking = false;
    // Simulation: der erste Versuch beim Kontoauszug ist „unscharf“
    if(u.proofId === "ka" && S.attempts.ka === 1) u.bad = {src, reason:"badBlur", cssBlur:!fromDemo};
    else u.pages.push(src);
    render();
    const f = $("#fbBad"); if(f) f.scrollIntoView({block:"center"});
  }, 900);
}
function demoShot(){
  const u = S.up;
  const willFail = u.proofId === "ka" && !S.attempts.ka;
  addImage(makeDoc(u.proofId, willFail ? "blur" : null, u.pages.length+1), true);
}
function readFile(f){
  if(!f) return;
  const r = new FileReader();
  r.onload = () => addImage(r.result, false);
  r.readAsDataURL(f);
}
function submit(){
  const u = S.up, p = proof(u.proofId);
  const rec = {proofId:u.proofId, pages:u.pages.slice(), at:Date.now(), no:"EB-2026-" + String(Math.floor(1000+Math.random()*8999))};
  p.files.push({pages:rec.pages, at:rec.at, no:rec.no});
  p.status = "received";
  S.threads.push({id:"r"+rec.no, read:true, at:rec.at, subj:["mRecSubj",{proof:u.proofId}], msgs:[{from:"office", key:"mRecBody", p:{time:rec.at, no:rec.no, n:rec.pages.length}, at:rec.at}]});
  S.receipt = rec; S.up = null;
  go("confirm");
  if(rec.proofId === "ka" && !S.flags.payMsg && proof("pay").status === "open"){
    S.flags.payMsg = true;
    setTimeout(() => {
      const at = Date.now();
      S.threads.push({id:"t2", read:false, at, action:"pay", subj:["m2Subj"], msgs:[{from:"office", key:"m2Body", at}]});
      render();
      showPush({title:() => t("pushMsgTitle"), body:() => t("m2Subj"), go:() => { S.role="client"; openThread("t2"); }});
    }, 2500);
  }
}
function openThread(id){ const th = S.threads.find(x=>x.id===id); th.read = true; S.threadId = id; go("thread"); }

/* Copy */
function copyPhone(){
  const txt = t("phoneVal");
  const ok = () => toast(t("copied"));
  try{
    navigator.clipboard.writeText(txt).then(ok, () => selectPhone());
  }catch(e){ selectPhone(); }
}
function selectPhone(){ const el = $("#phoneNo"); if(!el) return; const r = document.createRange(); r.selectNodeContents(el); const s = getSelection(); s.removeAllRanges(); s.addRange(r); }

/* ===================== Ereignisse ===================== */
const A = {
  role:v => { S.role = v; S.staffReq = null; render(); if(v==="client" && S.pendingPush.length){ const p = S.pendingPush.shift(); setTimeout(()=>showPush(p), 400); } },
  go:v => { if(v==="upload" && !S.up) v="checklist"; go(v); },
  upload:v => startUpload(v),
  why:v => { S.open[v] = !S.open[v]; render(); const b = document.querySelector(`[data-act="why"][data-v="${v}"]`); if(b) b.focus(); },
  cam:() => { S.lastSrc="cam"; $("#inCam").click(); },
  file:() => { S.lastSrc="file"; $("#inFile").click(); },
  demo:() => { S.lastSrc="demo"; demoShot(); },
  retake:() => { S.up.bad = null; if(S.lastSrc==="demo") demoShot(); else { render(); (S.lastSrc==="file"?$("#inFile"):$("#inCam")).click(); } },
  rmPage:v => { S.up.pages.splice(+v,1); render(); },
  toReview:() => { S.reviewOk = false; go("review"); },
  submit:() => submit(),
  thread:v => openThread(v),
  logout:() => { S.loggedIn = false; S.screen = "login"; S.role="client"; render(); },
  copyPhone:() => copyPhone(),
  pushOpen:() => { const p = S.push; S.push = null; renderPush(); if(p && p.go) p.go(); },
  pushClose:() => { S.push = null; renderPush(); },
  ans:v => { const k = ["accounts","cash","car","ins"][S.asset.step]; S.asset[k] = v==="yes"; render(); },
  cnt:v => { S.asset.count = Math.min(9, Math.max(1, S.asset.count + (+v))); render(); },
  aStep:v => { S.asset.step = Math.max(0, S.asset.step + (+v)); render(); },
  aReset:() => { S.asset = {step:0, accounts:null, count:1, cash:null, car:null, ins:null}; render(); },
  sOk:v => { proof(v).status = "checked"; toast(t("staffSet",{s:t("st_checked")})); render(); },
  sReq:v => { S.staffReq = v; S.staffReason = "r_blur"; render(); },
  sCancel:() => { S.staffReq = null; render(); },
  sSend:v => {
    const at = Date.now(), id = "q"+at, reason = S.staffReason;
    proof(v).status = "resubmit"; S.staffReq = null;
    S.threads.push({id, read:false, at, action:v, subj:["mResSubj",{proof:v}], msgs:[{from:"office", key:"mResBody", p:{reason}, at}]});
    S.pendingPush.push({title:() => t("pushMsgTitle"), body:() => t("mResSubj",{proof:ptitle(v)}), go:() => openThread(id)});
    toast(t("staffSet",{s:t("st_resubmit")})); render();
  },
  sRemind:v => {
    const at = Date.now(), id = "m"+at;
    S.reminded[v] = true;
    S.threads.push({id, read:false, at, action:v, subj:["mRemSubj",{proof:v}], msgs:[{from:"office", key:"mRemBody", p:{date:+DEADLINE}, at}]});
    S.pendingPush.push({title:() => t("mRemSubj",{proof:ptitle(v)}), body:() => t("mRemBody",{date:fDate(DEADLINE)}), go:() => openThread(id)});
    toast(t("reminded")); render();
  }
};
document.addEventListener("click", e => {
  const el = e.target.closest("[data-act]");
  if(!el || el.disabled) return;
  const f = A[el.dataset.act]; if(f){ e.preventDefault(); f(el.dataset.v, el); }
});
document.addEventListener("change", e => {
  if(e.target.id === "langSel") setLang(e.target.value);
  else if(e.target.id === "revOk"){ S.reviewOk = e.target.checked; const b = document.querySelector('[data-act="submit"]'); if(b) b.disabled = !S.reviewOk; }
  else if(e.target.name === "reason") S.staffReason = e.target.value;
  else if(e.target.id === "inCam" || e.target.id === "inFile"){ readFile(e.target.files[0]); e.target.value = ""; }
});
document.addEventListener("submit", e => {
  e.preventDefault();
  if(e.target.id === "loginForm"){
    S.loggedIn = true; S.screen = "home"; render();
    if(!S.flags.remPush){ S.flags.remPush = true; setTimeout(reminderPush, 1500); }
  } else if(e.target.id === "replyForm"){
    const ta = $("#replyText"), txt = ta.value.trim();
    if(!txt){ toast(t("emptyReply")); ta.focus(); return; }
    const th = S.threads.find(x => x.id === S.threadId), at = Date.now();
    th.msgs.push({from:"you", text:txt, at}); th.at = at;
    render(); toast(t("msgSent"));
    const tid = th.id;
    setTimeout(() => { const t2 = S.threads.find(x=>x.id===tid); t2.msgs.push({from:"office", key:"autoReply", at:Date.now()}); if(!(S.screen==="thread" && S.threadId===tid)) t2.read = false; render(); }, 1400);
  }
});
setInterval(() => { const c = $("#cd"); if(c) c.textContent = cdText(); }, 20000);

setLang("de");
})();
</script>
</body>
</html>
