<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>2026 3학년 지덕체 트레이닝 — 내 몸 바로 알기</title>
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+KR:wght@400;500;700;900&display=swap" rel="stylesheet">
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
    :root {
      --green:#1D9E75; --green-light:#E1F5EE; --green-mid:#5DCAA5; --green-dark:#0F6E56;
      --blue:#185FA5; --blue-light:#E6F1FB; --blue-mid:#378ADD;
      --amber:#854F0B; --amber-light:#FAEEDA; --amber-mid:#EF9F27;
      --red:#A32D2D; --red-light:#FCEBEB; --red-mid:#E24B4A;
      --bg:#fff; --bg-secondary:#f5f4f0; --bg-tertiary:#eeedea;
      --text:#1a1a1a; --text-secondary:#6b6b68; --text-tertiary:#9b9b97;
      --border:rgba(0,0,0,.1); --border-strong:rgba(0,0,0,.18);
      --radius:12px; --radius-sm:8px;
    }
    @media (prefers-color-scheme:dark){
      :root{
        --bg:#1a1a1a; --bg-secondary:#242424; --bg-tertiary:#2e2e2e;
        --text:#f0efeb; --text-secondary:#a0a09c; --text-tertiary:#6b6b68;
        --border:rgba(255,255,255,.1); --border-strong:rgba(255,255,255,.18);
        --green-light:#0a3d2e; --blue-light:#0c2d4e; --amber-light:#3d2505; --red-light:#3d1212;
      }
    }
    html{scroll-behavior:smooth}
    body{font-family:'Noto Sans KR',sans-serif;background:var(--bg-tertiary);color:var(--text);min-height:100vh}

    .hero{background:var(--bg);border-bottom:1px solid var(--border);padding:2rem 1.5rem 1.75rem;margin-bottom:1.5rem}
    .hero-inner{max-width:680px;margin:0 auto}
    .hero-eyebrow{display:flex;align-items:center;gap:8px;margin-bottom:12px;flex-wrap:wrap}
    .tag-year{font-size:11px;font-weight:700;letter-spacing:.1em;background:var(--green-light);color:var(--green-dark);padding:3px 10px;border-radius:4px}
    .tag-sub{font-size:11px;color:var(--text-tertiary)}
    .hero-title{font-size:clamp(22px,5vw,30px);font-weight:900;color:var(--text);line-height:1.2;letter-spacing:-.025em;margin-bottom:8px}
    .hero-title span{color:var(--green)}
    .hero-desc{font-size:14px;color:var(--text-secondary);line-height:1.7;margin-bottom:14px}
    .hero-pills{display:flex;gap:6px;flex-wrap:wrap}
    .hero-pill{font-size:12px;color:var(--text-secondary);border:.5px solid var(--border-strong);border-radius:20px;padding:4px 12px}

    .page-wrap{max-width:680px;margin:0 auto;padding:0 1rem 5rem}

    .progress-wrap{margin-bottom:1.5rem}
    .progress-steps{display:flex;gap:6px;margin-bottom:8px}
    .prog-step{flex:1;height:4px;border-radius:3px;background:var(--border);transition:background .35s}
    .prog-step.done{background:var(--green)}
    .prog-step.active{background:var(--green-mid)}
    .progress-labels{display:flex;justify-content:space-between}
    .prog-label{font-size:10px;color:var(--text-tertiary);letter-spacing:.04em}
    .prog-label.active{color:var(--green);font-weight:500}

    .step{display:none}
    .step.active{display:block}
    .step-eyebrow{font-size:11px;font-weight:700;color:var(--green);letter-spacing:.1em;text-transform:uppercase;margin-bottom:4px}
    .step-title{font-size:22px;font-weight:700;color:var(--text);letter-spacing:-.02em;margin-bottom:5px}
    .step-desc{font-size:13px;color:var(--text-secondary);line-height:1.65;margin-bottom:1.25rem}

    .card{background:var(--bg);border:.5px solid var(--border);border-radius:var(--radius);padding:1.25rem;margin-bottom:1rem}
    .card-title{font-size:11px;font-weight:700;color:var(--text-secondary);letter-spacing:.06em;text-transform:uppercase;margin-bottom:14px;padding-bottom:8px;border-bottom:.5px solid var(--border)}

    .input-row{display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-bottom:10px}
    .input-row3{display:grid;grid-template-columns:1fr 1fr 1fr;gap:10px;margin-bottom:10px}
    .input-row:last-child,.input-row3:last-child{margin-bottom:0}
    .field{display:flex;flex-direction:column;gap:4px}
    .field label{font-size:11px;color:var(--text-secondary);line-height:1.4}
    .field input,.field select{height:38px;border:.5px solid var(--border-strong);border-radius:var(--radius-sm);padding:0 10px;font-size:13px;color:var(--text);background:var(--bg);font-family:'Noto Sans KR',sans-serif;transition:border-color .15s,box-shadow .15s;-webkit-appearance:none}
    .field input:focus,.field select:focus{outline:none;border-color:var(--green);box-shadow:0 0 0 2px rgba(29,158,117,.12)}
    .field input::placeholder{color:var(--text-tertiary)}
    /* 에러 상태 */
    .field input.error,.field select.error{border-color:var(--red-mid)!important;box-shadow:0 0 0 2px rgba(224,75,74,.15)!important;background:var(--red-light)!important}
    .field-error-msg{font-size:11px;color:var(--red-mid);margin-top:2px;display:none}
    .field input.error ~ .field-error-msg,.field select.error ~ .field-error-msg{display:block}

    /* 체성분 분석 레이블 */
    .comp-item{display:flex;flex-direction:column;gap:4px}
    .comp-label{display:flex;flex-direction:column;gap:1px}
    .comp-label-main{font-size:11px;font-weight:500;color:var(--text-secondary)}
    .comp-label-desc{font-size:10px;color:var(--text-tertiary);line-height:1.4}
    .comp-item input{height:38px;border:.5px solid var(--border-strong);border-radius:var(--radius-sm);padding:0 10px;font-size:13px;color:var(--text);background:var(--bg);font-family:'Noto Sans KR',sans-serif;transition:border-color .15s,box-shadow .15s;-webkit-appearance:none}
    .comp-item input:focus{outline:none;border-color:var(--green);box-shadow:0 0 0 2px rgba(29,158,117,.12)}
    .comp-item input::placeholder{color:var(--text-tertiary)}
    .comp-item input.error{border-color:var(--red-mid)!important;box-shadow:0 0 0 2px rgba(224,75,74,.15)!important;background:var(--red-light)!important}

    /* 합계 행 */
    .comp-sum-row{display:flex;align-items:center;gap:6px;margin-top:10px;padding:10px 12px;background:var(--bg-secondary);border-radius:8px;flex-wrap:wrap;transition:background .2s}
    .comp-sum-eq{font-size:11px;color:var(--text-secondary)}
    .comp-sum-badge{font-size:11px;font-weight:500;padding:2px 8px;border-radius:4px;background:var(--green-light);color:var(--green-dark)}
    .comp-sum-result{font-size:12px;font-weight:500;margin-left:auto;padding:2px 10px;border-radius:20px;transition:all .2s}
    .comp-sum-result.match{background:var(--green-light);color:var(--green-dark)}
    .comp-sum-result.close{background:var(--amber-light);color:var(--amber)}
    .comp-sum-result.far{background:var(--red-light);color:var(--red)}
    .comp-sum-result.empty{background:var(--bg-tertiary);color:var(--text-tertiary)}

    /* 토스트 알림 */
    .toast{position:fixed;bottom:24px;left:50%;transform:translateX(-50%) translateY(80px);background:#1a1a1a;color:#fff;padding:10px 18px;border-radius:10px;font-size:13px;font-weight:500;z-index:9999;opacity:0;transition:all .3s;pointer-events:none;white-space:nowrap;max-width:90vw;text-align:center}
    .toast.show{opacity:1;transform:translateX(-50%) translateY(0)}

    .check-group{display:flex;flex-wrap:wrap;gap:8px}
    .check-group label{font-size:12px;color:var(--text);display:flex;align-items:center;gap:5px;cursor:pointer}
    .check-group input[type=radio]{accent-color:var(--green);width:13px;height:13px}
    .tag-row{display:flex;align-items:flex-start;gap:8px;margin-bottom:10px}
    .tag-row:last-child{margin-bottom:0}
    .tag-name{font-size:12px;color:var(--text-secondary);width:80px;flex-shrink:0;padding-top:2px}

    /* SEGMENTAL */
    .seg-grid{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:8px}
    .seg-panel{background:var(--bg-secondary);border-radius:8px;padding:.65rem .65rem .5rem}
    .seg-panel-title{font-size:10px;font-weight:700;color:var(--text-secondary);letter-spacing:.06em;text-transform:uppercase;text-align:center;margin-bottom:6px}
    .body-frame{position:relative;width:100%;aspect-ratio:1/1.2;border-radius:6px;overflow:hidden;background:var(--bg-tertiary)}
    .cross-h{position:absolute;top:50%;left:0;right:0;height:1px;background:var(--border-strong);transform:translateY(-50%)}
    .cross-v{position:absolute;left:50%;top:0;bottom:0;width:1px;background:var(--border-strong);transform:translateX(-50%)}
    .side-l{position:absolute;left:5px;top:50%;transform:translateY(-8px);font-size:10px;color:var(--text-tertiary)}
    .side-r{position:absolute;right:5px;top:50%;transform:translateY(-8px);font-size:10px;color:var(--text-tertiary)}
    .sil{position:absolute;top:50%;left:50%;transform:translate(-50%,-50%);pointer-events:none;opacity:.28}
    .seg{position:absolute;transform:translate(-50%,-50%);font-size:11px;font-weight:500;cursor:pointer;user-select:none;padding:3px 8px;border-radius:4px;transition:all .15s;white-space:nowrap}
    .seg:active{transform:translate(-50%,-50%) scale(.95)}
    .s-none{color:var(--text-tertiary)}
    .s-under{color:#0C447C;background:rgba(181,212,244,.6)}
    .s-normal{color:#085041;background:rgba(159,225,203,.55)}
    .s-over{color:#633806;background:rgba(250,199,117,.6)}
    .seg-hint{font-size:10px;color:var(--text-tertiary);text-align:center;margin-top:4px}
    .seg-legend{display:flex;justify-content:center;gap:10px;flex-wrap:wrap}
    .seg-leg-item{display:flex;align-items:center;gap:4px;font-size:11px;color:var(--text-secondary)}
    .seg-leg-dot{width:8px;height:8px;border-radius:50%}

    /* STEP 2 */
    .item-card{background:var(--bg);border:.5px solid var(--border);border-radius:var(--radius);padding:1.1rem 1.25rem;margin-bottom:.75rem}
    .item-header{display:flex;align-items:center;gap:10px;margin-bottom:10px}
    .item-icon{width:34px;height:34px;border-radius:9px;display:flex;align-items:center;justify-content:center;font-size:17px;flex-shrink:0}
    .item-name{font-size:15px;font-weight:700;color:var(--text)}
    .item-eng{font-size:11px;color:var(--text-tertiary);margin-top:1px}
    .item-value{font-size:30px;font-weight:900;color:var(--text);line-height:1;margin-bottom:10px}
    .item-unit{font-size:13px;font-weight:400;color:var(--text-secondary)}
    .block{border-radius:8px;padding:.85rem 1rem;margin-bottom:.6rem}
    .block:last-child{margin-bottom:0}
    .block-label{font-size:10px;font-weight:700;letter-spacing:.08em;text-transform:uppercase;margin-bottom:5px}
    .block-text{font-size:14px;line-height:1.85;color:var(--text)}
    .block-text strong{font-weight:500}
    .hl{display:inline-block;padding:1px 7px;border-radius:4px;font-weight:600;font-size:13px}
    .hl-good{background:var(--green-light);color:var(--green-dark)}
    .hl-warn{background:var(--amber-light);color:var(--amber)}
    .hl-danger{background:var(--red-light);color:var(--red)}
    .hl-info{background:var(--blue-light);color:var(--blue)}

    .advice-section{background:var(--bg);border:.5px solid var(--border);border-radius:var(--radius);padding:1.25rem;margin-bottom:1rem}
    .advice-section-header{display:flex;align-items:center;gap:10px;margin-bottom:14px;padding-bottom:10px;border-bottom:.5px solid var(--border)}
    .advice-section-icon{width:38px;height:38px;border-radius:10px;display:flex;align-items:center;justify-content:center;font-size:20px;flex-shrink:0}
    .advice-section-title{font-size:16px;font-weight:700;color:var(--text)}
    .advice-section-sub{font-size:12px;color:var(--text-secondary);margin-top:2px}
    .advice-row{display:flex;align-items:flex-start;gap:10px;padding:9px 0;border-bottom:.5px solid var(--border)}
    .advice-row:last-child{border-bottom:none}
    .advice-dot{width:7px;height:7px;border-radius:50%;margin-top:6px;flex-shrink:0}
    .advice-text{font-size:14px;color:var(--text);line-height:1.7;font-weight:500}
    .advice-sub{font-size:13px;color:var(--text-secondary);margin-top:3px;line-height:1.65}

    .btn-row{display:flex;gap:10px;margin-top:1.5rem}
    .btn-primary{flex:1;height:46px;background:var(--green);border:none;border-radius:10px;color:#fff;font-size:15px;font-weight:500;cursor:pointer;font-family:inherit;transition:background .2s,transform .1s}
    .btn-primary:hover{background:var(--green-dark)}
    .btn-primary:active{transform:scale(.98)}
    .btn-secondary{height:46px;padding:0 20px;background:none;border:.5px solid var(--border-strong);border-radius:10px;color:var(--text-secondary);font-size:14px;cursor:pointer;font-family:inherit;transition:background .15s}
    .btn-secondary:hover{background:var(--bg-secondary)}

    .badge{display:inline-block;padding:3px 10px;border-radius:20px;font-size:11px;font-weight:500}
    .badge-good{background:var(--green-light);color:var(--green-dark)}
    .badge-warn{background:var(--amber-light);color:var(--amber)}
    .badge-danger{background:var(--red-light);color:var(--red)}
    .badge-info{background:var(--blue-light);color:var(--blue)}

    .result-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:10px;margin-bottom:1rem}
    .result-card{background:var(--bg-secondary);border-radius:10px;padding:.9rem .75rem;text-align:center}
    .result-card .val{font-size:22px;font-weight:700;color:var(--text)}
    .result-card .val-unit{font-size:13px;font-weight:400}
    .result-card .lbl{font-size:11px;color:var(--text-secondary);margin-top:2px}

    .chart-bar-row{display:flex;align-items:center;gap:10px;margin-bottom:8px}
    .chart-bar-label{font-size:12px;color:var(--text-secondary);width:70px;flex-shrink:0;text-align:right}
    .chart-bar-outer{flex:1;height:12px;background:var(--bg-secondary);border-radius:6px;overflow:hidden}
    .chart-bar-inner{height:100%;border-radius:6px;transition:width .7s cubic-bezier(.4,0,.2,1)}
    .chart-bar-val{font-size:12px;color:var(--text-secondary);width:45px;flex-shrink:0}

    .summary-doc-header{text-align:center;padding:1.25rem 0 1rem;border-bottom:.5px solid var(--border);margin-bottom:1rem}
    .summary-eyebrow{font-size:11px;font-weight:700;color:var(--green);letter-spacing:.1em;margin-bottom:5px}
    .summary-title{font-size:18px;font-weight:700;color:var(--text);letter-spacing:-.02em}
    .summary-meta{font-size:12px;color:var(--text-tertiary);margin-top:5px}
    .summary-section{margin-bottom:1.25rem}
    .summary-section h3{font-size:11px;font-weight:700;color:var(--green);letter-spacing:.1em;text-transform:uppercase;margin-bottom:8px;padding-bottom:5px;border-bottom:1px solid var(--green-light)}
    .summary-row{display:flex;justify-content:space-between;align-items:center;font-size:13px;padding:5px 0;border-bottom:.5px solid var(--border)}
    .summary-row:last-child{border-bottom:none}
    .summary-row .lbl{color:var(--text-secondary)}
    .summary-row .val{color:var(--text);font-weight:500}
    .smr-note{font-size:13px;color:var(--text-secondary);line-height:1.7;padding:4px 0}
    .finish-note{margin-top:.75rem;padding:1rem 1.25rem;background:var(--green-light);border-radius:10px;text-align:center;font-size:13px;color:var(--green-dark);line-height:1.7}

    .footer{text-align:center;padding:2rem 0 1rem;font-size:11px;color:var(--text-tertiary)}

    @media(max-width:480px){
      .input-row3{grid-template-columns:1fr 1fr}
      .hero{padding:1.5rem 1rem 1.25rem}
    }
    @media print{
      .hero,.progress-wrap,.step-eyebrow,.step-desc,.btn-row,.footer{display:none!important}
      body{background:white}
      .page-wrap{padding:0;max-width:100%}
      .card{border:1px solid #ccc}
    }
  </style>
</head>
<body>

<!-- 토스트 -->
<div class="toast" id="toast"></div>

<div class="hero">
  <div class="hero-inner">
    <div class="hero-eyebrow">
      <span class="tag-year">2026 · 3학년</span>
      <span class="tag-sub">주제중심창의적체험활동</span>
    </div>
    <div class="hero-title">지덕체 트레이닝<br><span>내 몸 바로 알기</span></div>
    <div class="hero-desc">인바디 결과지를 보면서 나의 체성분을 분석하고,<br>건강한 생활 습관을 계획해봐요.</div>
    <div class="hero-pills">
      <span class="hero-pill">📊 체성분 분석</span>
      <span class="hero-pill">💡 내 수치 해설</span>
      <span class="hero-pill">✏️ 자기 성찰</span>
      <span class="hero-pill">📋 실천 계획</span>
    </div>
  </div>
</div>

<div class="page-wrap">

  <div class="progress-wrap">
    <div class="progress-steps">
      <div class="prog-step active" id="ps0"></div>
      <div class="prog-step" id="ps1"></div>
    </div>
    <div class="progress-labels">
      <span class="prog-label active" id="pl0">정보 입력</span>
      <span class="prog-label" id="pl1">결과 분석</span>
    </div>
  </div>

  <!-- ══ STEP 0 ══ -->
  <div class="step active" id="step0">
    <div class="step-eyebrow">Step 1 / 2</div>
    <div class="step-title">기본 정보 &amp; 인바디 결과 입력</div>
    <div class="step-desc">결과지를 보면서 <strong>모든 항목</strong>을 빠짐없이 입력해 주세요.</div>

    <!-- 개인 정보 -->
    <div class="card">
      <div class="card-title">개인 정보</div>
      <div class="input-row">
        <div class="field">
          <label>이름</label>
          <input type="text" id="name" placeholder="홍길동" data-label="이름">
        </div>
        <div class="field">
          <label>반</label>
          <input type="text" id="classnum" placeholder="3학년 2반" data-label="반">
        </div>
      </div>
      <div class="input-row">
        <div class="field">
          <label>번호</label>
          <input type="number" id="studentno" placeholder="15" min="1" max="50" data-label="번호">
        </div>
        <div class="field">
          <label>성별</label>
          <select id="gender" data-label="성별">
            <option value="">선택</option>
            <option value="female">여</option>
            <option value="male">남</option>
          </select>
        </div>
      </div>
      <div class="input-row">
        <div class="field">
          <label>나이</label>
          <input type="number" id="age" placeholder="15" min="10" max="20" data-label="나이">
        </div>
        <div class="field">
          <label>신장 (cm)</label>
          <input type="number" id="height" placeholder="165" step="0.1" data-label="신장">
        </div>
      </div>
    </div>

    <!-- 체성분 분석 -->
    <div class="card">
      <div class="card-title">체성분 분석 Body Composition Analysis</div>
      <div style="display:grid;grid-template-columns:1fr 1fr;gap:10px;margin-bottom:10px">
        <div class="comp-item">
          <div class="comp-label">
            <span class="comp-label-main">체수분 (L)</span>
            <span class="comp-label-desc">우리 몸을 이루고 있는 물</span>
          </div>
          <input type="number" id="tbw" placeholder="27.7" step="0.1" data-label="체수분" data-sum="yes" oninput="updateSum()">
        </div>
        <div class="comp-item">
          <div class="comp-label">
            <span class="comp-label-main">단백질 (kg)</span>
            <span class="comp-label-desc">근육을 만들어주는</span>
          </div>
          <input type="number" id="protein" placeholder="7.3" step="0.1" data-label="단백질" data-sum="yes" oninput="updateSum()">
        </div>
      </div>
      <div style="display:grid;grid-template-columns:1fr 1fr;gap:10px">
        <div class="comp-item">
          <div class="comp-label">
            <span class="comp-label-main">무기질 (kg)</span>
            <span class="comp-label-desc">뼈를 단단하게 해주는</span>
          </div>
          <input type="number" id="mineral" placeholder="2.65" step="0.01" data-label="무기질" data-sum="yes" oninput="updateSum()">
        </div>
        <div class="comp-item">
          <div class="comp-label">
            <span class="comp-label-main">체지방량 (kg)</span>
            <span class="comp-label-desc">남은 에너지를 저장해 놓은</span>
          </div>
          <input type="number" id="fat" placeholder="17.6" step="0.1" data-label="체지방량" data-sum="yes" oninput="updateSum()">
        </div>
      </div>
      <!-- 합계 자동계산 행 -->
      <div class="comp-sum-row" id="sumRow">
        <span class="comp-sum-eq">체수분 + 단백질 + 무기질 + 체지방량</span>
        <span style="font-size:11px;color:var(--text-secondary)">=</span>
        <span class="comp-sum-badge" id="sumVal">? kg</span>
        <span class="comp-sum-result empty" id="sumMatch">체중 입력 후 비교</span>
      </div>
      <div style="margin-top:10px">
        <div class="comp-item">
          <div class="comp-label">
            <span class="comp-label-main">체중 (kg)</span>
            <span class="comp-label-desc">체수분, 단백질, 무기질, 체지방을 모두 합치면</span>
          </div>
          <input type="number" id="weight" placeholder="55.3" step="0.1" data-label="체중" oninput="updateSum()">
        </div>
      </div>
    </div>

    <!-- 골격근·지방 분석 -->
    <div class="card">
      <div class="card-title">골격근·지방 분석 Muscle-Fat Analysis</div>
      <div class="input-row3">
        <div class="field"><label>체중 (kg)</label><input type="number" id="weight2" placeholder="55.3" step="0.1" data-label="골격근 분석 체중"></div>
        <div class="field"><label>골격근량 (kg)</label><input type="number" id="muscle" placeholder="20.3" step="0.1" data-label="골격근량"></div>
        <div class="field"><label>체지방량 (kg)</label><input type="number" id="fat2" placeholder="17.6" step="0.1" data-label="골격근 분석 체지방량"></div>
      </div>
    </div>

    <!-- 비만 분석 -->
    <div class="card">
      <div class="card-title">비만 분석 Obesity Analysis</div>
      <div class="input-row">
        <div class="field"><label>BMI (kg/m²)</label><input type="number" id="bmi" placeholder="22.4" step="0.1" data-label="BMI"></div>
        <div class="field"><label>체지방률 (%)</label><input type="number" id="fatpct" placeholder="31.9" step="0.1" data-label="체지방률"></div>
      </div>
      <div style="margin-top:10px">
        <div class="tag-row">
          <span class="tag-name">BMI 판정</span>
          <div class="check-group" id="bmi_grade_group">
            <label><input type="radio" name="bmi_grade" value="under"> 표준이하</label>
            <label><input type="radio" name="bmi_grade" value="normal" checked> 표준</label>
            <label><input type="radio" name="bmi_grade" value="over"> 표준이상</label>
          </div>
        </div>
        <div class="tag-row">
          <span class="tag-name">체지방 판정</span>
          <div class="check-group" id="fat_grade_group">
            <label><input type="radio" name="fat_grade" value="under"> 표준이하</label>
            <label><input type="radio" name="fat_grade" value="normal" checked> 표준</label>
            <label><input type="radio" name="fat_grade" value="over"> 표준이상</label>
          </div>
        </div>
      </div>
    </div>

    <!-- 부위별 분석 -->
    <div class="card">
      <div class="card-title">부위별 분석 Segmental Analysis</div>
      <div class="seg-grid">
        <div class="seg-panel">
          <div class="seg-panel-title">근육 분석</div>
          <div class="body-frame">
            <svg class="sil" width="130" height="200" viewBox="0 0 130 200">
              <circle cx="65" cy="13" r="12" fill="#888"/>
              <rect x="60" y="24" width="10" height="9" rx="2" fill="#888"/>
              <rect x="40" y="32" width="50" height="55" rx="7" fill="#888"/>
              <rect x="18" y="32" width="18" height="62" rx="7" fill="#888"/>
              <rect x="94" y="32" width="18" height="62" rx="7" fill="#888"/>
              <rect x="40" y="90" width="22" height="108" rx="7" fill="#888"/>
              <rect x="68" y="90" width="22" height="108" rx="7" fill="#888"/>
            </svg>
            <div class="cross-h"></div><div class="cross-v"></div>
            <div class="side-l">왼</div><div class="side-r">오른</div>
            <span class="seg s-normal" id="m-larm"  data-state="normal" style="left:18%;top:30%" onclick="cycle('m-larm')">표준</span>
            <span class="seg s-normal" id="m-rarm"  data-state="normal" style="left:82%;top:30%" onclick="cycle('m-rarm')">표준</span>
            <span class="seg s-normal" id="m-trunk" data-state="normal" style="left:50%;top:42%" onclick="cycle('m-trunk')">표준</span>
            <span class="seg s-normal" id="m-lleg"  data-state="normal" style="left:26%;top:72%" onclick="cycle('m-lleg')">표준</span>
            <span class="seg s-normal" id="m-rleg"  data-state="normal" style="left:74%;top:72%" onclick="cycle('m-rleg')">표준</span>
          </div>
          <div class="seg-hint">클릭하면 상태가 바뀌어요</div>
        </div>
        <div class="seg-panel">
          <div class="seg-panel-title">체지방 분석</div>
          <div class="body-frame">
            <svg class="sil" width="130" height="200" viewBox="0 0 130 200">
              <circle cx="65" cy="13" r="12" fill="#888"/>
              <rect x="60" y="24" width="10" height="9" rx="2" fill="#888"/>
              <rect x="40" y="32" width="50" height="55" rx="7" fill="#888"/>
              <rect x="18" y="32" width="18" height="62" rx="7" fill="#888"/>
              <rect x="94" y="32" width="18" height="62" rx="7" fill="#888"/>
              <rect x="40" y="90" width="22" height="108" rx="7" fill="#888"/>
              <rect x="68" y="90" width="22" height="108" rx="7" fill="#888"/>
            </svg>
            <div class="cross-h"></div><div class="cross-v"></div>
            <div class="side-l">왼</div><div class="side-r">오른</div>
            <span class="seg s-normal" id="f-larm"  data-state="normal" style="left:18%;top:30%" onclick="cycle('f-larm')">표준</span>
            <span class="seg s-normal" id="f-rarm"  data-state="normal" style="left:82%;top:30%" onclick="cycle('f-rarm')">표준</span>
            <span class="seg s-normal" id="f-trunk" data-state="normal" style="left:50%;top:42%" onclick="cycle('f-trunk')">표준</span>
            <span class="seg s-normal" id="f-lleg"  data-state="normal" style="left:26%;top:72%" onclick="cycle('f-lleg')">표준</span>
            <span class="seg s-normal" id="f-rleg"  data-state="normal" style="left:74%;top:72%" onclick="cycle('f-rleg')">표준</span>
          </div>
          <div class="seg-hint">클릭하면 상태가 바뀌어요</div>
        </div>
      </div>
      <div class="seg-legend">
        <div class="seg-leg-item"><div class="seg-leg-dot" style="background:rgba(181,212,244,.7);border:1px solid #B5D4F4"></div>표준이하</div>
        <div class="seg-leg-item"><div class="seg-leg-dot" style="background:rgba(159,225,203,.7);border:1px solid #9FE1CB"></div>표준</div>
        <div class="seg-leg-item"><div class="seg-leg-dot" style="background:rgba(250,199,117,.7);border:1px solid #FAC775"></div>표준이상</div>
      </div>
    </div>

    <!-- 인바디 점수 -->
    <div class="card">
      <div class="card-title">인바디 점수 InBody Score</div>
      <div style="display:flex;align-items:center;gap:12px">
        <div style="flex:1;font-size:13px;color:var(--text-secondary);line-height:1.6">체성분을 종합해서 100점 만점으로 나타낸 점수예요. 근육이 매우 많은 경우 100점을 넘을 수도 있어요.</div>
        <div style="display:flex;align-items:baseline;gap:3px;flex-shrink:0">
          <input type="number" id="inbodyscore" placeholder="72" min="0" max="120" data-label="인바디 점수"
            style="width:66px;height:48px;font-size:28px;font-weight:700;text-align:center;border:.5px solid var(--border-strong);border-radius:8px;background:var(--bg);color:var(--text);font-family:'Noto Sans KR',sans-serif;transition:border-color .15s;--placeholder-color:rgba(180,180,180,0.35)">
          <style>#inbodyscore::placeholder{color:rgba(180,180,180,0.35)}</style>
          <span style="font-size:15px;color:var(--text-secondary)">/100</span>
        </div>
      </div>
    </div>

    <!-- 전신 위상각 -->
    <div class="card">
      <div class="card-title">전신 위상각 Phase Angle</div>
      <div style="margin-bottom:10px;font-size:13px;color:var(--text-secondary);line-height:1.6">세포의 건강 상태를 나타내는 지표예요. 숫자가 높을수록 세포가 더 건강하고 근육의 질이 좋다는 의미예요.</div>
      <div class="field"><label>전신 위상각 (°)</label><input type="number" id="phaseangle" placeholder="5.8" step="0.1" data-label="전신 위상각"></div>
    </div>

    <!-- 체중조절 -->
    <div class="card">
      <div class="card-title">체중조절 Weight Control</div>
      <div class="input-row">
        <div class="field"><label>적정체중 (kg)</label><input type="number" id="idealwt" placeholder="51.8" step="0.1" data-label="적정체중"></div>
        <div class="field"><label>체중조절 (kg)</label><input type="number" id="wtctrl" placeholder="-3.5" step="0.1" data-label="체중조절"></div>
      </div>
      <div class="input-row">
        <div class="field"><label>지방조절 (kg)</label><input type="number" id="fatctrl" placeholder="-5.7" step="0.1" data-label="지방조절"></div>
        <div class="field"><label>근육조절 (kg)</label><input type="number" id="musctrl" placeholder="+2.2" step="0.1" data-label="근육조절"></div>
      </div>
    </div>

    <!-- 내장지방레벨 -->
    <div class="card">
      <div class="card-title">내장지방레벨 &amp; 비만도</div>
      <div style="margin-bottom:10px;font-size:13px;color:var(--text-secondary);line-height:1.6">장기(위, 장, 간 등) 주변에 쌓인 지방의 양이에요. <strong style="color:var(--text)">1~9단계</strong>가 정상이에요.</div>
      <div class="input-row">
        <div class="field"><label>내장지방레벨</label><input type="number" id="vfat" placeholder="8" min="1" max="20" data-label="내장지방레벨"></div>
        <div class="field"><label>비만도 (%)</label><input type="number" id="obesity" placeholder="107" step="0.1" data-label="비만도"></div>
      </div>
    </div>

    <!-- 연구 항목 -->
    <div class="card">
      <div class="card-title">연구 항목 Research Parameters</div>
      <div class="input-row">
        <div class="field"><label>골격근량 (kg)</label><input type="number" id="muscle2" placeholder="20.3" step="0.1" data-label="연구 골격근량"></div>
        <div class="field"><label>제지방량 (kg)</label><input type="number" id="lbm" placeholder="17.6" step="0.1" data-label="제지방량"></div>
      </div>
      <div class="input-row">
        <div class="field"><label>기초대사량 (kcal)</label><input type="number" id="bmr" placeholder="1184" data-label="기초대사량"></div>
        <div class="field"><label>복부지방률</label><input type="number" id="visceral" placeholder="0.95" step="0.01" data-label="복부지방률"></div>
      </div>
      <div class="input-row">
        <div class="field"><label>권장섭취열량 (kcal)</label><input type="number" id="tdee" placeholder="2051" data-label="권장섭취열량"></div>
        <div class="field"></div>
      </div>
    </div>

    <div class="btn-row">
      <button class="btn-primary" onclick="validateAndNext()">다음 → 결과 분석</button>
    </div>
  </div>

  <!-- ══ STEP 1 ══ -->
  <div class="step" id="step1">
    <div class="step-eyebrow">Step 2 / 2</div>
    <div class="step-title">내 몸 분석 결과</div>
    <div class="step-desc">내가 입력한 수치들을 분석했어요. 천천히 읽어봐요.</div>
    <div id="analysisContent"></div>
    <div class="btn-row">
      <button class="btn-secondary" onclick="goStep(0)">← 수정</button>
    </div>
  </div>

  <!-- STEP 2, 3, 4 제거됨 — 성찰·계획은 학습지(워크시트)로 진행 -->

  <div class="footer">2026 지덕체 트레이닝 · 내 몸 바로 알기</div>
</div>


<script>
  let currentStep = 0;
  const TOTAL = 2;

  /* ── 토스트 ── */
  let toastTimer;
  function showToast(msg) {
    const t = document.getElementById('toast');
    t.textContent = msg;
    t.classList.add('show');
    clearTimeout(toastTimer);
    toastTimer = setTimeout(() => t.classList.remove('show'), 2800);
  }

  /* ── 합계 자동계산 ── */
  function updateSum() {
    const tbw  = parseFloat(document.getElementById('tbw').value)     || 0;
    const prot = parseFloat(document.getElementById('protein').value)  || 0;
    const min  = parseFloat(document.getElementById('mineral').value)  || 0;
    const fat  = parseFloat(document.getElementById('fat').value)      || 0;
    const wt   = parseFloat(document.getElementById('weight').value)   || 0;
    const sum  = tbw + prot + min + fat;
    const sumEl = document.getElementById('sumVal');
    const matchEl = document.getElementById('sumMatch');

    if (sum === 0) {
      sumEl.textContent = '? kg';
      matchEl.textContent = '체중 입력 후 비교';
      matchEl.className = 'comp-sum-result empty';
      return;
    }
    sumEl.textContent = sum.toFixed(2) + ' kg';
    if (wt === 0) {
      matchEl.textContent = '체중 입력 후 비교';
      matchEl.className = 'comp-sum-result empty';
      return;
    }
    const diff = Math.abs(sum - wt);
    if (diff <= 0.1) {
      matchEl.textContent = '✅ 체중과 일치해요!';
      matchEl.className = 'comp-sum-result match';
    } else if (diff <= 0.5) {
      matchEl.textContent = `⚠️ 체중과 ${diff.toFixed(2)}kg 차이나요`;
      matchEl.className = 'comp-sum-result close';
    } else {
      matchEl.textContent = `❌ ${diff.toFixed(2)}kg 차이 — 다시 확인해봐요`;
      matchEl.className = 'comp-sum-result far';
    }
  }

  /* ── 필수 입력 검증 ── */
  function validateAndNext() {
    // 이전 에러 초기화
    document.querySelectorAll('.error').forEach(el => el.classList.remove('error'));

    // 검사할 input/select id 목록 (부위별 클릭 제외, 체중2/fat2/muscle2는 별개 섹션이라 포함)
    const requiredIds = [
      'name','classnum','studentno','gender','age','height',
      'tbw','protein','mineral','fat','weight',
      'weight2','muscle','fat2',
      'bmi','fatpct',
      'inbodyscore','phaseangle',
      'idealwt','wtctrl','fatctrl','musctrl',
      'vfat','obesity',
      'muscle2','lbm','bmr','visceral','tdee'
    ];

    let firstEmpty = null;
    const emptyLabels = [];

    requiredIds.forEach(id => {
      const el = document.getElementById(id);
      if (!el) return;
      const val = el.value.trim();
      if (!val || val === '') {
        el.classList.add('error');
        emptyLabels.push(el.dataset.label || id);
        if (!firstEmpty) firstEmpty = el;
      }
    });

    if (firstEmpty) {
      // 첫 번째 빈 칸으로 스크롤
      firstEmpty.scrollIntoView({ behavior: 'smooth', block: 'center' });
      // 토스트
      const label = firstEmpty.dataset.label || '항목';
      showToast(`📝 "${label}"을(를) 입력해주세요`);
      // 포커스
      setTimeout(() => firstEmpty.focus(), 400);
      return;
    }

    // 에러 없으면 다음으로
    goStep(1);
  }

  /* 에러 칸 클릭 시 에러 해제 */
  document.addEventListener('input', e => {
    if (e.target.classList.contains('error')) e.target.classList.remove('error');
  });
  document.addEventListener('change', e => {
    if (e.target.classList.contains('error')) e.target.classList.remove('error');
  });

  /* ── 스텝 이동 ── */
  function goStep(n) {
    document.getElementById('step' + currentStep).classList.remove('active');
    currentStep = n;
    document.getElementById('step' + n).classList.add('active');
    for (let i = 0; i < TOTAL; i++) {
      const ps = document.getElementById('ps' + i), pl = document.getElementById('pl' + i);
      if (!ps) continue;
      ps.classList.remove('active','done'); pl && pl.classList.remove('active');
      if (i < n) ps.classList.add('done');
      else if (i === n) { ps.classList.add('active'); pl && pl.classList.add('active'); }
    }
    if (n === 1) renderAnalysis();
    window.scrollTo({ top: 0, behavior: 'smooth' });
  }

  /* ── 부위별 ── */
  const SS=['none','under','normal','over'];
  const SL={none:'—',under:'표준이하',normal:'표준',over:'표준이상'};
  const SC={none:'s-none',under:'s-under',normal:'s-normal',over:'s-over'};
  function cycle(id) {
    const el = document.getElementById(id);
    const next = SS[(SS.indexOf(el.dataset.state||'normal')+1)%SS.length];
    el.dataset.state = next; el.className = 'seg '+SC[next]; el.textContent = SL[next];
  }

  function gv(id) { return parseFloat(document.getElementById(id)?.value) || 0; }
  function gs(id) { return (document.getElementById(id)?.value || '').trim(); }
  function segTxt(id) { return SL[document.getElementById(id)?.dataset.state||'none']||'—'; }
  function hl(txt,type){ const m={good:'hl-good',warn:'hl-warn',danger:'hl-danger',info:'hl-info'}; return `<span class="hl ${m[type]||'hl-info'}">${txt}</span>`; }

  function bmiStatus(v){ if(v<18.5)return{t:'저체중',c:'badge-info',type:'info'}; if(v<23)return{t:'정상',c:'badge-good',type:'good'}; if(v<25)return{t:'과체중',c:'badge-warn',type:'warn'}; return{t:'비만',c:'badge-danger',type:'danger'}; }
  function fatStatus(v,g){ const m=g==='male'; if(m){if(v<10)return{t:'부족',c:'badge-info',type:'info'};if(v<=20)return{t:'정상',c:'badge-good',type:'good'};if(v<=25)return{t:'약간높음',c:'badge-warn',type:'warn'};return{t:'높음',c:'badge-danger',type:'danger'};}else{if(v<18)return{t:'부족',c:'badge-info',type:'info'};if(v<=28)return{t:'정상',c:'badge-good',type:'good'};if(v<=33)return{t:'약간높음',c:'badge-warn',type:'warn'};return{t:'높음',c:'badge-danger',type:'danger'};} }
  function muscleStatus(m,g,w){ if(!w)return{t:'—',c:'badge-info',type:'info'}; const r=(m/w)*100,norm=g==='male'?44:37; if(r>=norm+5)return{t:'우수',c:'badge-good',type:'good'}; if(r>=norm)return{t:'보통',c:'badge-info',type:'info'}; return{t:'부족',c:'badge-warn',type:'warn'}; }

  function itemCard(icon,bg,name,eng,valueStr,badgeTxt,badgeCls,blockType,summaryHtml,explainHtml){
    const bgMap={good:'var(--green-light)',warn:'var(--amber-light)',danger:'var(--red-light)',info:'var(--blue-light)'};
    const colorMap={good:'var(--green-dark)',warn:'var(--amber)',danger:'var(--red)',info:'var(--blue)'};
    return`<div class="item-card">
      <div class="item-header">
        <div class="item-icon" style="background:${bg}">${icon}</div>
        <div><div class="item-name">${name}</div><div class="item-eng">${eng}</div></div>
        ${badgeTxt?`<span class="badge ${badgeCls}" style="margin-left:auto">${badgeTxt}</span>`:''}
      </div>
      <div class="item-value">${valueStr}</div>
      <div class="block" style="background:${bgMap[blockType]||bgMap.info}">
        <div class="block-label" style="color:${colorMap[blockType]||colorMap.info}">📌 총평</div>
        <div class="block-text">${summaryHtml}</div>
      </div>
      <div class="block" style="background:var(--bg-secondary)">
        <div class="block-label" style="color:var(--text-secondary)">💬 이게 무슨 뜻이야?</div>
        <div class="block-text">${explainHtml}</div>
      </div>
    </div>`; }

  function adviceRows(rows){
    return rows.map(r=>`<div class="advice-row"><div class="advice-dot" style="background:${r.color}"></div><div><div class="advice-text">${r.text}</div><div class="advice-sub">${r.sub}</div></div></div>`).join('');
  }

  function renderAnalysis() {
    const name=gs('name'), gender=gs('gender'), isMale=gender==='male';
    const bmi=gv('bmi'), fatpct=gv('fatpct');
    const muscle=gv('muscle')||gv('muscle2');
    const weight=gv('weight')||gv('weight2');
    const fat=gv('fat')||gv('fat2')||gv('lbm');
    const bmr=gv('bmr'), visceral=gv('visceral'), vfat=gv('vfat');
    const protein=gv('protein'), tbw=gv('tbw'), mineral=gv('mineral');
    const tdee=gv('tdee'), score=gv('inbodyscore');
    const idealwt=gv('idealwt'), wtctrl=gv('wtctrl'), fatctrl=gv('fatctrl'), musctrl=gv('musctrl');
    const obesity=gv('obesity');

    const bmiS=bmiStatus(bmi), fatS=fatStatus(fatpct,gender), muscleS=muscleStatus(muscle,gender,weight);

    function overallGrade(){
      let good=0,warn=0,bad=0;
      [bmiS,fatS,muscleS].forEach(s=>{if(s.type==='good')good++;else if(s.type==='warn')warn++;else if(s.type==='danger')bad++;});
      if(visceral>(isMale?0.9:0.85))bad++;
      if(vfat>=10)warn++;
      if(bad>=2)return{grade:'지금 당장 바꿔야 할 때야!',type:'danger',emoji:'⚠️',msg:'몸 여러 곳에서 경고 신호가 오고 있어. 나쁜 소식은 아니야 — 지금 알았으니까 지금부터 바꾸면 돼.'};
      if(bad>=1||warn>=2)return{grade:'조금씩 관리가 필요해',type:'warn',emoji:'💛',msg:'전체적으로 나쁘지 않지만, 몇 가지 항목에서 주의 신호가 있어. 지금 습관을 조금만 바꾸면 충분히 좋아질 수 있어.'};
      if(good>=2)return{grade:'잘 관리되고 있어!',type:'good',emoji:'✅',msg:'전반적으로 몸 상태가 좋은 편이야. 지금처럼만 유지하면 돼. 근데 방심은 금물 — 꾸준히 챙기는 게 중요해.'};
      return{grade:'보통 수준이야',type:'info',emoji:'💙',msg:'크게 걱정할 부분은 없지만, 좀 더 신경 쓰면 훨씬 좋아질 수 있어. 작은 습관 하나씩 바꿔봐.'};
    }
    const og=overallGrade();
    const bgMap={good:'var(--green-light)',warn:'var(--amber-light)',danger:'var(--red-light)',info:'var(--blue-light)'};
    const colorMap={good:'var(--green-dark)',warn:'var(--amber)',danger:'var(--red)',info:'var(--blue)'};
    const borderMap={good:'var(--green)',warn:'var(--amber-mid)',danger:'var(--red-mid)',info:'var(--blue-mid)'};

    let itemsHTML='';

    // BMI
    const bmiSum=(()=>{ const t={저체중:`${hl('저체중','info')}이야. 키에 비해 몸무게가 너무 가벼운 상태야.`,정상:`${hl('딱 정상','good')}이야! 키랑 몸무게 비율이 건강한 수준이야.`,과체중:`${hl('과체중','warn')}이야. 키에 비해 몸무게가 살짝 무거운 상태야.`,비만:`${hl('비만','danger')}이야. 체중 관리가 필요한 시점이야.`}; return t[bmiS.t]||t['정상']; })();
    const bmiExp=`<strong>BMI</strong>는 몸무게(kg)를 키(m)의 제곱으로 나눈 숫자야.<br><br>
근데 BMI에는 큰 함정이 있어. <strong>근육이랑 지방을 구분 못 해.</strong> 운동을 엄청 해서 근육이 많은 사람도 BMI는 높게 나올 수 있거든. 그래서 BMI만 보지 말고 체지방률이랑 같이 봐야 정확해.<br><br>청소년 정상 범위: <strong>18.5 ~ 22.9</strong>`;
    itemsHTML+=itemCard('⚖️','var(--blue-light)','BMI','Body Mass Index · 체질량지수',bmi.toFixed(1),bmiS.t,bmiS.c,bmiS.type,bmiSum,bmiExp);

    // 체지방률
    const fatNormal=isMale?'10~20%':'18~28%';
    const fatSum=(()=>{ if(fatS.t==='부족')return`체지방이 ${hl('너무 적어','info')}. 지방도 몸에 꼭 필요해! 없으면 호르몬이 망가지고 면역력도 떨어져.`; if(fatS.t==='정상')return`${hl('딱 정상','good')}이야! 지방 비율이 건강한 수준이야. 지금처럼 유지하면 돼.`; if(fatS.t==='약간높음')return`${hl('조금 높은 편','warn')}이야. 유산소 운동이랑 식단 조절을 하면 충분히 줄일 수 있어.`; return`${hl('높아','danger')}. 지방이 많으면 심장이나 혈관에 무리가 가고, 나중에 당뇨 같은 병에 걸릴 위험이 높아져.`; })();
    const fatExp=`<strong>체지방률</strong>은 내 몸무게 중에서 지방이 얼마나 차지하는지 보여주는 숫자야.<br><br>
지방은 무조건 나쁜 게 아니야. 적당한 지방은 <strong>에너지를 저장</strong>하고, 몸을 따뜻하게 보호하고, 장기를 충격에서 지켜줘. 문제는 <strong>너무 많을 때</strong>야.<br><br>
특히 <strong>내장 지방</strong>이 많으면 심장병, 당뇨, 고혈압 위험이 높아져.<br><br>${isMale?'남자':'여자'} 정상 범위: <strong>${fatNormal}</strong>`;
    itemsHTML+=itemCard('🔥','var(--red-light)','체지방률','Percent Body Fat',fatpct.toFixed(1)+'%',fatS.t,fatS.c,fatS.type,fatSum,fatExp);

    // 골격근량
    const muscleSum=(()=>{ if(muscleS.t==='우수')return`근육량이 ${hl('우수한 편','good')}이야! 기초대사량도 높고 체력도 좋을 거야. 계속 유지해봐.`; if(muscleS.t==='보통')return`${hl('보통 수준','info')}이야. 나쁘지 않지만, 꾸준히 운동하면 더 올릴 수 있어.`; return`근육이 ${hl('부족한 편','warn')}이야. 청소년 때가 근육 만들기 <strong>가장 좋은 시기</strong>야. 지금 운동이 제일 효과 있어!`; })();
    const muscleExp=`<strong>골격근량</strong>은 팔, 다리, 배 같은 곳에 붙어있는 근육의 무게야.<br><br>
근육이 많으면 <strong>기초대사량</strong>이 올라가. 기초대사량이란 아무것도 안 하고 누워 있어도 몸이 알아서 소비하는 칼로리야. 근육이 많으면 가만히 있어도 살이 덜 찌는 몸이 되는 거야!<br><br>
청소년기에 근육량을 늘려두는 게 평생 건강의 기초가 돼.<br><br>💪 대표 운동: 걷기, 스쿼트, 팔굽혀펴기, 계단 오르기`;
    itemsHTML+=itemCard('💪','var(--green-light)','골격근량','Skeletal Muscle Mass',muscle.toFixed(1)+'kg',muscleS.t,muscleS.c,muscleS.type,muscleSum,muscleExp);

    // 체성분
    if(tbw||protein||mineral){
      let lines=[];
      if(tbw){ const pct=weight?(tbw/weight*100):0; const st=pct<50?hl('낮은 편','warn'):pct>65?hl('높은 편','info'):hl('적당해','good'); lines.push(`<strong>💧 체수분 ${tbw}L</strong> — 몸의 약 ${pct.toFixed(0)}%가 물이야. ${st}<br>물은 영양분을 온몸에 운반하고, 체온을 조절하고, 노폐물을 배출해. 혈액도 체수분에 포함돼.<br>물이 부족하면 쉽게 피곤하고 집중력이 떨어져. 하루 ${isMale?'2L':'1.5~2L'} 이상 물 마시기!`); }
      if(protein){ const ideal=weight?weight*0.15:0; const st=protein<ideal-1?hl('좀 부족해','warn'):hl('적당해','good'); lines.push(`<strong>🥩 단백질 ${protein}kg</strong> — ${st}<br>단백질은 근육, 피부, 머리카락, 손톱 등 <strong>우리 몸을 구성하는 가장 중요한 재료</strong>야.<br>소고기, 돼지고기, 닭고기, 콩, 생선, 달걀에 많이 들어있어.`); }
      if(mineral){ const ideal=weight?weight*0.04:0; const st=mineral<ideal-0.3?hl('좀 부족해','warn'):hl('적당해','good'); lines.push(`<strong>🦴 무기질 ${mineral}kg</strong> — ${st}<br>뼈와 치아를 형성하는 핵심 성분이야. 지금 청소년기가 뼈가 완성되는 가장 중요한 시기야!<br>달걀 노른자, 해조류, 진한 녹색 채소, 우유에 많아.`); }
      itemsHTML+=itemCard('🧬','var(--blue-light)','체성분 구성','Body Composition',tbw?`체수분 ${tbw}L`:'—','','badge-info','info','체수분·단백질·무기질, 이 세 가지가 몸을 건강하게 유지하는 기본 재료야.',lines.join('<br><br>'));
    }

    // 기초대사량
    if(bmr){ const t=bmr<1200?'warn':bmr>=1500?'good':'info'; const s=bmr<1200?`기초대사량이 ${hl('낮은 편','warn')}이야. 근육을 늘리면 같이 올라가.`:bmr>=1500?`기초대사량이 ${hl('높은 편','good')}이야! 근육이 많다는 신호.`:`${hl('평균 수준','info')}이야.`; itemsHTML+=itemCard('⚡','var(--amber-light)','기초대사량','Basal Metabolic Rate',`${bmr} kcal`,'','badge-info',t,s,`<strong>기초대사량</strong>이란 아무것도 안 해도 숨만 쉬고 누워있어도 몸이 하루에 이만큼 칼로리를 쓴다는 뜻이야.<br><br><strong>근육이 많을수록 기초대사량이 높아져</strong>. 근육이 많으면 가만히 있어도 살이 덜 쪄.${tdee?`<br><br>네 권장섭취열량은 <strong>${tdee} kcal</strong>야. 이보다 훨씬 많이 먹으면 남은 게 지방으로 쌓여.`:''}`); }

    // 복부지방·내장지방
    if(visceral||vfat){ const lim=isMale?0.9:0.85; const vt=visceral>lim+0.1?'danger':visceral>lim?'warn':'good'; const vs=visceral?(visceral>lim+0.1?`복부지방률이 ${hl('많이 높아','danger')}. 뱃살은 건강에 제일 안 좋은 지방이야.`:visceral>lim?`정상보다 ${hl('조금 높아','warn')}. 뱃살이 쌓이기 시작하는 신호야.`:`${hl('정상 범위','good')}야!`):'내장지방 확인 중'; itemsHTML+=itemCard('📍','var(--amber-light)','복부지방률·내장지방','Visceral Fat',visceral?visceral.toString():(vfat?`Lv.${vfat}`:'—'),'','badge-info',vt,vs,`배 주변 지방은 심장병, 당뇨, 고혈압과 직접 연결돼 있어서 <strong>가장 위험한 지방</strong>으로 꼽혀.<br><br>${vfat?`<strong>내장지방레벨 ${vfat}단계</strong> — ${vfat>=10?hl('정상(1~9)보다 높아. 위험 신호야!','danger'):hl('정상 범위','good')}<br><br><strong>내장지방 줄이는 방법:</strong><br>① 탄수화물과 당분 섭취 줄이기 (탄산음료, 과자, 단 음식)<br>② 식후에 앉아있지 말고 10~15분 걷기<br>③ 야식 줄이기<br>④ 유산소 운동 주 3회 이상`:''}`); }

    // 체중조절
    if(idealwt){ const wt2=Math.abs(wtctrl)<=1?'good':Math.abs(wtctrl)<=4?'warn':'danger'; const ws=Math.abs(wtctrl)<=1?`${hl('적정체중에 매우 가까워','good')}! 지금 체중을 유지하면 돼.`:`적정체중까지 ${hl(`${Math.abs(wtctrl).toFixed(1)}kg ${wtctrl<0?'감량':'증량'}`,wt2)} 필요해.`; itemsHTML+=itemCard('🎯','var(--green-light)','체중조절 목표','Weight Control',`적정 ${idealwt}kg`,'','badge-info',wt2,ws,`<strong>적정체중 ${idealwt}kg</strong>은 네 키와 나이에 맞는 이상적인 몸무게야.<br><br>${wtctrl!==0?`지금보다 <strong>${Math.abs(wtctrl).toFixed(1)}kg ${wtctrl<0?'줄여야':'늘려야'}</strong> 해.<br>`:''}${fatctrl?`지방 <strong>${Math.abs(fatctrl).toFixed(1)}kg ${fatctrl<0?'줄이고':'늘리고'}</strong>`:''}${musctrl?`, 근육 <strong>${Math.abs(musctrl).toFixed(1)}kg ${musctrl<0?'줄이면':'늘리면'}</strong> 도달해.`:''}<br><br>⚠️ 절대 급하게 굶으면 안 돼. 갑자기 밥을 안 먹으면 <strong>근육이 먼저 빠지고</strong>, 기초대사량이 낮아져서 오히려 더 살찌기 쉬운 몸이 돼.`); }

    /* 운동 조언 */
    function buildEx(){
      const r=[];
      if(muscleS.t==='부족'){ r.push({color:'var(--green)',text:'근력 운동을 시작해야 해.',sub:'팔굽혀펴기, 스쿼트, 런지처럼 도구 없이 할 수 있는 운동부터! 주 2~3회, 하루 20~30분이면 충분해.'}); r.push({color:'var(--green)',text:'일상에서 쉽게 할 수 있는 운동 3가지',sub:'① <strong>걷기</strong> — 빠르게 걷거나 경사진 곳 걷기<br>② <strong>의자 스쿼트</strong> — 앉았다 일어나기 반복. 하체 근육 강화<br>③ <strong>계단 오르기</strong> — 엘리베이터 대신 계단! 하체+심폐 동시'}); }
      else if(muscleS.t==='보통') r.push({color:'var(--green)',text:'지금 운동 습관 유지하면서 강도 올려봐.',sub:'횟수를 늘리거나 강도를 높이면 더 빠르게 좋아질 거야.'});
      else r.push({color:'var(--green)',text:'근육 상태 좋아! 지금 루틴을 유지해.',sub:'꾸준함이 제일 중요해. 운동을 갑자기 줄이면 근육이 빠르게 빠져.'});
      if(fatS.t==='높음'||fatS.t==='약간높음'){ r.push({color:'var(--amber-mid)',text:'유산소 운동을 추가해야 해.',sub:'걷기, 줄넘기, 자전거, 수영 — 주 3~5회 30분씩. 체지방 줄이는 데 제일 효과적이야.'}); r.push({color:'var(--amber-mid)',text:'생활 속 작은 운동 습관',sub:'엘리베이터 대신 계단, 버스 한 정거장 일찍 내리기. 하루 8000보 이상 목표!'}); }
      if(vfat>=10) r.push({color:'var(--red-mid)',text:'내장지방엔 유산소 운동이 최고야.',sub:'뱃살은 식단+유산소 조합으로 빠져. 오늘부터 하루 30분 걷기, 식후 걷기가 특히 효과 있어!'});
      const up=[]; if(segTxt('m-lleg')==='표준이하'||segTxt('m-rleg')==='표준이하')up.push('다리(스쿼트, 런지, 계단)'); if(segTxt('m-larm')==='표준이하'||segTxt('m-rarm')==='표준이하')up.push('팔(팔굽혀펴기, 물병 들기)'); if(segTxt('m-trunk')==='표준이하')up.push('몸통·코어(플랭크, 윗몸일으키기)');
      if(up.length) r.push({color:'var(--green)',text:`${up.map(p=>p.split('(')[0]).join(', ')} 집중 운동 필요!`,sub:up.map(p=>`• <strong>${p.split('(')[0]}</strong>: ${p.match(/\((.+)\)/)?.[1]||''}`).join('<br>')});
      if(r.length===0) r.push({color:'var(--green)',text:'전반적으로 근육 상태 좋아!',sub:'지금처럼 꾸준히 운동하면 돼.'});
      return r;
    }

    /* 식단 조언 */
    function buildDiet(){
      const r=[];
      if(tbw&&weight){ const p=tbw/weight*100; if(p<55)r.push({color:'var(--blue-mid)',text:'물을 더 마셔야 해.',sub:`체수분 비율 ${p.toFixed(0)}%로 낮아. 하루 ${isMale?'2L':'1.5~2L'} 물(음료수 말고 진짜 물!) 마시기 목표!`}); else r.push({color:'var(--blue-mid)',text:'체수분 상태 양호해.',sub:'물을 꾸준히 마시고 있어. 운동할 때는 더 많이 마셔.'}); }
      if(protein&&weight){ const ideal=weight*0.15; if(protein<ideal-1)r.push({color:'var(--green)',text:'단백질을 더 먹어야 해.',sub:'달걀, 닭가슴살, 두부, 콩, 우유에 단백질이 많아. 운동 후 단백질 식품 꼭 챙겨 먹어봐.'}); else r.push({color:'var(--green)',text:'단백질 섭취 OK.',sub:'현재 수준 적당해. 근력 운동 한다면 조금 더 먹어도 좋아.'}); }
      if(mineral&&weight){ const ideal=weight*0.04; if(mineral<ideal-0.3)r.push({color:'var(--blue-mid)',text:'무기질(미네랄)이 좀 부족해.',sub:'달걀 노른자, 해조류(미역, 김), 브로콜리, 우유에 무기질이 많아. 뼈가 완성되는 청소년기에 꼭 챙겨야 해!'}); }
      if(fat&&weight){ const ideal=weight*(isMale?0.15:0.23); if(fat>ideal+3)r.push({color:'var(--amber-mid)',text:'기름진 음식이랑 단 음식 줄여야 해.',sub:'튀긴 음식, 패스트푸드, 과자, 음료수 — 이것만 줄여도 체지방이 확 줄어들어.'}); else if(fat<ideal-3)r.push({color:'var(--amber-mid)',text:'지방을 아예 안 먹으면 안 돼.',sub:'견과류, 아보카도 같은 건강한 지방은 꼭 먹어야 해. 뇌 발달이랑 호르몬에 필수야.'}); }
      if(vfat>=10) r.push({color:'var(--red-mid)',text:'탄수화물이랑 당분부터 줄여야 해.',sub:'탄산음료, 과자, 단 빵 — 이게 내장지방의 주범이야. 식사 후엔 바로 걸어봐.'});
      if(wtctrl<-3) r.push({color:'var(--amber-mid)',text:'급하게 굶으면 절대 안 돼.',sub:'갑자기 밥을 안 먹으면 근육이 먼저 빠지고 기초대사량이 낮아져서 오히려 더 살찌기 쉬운 몸이 돼.'});
      if(tdee) r.push({color:'var(--green)',text:`하루 권장섭취열량: ${tdee} kcal`,sub:'밥이랑 간식 합쳐서 이 정도가 하루 목표야. 무리한 다이어트보다 이 숫자를 기준으로 조절해봐!'});
      if(r.length===0) r.push({color:'var(--green)',text:'식단 상태 전반적으로 좋아!',sub:'채소, 단백질, 탄수화물 골고루 먹는 지금 식습관 유지해봐.'});
      return r;
    }

    document.getElementById('analysisContent').innerHTML = `
      <div class="card" style="border-color:${borderMap[og.type]};background:${bgMap[og.type]}">
        <div style="display:flex;align-items:center;gap:10px;margin-bottom:12px">
          <div style="font-size:28px">${og.emoji}</div>
          <div>
            <div style="font-size:11px;font-weight:700;letter-spacing:.08em;color:${colorMap[og.type]};text-transform:uppercase">종합 총평</div>
            <div style="font-size:18px;font-weight:700;color:${colorMap[og.type]};letter-spacing:-.01em">${og.grade}</div>
          </div>
          ${score?`<div style="margin-left:auto;text-align:center"><div style="font-size:32px;font-weight:900;color:${colorMap[og.type]};line-height:1">${score}</div><div style="font-size:11px;color:${colorMap[og.type]}">/100점</div></div>`:''}
        </div>
        <div style="font-size:14px;color:${colorMap[og.type]};line-height:1.8">${og.msg}</div>
        ${idealwt?`<div style="margin-top:10px;padding:8px 10px;background:rgba(255,255,255,.4);border-radius:7px;font-size:13px;color:${colorMap[og.type]}">적정체중 <strong>${idealwt}kg</strong> — 지금보다 ${Math.abs(wtctrl).toFixed(1)}kg ${wtctrl<0?'감량':'증량'} 목표</div>`:''}
      </div>
      <div style="font-size:13px;font-weight:700;color:var(--text-secondary);letter-spacing:.04em;margin:4px 0 8px">📊 항목별 수치 분석</div>
      ${itemsHTML}
      <div class="advice-section">
        <div class="advice-section-header">
          <div class="advice-section-icon" style="background:var(--green-light)">🏃</div>
          <div><div class="advice-section-title">운동 조언</div><div class="advice-section-sub">골격근량 · 부위별 분석 기반 맞춤 가이드</div></div>
        </div>
        ${adviceRows(buildEx())}
      </div>
      <div class="advice-section">
        <div class="advice-section-header">
          <div class="advice-section-icon" style="background:var(--blue-light)">🥗</div>
          <div><div class="advice-section-title">식단 조언</div><div class="advice-section-sub">체수분 · 단백질 · 무기질 · 체지방 기반 가이드</div></div>
        </div>
        ${adviceRows(buildDiet())}
      </div>`;
  }

  function addPlan(containerId, cls, placeholder) {
    const c = document.getElementById(containerId);
    const d = document.createElement('div');
    d.style.cssText = 'display:flex;gap:8px;margin-bottom:7px';
    d.innerHTML = `<input type="text" placeholder="${placeholder}" class="${cls}" style="flex:1;height:38px;border:.5px solid var(--border-strong);border-radius:7px;padding:0 10px;font-size:13px;color:var(--text);background:var(--bg);font-family:'Noto Sans KR',sans-serif">`;
    c.appendChild(d);
    d.querySelector('input').focus();
  }

  function getPlanTexts(cls) {
    return Array.from(document.querySelectorAll('.'+cls)).map(i=>i.value.trim()).filter(Boolean);
  }

  function showSummary() {
    const name = gs('name')||'학생';
    const classnum = gs('classnum'), studentno = gs('studentno');
    const classno = classnum&&studentno?`${classnum} ${studentno}번`:classnum||'';
    const bmi=gv('bmi'), fatpct=gv('fatpct');
    const muscle=gv('muscle')||gv('muscle2');
    const weight=gv('weight')||gv('weight2');
    const bmr=gv('bmr'), visceral=gv('visceral'), vfat=gv('vfat');
    const score=gv('inbodyscore'), gender=gs('gender');
    const today=new Date().toLocaleDateString('ko-KR');
    const bmiS=bmiStatus(bmi), fatS=fatStatus(fatpct,gender), muscleS=muscleStatus(muscle,gender,weight);
    const ep=getPlanTexts('ep-input'), fp=getPlanTexts('fp-input'), lp=getPlanTexts('lp-input');
    const goal=gs('goal1');
    const segRows=[['왼팔',segTxt('m-larm'),segTxt('f-larm')],['오른팔',segTxt('m-rarm'),segTxt('f-rarm')],['몸통',segTxt('m-trunk'),segTxt('f-trunk')],['왼다리',segTxt('m-lleg'),segTxt('f-lleg')],['오른다리',segTxt('m-rleg'),segTxt('f-rleg')]];
    const mkRows=(items,color)=>items.map(t=>`<div style="display:flex;align-items:center;gap:8px;font-size:13px;color:var(--text);padding:4px 0"><div style="width:5px;height:5px;border-radius:50%;background:${color};flex-shrink:0"></div>${t}</div>`).join('');

    document.getElementById('step4').innerHTML=`
      <div class="step-eyebrow">완료!</div>
      <div class="step-title">나의 자기관리 계획서</div>
      <div class="step-desc">작성이 완료되었어요. 화면을 캡처하거나 인쇄해서 선생님께 제출하세요.</div>
      <div class="card">
        <div class="summary-doc-header">
          <div class="summary-eyebrow">2026 · 3학년 지덕체 트레이닝</div>
          <div class="summary-title">내 몸 바로 알기 — 자기관리 계획서</div>
          <div class="summary-meta">${classno?classno+' · ':''}${name} · ${today}</div>
        </div>
        <div class="summary-section">
          <h3>체성분 결과</h3>
          ${score?`<div class="summary-row"><span class="lbl">인바디 점수</span><span class="val" style="color:var(--green);font-weight:700;font-size:16px">${score}점 / 100점</span></div>`:''}
          <div class="summary-row"><span class="lbl">체중</span><span class="val">${weight} kg</span></div>
          <div class="summary-row"><span class="lbl">BMI</span><span class="val">${bmi.toFixed(1)} &nbsp;<span class="badge ${bmiS.c}">${bmiS.t}</span></span></div>
          <div class="summary-row"><span class="lbl">체지방률</span><span class="val">${fatpct.toFixed(1)}% &nbsp;<span class="badge ${fatS.c}">${fatS.t}</span></span></div>
          <div class="summary-row"><span class="lbl">골격근량</span><span class="val">${muscle.toFixed(1)} kg &nbsp;<span class="badge ${muscleS.c}">${muscleS.t}</span></span></div>
          <div class="summary-row"><span class="lbl">기초대사량</span><span class="val">${bmr} kcal</span></div>
          <div class="summary-row"><span class="lbl">복부지방률 / 내장지방</span><span class="val">${visceral} / Lv.${vfat}</span></div>
        </div>
        <div class="summary-section">
          <h3>부위별 분석</h3>
          <div style="display:grid;grid-template-columns:1fr 1fr 1fr;font-size:12px">
            <div style="padding:5px 0;color:var(--text-secondary);font-weight:500">부위</div>
            <div style="padding:5px 0;color:var(--text-secondary);font-weight:500;text-align:center">근육</div>
            <div style="padding:5px 0;color:var(--text-secondary);font-weight:500;text-align:center">체지방</div>
            ${segRows.map(r=>`<div style="padding:5px 0;border-top:.5px solid var(--border);color:var(--text-secondary)">${r[0]}</div><div style="padding:5px 0;border-top:.5px solid var(--border);text-align:center;color:var(--text);font-weight:500">${r[1]}</div><div style="padding:5px 0;border-top:.5px solid var(--border);text-align:center;color:var(--text);font-weight:500">${r[2]}</div>`).join('')}
          </div>
        </div>
        <div class="summary-section">
          <h3>나의 생각</h3>
          <div class="smr-note"><strong style="color:var(--text);font-weight:500">놀랐던 점: </strong>${gs('r1')||'—'}</div>
          <div class="smr-note" style="margin-top:5px"><strong style="color:var(--text);font-weight:500">현재 습관: </strong>${gs('r2')||'—'}</div>
          <div class="smr-note" style="margin-top:5px"><strong style="color:var(--text);font-weight:500">개선 목표: </strong>${gs('r3')||'—'}</div>
        </div>
        <div class="summary-section">
          <h3>4주 실천 계획</h3>
          ${ep.length?`<div style="margin-bottom:10px"><div style="font-size:11px;font-weight:700;color:var(--green);letter-spacing:.06em;margin-bottom:4px">운동</div>${mkRows(ep,'var(--green)')}</div>`:''}
          ${fp.length?`<div style="margin-bottom:10px"><div style="font-size:11px;font-weight:700;color:var(--blue);letter-spacing:.06em;margin-bottom:4px">식습관</div>${mkRows(fp,'var(--blue-mid)')}</div>`:''}
          ${lp.length?`<div style="margin-bottom:10px"><div style="font-size:11px;font-weight:700;color:var(--amber);letter-spacing:.06em;margin-bottom:4px">생활습관</div>${mkRows(lp,'var(--amber-mid)')}</div>`:''}
        </div>
        ${goal?`<div class="summary-section"><h3>한 달 후 목표</h3><div class="smr-note">${goal}</div></div>`:''}
        <div class="finish-note">계획을 세웠으니 이제 실천이 중요해요!<br>작은 것부터 꾸준히 — 4주 후 변화를 기대해봐요 💪</div>
      </div>
      <div class="btn-row">
        <button class="btn-secondary" onclick="location.reload()">← 처음부터</button>
        <button class="btn-primary" onclick="window.print()">🖨️ 인쇄 / 저장</button>
      </div>`;

    for(let i=0;i<TOTAL;i++){
      const ps=document.getElementById('ps'+i),pl=document.getElementById('pl'+i);
      if(ps){ps.classList.remove('active');ps.classList.add('done');}
      if(pl)pl.classList.remove('active');
    }
    document.getElementById('step3').classList.remove('active');
    currentStep=4;
    document.getElementById('step4').classList.add('active');
    window.scrollTo({top:0,behavior:'smooth'});
  }
</script>
</body>
</html>
