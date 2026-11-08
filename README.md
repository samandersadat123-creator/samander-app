<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>SAMANDER Forex Analyzer</title>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  min-height: 100vh;
  background: #090d18;
  color: white;
  font-family: Arial, sans-serif;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 20px;
}

.app {
  width: 100%;
  max-width: 420px;
  text-align: center;
}

h1 {
  font-size: 25px;
  letter-spacing: 2px;
  margin-bottom: 6px;
}

.subtitle {
  color: #8994aa;
  font-size: 13px;
  margin-bottom: 30px;
}

select, button {
  width: 100%;
  padding: 16px;
  margin: 8px 0;
  border-radius: 12px;
  border: 1px solid #29334b;
  background: #151d30;
  color: white;
  font-size: 16px;
  outline: none;
}

button {
  background: linear-gradient(90deg, #6558ff, #258bff);
  border: none;
  font-weight: bold;
  cursor: pointer;
  margin-top: 18px;
}

.circle {
  width: 220px;
  height: 220px;
  margin: 30px auto;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  background: #151d30;
  border: 5px solid #46516a;
  box-shadow: 0 0 35px #283552;
  transition: all .5s ease;
}

.circle span {
  font-size: 30px;
  font-weight: bold;
  letter-spacing: 2px;
}

.buy {
  border-color: #00e69a;
  box-shadow: 0 0 35px #00e69a66,
              inset 0 0 30px #00e69a22;
  color: #00e69a;
}

.sell {
  border-color: #ff496c;
  box-shadow: 0 0 35px #ff496c66,
              inset 0 0 30px #ff496c22;
  color: #ff496c;
}

.status {
  color: #8d9ab1;
  font-size: 12px;
  margin-top: 15px;
}

.notice {
  color: #f3bd63;
  font-size: 11px;
  margin-top: 25px;
  line-height: 1.6;
}
</style>
</head>

<body>
<div class="app">

  <h1>SAMANDER</h1>
  <div class="subtitle">FOREX PRACTICE ANALYZER</div>

  <select id="pair">
    <option>USD/CHF</option>
    <option>EUR/USD</option>
    <option>GBP/USD</option>
    <option>AUD/USD</option>
    <option>USD/JPY</option>
    <option>USD/CAD</option>
    <option>EUR/JPY</option>
    <option>GBP/JPY</option>
  </select>

  <select id="timeframe">
    <option value="1">1 Minute</option>
    <option value="5">5 Minutes</option>
  </select>

  <button onclick="analyze()">ANALYZE</button>

  <div class="circle" id="circle">
    <span id="result">READY</span>
  </div>

  <div class="status" id="status">
    Select a pair and press Analyze
  </div>

  <div class="notice">
    SIMULATED PRACTICE DATA — NOT LIVE MARKET DATA
  </div>

</div>

<script>
function analyze() {
  const circle = document.getElementById("circle");
  const result = document.getElementById("result");
  const status = document.getElementById("status");

  circle.className = "circle";
  result.textContent = "ANALYZING";
  status.textContent = "Calculating practice data...";

  setTimeout(() => {
    const practiceDirection = Math.random() >= 0.5;

    if (practiceDirection) {
      circle.className = "circle buy";
      result.textContent = "BUY";
    } else {
      circle.className = "circle sell";
      result.textContent = "SELL";
    }

    const pair = document.getElementById("pair").value;
    const timeframe = document.getElementById("timeframe").value;

    status.textContent =
      pair + "  •  " + timeframe + " Minute Practice";
  }, 1200);
}
</script>

</body>
</html>
<style>
.indicator-panel {
  background: #151d30;
  border: 1px solid #293650;
  border-radius: 16px;
  padding: 18px;
  margin-top: 25px;
  text-align: left;
}

.indicator-panel h3 {
  text-align: center;
  color: #72aaff;
  margin-top: 0;
}

.indicator-row {
  display: flex;
  justify-content: space-between;
  padding: 11px 2px;
  border-bottom: 1px solid #293650;
  font-size: 14px;
}

.indicator-row:last-child {
  border-bottom: none;
}

.indicator-value {
  color: #00e6a0;
  font-weight: bold;
}
</style>

<script>
const panel = document.createElement("div");
panel.className = "indicator-panel";

panel.innerHTML = `
<h3>TECHNICAL INDICATORS</h3>
<div class="indicator-row"><span>EMA 9</span><b class="indicator-value" id="ema9">--</b></div>
<div class="indicator-row"><span>EMA 20</span><b class="indicator-value" id="ema20">--</b></div>
<div class="indicator-row"><span>EMA 50</span><b class="indicator-value" id="ema50">--</b></div>
<div class="indicator-row"><span>EMA 200</span><b class="indicator-value" id="ema200">--</b></div>
<div class="indicator-row"><span>RSI 14</span><b class="indicator-value" id="rsi">--</b></div>
<div class="indicator-row"><span>MACD</span><b class="indicator-value" id="macd">--</b></div>
<div class="indicator-row"><span>MACD Signal</span><b class="indicator-value" id="macds">--</b></div>
<div class="indicator-row"><span>ADX 14</span><b class="indicator-value" id="adx">--</b></div>
<div class="indicator-row"><span>ATR 14</span><b class="indicator-value" id="atr">--</b></div>
<div class="indicator-row"><span>Bollinger Upper</span><b class="indicator-value" id="upper">--</b></div>
<div class="indicator-row"><span>Bollinger Lower</span><b class="indicator-value" id="lower">--</b></div>
<div class="indicator-row"><span>Support</span><b class="indicator-value" id="support">--</b></div>
<div class="indicator-row"><span>Resistance</span><b class="indicator-value" id="resistance">--</b></div>
<div class="indicator-row"><span>Trend</span><b class="indicator-value" id="trend">--</b></div>
<div class="indicator-row"><span>Candle Pattern</span><b class="indicator-value" id="pattern">--</b></div>
<p style="color:#f3bd63;font-size:11px;text-align:center;margin-bottom:0">
SIMULATED PRACTICE VALUES — NOT LIVE MARKET DATA
</p>
`;

document.querySelector(".app").appendChild(panel);

const oldAnalyze = window.analyze;

window.analyze = function() {
  oldAnalyze();

  setTimeout(() => {
    const n = (min, max, decimals = 5) =>
      (Math.random() * (max - min) + min).toFixed(decimals);

    document.getElementById("ema9").textContent = n(1.080, 1.120);
    document.getElementById("ema20").textContent = n(1.080, 1.120);
    document.getElementById("ema50").textContent = n(1.080, 1.120);
    document.getElementById("ema200").textContent = n(1.080, 1.120);
    document.getElementById("rsi").textContent = n(20, 80, 2);
    document.getElementById("macd").textContent = n(-0.002, 0.002, 5);
    document.getElementById("macds").textContent = n(-0.002, 0.002, 5);
    document.getElementById("adx").textContent = n(10, 50, 2);
    document.getElementById("atr").textContent = n(0.0001, 0.003, 5);
    document.getElementById("upper").textContent = n(1.090, 1.130);
    document.getElementById("lower").textContent = n(1.060, 1.090);
    document.getElementById("support").textContent = n(1.060, 1.090);
    document.getElementById("resistance").textContent = n(1.100, 1.130);

    document.getElementById("trend").textContent =
      Math.random() > 0.5 ? "Uptrend" : "Downtrend";

    const patterns = [
      "Doji",
      "Hammer",
      "Engulfing",
      "Shooting Star",
      "No clear pattern"
    ];

    document.getElementById("pattern").textContent =
      patterns[Math.floor(Math.random() * patterns.length)];

  }, 1300);
};
</script>
<div id="shortAnalysis" class="indicator-panel">
  <h3>SHORT-TIMEFRAME ANALYSIS</h3>

  <div class="indicator-row">
    <span>RSI 7</span><b id="sRsi7">--</b>
  </div>
  <div class="indicator-row">
    <span>RSI 14</span><b id="sRsi14">--</b>
  </div>
  <div class="indicator-row">
    <span>MACD Fast (6,13,5)</span><b id="sMacdFast">--</b>
  </div>
  <div class="indicator-row">
    <span>MACD Standard (12,26,9)</span><b id="sMacdStandard">--</b>
  </div>
  <div class="indicator-row">
    <span>EMA 5</span><b id="sEma5">--</b>
  </div>
  <div class="indicator-row">
    <span>EMA 9</span><b id="sEma9">--</b>
  </div>
  <div class="indicator-row">
    <span>EMA 20</span><b id="sEma20">--</b>
  </div>
  <div class="indicator-row">
    <span>Momentum</span><b id="sMomentum">--</b>
  </div>
  <div class="indicator-row">
    <span>Short-term trend</span><b id="sTrend">--</b>
  </div>

  <p style="font-size:11px;color:#f3bd63;text-align:center">
    SIMULATED PRACTICE VALUES — NOT LIVE DATA
  </p>
</div>

<script>
(function () {
  const fields = [
    "sRsi7", "sRsi14", "sMacdFast", "sMacdStandard",
    "sEma5", "sEma9", "sEma20", "sMomentum", "sTrend"
  ];

  const originalAnalyze = window.analyze;

  window.analyze = function () {
    originalAnalyze();

    setTimeout(() => {
      const rsi7 = 20 + Math.random() * 60;
      const rsi14 = 20 + Math.random() * 60;
      const fast = (Math.random() - 0.5) * 0.004;
      const standard = (Math.random() - 0.5) * 0.004;
      const base = 1.08 + Math.random() * 0.04;

      document.getElementById("sRsi7").textContent = rsi7.toFixed(2);
      document.getElementById("sRsi14").textContent = rsi14.toFixed(2);
      document.getElementById("sMacdFast").textContent = fast.toFixed(5);
      document.getElementById("sMacdStandard").textContent = standard.toFixed(5);

      document.getElementById("sEma5").textContent = base.toFixed(5);
      document.getElementById("sEma9").textContent = (base - 0.0002).toFixed(5);
      document.getElementById("sEma20").textContent = (base - 0.0004).toFixed(5);

      document.getElementById("sMomentum").textContent =
        fast > 0 ? "Positive" : "Negative";

      document.getElementById("sTrend").textContent =
        fast > 0 && standard > 0 ? "Upward" :
        fast < 0 && standard < 0 ? "Downward" : "Mixed";
    }, 1400);
  };
})();
</script>
<script>
(function () {
  const panel = document.getElementById("shortAnalysis");
  const app = document.querySelector(".app");

  if (panel && app) {
    app.appendChild(panel);
    panel.style.display = "block";
    panel.style.visibility = "visible";
    panel.style.opacity = "1";
  }
})();
</script>
<script>
(function () {
  const pairSelect = document.getElementById("pair");

  const otcPairs = [
    "EUR/USD OTC",
    "GBP/USD OTC",
    "USD/JPY OTC",
    "AUD/USD OTC",
    "USD/CAD OTC",
    "EUR/JPY OTC",
    "GBP/JPY OTC",
    "AUD/CAD OTC",
    "EUR/GBP OTC",
    "NZD/USD OTC",
    "USD/CHF OTC"
  ];

  otcPairs.reverse().forEach(pair => {
    const option = document.createElement("option");
    option.value = pair;
    option.textContent = pair;
    pairSelect.insertBefore(option, pairSelect.firstChild);
  });

  pairSelect.selectedIndex = 0;
})();
</script>
<style>
#advancedEngine {
  background:#151d30;
  border:1px solid #34415d;
  border-radius:18px;
  padding:18px;
  margin-top:22px;
  text-align:left;
}
#advancedEngine h3 {
  color:#72aaff;
  text-align:center;
}
.engine-row {
  display:flex;
  justify-content:space-between;
  gap:10px;
  padding:11px 0;
  border-bottom:1px solid #293650;
  font-size:13px;
}
.engine-value {
  color:#00e6a0;
  font-weight:bold;
  text-align:right;
}
.engine-note {
  color:#f3bd63;
  font-size:11px;
  text-align:center;
  line-height:1.5;
}
</style>

