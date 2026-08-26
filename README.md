<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>RisingAMP</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Manrope:wght@400;500;600;700;800&family=DM+Serif+Display&display=swap" rel="stylesheet">
<style>
  :root{
    --steel-900:#17181C; --steel-800:#1F2127; --steel-700:#2A2D34;
    --ink:#1C1E23; --slate-600:#565B64; --slate-500:#6B7079; --slate-400:#8A9099;
    --hairline:#E7E9EC; --canvas:#F5F6F8; --surface:#FFFFFF;
    --accent:#E85D1A; --accent-600:#C64E12; --accent-tint:#FCEEE4;
    --pos:#2E7D57; --pos-tint:#E7F1EC; --warn:#B7862B; --warn-tint:#F7F0DF; --neg:#C0392B; --neg-tint:#F9E9E7;
    --c-labour:#5E82A6; --c-trade:#C08A3E; --c-materials:#B5654A; --c-service:#4E8C82; --c-equipment:#7E9B67;
    --c-yard:#5E82A6; --c-out:#E85D1A; --c-dam:#B7862B;
    --radius:12px; --shadow:0 1px 2px rgba(23,24,28,.05),0 2px 6px rgba(23,24,28,.04);
    --ui:'Manrope',system-ui,-apple-system,sans-serif;
    --serif:'DM Serif Display',serif;
  }
  *{box-sizing:border-box;margin:0;padding:0}
  html{scroll-behavior:smooth}
  body{font-family:var(--ui);background:var(--surface);color:var(--ink);-webkit-font-smoothing:antialiased;line-height:1.55}
  .tab{font-variant-numeric:tabular-nums}
  .wrap{max-width:1120px;margin:0 auto;padding:0 24px}
  .eyebrow{font-size:14px;font-weight:700;letter-spacing:.13em;text-transform:uppercase;color:var(--accent)}
  a{color:inherit}

  /* NAV */
  .nav{position:sticky;top:0;z-index:50;background:rgba(255,255,255,.9);backdrop-filter:blur(10px);border-bottom:1px solid var(--hairline)}
  .nav .row{display:flex;align-items:center;justify-content:space-between;height:66px}
  .logo{font-family:var(--serif);font-size:20px;font-weight:400;letter-spacing:-.005em;text-decoration:none}
  .nav .links{display:flex;align-items:center;gap:28px}
  .nav .links a{font-size:13.5px;font-weight:600;color:var(--slate-600);text-decoration:none}
  .nav .links a:hover{color:var(--ink)}
  .btn{display:inline-flex;align-items:center;gap:8px;font-family:var(--ui);font-weight:700;font-size:13.5px;padding:10px 18px;border-radius:10px;border:0;cursor:pointer;text-decoration:none}
  .btn.primary{background:var(--accent);color:#fff}
  .btn.primary:hover{background:var(--accent-600)}
  .btn.ghost{background:transparent;color:#fff;border:1px solid rgba(255,255,255,.28)}
  .btn.ghostdark{background:transparent;color:var(--ink);border:1px solid var(--hairline)}
  .btn.lg{padding:14px 24px;font-size:15px;border-radius:11px}

  /* HERO */
  .hero{background:var(--steel-900);color:#fff}
  .hero .wrap{padding:88px 24px 0;text-align:center}
  .wordmark{font-family:var(--serif);font-weight:400;font-size:88px;letter-spacing:-.01em;line-height:1;color:#fff}
  .hero h1{font-family:var(--ui);font-size:26px;font-weight:700;letter-spacing:-.015em;line-height:1.3;max-width:620px;margin:22px auto 0;color:#E4E6EA}
  .hero .lead{font-size:16px;color:#9CA3AD;margin:18px auto 0;max-width:540px;line-height:1.65}
  .hero .cta{display:flex;gap:12px;margin:30px auto 0;justify-content:center;flex-wrap:wrap}
  .hero .micro{margin-top:16px;font-size:12.5px;color:#767D87}
  .heroshot{margin-top:52px;position:relative}
  .win{background:var(--surface);border:1px solid #000;border-radius:16px 16px 0 0;overflow:hidden;box-shadow:0 -20px 60px rgba(0,0,0,.4);text-align:left;color:var(--ink)}
  .chrome{display:flex;align-items:center;gap:8px;padding:11px 15px;background:#0F1013;border-bottom:1px solid #000}
  .chrome i{width:11px;height:11px;border-radius:50%;background:#3A3D44;display:block}
  .chrome span{margin-left:10px;font-size:11px;color:#6E747D}

  /* app shell used inside shots */
  .app{display:flex;background:var(--canvas)}
  .side{width:190px;background:var(--steel-900);color:#C9CDD4;flex-shrink:0;padding:14px 10px;display:flex;flex-direction:column}
  .side .b{padding:6px 8px 12px;font-family:var(--serif);font-weight:400;font-size:16px;color:#fff}
  .switcher{display:flex;background:var(--steel-800);border-radius:8px;padding:3px;margin:0 6px 12px}
  .switcher span{flex:1;text-align:center;font-size:10.5px;font-weight:700;padding:5px 0;border-radius:6px;color:#8A9099}
  .switcher span.on{background:var(--accent);color:#fff}
  .side a{display:flex;align-items:center;gap:10px;padding:7px 9px;border-radius:7px;color:#B4B9C1;font-size:12.5px;font-weight:500;text-decoration:none;margin-bottom:1px;position:relative}
  .side a svg{width:15px;height:15px;stroke-width:1.6;opacity:.9}
  .side a.on{background:var(--steel-800);color:#fff}
  .side a.on::before{content:"";position:absolute;left:-10px;top:7px;bottom:7px;width:3px;border-radius:0 3px 3px 0;background:var(--accent)}
  .main{flex:1;padding:22px;min-width:0}
  .mhead{display:flex;justify-content:space-between;align-items:flex-start;margin-bottom:16px}
  .mhead h4{font-size:20px;font-weight:800;letter-spacing:-.02em}
  .mhead p{font-size:12.5px;color:var(--slate-600)}
  .seg{display:inline-flex;background:#fff;border:1px solid var(--hairline);border-radius:8px;padding:3px}
  .seg span{font-size:11.5px;font-weight:600;color:var(--slate-600);padding:5px 12px;border-radius:6px}
  .seg span.on{background:var(--accent);color:#fff}
  .banner{display:flex;align-items:center;gap:13px;background:#fff;border:1px solid var(--hairline);border-left:3px solid var(--pos);border-radius:11px;padding:13px 16px;box-shadow:var(--shadow);margin-bottom:14px}
  .banner .bd{width:30px;height:30px;border-radius:8px;background:var(--pos-tint);color:var(--pos);display:flex;align-items:center;justify-content:center;flex-shrink:0}
  .banner .bd svg{width:16px;height:16px;stroke-width:2}
  .banner b{font-size:13px;font-weight:800}
  .banner p{font-size:12px;color:var(--slate-600)}
  .banner p .g{color:var(--pos);font-weight:700}
  .stat4{display:flex;gap:12px}
  .stat4 .stat{flex:1;min-width:0}
  .stat{position:relative;background:#fff;border:1px solid var(--hairline);border-radius:11px;padding:14px;box-shadow:var(--shadow)}
  .stat.pr::before{content:"";position:absolute;left:14px;right:14px;top:0;height:2px;background:var(--accent);border-radius:0 0 2px 2px}
  .stat .l{font-size:11px;color:var(--slate-400);font-weight:600}
  .stat .f{font-size:20px;font-weight:800;letter-spacing:-.02em;margin:7px 0 5px}
  .stat .s{font-size:11px;color:var(--slate-600)}
  .stat .s .g{color:var(--pos);font-weight:700}

  /* SECTIONS */
  section{padding:88px 0}
  .sec-head{max-width:640px;margin:0 auto 52px;text-align:center}
  .sec-head h2{font-size:32px;font-weight:800;letter-spacing:-.025em;margin:10px 0 12px;line-height:1.18}
  .sec-head p{font-size:16px;color:var(--slate-600);line-height:1.6}

  .problem{background:var(--canvas)}
  .pgrid{display:flex;gap:20px}
  .pgrid .pcard{flex:1;min-width:0}
  .pcard{background:#fff;border:1px solid var(--hairline);border-radius:16px;padding:30px;box-shadow:var(--shadow)}
  .pcard .ic{width:44px;height:44px;border-radius:11px;background:var(--accent-tint);color:var(--accent);display:flex;align-items:center;justify-content:center;margin-bottom:16px}
  .pcard .ic svg{width:22px;height:22px;stroke-width:1.7}
  .pcard h3{font-size:19px;font-weight:800;margin-bottom:8px}
  .pcard p{font-size:14px;color:var(--slate-600);line-height:1.6}
  .pcard ul{list-style:none;margin-top:14px}
  .pcard li{display:flex;gap:9px;font-size:13.5px;color:var(--ink);padding:5px 0;font-weight:600}
  .pcard li svg{width:16px;height:16px;stroke-width:1.8;color:var(--accent);flex-shrink:0;margin-top:2px}

  /* FEATURE ROWS */
  .feat{display:flex;gap:52px;align-items:center;margin-bottom:64px}
  .feat .copy{flex:1 1 0;min-width:0}
  .feat .shot{flex:1.1 1 0;min-width:0}
  .feat:last-child{margin-bottom:0}
  .feat.rev .copy{order:2}
  .copy .eyebrow{margin-bottom:12px;display:block}
  .copy h3{font-size:26px;font-weight:800;letter-spacing:-.02em;line-height:1.2;margin-bottom:14px}
  .copy p{font-size:15px;color:var(--slate-600);line-height:1.65;margin-bottom:18px}
  .copy ul{list-style:none}
  .copy li{display:flex;gap:10px;font-size:14.5px;padding:7px 0;font-weight:600}
  .copy li svg{width:18px;height:18px;stroke-width:2.4;color:var(--pos);flex-shrink:0;margin-top:2px}
  .shot{background:#fff;border:1px solid var(--hairline);border-radius:16px;box-shadow:0 14px 40px rgba(23,24,28,.10);overflow:hidden}
  .shotpad{padding:20px}

  .panel{background:#fff;border:1px solid var(--hairline);border-radius:11px;padding:16px 18px;box-shadow:var(--shadow)}
  .panel h5{font-size:13px;font-weight:800;display:flex;justify-content:space-between;align-items:center;margin-bottom:6px}
  .panel h5 .cnt{font-size:10.5px;font-weight:700;color:var(--warn);background:var(--warn-tint);padding:2px 8px;border-radius:20px}
  .todo .t{display:flex;gap:11px;align-items:center;padding:11px 0;border-bottom:1px solid var(--hairline)}
  .todo .t:last-child{border-bottom:0}
  .todo .ic{width:32px;height:32px;border-radius:8px;background:var(--canvas);border:1px solid var(--hairline);display:flex;align-items:center;justify-content:center;color:var(--slate-600);flex-shrink:0}
  .todo .ic.w{background:var(--warn-tint);border-color:transparent;color:var(--warn)}.todo .ic.n{background:var(--neg-tint);border-color:transparent;color:var(--neg)}
  .todo .ic svg{width:15px;height:15px;stroke-width:1.7}
  .todo b{font-size:12.5px;font-weight:700;display:block}
  .todo small{font-size:11px;color:var(--slate-400)}
  .capcard{background:var(--canvas);border:1px solid var(--hairline);border-radius:12px;padding:16px}
  .capcard .ch{display:flex;align-items:center;gap:10px;margin-bottom:12px}
  .capcard .ci{width:32px;height:32px;border-radius:8px;background:#fff;border:1px solid var(--hairline);display:flex;align-items:center;justify-content:center;color:var(--slate-600)}
  .capcard .ci svg{width:16px;height:16px;stroke-width:1.7}
  .capcard .ch b{font-size:13px;font-weight:800}.capcard .ch small{font-size:11px;color:var(--slate-400);display:block}
  .fld{display:flex;justify-content:space-between;align-items:center;background:#fff;border:1px solid var(--hairline);border-radius:9px;padding:10px 12px;margin-bottom:7px}
  .fld .fk{font-size:10.5px;color:var(--slate-400);font-weight:700}
  .fld .fv{font-size:13.5px;font-weight:700}
  .fld .fv.cat{display:flex;align-items:center;gap:7px}.fld .fv.cat .d{width:8px;height:8px;border-radius:50%;background:var(--c-materials)}
  .fld.flag{border-color:var(--warn);background:var(--warn-tint)}
  .fld.flag .chk{font-size:10.5px;font-weight:700;color:var(--warn);display:flex;align-items:center;gap:5px}.fld.flag .chk svg{width:12px;height:12px;stroke-width:2.4}
  .invtable{width:100%;border-collapse:collapse}
  .invtable th{font-size:10px;text-transform:uppercase;letter-spacing:.05em;color:var(--slate-400);text-align:left;padding:8px 6px;border-bottom:1px solid var(--hairline);font-weight:700}
  .invtable td{font-size:12.5px;padding:11px 6px;border-bottom:1px solid var(--hairline)}
  .invtable td:last-child,.invtable th:last-child{text-align:right}
  .pill{display:inline-flex;align-items:center;gap:5px;font-size:10.5px;font-weight:700;padding:3px 9px;border-radius:20px}
  .pill .d{width:6px;height:6px;border-radius:50%}
  .p-ok{color:var(--pos);background:var(--pos-tint)}.p-ok .d{background:var(--pos)}
  .p-w{color:var(--warn);background:var(--warn-tint)}.p-w .d{background:var(--warn)}
  .p-r{color:var(--neg);background:var(--neg-tint)}.p-r .d{background:var(--neg)}

  .gsearch{display:flex;align-items:center;gap:9px;border:1px solid var(--accent);box-shadow:0 0 0 3px var(--accent-tint);border-radius:9px;padding:9px 12px;margin-bottom:12px;max-width:260px}
  .gsearch svg{width:15px;height:15px;stroke-width:1.7;color:var(--slate-400)}.gsearch b{font-size:13px}.gsearch .k{margin-left:auto;font-size:10px;color:var(--slate-400)}
  .grow{display:flex;gap:10px;align-items:center;padding:11px 0;border-bottom:1px solid var(--hairline)}
  .grow:last-child{border-bottom:0}
  .grow .cn{flex:1.5 1 0;min-width:0}
  .grow .cn b{font-size:12.5px;font-weight:700;display:block}.grow .cn small{font-size:10.5px;color:var(--slate-400)}
  .grow .gmid{flex:2 1 0;min-width:0}
  .sbar{display:flex;height:8px;border-radius:5px;overflow:hidden;background:#EEF0F2}.sbar i{display:block;height:100%}
  .sc{font-size:9.5px;font-weight:700;color:var(--slate-600);background:var(--canvas);border:1px solid var(--hairline);border-radius:4px;padding:1px 5px;margin-right:3px}
  .gval{flex:.8 1 0;text-align:right;font-size:12.5px;font-weight:800}
  .skey{display:flex;gap:12px;font-size:10.5px;color:var(--slate-500);font-weight:600;margin-top:10px}
  .skey span{display:inline-flex;align-items:center;gap:5px}.skey .d{width:6px;height:6px;border-radius:50%}
  .hire{border:1px dashed #E0C9A0;background:#FDFAF3;border-radius:10px;padding:14px 16px}
  .hire .hr{display:flex;justify-content:space-between;font-size:13px;padding:6px 0}
  .hire .hr .k{color:var(--slate-600)}.hire .hr .v{font-weight:700}.hire .hr .v.w{color:var(--warn)}
  .dkt{display:flex;align-items:center;gap:11px;padding:10px 0;border-bottom:1px solid var(--hairline);font-size:12.5px}
  .dkt:last-child{border-bottom:0}
  .dkt .dir{width:28px;height:28px;border-radius:8px;display:flex;align-items:center;justify-content:center;flex-shrink:0}
  .dkt .dir.out{background:var(--accent-tint);color:var(--accent)}.dkt .dir.in{background:var(--pos-tint);color:var(--pos)}
  .dkt .dir svg{width:14px;height:14px;stroke-width:2}
  .dkt b{font-weight:700;display:block}.dkt small{color:var(--slate-400);font-size:10.5px}
  .certrow{display:flex;align-items:center;gap:11px;padding:11px 0;border-bottom:1px solid var(--hairline)}
  .certrow:last-child{border-bottom:0}
  .certrow .ic{width:32px;height:32px;border-radius:8px;background:var(--canvas);border:1px solid var(--hairline);display:flex;align-items:center;justify-content:center;color:var(--slate-600)}
  .certrow .ic svg{width:15px;height:15px;stroke-width:1.7}
  .certrow b{font-size:12.5px;font-weight:700;display:block}.certrow small{font-size:10.5px;color:var(--slate-400)}

  /* dark band */
  .band{background:var(--steel-900);color:#fff;text-align:center}
  .band .wrap{padding:80px 24px}
  .band .eyebrow{color:#F2A176}
  .band h2{font-size:32px;font-weight:800;letter-spacing:-.025em;max-width:680px;margin:12px auto 14px;line-height:1.2}
  .band p{font-size:16px;color:#9CA3AD;max-width:580px;margin:0 auto;line-height:1.6}
  .bigstat{font-family:var(--serif);font-size:72px;font-weight:400;color:#F2A176;line-height:1}
  .bigstat + h2{margin-top:16px}

  /* mobile section */
  .mobile{background:var(--canvas)}
  .mobwrap{display:flex;gap:52px;align-items:center}
  .mobwrap>*{flex:1 1 0;min-width:0}
  .phone{width:284px;background:#0E0F12;border-radius:42px;padding:10px;box-shadow:0 22px 50px rgba(23,24,28,.22);margin:0 auto}
  .pscreen{position:relative;background:var(--canvas);border-radius:33px;overflow:hidden;height:560px}
  .island{position:absolute;top:8px;left:50%;transform:translateX(-50%);width:90px;height:24px;background:#0E0F12;border-radius:15px;z-index:5}
  .mstatus{display:flex;justify-content:space-between;padding:11px 22px 0;font-size:11.5px;font-weight:700}
  .mbody{padding:16px 15px;height:calc(100% - 32px);display:flex;flex-direction:column}
  .mtop{display:flex;justify-content:space-between;align-items:center;margin-bottom:11px}
  .mtop b{font-size:14px;font-weight:800}
  .mc{background:#fff;border:1px solid var(--hairline);border-radius:11px;padding:12px;margin-bottom:8px}
  .mr{display:flex;justify-content:space-between;font-size:12px;padding:6px 0;border-bottom:1px solid var(--hairline)}
  .mr:last-child{border-bottom:0}.mr .k{color:var(--slate-600);font-weight:600}.mr .v{font-weight:700}.mr .v .o{color:var(--slate-400);font-weight:600}
  .mr.short{background:var(--neg-tint);margin:0 -12px;padding:8px 12px;border-radius:8px;border-bottom:0}.mr.short .k{color:var(--neg);font-weight:700}.mr.short .v{color:var(--neg)}
  .mvar{background:#fff;border:1px solid var(--neg);border-radius:11px;padding:12px;margin-bottom:8px}
  .mvar b{font-size:12px;color:var(--neg);display:block}.mvar p{font-size:11px;color:var(--slate-600);margin:4px 0 9px}
  .mvb{display:flex;gap:7px}.mvb>div{flex:1;text-align:center;font-family:var(--ui);font-size:11px;font-weight:700;padding:8px;border-radius:8px;cursor:pointer}
  .mvb .a{background:var(--accent);color:#fff;border:0}.mvb .b{background:#fff;border:1px solid var(--hairline)}
  .msig{background:#fff;border:1px dashed #C9CDD4;border-radius:11px;height:54px;display:flex;align-items:center;justify-content:center;color:var(--slate-400);font-size:11px;font-weight:600;margin-bottom:8px}
  .msave{width:100%;text-align:center;background:var(--accent);color:#fff;border:0;font-family:var(--ui);font-weight:700;font-size:12.5px;padding:11px;border-radius:9px;margin-top:auto}

  /* trust */
  .trust{text-align:center}
  .trustquote{max-width:720px;margin:0 auto}
  .trustquote .q{font-size:24px;font-weight:700;letter-spacing:-.015em;line-height:1.4;color:var(--ink)}
  .trustquote .by{font-size:13.5px;color:var(--slate-500);margin-top:20px;font-weight:600}
  .valgrid{display:flex;gap:16px;margin-top:52px}
  .valgrid .val{flex:1;min-width:0}
  .val{background:var(--surface);border:1px solid var(--hairline);border-radius:14px;padding:22px;text-align:left}
  .val .ic{width:38px;height:38px;border-radius:10px;background:var(--canvas);border:1px solid var(--hairline);display:flex;align-items:center;justify-content:center;color:var(--accent);margin-bottom:14px}
  .val .ic svg{width:19px;height:19px;stroke-width:1.7}
  .val b{font-size:14px;font-weight:800;display:block;margin-bottom:5px}
  .val p{font-size:12.5px;color:var(--slate-600);line-height:1.55}

  /* pricing */
  .pricing{background:var(--canvas)}
  .prices{display:flex;gap:22px;max-width:820px;margin:0 auto}
  .prices .price{flex:1;min-width:0}
  .price{background:#fff;border:1px solid var(--hairline);border-radius:18px;padding:32px;box-shadow:var(--shadow);position:relative;display:flex;flex-direction:column}
  .price.best{border:2px solid var(--accent);box-shadow:0 18px 50px rgba(232,93,26,.14)}
  .price .tag{position:absolute;top:-13px;left:32px;background:var(--accent);color:#fff;font-size:11px;font-weight:800;letter-spacing:.04em;text-transform:uppercase;padding:5px 12px;border-radius:20px}
  .price .pn{font-size:13px;font-weight:800;letter-spacing:.02em;text-transform:uppercase;color:var(--slate-500)}
  .price .amt{display:flex;align-items:baseline;gap:6px;margin:14px 0 4px}
  .price .amt .n{font-size:42px;font-weight:800;letter-spacing:-.03em}
  .price .amt .per{font-size:14px;color:var(--slate-500);font-weight:600}
  .price .desc{font-size:13.5px;color:var(--slate-600);margin-bottom:22px;min-height:40px}
  .price ul{list-style:none;margin-bottom:24px;flex:1}
  .price li{display:flex;gap:10px;font-size:13.5px;padding:7px 0;font-weight:600}
  .price li svg{width:17px;height:17px;stroke-width:2.6;color:var(--pos);flex-shrink:0;margin-top:2px}
  .price li.add{color:var(--accent)}.price li.add svg{color:var(--accent)}
  .price .btn{width:100%;display:flex;justify-content:center;margin-top:auto}
  .price .foot{font-size:11.5px;color:var(--slate-400);text-align:center;margin-top:14px}
  .pricenote{text-align:center;font-size:13.5px;color:var(--slate-600);margin-top:26px}
  .pricenote b{color:var(--ink)}

  /* faq */
  .faq{max-width:720px;margin:0 auto}
  .qa{border-bottom:1px solid var(--hairline);padding:22px 0}
  .qa h4{font-size:16px;font-weight:800;margin-bottom:8px}
  .qa p{font-size:14px;color:var(--slate-600);line-height:1.6}

  /* final */
  .final{background:var(--steel-900);color:#fff;text-align:center}
  .final .wrap{padding:88px 24px}
  .final h2{font-size:34px;font-weight:800;letter-spacing:-.025em;margin-bottom:14px}
  .final p{font-size:16px;color:#9CA3AD;max-width:500px;margin:0 auto 30px;line-height:1.6}
  .final .cta{display:flex;gap:12px;justify-content:center;flex-wrap:wrap}

  footer{background:var(--steel-900);color:#8A9099;padding:36px 0}
  footer .row{display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:16px}
  footer .logo{color:#fff}
  footer .fl{display:flex;gap:22px;font-size:13px}
  footer a{text-decoration:none;color:#8A9099}
  footer a:hover{color:#fff}
  footer .cr{font-size:12px;color:#5B606A}

  @page{ size:1168px 1650px; margin:0; }
  @media print{
    .nav{display:none}
    *{ -webkit-print-color-adjust:exact !important; print-color-adjust:exact !important; }
    body{padding:0}
    section{padding:52px 0}
    .hero .wrap{padding-top:52px}
    .pcard,.feat,.shot,.price,.val,.qa,.stat,.panel,.win,.phone,.trustquote{break-inside:avoid;page-break-inside:avoid}
  }

  @media(max-width:860px){
    .nav .links{display:none}
    .wordmark{font-size:52px}
    .hero h1{font-size:22px}
    .pgrid,.feat,.mobwrap,.prices,.valgrid,.stat4{flex-direction:column}
    .feat{gap:26px}.feat.rev .copy{order:0}
    section{padding:60px 0}
  }
</style>
</head>
<body>

<!-- NAV -->
<div class="nav"><div class="wrap"><div class="row">
  <a class="logo" href="#">RisingAMP</a>
  <div class="links">
    <a href="#construction">For builders</a>
    <a href="#scaffold">For scaffolders</a>
    <a href="#pricing">Pricing</a>
    <a class="btn primary" href="#pricing">Get started</a>
  </div>
</div></div></div>

<!-- HERO -->
<header class="hero"><div class="wrap">
  <div class="wordmark">RisingAMP</div>
  <h1>Job costing for builders. A gear ledger for scaffolders.</h1>
  <p class="lead">Track what a job is actually costing you, or keep count of every piece of scaffold you own. One login, one app. Built inside a real construction business and used on real jobs for two years before we ever sold it.</p>
  <div class="cta">
    <a class="btn primary lg" href="#pricing">Get started</a>
    <a class="btn ghost lg" href="#construction">See how it works</a>
  </div>
  <p class="micro">From $50 a month. Cancel any time.</p>

  <div class="heroshot"><div class="win">
    <div class="chrome"><i></i><i></i><i></i><span>risingamp.com.au</span></div>
    <div class="app">
      <aside class="side">
        <div class="b">RisingAMP</div>
        <div class="switcher"><span class="on">Expenses</span><span>Scaffold</span></div>
        <a class="on"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><rect x="3" y="3" width="7" height="7" rx="1.5"/><rect x="14" y="3" width="7" height="7" rx="1.5"/><rect x="3" y="14" width="7" height="7" rx="1.5"/><rect x="14" y="14" width="7" height="7" rx="1.5"/></svg>Dashboard</a>
        <a><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><circle cx="12" cy="12" r="9"/><path d="M12 8v8M8 12h8"/></svg>Add expense</a>
        <a><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="M6 3h9l3 3v15H6z"/><path d="M9 9h6M9 13h6M9 17h4"/></svg>Invoices</a>
        <a><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><circle cx="12" cy="12" r="9"/><path d="M12 7v5l3 2"/></svg>History</a>
      </aside>
      <div class="main">
        <div class="mhead"><div><div class="eyebrow" style="color:var(--slate-400);font-size:11px">72 Centenary Dr</div><h4>Dashboard</h4></div><div class="seg"><span>Week</span><span class="on">Month</span><span>Quarter</span></div></div>
        <div class="banner"><div class="bd"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="m5 13 4 4L19 7"/></svg></div><div><b>On track</b><p>You are making <span class="g">$97,033 (11.9%)</span> on this job, and nothing is overdue.</p></div></div>
        <div class="stat4">
          <div class="stat"><div class="l">Contract</div><div class="f tab">$812,500</div><div class="s">Fully paid</div></div>
          <div class="stat"><div class="l">Cost to date</div><div class="f tab">$715,467</div><div class="s">119 expenses</div></div>
          <div class="stat pr"><div class="l">Margin</div><div class="f tab">$97,033</div><div class="s"><span class="g">11.9%</span> and holding</div></div>
          <div class="stat"><div class="l">This month</div><div class="f tab">$20,356</div><div class="s">Spend so far</div></div>
        </div>
      </div>
    </div>
  </div></div>
</div></header>

<!-- PROBLEM -->
<section class="problem" id="problem"><div class="wrap">
  <div class="sec-head">
    <div class="eyebrow">The problem</div>
    <h2>If it's only in your head, it's already costing you</h2>
    <p>Most builders and scaffolders run a business worth hundreds of thousands of dollars on memory, a notebook, and a spreadsheet that stopped matching reality months ago.</p>
  </div>
  <div class="pgrid">
    <div class="pcard">
      <div class="ic"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="M3 3v18h18"/><path d="m7 14 4-4 3 3 5-6"/></svg></div>
      <h3>Builders</h3>
      <p>You can see what you've spent. What you can't see is whether the job is actually making you money.</p>
      <ul>
        <li><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="M12 9v4M12 17h.01M10.3 3.9 1.8 18a2 2 0 0 0 1.7 3h17a2 2 0 0 0 1.7-3L13.7 3.9a2 2 0 0 0-3.4 0Z"/></svg>No idea if a job is making or losing money until it's over</li>
        <li><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="M12 9v4M12 17h.01M10.3 3.9 1.8 18a2 2 0 0 0 1.7 3h17a2 2 0 0 0 1.7-3L13.7 3.9a2 2 0 0 0-3.4 0Z"/></svg>Receipts lost, expenses uncategorised, invoices with no date</li>
        <li><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="M12 9v4M12 17h.01M10.3 3.9 1.8 18a2 2 0 0 0 1.7 3h17a2 2 0 0 0 1.7-3L13.7 3.9a2 2 0 0 0-3.4 0Z"/></svg>Numbers you can't quite trust, so you don't act on them</li>
      </ul>
    </div>
    <div class="pcard">
      <div class="ic"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="M4 20V8l8-5 8 5v12M4 12h16M8 8v12M16 8v12"/></svg></div>
      <h3>Scaffolders</h3>
      <p>Hundreds of thousands of dollars in steel, spread across sites, with no easy way to keep track of it all.</p>
      <ul>
        <li><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="M12 9v4M12 17h.01M10.3 3.9 1.8 18a2 2 0 0 0 1.7 3h17a2 2 0 0 0 1.7-3L13.7 3.9a2 2 0 0 0-3.4 0Z"/></svg>Gear that walks off site and never comes back</li>
        <li><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="M12 9v4M12 17h.01M10.3 3.9 1.8 18a2 2 0 0 0 1.7 3h17a2 2 0 0 0 1.7-3L13.7 3.9a2 2 0 0 0-3.4 0Z"/></svg>Hire weeks that tick past the off-hire and never get billed</li>
        <li><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="M12 9v4M12 17h.01M10.3 3.9 1.8 18a2 2 0 0 0 1.7 3h17a2 2 0 0 0 1.7-3L13.7 3.9a2 2 0 0 0-3.4 0Z"/></svg>The 30-day inspection or handover cert nobody can find</li>
      </ul>
    </div>
  </div>
</div></section>

<!-- CONSTRUCTION -->
<section id="construction"><div class="wrap">
  <div class="sec-head">
    <div class="eyebrow">For builders</div>
    <h2>Everything you need to know about a job, at a glance</h2>
    <p>You're already entering the numbers. RisingAMP works out what they mean, so you don't have to add it all up yourself.</p>
  </div>

  <div class="feat">
    <div class="copy">
      <span class="eyebrow">See your margin</span>
      <h3>See if a job is actually making you money</h3>
      <p>Add up what a job brings in, subtract what it costs, and there's your margin, in dollars and in percent, right on the dashboard. One line tells you straight away if you're on track.</p>
      <ul>
        <li><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="m5 13 4 4L19 7"/></svg>On track, margin at risk, or over budget, in one line</li>
        <li><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="m5 13 4 4L19 7"/></svg>Live margin as costs come in, not a surprise at the end</li>
        <li><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="m5 13 4 4L19 7"/></svg>Every job in one place, so you see which one is bleeding</li>
      </ul>
    </div>
    <div class="shot"><div class="shotpad">
      <div class="banner" style="margin-bottom:12px"><div class="bd"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="m5 13 4 4L19 7"/></svg></div><div><b>On track</b><p>Making <span class="g">$97,033 (11.9%)</span>, nothing overdue.</p></div></div>
      <div class="stat4" style="flex-wrap:wrap">
        <div class="stat pr"><div class="l">Margin</div><div class="f tab">$97,033</div><div class="s"><span class="g">11.9%</span> and holding</div></div>
        <div class="stat"><div class="l">Cost to date</div><div class="f tab">$715,467</div><div class="s">of $812,500 contract</div></div>
      </div>
    </div></div>
  </div>

  <div class="feat rev">
    <div class="copy">
      <span class="eyebrow">What needs you today</span>
      <h3>A short list of what actually needs your attention</h3>
      <p>Instead of a wall of numbers, RisingAMP checks your job for the things worth fixing, like an invoice with no date, or an expense with no receipt, and gives you a short list. Tap one and go straight to the fix.</p>
      <ul>
        <li><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="m5 13 4 4L19 7"/></svg>Turns silent data problems into a tidy to-do list</li>
        <li><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="m5 13 4 4L19 7"/></svg>Keeps your books clean enough to hand your accountant</li>
      </ul>
    </div>
    <div class="shot"><div class="shotpad"><div class="panel todo">
      <h5>What needs you today <span class="cnt">3</span></h5>
      <div class="t"><span class="ic w"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><rect x="3" y="5" width="18" height="16" rx="2"/><path d="M3 9h18M8 3v4M16 3v4"/></svg></span><div><b>3 invoices are missing dates</b><small>They can't age or be reported until dated</small></div></div>
      <div class="t"><span class="ic"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><rect x="3" y="6" width="18" height="14" rx="2"/><circle cx="12" cy="13" r="3.2"/></svg></span><div><b>2 expenses have no receipt</b><small>$4,120 across Materials and Trade</small></div></div>
      <div class="t"><span class="ic"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="M4 19V5M4 19h16M8 14l3-4 3 2 4-6"/></svg></span><div><b>Materials spend up 18% this month</b><small>Mostly bricks and LED, worth a look</small></div></div>
    </div></div></div>
  </div>

  <div class="feat">
    <div class="copy">
      <span class="eyebrow">Snap a receipt</span>
      <h3>Log an expense in seconds, from the ute</h3>
      <p>Take a photo of the receipt and RisingAMP reads off the vendor, the amount and the category for you. If it's not sure about something, like the date, it asks you to check rather than guessing.</p>
      <ul>
        <li><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="m5 13 4 4L19 7"/></svg>No forms, just a photo and a tap</li>
        <li><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="m5 13 4 4L19 7"/></svg>Flags what it's unsure of instead of guessing</li>
      </ul>
    </div>
    <div class="shot"><div class="shotpad"><div class="capcard">
      <div class="ch"><span class="ci"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><rect x="3" y="6" width="18" height="14" rx="2"/><circle cx="12" cy="13" r="3.2"/><path d="M8 6l1.5-2h5L16 6"/></svg></span><div><b>Receipt read</b><small>Bunnings Warehouse</small></div></div>
      <div class="fld"><span class="fk">Amount</span><span class="fv tab">$412.90</span></div>
      <div class="fld"><span class="fk">Category</span><span class="fv cat"><span class="d"></span>Materials</span></div>
      <div class="fld flag"><span><span class="fk">Date</span><br><span class="fv tab">14 Aug 2026</span></span><span class="chk"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="M12 9v4M12 17h.01M10.3 3.9 1.8 18a2 2 0 0 0 1.7 3h17a2 2 0 0 0 1.7-3L13.7 3.9a2 2 0 0 0-3.4 0Z"/></svg>Check this</span></div>
    </div></div></div>
  </div>

  <div class="feat rev">
    <div class="copy">
      <span class="eyebrow">Invoices &amp; progress claims</span>
      <h3>Invoices and HIA claims that are actually correct</h3>
      <p>Raise invoices, generate HIA progress claims, and see what's paid and what's still owed. No more invoices going out with the date missing.</p>
      <ul>
        <li><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="m5 13 4 4L19 7"/></svg>Paid, pending and overdue at a glance</li>
        <li><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="m5 13 4 4L19 7"/></svg>Your ABN and details on every invoice, done right</li>
      </ul>
    </div>
    <div class="shot"><div class="shotpad"><div class="panel">
      <h5>Invoices</h5>
      <table class="invtable">
        <tr><th>Invoice</th><th>Project</th><th>Date</th><th>Amount</th><th>Status</th></tr>
        <tr><td><b>INV-084</b></td><td>72 Centenary Dr</td><td class="tab">12 Jul 2026</td><td class="tab">$187,500</td><td><span class="pill p-ok"><span class="d"></span>Paid</span></td></tr>
        <tr><td><b>INV-091</b></td><td>72 Centenary Dr</td><td class="tab">2 Aug 2026</td><td class="tab">$157,500</td><td><span class="pill p-w"><span class="d"></span>Pending</span></td></tr>
        <tr><td><b>INV-097</b></td><td>Gurner St</td><td class="tab">18 Aug 2026</td><td class="tab">$30,000</td><td><span class="pill p-ok"><span class="d"></span>Paid</span></td></tr>
      </table>
    </div></div></div>
  </div>
</div></section>

<!-- SCAFFOLD BAND -->
<section class="band"><div class="wrap">
  <div class="eyebrow">For scaffolders</div>
  <div class="bigstat">5&ndash;10%</div>
  <h2>of a scaffolding fleet disappears every year</h2>
  <p>It gets left on finished sites, borrowed for another job and never brought back, or it just walks off. On half a million dollars of gear, that's tens of thousands of dollars a year. The Gear Ledger is built to catch it.</p>
</div></section>

<!-- SCAFFOLD FEATURES -->
<section id="scaffold"><div class="wrap">
  <div class="sec-head">
    <div class="eyebrow">RisingAMP Scaffold</div>
    <h2>Every stick of steel, accounted for</h2>
    <p>Know where it is, what it's worth, and what's missing. Your gear, your dockets, your hire clock and your paperwork, all in the same app as your job costs.</p>
  </div>

  <div class="feat">
    <div class="copy">
      <span class="eyebrow">The Gear Ledger</span>
      <h3>"Where are my 1.8s?" One search tells you.</h3>
      <p>Type in a size and see what you own, how much is in the yard, how much is out and at which site, and what's damaged. It adds up to a live dollar value for your whole fleet. This is the exact tool a scaffolder asked us for, so we built it.</p>
      <ul>
        <li><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="m5 13 4 4L19 7"/></svg>Standards, ledgers, planks, brackets, every size you run</li>
        <li><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="m5 13 4 4L19 7"/></svg>Yard, on site, and damaged, split at a glance</li>
        <li><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="m5 13 4 4L19 7"/></svg>A dollar value on your whole fleet, always current</li>
      </ul>
    </div>
    <div class="shot"><div class="shotpad">
      <div class="gsearch"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><circle cx="11" cy="11" r="7"/><path d="m20 20-3.5-3.5"/></svg><b>1.8</b><span class="k">2 matches</span></div>
      <div class="grow">
        <div class="cn"><b>Ledger &middot; 1.8m</b><small>640 owned &middot; $31 ea</small></div>
        <div class="gmid"><div class="sbar"><i style="width:28%;background:var(--c-yard)"></i><i style="width:69%;background:var(--c-out)"></i><i style="width:3%;background:var(--c-dam)"></i></div><div style="margin-top:5px"><span class="sc">Yard 180</span><span class="sc">Marsden Pk 240</span><span class="sc">Box Hill 168</span></div></div>
        <div class="gval tab">$19,840</div>
      </div>
      <div class="grow">
        <div class="cn"><b>Steel plank &middot; 1.8m</b><small>460 owned &middot; $55 ea</small></div>
        <div class="gmid"><div class="sbar"><i style="width:38%;background:var(--c-yard)"></i><i style="width:59%;background:var(--c-out)"></i><i style="width:3%;background:var(--c-dam)"></i></div><div style="margin-top:5px"><span class="sc">Yard 174</span><span class="sc">Marsden Pk 150</span><span class="sc">Box Hill 122</span></div></div>
        <div class="gval tab">$25,300</div>
      </div>
      <div class="skey"><span><span class="d" style="background:var(--c-yard)"></span>In yard</span><span><span class="d" style="background:var(--c-out)"></span>On site</span><span><span class="d" style="background:var(--c-dam)"></span>Damaged</span></div>
    </div></div>
  </div>

  <div class="feat rev">
    <div class="copy">
      <span class="eyebrow">The hire clock</span>
      <h3>Stop giving away extended hire for free</h3>
      <p>Base hire runs out, the builder runs late, and the extra weeks quietly go unbilled. RisingAMP flags the day base hire ends on every job, so you invoice every extra week instead of giving it away. For most scaffolders, that alone covers the subscription on the very first job.</p>
      <ul>
        <li><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="m5 13 4 4L19 7"/></svg>Automatic alert the moment base hire ends</li>
        <li><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="m5 13 4 4L19 7"/></svg>Timestamped off-hire requests end the "I called it off" argument</li>
      </ul>
    </div>
    <div class="shot"><div class="shotpad"><div class="hire">
      <div class="hr"><span class="k">Erect &amp; dismantle</span><span class="v tab">$6,800 &middot; invoiced</span></div>
      <div class="hr"><span class="k">Base hire (8 weeks)</span><span class="v tab">Ended 29 May</span></div>
      <div class="hr"><span class="k">Extended hire since</span><span class="v w tab">5 wks &times; $1,340 = $6,700</span></div>
      <div class="hr"><span class="k">Off-hire request</span><span class="v" style="color:var(--slate-400)">None received</span></div>
    </div>
    <p style="font-size:12px;color:var(--slate-600);margin-top:11px">$6,700 that would have quietly slipped away, sitting there ready to invoice.</p>
    </div></div>
  </div>

  <div class="feat">
    <div class="copy">
      <span class="eyebrow">Signed dockets</span>
      <h3>Win the argument, because you've got the paperwork</h3>
      <p>Every piece that leaves the yard goes out on a signed docket. If it comes back short, RisingAMP works out the cost at replacement price, with the builder's signature already on file. Charge it or write it off, it's your call.</p>
      <ul>
        <li><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="m5 13 4 4L19 7"/></svg>Load-out and return, counted and signed on glass</li>
        <li><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="m5 13 4 4L19 7"/></svg>Shortfalls priced automatically, ready to invoice</li>
      </ul>
    </div>
    <div class="shot"><div class="shotpad"><div class="panel">
      <h5>Dockets &middot; Box Hill duplex</h5>
      <div class="dkt"><span class="dir out"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="M12 19V5M6 11l6-6 6 6"/></svg></span><div><b>Load out &middot; 3 Apr</b><small>612 pieces &middot; signed J. Hooper</small></div><span class="pill p-ok" style="margin-left:auto"><span class="d"></span>Matched</span></div>
      <div class="dkt"><span class="dir out"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="M12 19V5M6 11l6-6 6 6"/></svg></span><div><b>Top-up &middot; 21 Apr</b><small>322 pieces &middot; signed site super</small></div><span class="pill p-ok" style="margin-left:auto"><span class="d"></span>Matched</span></div>
      <div class="dkt"><span class="dir in"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="M12 5v14M6 13l6 6 6-6"/></svg></span><div><b>Partial return &middot; 30 May</b><small>118 of 118 back</small></div><span class="pill p-ok" style="margin-left:auto"><span class="d"></span>Matched</span></div>
    </div></div></div>
  </div>

  <div class="feat rev">
    <div class="copy">
      <span class="eyebrow">Certs &amp; inspections</span>
      <h3>Never miss a 30-day check or lose a handover cert</h3>
      <p>Handover certificates and inspection records live on the job, with a countdown to the next 30-day check. When a SafeWork inspector or a head contractor asks, the answer is on your phone in seconds.</p>
      <ul>
        <li><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="m5 13 4 4L19 7"/></svg>Digital handover certs, signed and stored per job</li>
        <li><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="m5 13 4 4L19 7"/></svg>30-day inspection reminders before they fall due</li>
      </ul>
    </div>
    <div class="shot"><div class="shotpad"><div class="panel">
      <h5>Certs &amp; checks</h5>
      <div class="certrow"><span class="ic"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="M6 3h9l3 3v15H6z"/><path d="m9 14 2 2 4-4"/></svg></span><div><b>Handover certificate &middot; current</b><small>Issued 3 Apr &middot; duty 450kg/bay &middot; signed</small></div><span class="pill p-ok" style="margin-left:auto"><span class="d"></span>Valid</span></div>
      <div class="certrow"><span class="ic"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><circle cx="12" cy="12" r="9"/><path d="M12 7v5l3 2"/></svg></span><div><b>30-day inspection</b><small>Last done 18 Jun &middot; by D. Kaur, HRW SB0142</small></div><span class="pill p-w" style="margin-left:auto"><span class="d"></span>Due in 4d</span></div>
    </div></div></div>
  </div>
</div></section>

<!-- MOBILE -->
<section class="mobile"><div class="wrap"><div class="mobwrap">
  <div class="say" style="max-width:420px">
    <div class="eyebrow" style="margin-bottom:12px">Built for the tailgate</div>
    <h3 style="font-size:27px;font-weight:800;letter-spacing:-.02em;line-height:1.2;margin-bottom:16px">Made for dirty hands and one bar of signal</h3>
    <p style="font-size:15px;color:var(--slate-600);line-height:1.65;margin-bottom:16px">Count a return on the truck, the shortfall turns red by itself, and the builder signs on the screen. Takes about a minute, and the ledger stays accurate.</p>
    <ul style="list-style:none">
      <li style="display:flex;gap:10px;font-size:14.5px;padding:7px 0;font-weight:600"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" width="18" height="18" stroke-width="2.4" style="color:var(--pos);flex-shrink:0;margin-top:2px"><path d="m5 13 4 4L19 7"/></svg>Works on any phone, no app store needed</li>
      <li style="display:flex;gap:10px;font-size:14.5px;padding:7px 0;font-weight:600"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" width="18" height="18" stroke-width="2.4" style="color:var(--pos);flex-shrink:0;margin-top:2px"><path d="m5 13 4 4L19 7"/></svg>Big tap targets, made for gloves and glare</li>
      <li style="display:flex;gap:10px;font-size:14.5px;padding:7px 0;font-weight:600"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor" width="18" height="18" stroke-width="2.4" style="color:var(--pos);flex-shrink:0;margin-top:2px"><path d="m5 13 4 4L19 7"/></svg>If you can use your camera, you can use RisingAMP</li>
    </ul>
  </div>
  <div class="phone"><div class="pscreen"><div class="island"></div>
    <div class="mstatus"><span>4:38</span><span><svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M2 17h2v3H2zM6 13h2v7H6zM10 9h2v11h-2zM14 5h2v15h-2z"/></svg></span></div>
    <div class="mbody">
      <div class="mtop"><b>Return &middot; Penrith</b><span class="pill p-r"><span class="d"></span>Short</span></div>
      <div class="mc">
        <div class="mr"><span class="k">Standard 2.0m</span><span class="v tab">96 <span class="o">/ 96</span></span></div>
        <div class="mr"><span class="k">Ledger 1.8m</span><span class="v tab">204 <span class="o">/ 204</span></span></div>
        <div class="mr short"><span class="k">Steel plank 2.4m</span><span class="v tab">148 / 162</span></div>
        <div class="mr"><span class="k">Hop-up 3 board</span><span class="v tab">40 <span class="o">/ 40</span></span></div>
      </div>
      <div class="mvar">
        <b>14 &times; steel plank 2.4m not returned</b>
        <p>$770 at replacement. Docket #241, signed M. Torresi.</p>
        <div class="mvb"><div class="a">Charge builder</div><div class="b">Write off</div></div>
      </div>
      <div class="msig">Builder signs here</div>
      <div class="msave">Save return docket</div>
    </div>
  </div></div>
</div></div></section>

<!-- TRUST -->
<section class="trust"><div class="wrap">
  <div class="trustquote">
    <div class="eyebrow">Why us</div>
    <p class="q" style="margin-top:14px">We built RisingAMP for our own construction business first, and used it to run real jobs for two years. A scaffolder we worked with saw it and asked if we had something similar for tracking his gear. We didn't, so we built it.</p>
    <div class="by">Made by a construction business, for builders and the scaffolders they work with.</div>
  </div>
  <div class="valgrid">
    <div class="val"><div class="ic"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="M12 2 4 6v6c0 5 3.5 8 8 10 4.5-2 8-5 8-10V6z"/></svg></div><b>Your data is yours</b><p>Encrypted, private, and never sold. Export everything to a spreadsheet any time.</p></div>
    <div class="val"><div class="ic"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="M5 12h14M12 5l7 7-7 7"/></svg></div><b>No lock-in</b><p>Cancel any time and take your data with you. No lock-in contracts.</p></div>
    <div class="val"><div class="ic"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><circle cx="12" cy="12" r="9"/><path d="M3 12h18M12 3a15 15 0 0 1 0 18M12 3a15 15 0 0 0 0 18"/></svg></div><b>Built for Australia</b><p>Set up for ABNs, HIA claims, GST and SafeWork paperwork, the way it actually works here.</p></div>
    <div class="val"><div class="ic"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="M12 8v5l3 2"/><circle cx="12" cy="12" r="9"/></svg></div><b>Up and running in a day</b><p>We help you bring across what you've already got. No week-long setup.</p></div>
  </div>
</div></section>

<!-- PRICING -->
<section class="pricing" id="pricing"><div class="wrap">
  <div class="sec-head">
    <div class="eyebrow">Simple pricing</div>
    <h2>One fair price. Add scaffold when you're ready.</h2>
    <p>No per-seat charges, so bring your whole crew. Billed monthly, cancel any time.</p>
  </div>
  <div class="prices">
    <div class="price">
      <div class="pn">Basic</div>
      <div class="amt"><span class="n">$50</span><span class="per">/ month</span></div>
      <div class="desc">Track what every job costs, and see if you're making money on it.</div>
      <ul>
        <li><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="m5 13 4 4L19 7"/></svg>Unlimited jobs</li>
        <li><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="m5 13 4 4L19 7"/></svg>Margin dashboard &amp; plain-English verdict</li>
        <li><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="m5 13 4 4L19 7"/></svg>What needs you today</li>
        <li><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="m5 13 4 4L19 7"/></svg>Receipt scanning</li>
        <li><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="m5 13 4 4L19 7"/></svg>Invoices &amp; HIA progress claims</li>
        <li><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="m5 13 4 4L19 7"/></svg>Your whole team, no per-seat fees</li>
        <li><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="m5 13 4 4L19 7"/></svg>Export to spreadsheet any time</li>
      </ul>
      <a class="btn ghostdark" href="#">Choose Basic</a>
      <div class="foot">Billed monthly &middot; cancel any time</div>
    </div>

    <div class="price best">
      <div class="tag">Best value</div>
      <div class="pn">Premium</div>
      <div class="amt"><span class="n">$75</span><span class="per">/ month</span></div>
      <div class="desc">The tracker plus the full scaffold suite, for scaffolders who also want their jobs costed.</div>
      <ul>
        <li><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="m5 13 4 4L19 7"/></svg><b>Everything in Basic</b></li>
        <li class="add"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="m5 13 4 4L19 7"/></svg>Gear Ledger, live inventory across sites</li>
        <li class="add"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="m5 13 4 4L19 7"/></svg>Signed dockets, load-out &amp; return</li>
        <li class="add"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="m5 13 4 4L19 7"/></svg>Hire clock &amp; extended-hire alerts</li>
        <li class="add"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="m5 13 4 4L19 7"/></svg>Handover certs &amp; 30-day inspection reminders</li>
        <li class="add"><svg viewBox="0 0 24 24" fill="none" stroke="currentColor"><path d="m5 13 4 4L19 7"/></svg>Yard stocktake mode</li>
      </ul>
      <a class="btn primary" href="#">Choose Premium</a>
      <div class="foot">Billed monthly &middot; cancel any time</div>
    </div>
  </div>
  <p class="pricenote">Purpose-built scaffolding software usually runs into the <b>hundreds of dollars a month</b>. The whole scaffold suite here is <b>$25 on top of your tracker</b>.</p>
</div></section>

<!-- FAQ -->
<section><div class="wrap">
  <div class="sec-head"><div class="eyebrow">Questions</div><h2>Straight answers</h2></div>
  <div class="faq">
    <div class="qa"><h4>Do I have to buy both?</h4><p>No. Start with Basic at $50 a month and add the scaffold suite whenever you want it. Nothing is bundled that you don't need.</p></div>
    <div class="qa"><h4>Can my whole team use it?</h4><p>Yes. Invite your crew and your office at no extra charge. There are no per-seat fees, so the price is the price no matter how many people log in.</p></div>
    <div class="qa"><h4>Is my data safe, and can I get it out?</h4><p>Your data is encrypted, private, and never sold. You can export everything to a spreadsheet at any time, so you're never locked in.</p></div>
    <div class="qa"><h4>What if I want to stop?</h4><p>Cancel any time, no contract. You can take your data with you when you go.</p></div>
    <div class="qa"><h4>How long does it take to get going?</h4><p>About a day. We help you bring across the jobs, expenses or gear you've already got, so you're not starting from a blank screen.</p></div>
    <div class="qa"><h4>Do I need to be good with computers?</h4><p>No. If you can take a photo on your phone, you can use RisingAMP.</p></div>
  </div>
</div></section>

<!-- FINAL CTA -->
<section class="final"><div class="wrap">
  <h2>Stop running it in your head</h2>
  <p>See what every job is costing you, or find any piece of scaffold gear, from tomorrow morning. Setup takes about a day, and you can cancel any time.</p>
  <div class="cta">
    <a class="btn primary lg" href="#">Get started</a>
    <a class="btn ghost lg" href="#">Book a 15-minute demo</a>
  </div>
</div></section>

<!-- FOOTER -->
<footer><div class="wrap"><div class="row">
  <a class="logo" href="#">RisingAMP</a>
  <div class="fl"><a href="#construction">For builders</a><a href="#scaffold">For scaffolders</a><a href="#pricing">Pricing</a><a href="#">Privacy</a><a href="#">Terms</a></div>
  <div class="cr">&copy; 2026 RisingAMP</div>
</div></div></footer>

</body>
</html>
