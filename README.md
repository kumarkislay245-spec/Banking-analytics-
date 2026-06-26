<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Banking Analytics Banner</title>
<style>
  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    width: 1200px;
    background: #0a0f1e;
    font-family: 'Segoe UI', system-ui, sans-serif;
    overflow: hidden;
  }

  .banner {
    width: 1200px;
    height: 400px;
    background: linear-gradient(135deg, #0a0f1e 0%, #0d1b35 50%, #0a0f1e 100%);
    position: relative;
    overflow: hidden;
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding: 48px 64px;
  }

  /* grid lines background */
  .banner::before {
    content: '';
    position: absolute;
    inset: 0;
    background-image:
      linear-gradient(rgba(30,144,255,0.05) 1px, transparent 1px),
      linear-gradient(90deg, rgba(30,144,255,0.05) 1px, transparent 1px);
    background-size: 48px 48px;
  }

  /* glow orbs */
  .orb {
    position: absolute;
    border-radius: 50%;
    filter: blur(80px);
    pointer-events: none;
  }
  .orb-1 { width: 360px; height: 360px; background: rgba(29,100,255,0.18); top: -80px; right: 160px; }
  .orb-2 { width: 240px; height: 240px; background: rgba(0,200,130,0.12); bottom: -60px; right: 60px; }
  .orb-3 { width: 200px; height: 200px; background: rgba(120,40,255,0.10); top: 40px; left: 500px; }

  /* top badge */
  .badge {
    display: inline-flex;
    align-items: center;
    gap: 7px;
    background: rgba(29,100,255,0.15);
    border: 1px solid rgba(29,100,255,0.35);
    border-radius: 99px;
    padding: 5px 14px;
    font-size: 12px;
    color: #60a5fa;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    font-weight: 600;
    margin-bottom: 20px;
    width: fit-content;
  }
  .badge-dot {
    width: 6px; height: 6px;
    background: #3b82f6;
    border-radius: 50%;
    box-shadow: 0 0 6px #3b82f6;
  }

  /* main title */
  .title {
    font-size: 52px;
    font-weight: 700;
    color: #ffffff;
    line-height: 1.1;
    letter-spacing: -0.02em;
    margin-bottom: 8px;
  }
  .title span {
    background: linear-gradient(90deg, #3b82f6, #06b6d4);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }

  /* subtitle */
  .subtitle {
    font-size: 16px;
    color: #94a3b8;
    margin-bottom: 36px;
    font-weight: 400;
    max-width: 560px;
    line-height: 1.5;
  }

  /* pipeline */
  .pipeline {
    display: flex;
    align-items: center;
    gap: 0;
  }

  .pipe-step {
    display: flex;
    align-items: center;
    gap: 10px;
    background: rgba(255,255,255,0.04);
    border: 1px solid rgba(255,255,255,0.10);
    border-radius: 10px;
    padding: 10px 18px;
    transition: all 0.2s;
  }

  .pipe-icon {
    width: 32px; height: 32px;
    border-radius: 8px;
    display: flex; align-items: center; justify-content: center;
    font-size: 16px;
    flex-shrink: 0;
  }
  .icon-sql  { background: rgba(249,115,22,0.18); }
  .icon-py   { background: rgba(59,130,246,0.18); }
  .icon-bi   { background: rgba(234,179,8,0.18); }
  .icon-dash { background: rgba(0,200,130,0.18); }

  .pipe-text { display: flex; flex-direction: column; }
  .pipe-label { font-size: 13px; font-weight: 600; color: #e2e8f0; }
  .pipe-desc  { font-size: 11px; color: #64748b; margin-top: 1px; }

  .pipe-arrow {
    width: 32px;
    display: flex; align-items: center; justify-content: center;
    flex-shrink: 0;
  }
  .pipe-arrow svg { opacity: 0.35; }

  /* right side stats */
  .stats {
    position: absolute;
    right: 64px;
    top: 50%;
    transform: translateY(-50%);
    display: flex;
    flex-direction: column;
    gap: 14px;
  }

  .stat-card {
    background: rgba(255,255,255,0.03);
    border: 1px solid rgba(255,255,255,0.08);
    border-radius: 12px;
    padding: 14px 20px;
    min-width: 150px;
    text-align: center;
  }

  .stat-value {
    font-size: 26px;
    font-weight: 700;
    color: #fff;
    line-height: 1;
  }
  .stat-value.blue { color: #60a5fa; }
  .stat-value.green { color: #34d399; }
  .stat-value.yellow { color: #fbbf24; }

  .stat-label {
    font-size: 11px;
    color: #475569;
    margin-top: 4px;
    text-transform: uppercase;
    letter-spacing: 0.06em;
    font-weight: 500;
  }

  /* author strip at bottom */
  .author-strip {
    position: absolute;
    bottom: 0; left: 0; right: 0;
    height: 40px;
    background: rgba(255,255,255,0.02);
    border-top: 1px solid rgba(255,255,255,0.06);
    display: flex;
    align-items: center;
    padding: 0 64px;
    gap: 24px;
  }
  .author-name { font-size: 12px; color: #64748b; font-weight: 500; }
  .author-sep  { color: #1e293b; font-size: 16px; }
  .author-tag  { 
    font-size: 11px; 
    color: #3b82f6; 
    background: rgba(59,130,246,0.1); 
    border: 1px solid rgba(59,130,246,0.2);
    border-radius: 4px;
    padding: 2px 8px;
    font-weight: 500;
  }

  /* decorative chart lines on far right */
  .deco-chart {
    position: absolute;
    right: 280px;
    bottom: 48px;
    opacity: 0.08;
  }
</style>
</head>
<body>
<div class="banner">

  <div class="orb orb-1"></div>
  <div class="orb orb-2"></div>
  <div class="orb orb-3"></div>

  <!-- decorative chart -->
  <svg class="deco-chart" width="120" height="80" viewBox="0 0 120 80">
    <polyline points="0,70 20,55 40,60 60,35 80,40 100,15 120,20" fill="none" stroke="#3b82f6" stroke-width="2"/>
    <polyline points="0,80 20,72 40,75 60,60 80,65 100,45 120,50" fill="none" stroke="#06b6d4" stroke-width="1.5"/>
  </svg>

  <!-- badge -->
  <div class="badge">
    <div class="badge-dot"></div>
    End-to-End Analytics Project
  </div>

  <!-- title -->
  <div class="title">Banking <span>Analytics</span></div>
  <div class="subtitle">Risk profiling, loan analysis &amp; customer insights across demographic and financial segments</div>

  <!-- pipeline -->
  <div class="pipeline">

    <div class="pipe-step">
      <div class="pipe-icon icon-sql">🗄️</div>
      <div class="pipe-text">
        <span class="pipe-label">PostgreSQL</span>
        <span class="pipe-desc">Data joins &amp; querying</span>
      </div>
    </div>

    <div class="pipe-arrow">
      <svg width="24" height="14" viewBox="0 0 24 14">
        <path d="M0 7h20M14 1l6 6-6 6" stroke="#94a3b8" stroke-width="1.5" fill="none" stroke-linecap="round" stroke-linejoin="round"/>
      </svg>
    </div>

    <div class="pipe-step">
      <div class="pipe-icon icon-py">🐍</div>
      <div class="pipe-text">
        <span class="pipe-label">Python</span>
        <span class="pipe-desc">EDA &amp; feature engineering</span>
      </div>
    </div>

    <div class="pipe-arrow">
      <svg width="24" height="14" viewBox="0 0 24 14">
        <path d="M0 7h20M14 1l6 6-6 6" stroke="#94a3b8" stroke-width="1.5" fill="none" stroke-linecap="round" stroke-linejoin="round"/>
      </svg>
    </div>

    <div class="pipe-step">
      <div class="pipe-icon icon-bi">📊</div>
      <div class="pipe-text">
        <span class="pipe-label">Power BI</span>
        <span class="pipe-desc">Interactive dashboard</span>
      </div>
    </div>

    <div class="pipe-arrow">
      <svg width="24" height="14" viewBox="0 0 24 14">
        <path d="M0 7h20M14 1l6 6-6 6" stroke="#94a3b8" stroke-width="1.5" fill="none" stroke-linecap="round" stroke-linejoin="round"/>
      </svg>
    </div>

    <div class="pipe-step">
      <div class="pipe-icon icon-dash">💡</div>
      <div class="pipe-text">
        <span class="pipe-label">Insights</span>
        <span class="pipe-desc">7-point action plan</span>
      </div>
    </div>

  </div>

  <!-- right side stats -->
  <div class="stats">
    <div class="stat-card">
      <div class="stat-value blue">3K+</div>
      <div class="stat-label">Customers</div>
    </div>
    <div class="stat-card">
      <div class="stat-value green">4.38bn</div>
      <div class="stat-label">Total Loans</div>
    </div>
    <div class="stat-card">
      <div class="stat-value yellow">7</div>
      <div class="stat-label">Risk Insights</div>
    </div>
  </div>

  <!-- author strip -->
  <div class="author-strip">
    <span class="author-name">Kislay Kumar · NIT Warangal</span>
    <span class="author-sep">|</span>
    <span class="author-tag">BFSI Domain</span>
    <span class="author-tag">Risk Analytics</span>
    <span class="author-tag">Business Intelligence</span>
  </div>

</div>
</body>
</html>