<div id="advancedEngine">
  <h3>ADVANCED PRACTICE ENGINE</h3>

  <div class="engine-row"><span>RSI 7</span><b class="engine-value" id="aRsi7">--</b></div>
  <div class="engine-row"><span>RSI 14</span><b class="engine-value" id="aRsi14">--</b></div>
  <div class="engine-row"><span>RSI 21</span><b class="engine-value" id="aRsi21">--</b></div>

  <div class="engine-row"><span>MACD Fast (6,13,5)</span><b class="engine-value" id="aMacdFast">--</b></div>
  <div class="engine-row"><span>MACD Standard (12,26,9)</span><b class="engine-value" id="aMacd">--</b></div>

  <div class="engine-row"><span>EMA 5</span><b class="engine-value" id="aEma5">--</b></div>
  <div class="engine-row"><span>EMA 9</span><b class="engine-value" id="aEma9">--</b></div>
  <div class="engine-row"><span>EMA 20</span><b class="engine-value" id="aEma20">--</b></div>
  <div class="engine-row"><span>EMA 50</span><b class="engine-value" id="aEma50">--</b></div>
  <div class="engine-row"><span>EMA 200</span><b class="engine-value" id="aEma200">--</b></div>

  <div class="engine-row"><span>Bollinger Upper</span><b class="engine-value" id="aUpper">--</b></div>
  <div class="engine-row"><span>Bollinger Middle</span><b class="engine-value" id="aMiddle">--</b></div>
  <div class="engine-row"><span>Bollinger Lower</span><b class="engine-value" id="aLower">--</b></div>

  <div class="engine-row"><span>ATR 14</span><b class="engine-value" id="aAtr">--</b></div>
  <div class="engine-row"><span>ADX estimate</span><b class="engine-value" id="aAdx">--</b></div>
  <div class="engine-row"><span>Support</span><b class="engine-value" id="aSupport">--</b></div>
  <div class="engine-row"><span>Resistance</span><b class="engine-value" id="aResistance">--</b></div>
  <div class="engine-row"><span>Momentum</span><b class="engine-value" id="aMomentum">--</b></div>
  <div class="engine-row"><span>Candle pattern</span><b class="engine-value" id="aPattern">--</b></div>
  <div class="engine-row"><span>Practice trend</span><b class="engine-value" id="aTrend">--</b></div>

  <p class="engine-note">
    SIMULATED PRACTICE CANDLES — NOT LIVE MARKET DATA.
    OTC prices are not connected to Pocket Option.
  </p>
