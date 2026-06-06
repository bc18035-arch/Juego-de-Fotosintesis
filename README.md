<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>La Fotosíntesis — Juego de Preguntas</title>
<link href="https://fonts.googleapis.com/css2?family=Nunito:wght@400;600;700;900&family=Nunito+Sans:wght@400;600&display=swap" rel="stylesheet">
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  :root {
    --green: #16a34a;
    --green-light: #dcfce7;
    --green-dark: #14532d;
    --red: #dc2626;
    --red-light: #fee2e2;
    --red-dark: #7f1d1d;
    --yellow: #ca8a04;
    --yellow-light: #fef9c3;
    --blue: #2563eb;
    --blue-light: #dbeafe;
    --purple: #7c3aed;
    --purple-light: #ede9fe;
    --orange: #ea580c;
    --orange-light: #ffedd5;
    --bg: #f0fdf4;
    --card: #ffffff;
    --text: #1a1a1a;
    --text-muted: #6b7280;
    --border: #e5e7eb;
    --shadow: 0 4px 24px rgba(0,0,0,0.10);
    --shadow-lg: 0 8px 40px rgba(0,0,0,0.15);
    --radius: 16px;
    --radius-sm: 10px;
  }

  body {
    font-family: 'Nunito Sans', sans-serif;
    background: var(--bg);
    color: var(--text);
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 0;
  }

  /* ── TOP BANNER ── */
  .top-banner {
    width: 100%;
    background: linear-gradient(135deg, #166534 0%, #16a34a 60%, #4ade80 100%);
    padding: 18px 24px;
    display: flex;
    align-items: center;
    gap: 14px;
    box-shadow: 0 2px 12px rgba(22,163,74,0.25);
  }
  .banner-leaf { font-size: 32px; animation: sway 3s ease-in-out infinite; }
  @keyframes sway { 0%,100%{transform:rotate(-5deg)} 50%{transform:rotate(5deg)} }
  .banner-title { color: #fff; font-family: 'Nunito', sans-serif; font-weight: 900; font-size: 22px; letter-spacing: -0.3px; }
  .banner-sub { color: rgba(255,255,255,0.80); font-size: 13px; font-weight: 600; margin-top: 1px; }
  .banner-badge {
    margin-left: auto;
    background: rgba(255,255,255,0.20);
    color: #fff;
    font-family: 'Nunito', sans-serif;
    font-weight: 700;
    font-size: 12px;
    padding: 5px 12px;
    border-radius: 999px;
    border: 1px solid rgba(255,255,255,0.35);
    white-space: nowrap;
  }

  /* ── MAIN CONTAINER ── */
  .main { width: 100%; max-width: 680px; padding: 28px 16px 60px; }

  /* ── PROGRESS ── */
  .progress-wrap { margin-bottom: 20px; }
  .progress-meta { display: flex; justify-content: space-between; font-size: 13px; font-weight: 600; color: var(--text-muted); margin-bottom: 6px; }
  .progress-track { height: 8px; background: #d1fae5; border-radius: 999px; overflow: hidden; }
  .progress-fill { height: 100%; background: linear-gradient(90deg, #16a34a, #4ade80); border-radius: 999px; transition: width 0.5s cubic-bezier(.4,0,.2,1); }

  /* ── SCORE BAR ── */
  .score-bar { display: flex; gap: 10px; margin-bottom: 20px; }
  .score-pill {
    flex: 1; background: var(--card); border: 1.5px solid var(--border); border-radius: var(--radius-sm);
    padding: 10px 14px; display: flex; align-items: center; gap: 8px;
  }
  .score-pill-icon { font-size: 20px; }
  .score-pill-label { font-size: 12px; color: var(--text-muted); font-weight: 600; }
  .score-pill-value { font-family: 'Nunito', sans-serif; font-size: 20px; font-weight: 900; color: var(--text); margin-left: auto; }

  /* ── QUESTION CARD ── */
  .q-card {
    background: var(--card);
    border-radius: var(--radius);
    box-shadow: var(--shadow);
    padding: 28px 28px 24px;
    margin-bottom: 16px;
    border: 1.5px solid var(--border);
    animation: slideIn 0.35s cubic-bezier(.4,0,.2,1);
  }
  @keyframes slideIn { from{opacity:0;transform:translateY(12px)} to{opacity:1;transform:translateY(0)} }

  .q-header { display: flex; align-items: center; gap: 10px; margin-bottom: 16px; }
  .q-num {
    background: linear-gradient(135deg, #166534, #16a34a);
    color: #fff;
    font-family: 'Nunito', sans-serif;
    font-weight: 900;
    font-size: 13px;
    padding: 4px 12px;
    border-radius: 999px;
    white-space: nowrap;
  }
  .timer-wrap {
    margin-left: auto;
    display: flex;
    align-items: center;
    gap: 6px;
    font-family: 'Nunito', sans-serif;
    font-weight: 900;
    font-size: 18px;
  }
  .timer-val { transition: color 0.3s; }
  .timer-val.urgent { color: var(--red); animation: pulse 0.5s infinite alternate; }
  @keyframes pulse { from{transform:scale(1)} to{transform:scale(1.08)} }

  .q-text {
    font-family: 'Nunito', sans-serif;
    font-size: 18px;
    font-weight: 700;
    color: var(--text);
    line-height: 1.5;
    margin-bottom: 24px;
  }

  /* ── OPTIONS ── */
  .options-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; }
  @media (max-width: 520px) { .options-grid { grid-template-columns: 1fr; } }

  .opt-btn {
    position: relative;
    padding: 14px 16px;
    border-radius: var(--radius-sm);
    border: 2px solid transparent;
    cursor: pointer;
    text-align: left;
    font-family: 'Nunito Sans', sans-serif;
    font-size: 14px;
    font-weight: 600;
    color: #fff;
    line-height: 1.4;
    display: flex;
    align-items: flex-start;
    gap: 10px;
    transition: transform 0.1s, box-shadow 0.1s, opacity 0.2s;
    box-shadow: 0 3px 0 rgba(0,0,0,0.15);
  }
  .opt-btn:hover:not(:disabled) { transform: translateY(-2px); box-shadow: 0 6px 0 rgba(0,0,0,0.12); }
  .opt-btn:active:not(:disabled) { transform: translateY(1px); box-shadow: 0 1px 0 rgba(0,0,0,0.12); }
  .opt-btn:disabled { cursor: default; }

  .opt-btn.color-a { background: #2563eb; }
  .opt-btn.color-b { background: #dc2626; }
  .opt-btn.color-c { background: #ca8a04; }
  .opt-btn.color-d { background: #7c3aed; }

  .opt-btn.state-correct { background: #16a34a !important; border-color: #14532d; animation: correct-pop 0.4s cubic-bezier(.4,0,.2,1); }
  .opt-btn.state-wrong   { background: #6b7280 !important; opacity: 0.6; }
  .opt-btn.state-reveal  { background: #16a34a !important; border-color: #14532d; }
  .opt-btn.state-dim     { opacity: 0.45; }

  @keyframes correct-pop {
    0%  { transform: scale(1); }
    40% { transform: scale(1.06); }
    70% { transform: scale(0.97); }
    100%{ transform: scale(1); }
  }

  .opt-letter {
    width: 26px; height: 26px; border-radius: 6px;
    background: rgba(255,255,255,0.25);
    display: flex; align-items: center; justify-content: center;
    font-family: 'Nunito', sans-serif; font-weight: 900; font-size: 14px;
    flex-shrink: 0; margin-top: 1px;
  }

  /* ── FEEDBACK ── */
  .feedback-box {
    border-radius: var(--radius-sm);
    padding: 14px 16px;
    margin-top: 18px;
    font-size: 14px;
    line-height: 1.65;
    display: none;
    animation: fadeIn 0.3s ease;
  }
  @keyframes fadeIn { from{opacity:0} to{opacity:1} }
  .feedback-box.correct { background: var(--green-light); color: var(--green-dark); border: 1.5px solid #86efac; }
  .feedback-box.wrong   { background: var(--red-light);   color: var(--red-dark);   border: 1.5px solid #fca5a5; }
  .feedback-box.timeout { background: var(--yellow-light); color: #713f12; border: 1.5px solid #fde68a; }

  /* ── NAV ── */
  .nav-row { display: flex; justify-content: flex-end; margin-top: 4px; }
  .next-btn {
    background: linear-gradient(135deg, #166534, #16a34a);
    color: #fff;
    font-family: 'Nunito', sans-serif;
    font-weight: 800;
    font-size: 15px;
    padding: 12px 28px;
    border-radius: var(--radius-sm);
    border: none;
    cursor: pointer;
    display: flex; align-items: center; gap: 8px;
    box-shadow: 0 3px 0 #14532d;
    transition: transform 0.1s, box-shadow 0.1s;
    display: none;
  }
  .next-btn:hover { transform: translateY(-2px); box-shadow: 0 6px 0 #14532d; }
  .next-btn:active { transform: translateY(1px); box-shadow: 0 1px 0 #14532d; }

  /* ── CRISIS SECTION ── */
  .crisis-card {
    background: var(--card);
    border-radius: var(--radius);
    box-shadow: var(--shadow-lg);
    padding: 28px;
    border: 2px solid var(--red);
    animation: slideIn 0.4s cubic-bezier(.4,0,.2,1);
  }
  .crisis-tag {
    display: inline-flex; align-items: center; gap: 6px;
    background: var(--red-light); color: var(--red);
    font-family: 'Nunito', sans-serif; font-weight: 800; font-size: 12px;
    padding: 5px 12px; border-radius: 999px;
    margin-bottom: 16px; border: 1px solid #fca5a5;
    text-transform: uppercase; letter-spacing: 0.5px;
  }
  .crisis-text {
    font-size: 15px; color: var(--text); line-height: 1.7; margin-bottom: 22px;
  }
  .crisis-text strong { font-weight: 700; }
  .crisis-options { display: grid; grid-template-columns: 1fr 1fr; gap: 14px; }
  @media (max-width: 520px) { .crisis-options { grid-template-columns: 1fr; } }
  .crisis-opt {
    padding: 18px 16px;
    border-radius: var(--radius-sm);
    border: 2px solid var(--border);
    background: #f9fafb;
    font-family: 'Nunito Sans', sans-serif;
    font-size: 14px; color: var(--text);
    cursor: pointer; text-align: left; line-height: 1.55;
    transition: border-color 0.2s, background 0.2s, transform 0.1s;
  }
  .crisis-opt:hover { border-color: #16a34a; background: var(--green-light); transform: translateY(-2px); }
  .crisis-opt strong { display: block; font-family: 'Nunito', sans-serif; font-weight: 900; font-size: 16px; margin-bottom: 6px; }
  .crisis-opt.chosen-correct { border-color: #16a34a; background: var(--green-light); pointer-events: none; }
  .crisis-opt.chosen-wrong   { border-color: var(--red); background: var(--red-light); pointer-events: none; }
  .crisis-opt.disabled { pointer-events: none; opacity: 0.55; }

  .crisis-feedback {
    border-radius: var(--radius-sm);
    padding: 16px 18px;
    margin-top: 18px;
    font-size: 14px; line-height: 1.7;
    display: none;
    animation: fadeIn 0.3s ease;
  }
  .crisis-feedback.correct { background: var(--green-light); color: var(--green-dark); border: 1.5px solid #86efac; }
  .crisis-feedback.partial { background: var(--yellow-light); color: #713f12; border: 1.5px solid #fde68a; }
  .crisis-feedback strong { display: block; font-weight: 700; margin-bottom: 6px; font-size: 15px; }

  /* ── RESULTS ── */
  .results-card {
    background: var(--card);
    border-radius: var(--radius);
    box-shadow: var(--shadow-lg);
    padding: 40px 32px;
    text-align: center;
    border: 1.5px solid var(--border);
    animation: slideIn 0.4s cubic-bezier(.4,0,.2,1);
  }
  .results-trophy { font-size: 60px; margin-bottom: 12px; animation: bounce 0.6s cubic-bezier(.4,0,.2,1); }
  @keyframes bounce { 0%{transform:scale(0.5);opacity:0} 70%{transform:scale(1.15)} 100%{transform:scale(1);opacity:1} }
  .results-score-num {
    font-family: 'Nunito', sans-serif;
    font-size: 52px; font-weight: 900;
    background: linear-gradient(135deg, #166534, #16a34a);
    -webkit-background-clip: text; -webkit-text-fill-color: transparent;
    margin-bottom: 4px;
  }
  .results-score-label { font-size: 15px; color: var(--text-muted); font-weight: 600; margin-bottom: 24px; }
  .results-stars { font-size: 28px; letter-spacing: 4px; margin-bottom: 20px; }
  .results-msg {
    font-size: 15px; line-height: 1.7; color: var(--text);
    max-width: 400px; margin: 0 auto 28px;
    background: var(--green-light); border-radius: var(--radius-sm);
    padding: 14px 18px; border: 1.5px solid #86efac;
  }
  .restart-btn {
    background: linear-gradient(135deg, #166534, #16a34a);
    color: #fff;
    font-family: 'Nunito', sans-serif;
    font-weight: 800; font-size: 16px;
    padding: 14px 36px;
    border-radius: var(--radius-sm);
    border: none; cursor: pointer;
    box-shadow: 0 4px 0 #14532d;
    transition: transform 0.1s, box-shadow 0.1s;
  }
  .restart-btn:hover { transform: translateY(-2px); box-shadow: 0 7px 0 #14532d; }
  .restart-btn:active { transform: translateY(2px); box-shadow: 0 1px 0 #14532d; }

  /* ── SCREEN MANAGEMENT ── */
  .screen { display: none; }
  .screen.active { display: block; }

  /* ── FOOTER ── */
  .footer { text-align: center; font-size: 12px; color: var(--text-muted); margin-top: 40px; padding-bottom: 24px; }
</style>
</head>
<body>

<div class="top-banner">
  <div class="banner-leaf">🌿</div>
  <div>
    <div class="banner-title">La Fotosíntesis</div>
    <div class="banner-sub">Juego de preguntas interactivo</div>
  </div>
  <div class="banner-badge">📚 Nivel Básico</div>
</div>

<div class="main">

  <!-- QUIZ SCREEN -->
  <div class="screen active" id="screen-quiz">
    <div class="progress-wrap">
      <div class="progress-meta">
        <span id="prog-label">Pregunta 1 de 5</span>
        <span id="score-meta">Puntaje: 0</span>
      </div>
      <div class="progress-track"><div class="progress-fill" id="progress" style="width:0%"></div></div>
    </div>

    <div class="score-bar">
      <div class="score-pill">
        <span class="score-pill-icon">✅</span>
        <div>
          <div class="score-pill-label">Correctas</div>
        </div>
        <div class="score-pill-value" id="correct-count">0</div>
      </div>
      <div class="score-pill">
        <span class="score-pill-icon">❌</span>
        <div>
          <div class="score-pill-label">Incorrectas</div>
        </div>
        <div class="score-pill-value" id="wrong-count">0</div>
      </div>
      <div class="score-pill">
        <span class="score-pill-icon">⏱</span>
        <div>
          <div class="score-pill-label">Tiempo</div>
        </div>
        <div class="score-pill-value" id="timer-val">20</div>
      </div>
    </div>

    <div class="q-card">
      <div class="q-header">
        <div class="q-num" id="q-num">Pregunta 1</div>
        <div class="timer-wrap">
          <span>⏱</span>
          <span class="timer-val" id="timer-display">20</span>
        </div>
      </div>
      <div class="q-text" id="q-text"></div>
      <div class="options-grid" id="options-grid"></div>
      <div class="feedback-box" id="feedback-box"></div>
    </div>

    <div class="nav-row">
      <button class="next-btn" id="next-btn" onclick="nextQuestion()">
        Siguiente pregunta ➜
      </button>
    </div>
  </div>

  <!-- CRISIS SCREEN -->
  <div class="screen" id="screen-crisis">
    <div class="crisis-card">
      <div class="crisis-tag">⚠️ Situación crítica final</div>
      <div class="crisis-text">
        🌎 <strong>El escenario:</strong> Un equipo científico investiga por qué una zona del bosque amazónico está muriendo. Las hojas se ponen amarillas y la producción de oxígeno ha caído drásticamente. Al analizar el área, descubren que hay una densa capa de contaminación en el aire que bloquea casi toda la luz solar.<br><br>
        Como asesor del equipo, ¿cuál es la conclusión más correcta sobre lo que está causando la muerte del bosque?
      </div>
      <div class="crisis-options">
        <button class="crisis-opt" id="crisis-a" onclick="chooseCrisis('A')">
          <strong>Opción A</strong>
          Sin luz solar, las plantas no pueden realizar la fotosíntesis. No producen glucosa ni oxígeno, agotan sus reservas de energía y mueren.
        </button>
        <button class="crisis-opt" id="crisis-b" onclick="chooseCrisis('B')">
          <strong>Opción B</strong>
          La contaminación es venenosa para las raíces. Sin poder absorber agua del suelo, las plantas se deshidratan y mueren.
        </button>
      </div>
      <div class="crisis-feedback correct" id="fb-a">
        <strong>✅ Opción A — ¡Correcta!</strong>
        Excelente razonamiento. La luz solar es el primer ingrediente esencial de la fotosíntesis. Sin ella, las plantas no pueden convertir el CO₂ y el agua en glucosa (su alimento) ni liberar oxígeno. Al detener la producción de energía, todos los procesos vitales se paralizan: crecimiento, reparación celular y respiración de tejidos. Las hojas amarillan porque los cloroplastos se degradan sin actividad fotosintética. Esto nos muestra que la fotosíntesis no es solo "hacer oxígeno" — es la base de toda la cadena alimentaria del bosque. Sin ella, el ecosistema completo colapsa. 🌱
      </div>
      <div class="crisis-feedback partial" id="fb-b">
        <strong>⚠️ Opción B — Válida pero incompleta</strong>
        Es cierto que el agua es un insumo esencial de la fotosíntesis (se usa en la fase luminosa) y que la contaminación puede afectar el suelo. Sin embargo, el enunciado indica que el problema central es el bloqueo de la luz solar. Sin luz, aunque haya agua disponible, la fotosíntesis no puede ocurrir de ninguna manera. Esta opción muestra pensamiento correcto sobre la importancia del agua, pero pierde de vista el factor limitante principal: la energía solar. En ciencia, identificar la causa raíz requiere jerarquizar todos los factores. 🔬
      </div>
    </div>
    <div class="nav-row" style="margin-top: 16px;">
      <button class="next-btn" id="crisis-next" style="display:none" onclick="showResults()">
        Ver resultados finales ➜
      </button>
    </div>
  </div>

  <!-- RESULTS SCREEN -->
  <div class="screen" id="screen-results">
    <div class="results-card">
      <div class="results-trophy" id="results-trophy">🏆</div>
      <div class="results-score-num" id="final-score">0/5</div>
      <div class="results-score-label">respuestas correctas</div>
      <div class="results-stars" id="results-stars">⭐⭐⭐⭐⭐</div>
      <div class="results-msg" id="results-msg"></div>
      <button class="restart-btn" onclick="restart()">🔄 Jugar de nuevo</button>
    </div>
  </div>

</div>

<div class="footer">
  Juego educativo sobre Fotosíntesis · Nivel Básico · Para uso en Google Classroom
</div>

<script>
const questions = [
  {
    text: "¿Cuáles son los tres ingredientes principales que las plantas necesitan para realizar la fotosíntesis?",
    options: [
      "Dióxido de carbono, agua y luz solar",
      "Oxígeno, sal y luz solar",
      "Glucosa, nitrógeno y lluvia",
      "Agua, sal y sombra"
    ],
    correct: 0,
    feedbackOk: "✅ ¡Correcto! La fotosíntesis necesita CO₂ (del aire), agua (de las raíces) y luz solar (la fuente de energía). ¡Los tres son indispensables!",
    feedbackWrong: "❌ Los tres ingredientes son: dióxido de carbono (CO₂), agua y luz solar. Sin cualquiera de estos, la fotosíntesis no puede ocurrir."
  },
  {
    text: "¿Qué parte de la célula vegetal captura la luz solar para la fotosíntesis?",
    options: [
      "Las raíces",
      "Los estomas",
      "Los cloroplastos",
      "Los pétalos"
    ],
    correct: 2,
    feedbackOk: "✅ ¡Muy bien! Los cloroplastos contienen clorofila, el pigmento verde que absorbe la energía de la luz. Son como pequeñas 'plantas solares' dentro de las células.",
    feedbackWrong: "❌ Son los cloroplastos. Contienen clorofila (el pigmento verde) y son responsables de capturar la energía solar que impulsa la fotosíntesis."
  },
  {
    text: "¿Qué dos productos genera la fotosíntesis?",
    options: [
      "CO₂ y agua",
      "Glucosa y oxígeno",
      "Nitrógeno y sales minerales",
      "Luz y calor"
    ],
    correct: 1,
    feedbackOk: "✅ ¡Exacto! La fotosíntesis produce glucosa (alimento para la planta) y oxígeno (que se libera al aire y es vital para los seres vivos).",
    feedbackWrong: "❌ Los productos son glucosa y oxígeno. La glucosa alimenta a la planta y el oxígeno se libera al ambiente — ¡el mismo que respiramos nosotros!"
  },
  {
    text: "¿Por qué la mayoría de las hojas de las plantas son de color verde?",
    options: [
      "Porque absorben toda la luz verde",
      "Porque la clorofila refleja la luz verde",
      "Porque el suelo les da ese color",
      "Porque producen glucosa de color verde"
    ],
    correct: 1,
    feedbackOk: "✅ ¡Correcto! La clorofila absorbe principalmente luz roja y azul para usarla en la fotosíntesis, y refleja la luz verde, que es la que vemos nosotros.",
    feedbackWrong: "❌ La clorofila absorbe luz roja y azul, y refleja la luz verde. Por eso vemos ese color — no porque la absorba ni por el suelo."
  },
  {
    text: "¿Qué le pasaría a una planta que es colocada en un cuarto completamente oscuro durante varias semanas?",
    options: [
      "Crecería más rápido al estar protegida",
      "Moriría porque sin luz no puede hacer fotosíntesis",
      "Produciría más oxígeno para compensar",
      "No le pasaría nada, porque tiene raíces"
    ],
    correct: 1,
    feedbackOk: "✅ ¡Bien razonado! Sin luz, la planta no produce glucosa. Al agotar sus reservas de energía, todos sus procesos vitales se detienen y muere.",
    feedbackWrong: "❌ La planta moriría. Sin luz no hay fotosíntesis, sin fotosíntesis no hay glucosa, y sin glucosa la planta no tiene energía para sobrevivir."
  }
];

const colors = ['color-a','color-b','color-c','color-d'];
const letters = ['A','B','C','D'];

let current = 0, score = 0, wrong = 0, answered = false, crisisAnswered = false;
let timer, timeLeft = 20;

function $(id){ return document.getElementById(id); }

function updateProgress(){
  const pct = (current / questions.length) * 100;
  $('progress').style.width = pct + '%';
  $('prog-label').textContent = 'Pregunta ' + (current+1) + ' de ' + questions.length;
  $('score-meta').textContent = 'Puntaje: ' + score;
  $('correct-count').textContent = score;
  $('wrong-count').textContent = wrong;
  $('q-num').textContent = 'Pregunta ' + (current+1);
}

function startTimer(){
  clearInterval(timer);
  timeLeft = 20;
  updateTimerUI();
  timer = setInterval(function(){
    timeLeft--;
    updateTimerUI();
    if(timeLeft <= 0){ clearInterval(timer); if(!answered) timeOut(); }
  }, 1000);
}

function updateTimerUI(){
  $('timer-display').textContent = timeLeft;
  $('timer-val').textContent = timeLeft;
  var urgent = timeLeft <= 5;
  $('timer-display').className = 'timer-val' + (urgent ? ' urgent' : '');
}

function renderQuestion(){
  answered = false;
  var q = questions[current];
  updateProgress();
  $('q-text').textContent = q.text;
  var fb = $('feedback-box');
  fb.style.display = 'none'; fb.className = 'feedback-box';
  $('next-btn').style.display = 'none';
  var grid = $('options-grid');
  grid.innerHTML = '';
  q.options.forEach(function(opt, i){
    var btn = document.createElement('button');
    btn.className = 'opt-btn ' + colors[i];
    btn.innerHTML = '<span class="opt-letter">' + letters[i] + '</span><span>' + opt + '</span>';
    btn.onclick = function(){ selectAnswer(i); };
    grid.appendChild(btn);
  });
  startTimer();
}

function selectAnswer(i){
  if(answered) return;
  answered = true;
  clearInterval(timer);
  var q = questions[current];
  var btns = document.querySelectorAll('.opt-btn');
  btns.forEach(function(b, idx){
    b.disabled = true;
    if(idx === i){
      b.classList.add(i === q.correct ? 'state-correct' : 'state-wrong');
    }
    if(idx === q.correct && i !== q.correct){
      b.classList.add('state-reveal');
    }
    if(idx !== q.correct && idx !== i){
      b.classList.add('state-dim');
    }
  });
  var fb = $('feedback-box');
  if(i === q.correct){
    score++;
    fb.className = 'feedback-box correct';
    fb.textContent = q.feedbackOk;
  } else {
    wrong++;
    fb.className = 'feedback-box wrong';
    fb.textContent = q.feedbackWrong;
  }
  fb.style.display = 'block';
  $('correct-count').textContent = score;
  $('wrong-count').textContent = wrong;
  $('next-btn').style.display = 'flex';
}

function timeOut(){
  answered = true;
  wrong++;
  var q = questions[current];
  var btns = document.querySelectorAll('.opt-btn');
  btns.forEach(function(b, idx){
    b.disabled = true;
    if(idx === q.correct) b.classList.add('state-reveal');
    else b.classList.add('state-dim');
  });
  var fb = $('feedback-box');
  fb.className = 'feedback-box timeout';
  fb.textContent = '⏰ Tiempo agotado. ' + q.feedbackWrong;
  fb.style.display = 'block';
  $('wrong-count').textContent = wrong;
  $('next-btn').style.display = 'flex';
}

function nextQuestion(){
  current++;
  if(current < questions.length){
    renderQuestion();
  } else {
    clearInterval(timer);
    $('screen-quiz').classList.remove('active');
    $('screen-crisis').classList.add('active');
  }
}

function chooseCrisis(opt){
  if(crisisAnswered) return;
  crisisAnswered = true;
  $('crisis-a').classList.add('disabled');
  $('crisis-b').classList.add('disabled');
  if(opt === 'A'){
    $('crisis-a').classList.add('chosen-correct');
    $('fb-a').style.display = 'block';
  } else {
    $('crisis-b').classList.add('chosen-wrong');
    $('fb-b').style.display = 'block';
  }
  $('crisis-next').style.display = 'flex';
}

function showResults(){
  $('screen-crisis').classList.remove('active');
  $('screen-results').classList.add('active');
  $('final-score').textContent = score + '/5';
  var stars, trophy, msg;
  if(score === 5){
    trophy = '🏆'; stars = '⭐⭐⭐⭐⭐';
    msg = '¡Perfecto! Dominas los fundamentos de la fotosíntesis. Entiendes cómo las plantas transforman la luz en vida — eso es pensar como un científico. ¡Sigue así!';
  } else if(score >= 4){
    trophy = '🥇'; stars = '⭐⭐⭐⭐';
    msg = '¡Excelente trabajo! Tienes un dominio muy sólido del tema. Repasa algún detalle sobre los productos o las partes de la célula para llegar al 100%.';
  } else if(score >= 3){
    trophy = '🥈'; stars = '⭐⭐⭐';
    msg = 'Buen trabajo. Tienes una base sólida. Repasa los conceptos sobre cloroplastos, productos y la importancia de cada ingrediente para afianzar tu conocimiento.';
  } else if(score >= 1){
    trophy = '🌱'; stars = '⭐⭐';
    msg = 'Vas bien empezando. La fotosíntesis tiene muchas piezas: luz, clorofila, glucosa y oxígeno. Repasa el tema y vuelve a intentarlo — ¡puedes mejorar!';
  } else {
    trophy = '📖'; stars = '⭐';
    msg = 'Es un buen inicio. Te recomendamos repasar el tema de la fotosíntesis en tu libro de texto y luego volver a intentar el juego. ¡Tú puedes!';
  }
  $('results-trophy').textContent = trophy;
  $('results-stars').textContent = stars;
  $('results-msg').textContent = msg;
}

function restart(){
  current = 0; score = 0; wrong = 0; answered = false; crisisAnswered = false;
  $('fb-a').style.display = 'none';
  $('fb-b').style.display = 'none';
  $('crisis-a').className = 'crisis-opt';
  $('crisis-b').className = 'crisis-opt';
  $('crisis-next').style.display = 'none';
  $('screen-results').classList.remove('active');
  $('screen-crisis').classList.remove('active');
  $('screen-quiz').classList.add('active');
  $('progress').style.width = '0%';
  renderQuestion();
}

renderQuestion();
</script>
</body>
</html>