</div>

<script>
(function () {
  const originalAnalyze = window.analyze;

  function ema(data, period) {
    const k = 2 / (period + 1);
    let value = data[0];

    for (let i = 1; i < data.length; i++) {
      value = data[i] * k + value * (1 - k);
    }
    return value;
  }

  function rsi(data, period) {
    let gains = 0, losses = 0;

    for (let i = data.length - period; i < data.length; i++) {
      const change = data[i] - data[i - 1];
      if (change > 0) gains += change;
      else losses -= change;
    }

    if (losses === 0) return 100;
    return 100 - 100 / (1 + gains / losses);
  }

  function calculate() {
    const closes = [];
    const highs = [];
    const lows = [];

    let price = 1.10;

    for (let i = 0; i < 250; i++) {
      const change = (Math.random() - 0.49) * 0.001;
      const open = price;
      price += change;

      closes.push(price);
      highs.push(Math.max(open, price) + Math.random() * 0.0003);
      lows.push(Math.min(open, price) - Math.random() * 0.0003);
    }

    const last = closes.length - 1;
    const current = closes[last];

    const e5 = ema(closes.slice(-80), 5);
    const e9 = ema(closes.slice(-80), 9);
    const e20 = ema(closes.slice(-100), 20);
    const e50 = ema(closes.slice(-150), 50);
    const e200 = ema(closes, 200);

    const r7 = rsi(closes, 7);
    const r14 = rsi(closes, 14);
    const r21 = rsi(closes, 21);

    const macdLine =
      ema(closes.slice(-100), 12) -
      ema(closes.slice(-100), 26);

    const macdSignal = ema(
      closes.slice(-100).map((_, i, arr) => {
        return ema(arr.slice(0, i + 1), 12) -
               ema(arr.slice(0, i + 1), 26);
      }).slice(-30),
      9
    );

    const fastMacd =
      ema(closes.slice(-60), 6) -
      ema(closes.slice(-60), 13);

    const avg = closes.slice(-20).reduce((a,b) => a+b,0) / 20;

    const variance = closes.slice(-20)
      .reduce((sum,v) => sum + Math.pow(v-avg,2),0) / 20;

    const deviation = Math.sqrt(variance);

    const upper = avg + 2 * deviation;
    const lower = avg - 2 * deviation;

    const ranges = [];

    for (let i = last - 13; i <= last; i++) {
      ranges.push(highs[i] - lows[i]);
    }

    const atr = ranges.reduce((a,b) => a+b,0) / ranges.length;

    const support = Math.min(...lows.slice(-30));
    const resistance = Math.max(...highs.slice(-30));

    const recentMove = closes[last] - closes[last - 10];

    const trend =
      e5 > e9 && e9 > e20 ? "Short uptrend" :
      e5 < e9 && e9 < e20 ? "Short downtrend" :
      "Mixed trend";

    const momentum = recentMove > 0 ? "Positive" : "Negative";

    const candleOpen = closes[last - 1];
    const candleClose = closes[last];
    const candleRange = highs[last] - lows[last];
    const candleBody = Math.abs(candleClose - candleOpen);

    let pattern = "No clear pattern";

    if (candleBody < candleRange * 0.1) {
      pattern = "Doji-like";
    } else if (candleClose > candleOpen &&
               candleBody > candleRange * 0.65) {
      pattern = "Bullish candle";
    } else if (candleClose < candleOpen &&
               candleBody > candleRange * 0.65) {
      pattern = "Bearish candle";
    }

    // Simplified directional-movement strength estimate
    const directionalChanges = [];

    for (let i = last - 13; i <= last; i++) {
      directionalChanges.push(
        Math.abs(closes[i] - closes[i-1])
      );
    }

    const adxEstimate =
      100 * directionalChanges.reduce((a,b) => a+b,0) /
      Math.max(0.0000001, atr * 14);

    const values = {
      aRsi7: r7.toFixed(2),
      aRsi14: r14.toFixed(2),
      aRsi21: r21.toFixed(2),
      aMacdFast: fastMacd.toFixed(6),
      aMacd: macdLine.toFixed(6),
      aEma5: e5.toFixed(5),
      aEma9: e9.toFixed(5),
      aEma20: e20.toFixed(5),
      aEma50: e50.toFixed(5),
      aEma200: e200.toFixed(5),
      aUpper: upper.toFixed(5),
      aMiddle: avg.toFixed(5),
      aLower: lower.toFixed(5),
      aAtr: atr.toFixed(6),
      aAdx: Math.min(100, adxEstimate).toFixed(2),
      aSupport: support.toFixed(5),
      aResistance: resistance.toFixed(5),
      aMomentum: momentum,
      aPattern: pattern,
      aTrend: trend
    };

    Object.entries(values).forEach(([id, value]) => {
      document.getElementById(id).textContent = value;
    });
  }

  window.analyze = function () {
    originalAnalyze();
    setTimeout(calculate, 1500);
  };
})();
</script>
<script>
(function () {
  function showAdvancedEngine() {
    const panel = document.getElementById("advancedEngine");
    const app = document.querySelector(".app");

    if (panel && app) {
      panel.style.display = "block";
      panel.style.visibility = "visible";
      panel.style.opacity = "1";
      app.appendChild(panel);
    }
  }

  showAdvancedEngine();
  window.addEventListener("load", showAdvancedEngine);
})();
</script>
<style>
.pocket-logo {
  width: 76px;
  height: 76px;
  margin: 0 auto 12px;
  border-radius: 22px;
  background: linear-gradient(135deg,#19b5ff,#1454dc);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 30px;
  font-weight: 900;
  color: white;
  box-shadow: 0 0 28px #168bff77;
  border: 2px solid #70caff;
}

.subtitle {
  font-size: 17px !important;
  color: #43aaff !important;
  font-weight: bold;
  letter-spacing: 3px;
}
</style>

<script>
(function () {
  const app = document.querySelector(".app");
  const heading = app.querySelector("h1");
  const subtitle = app.querySelector(".subtitle");

  subtitle.textContent = "POCKET OPTION";

  const logo = document.createElement("div");
  logo.className = "pocket-logo";
  logo.textContent = "PO";

  app.insertBefore(logo, heading);
})();
</script>
<style>
.pocket-logo {
  width: 100px !important;
  height: 100px !important;
  position: relative;
  margin: 20px auto 18px !important;
  border-radius: 30px !important;
  background: linear-gradient(145deg,#42d8ff,#1674ff 55%,#102caa) !important;
  border: 2px solid #a4eaff !important;
  box-shadow:
    0 0 15px #168bff,
    0 0 35px #168bff99,
    inset 0 0 18px #ffffff55 !important;
  font-size: 35px !important;
  font-weight: 900 !important;
  letter-spacing: -3px;
  animation: logoFloat 3s ease-in-out infinite;
}

.pocket-logo::before {
  content: "";
  position: absolute;
  inset: -9px;
  border: 2px solid #36baff88;
  border-radius: 36px;
  animation: logoGlow 2.5s ease-in-out infinite;
}

.pocket-logo::after {
  content: "";
  position: absolute;
  width: 13px;
  height: 13px;
  background: #ffffff;
  border-radius: 50%;
  top: 12px;
  right: 13px;
  box-shadow: 0 0 15px white;
}

@keyframes logoFloat {
  0%,100% { transform: translateY(0) scale(1); }
  50% { transform: translateY(-5px) scale(1.04); }
}

@keyframes logoGlow {
  0%,100% { opacity: .35; transform: scale(1); }
  50% { opacity: 1; transform: scale(1.08); }
}
</style>
<style>
.pocket-logo {
  font-size: 0 !important;
  overflow: visible !important;
}

.pocket-logo svg {
  width: 65px;
  height: 65px;
  filter: drop-shadow(0 0 9px #ffffffaa);
  animation: signalPulse 2s ease-in-out infinite;
}

@keyframes signalPulse {
  0%,100% { transform: scale(1); }
  50% { transform: scale(1.1); }
}
</style>

<script>
document.querySelectorAll(".pocket-logo").forEach(logo => {
  logo.innerHTML = `
    <svg viewBox="0 0 100 100" fill="none">
      <path d="M12 78 L34 56 L49 68 L76 32"
        stroke="white" stroke-width="7"
        stroke-linecap="round" stroke-linejoin="round"/>
      <path d="M59 32 H76 V49"
        stroke="white" stroke-width="7"
        stroke-linecap="round" stroke-linejoin="round"/>
      <path d="M12 88 H88"
        stroke="#a9eaff" stroke-width="4"
        stroke-linecap="round"/>
    </svg>
  `;
});
</script>
<script>
document.querySelectorAll("p").forEach(p => {
  if (
    p.textContent.includes("SIMULATED") ||
    p.textContent.includes("LIVE MARKET DATA")
  ) {
    p.textContent = "• SIMULATED DATA";
  }
});
</script>
<style>
.app h1 {
  font-size: 34px !important;
  font-weight: 900 !important;
  letter-spacing: 5px !important;
  background: linear-gradient(
    90deg,
    #00eaff,
    #438cff,
    #b66bff,
    #ff55bd,
    #00eaff
  );
  background-size: 300% auto;
  -webkit-background-clip: text;
  background-clip: text;
  -webkit-text-fill-color: transparent;
  animation: samanderGlow 5s linear infinite;
  filter: drop-shadow(0 0 12px #548cff88);
}

@keyframes samanderGlow {
  0% { background-position: 0% center; }
  100% { background-position: 300% center; }
}
</style>
