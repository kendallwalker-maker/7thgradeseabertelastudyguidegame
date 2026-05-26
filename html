// =========================================================
// APP STATE
// =========================================================
let currentBook = null;
let quizQuestions = [];
let currentQIndex = 0;
let score = 0;
let streak = 0;
let answered = false;
let lastMode = 'book';
let flashQuestions = [];
let flashIndex = 0;
let flashFlipped = false;

// =========================================================
// NAVIGATION & CODES
// =========================================================
function setColor(c) {
  document.documentElement.style.setProperty('--cc', c);
}

function showScreen(id) {
  document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
  document.getElementById(id).classList.add('active');
}

function selectBook(id) {
  currentBook = BOOKS[id];
  setColor(currentBook.color);
  document.getElementById('bh-emoji').textContent = currentBook.emoji;
  document.getElementById('bh-title').textContent = currentBook.title;
  document.getElementById('bh-sub').textContent = currentBook.desc;
  showScreen('book-screen');
  updateDisplays(); // Refresh when opening a book layout
}

function goHome() { 
  showScreen('home'); 
  updateDisplays(); // Forces home screen wallet to update instantly!
}

function goBook() { 
  showScreen('book-screen'); 
  updateDisplays(); // Forces book screen wallet to update instantly!
}

function switchScreen(id) {
  showScreen(id);
  updateDisplays(); // Keeps totals accurate everywhere!
}

// =========================================================
// SHUFFLE SYSTEM
// =========================================================
function shuffle(arr) {
  let a = [...arr];
  for (let i = a.length - 1; i > 0; i--) {
    const j = Math.floor(Math.random() * (i + 1));
    [a[i], a[j]] = [a[j], a[i]];
  }
  return a;
}

// =========================================================
// QUIZ ENGINE
// =========================================================
function startQuiz(mode) {
  lastMode = mode;
  currentQIndex = 0; score = 0; streak = 0;
  if (mode === 'book') quizQuestions = shuffle([...currentBook.questions]);
  else if (mode === 'skills') quizQuestions = shuffle([...SKILLS_Q]);
  else quizQuestions = shuffle([...currentBook.questions, ...SKILLS_Q]);
  showScreen('quiz-screen');
  renderQuestion();
}

function retryQuiz() { startQuiz(lastMode); }

function renderQuestion() {
  const q = quizQuestions[currentQIndex];
  answered = false;
  document.getElementById('q-info').textContent = `Question ${currentQIndex + 1} / ${quizQuestions.length}`;
  document.getElementById('score-disp').textContent = `⭐ ${score} pts`;
  document.getElementById('streak-disp').textContent = streak >= 2 ? `🔥 ${streak} streak!` : '';
  document.getElementById('prog-fill').style.width = (currentQIndex / quizQuestions.length * 100) + '%';
  document.getElementById('q-cat').textContent = q.cat;
  document.getElementById('q-text').textContent = q.q;
  const fb = document.getElementById('feedback');
  fb.classList.remove('show', 'wrong-fb');
  fb.textContent = '';
  document.getElementById('next-btn').classList.remove('show');
  const choicesEl = document.getElementById('choices');
  choicesEl.innerHTML = '';
  const letters = ['A', 'B', 'C', 'D'];
  q.choices.forEach((c, i) => {
    const btn = document.createElement('button');
    btn.className = 'choice-btn';
    btn.innerHTML = `<span style="font-weight:800;color:var(--cc);margin-right:.5rem">${letters[i]}.</span>${c}`;
    btn.onclick = () => selectAnswer(i, q, btn);
    choicesEl.appendChild(btn);
  });
}

function selectAnswer(idx, q, btn) {
  if (answered) return;
  answered = true;
  document.querySelectorAll('.choice-btn').forEach(b => b.classList.add('locked'));
  const fb = document.getElementById('feedback');
  
  if (idx === q.correct) {
    btn.classList.add('correct');
    
    // Calculate the points earned for this specific correct answer
    const pts = 10 + (streak >= 2 ? streak * 2 : 0);
    score += pts; 
    streak++;
    
    // PAY-AS-YOU-GO: Instantly save points to the browser database right now!
    let currentWallet = parseInt(localStorage.getItem('lit_wallet') || '0');
    localStorage.setItem('lit_wallet', currentWallet + pts);
    
    // Refresh the wallet counters on screen instantly
    updateDisplays();
    
    fb.textContent = `✅ Correct! +${pts} points — ${q.feedback}`;
    fb.classList.remove('wrong-fb');
  } else {
    btn.classList.add('wrong');
    document.querySelectorAll('.choice-btn')[q.correct].classList.add('correct');
    streak = 0;
    fb.textContent = `❌ Not quite. ${q.feedback}`;
    fb.classList.add('wrong-fb');
  }
  fb.classList.add('show');
  document.getElementById('next-btn').classList.add('show');
  document.getElementById('score-disp').textContent = `⭐ ${score} pts`;
  document.getElementById('streak-disp').textContent = streak >= 2 ? `🔥 ${streak} streak!` : '';
}

function nextQuestion() {
  currentQIndex++;
  if (currentQIndex >= quizQuestions.length) showResults();
  else renderQuestion();
}

// =========================================================
// RESULTS & CONFETTI
// =========================================================
function showResults() {
  const total = quizQuestions.length;
  const pct = score / (total * 10);
  let trophy, title, stars, msg;
  if (pct >= .9) { trophy = '🏆'; title = 'Amazing!'; stars = '⭐⭐⭐'; msg = "You're a reading champion! You know this material inside and out. Excellent work!"; }
  else if (pct >= .7) { trophy = '🥇'; title = 'Great Job!'; stars = '⭐⭐✨'; msg = "Excellent work! Review the questions you missed and try again to get a perfect score."; }
  else if (pct >= .5) { trophy = '🥈'; title = 'Good Effort!'; stars = '⭐✨✨'; msg = "You're getting there! Try the flash cards to review, then take the quiz again."; }
  else { trophy = '📚'; title = 'Keep Studying!'; stars = '✨✨✨'; msg = "Don't give up — use the flash cards first, then try the quiz again. You can do it!"; }
  document.getElementById('trophy-emoji').textContent = trophy;
  document.getElementById('result-title').textContent = title;
  document.getElementById('result-big').textContent = `${score} pts`;
  document.getElementById('result-stars').textContent = stars;
  document.getElementById('result-msg').textContent = msg;
  showScreen('results-screen');
  updateDisplays();
  if (pct >= .7) launchConfetti();
}

function launchConfetti() {
  const colors = ['#f7c948', '#ff6b6b', '#4ecdc4', '#a29bfe', '#55efc4', '#fd79a8'];
  for (let i = 0; i < 70; i++) {
    setTimeout(() => {
      const el = document.createElement('div');
      el.className = 'confetti-piece';
      el.style.left = Math.random() * 100 + 'vw';
      el.style.background = colors[Math.floor(Math.random() * colors.length)];
      el.style.animationDuration = (1.5 + Math.random() * 2) + 's';
      el.style.animationDelay = (Math.random() * .5) + 's';
      document.body.appendChild(el);
      setTimeout(() => el.remove(), 3500);
    }, i * 30);
  }
}

// =========================================================
// FLASH CARDS
// =========================================================
function startFlash() {
  flashIndex = 0; flashFlipped = false;
  flashQuestions = shuffle([...currentBook.questions, ...SKILLS_Q]);
  document.getElementById('fl-title').textContent = currentBook.title;
  document.getElementById('fl-mode-label').textContent = `${flashQuestions.length} cards — tap to flip`;
  showScreen('flash-screen');
  renderFlash();
}

function renderFlash() {
  const q = flashQuestions[flashIndex];
  document.getElementById('fl-counter').textContent = `${flashIndex + 1} / ${flashQuestions.length}`;
  document.getElementById('fl-front').textContent = q.q;
  const answer = `${String.fromCharCode(65 + q.correct)}. ${q.choices[q.correct]}\n\n💡 ${q.feedback}`;
  document.getElementById('fl-back').textContent = answer;
  document.getElementById('fl-back').style.display = 'none';
  document.querySelector('.flash-hint').textContent = 'Tap to see the answer!';
  flashFlipped = false;
}

function flipCard() {
  flashFlipped = !flashFlipped;
  document.getElementById('fl-back').style.display = flashFlipped ? 'block' : 'none';
  document.querySelector('.flash-hint').textContent = flashFlipped ? 'Tap to hide answer' : 'Tap to see the answer!';
}
function flashNext() { if (flashIndex < flashQuestions.length - 1) { flashIndex++; renderFlash(); } }
function flashPrev() { if (flashIndex > 0) { flashIndex--; renderFlash(); } }

// =========================================================
// BROWNIE STORE & DATA SYNC (PERSISTENCE)
// =========================================================
let classTarget = 15000;

window.onload = function() {
  updateDisplays();
};

function updateDisplays() {
  let myWallet = parseInt(localStorage.getItem('lit_wallet') || '0');
  let classTotal = parseInt(localStorage.getItem('lit_class_total') || '0');

  // Push total out to every possible point tracking ID element across screens
  const walletElements = ['my-wallet', 'shop-wallet', 'home-wallet-disp', 'book-wallet-disp'];
  walletElements.forEach(id => {
    let el = document.getElementById(id);
    if (el) el.textContent = myWallet;
  });

  let classTotalDisp = document.getElementById('class-total-disp');
  let classTargetDisp = document.getElementById('class-target-disp');
  if (classTotalDisp) classTotalDisp.textContent = classTotal;
  if (classTargetDisp) classTargetDisp.textContent = classTarget;

  let progressBar = document.getElementById('class-progress');
  if (progressBar) {
    let pct = Math.min((classTotal / classTarget) * 100, 100);
    progressBar.style.width = pct + '%';
  }
}

function generateContributionCode() {
  let myWallet = parseInt(localStorage.getItem('lit_wallet') || '0');
  if (myWallet <= 0) {
    alert("You don't have any points to donate right now! Go play a quiz!");
    return;
  }

  let classTotal = parseInt(localStorage.getItem('lit_class_total') || '0');
  localStorage.setItem('lit_class_total', classTotal + myWallet);
  localStorage.setItem('lit_wallet', '0');

  let receiptCode = `BROWNIE-DONATE-${Math.floor(1000 + Math.random() * 9000)}-PTS-${myWallet}`;
  let codeBox = document.getElementById('code-box');
  codeBox.textContent = receiptCode;
  codeBox.style.display = 'block';
  document.getElementById('shop-instruction').style.display = 'block';

  navigator.clipboard.writeText(receiptCode);
  updateDisplays();
}

// =========================================================
// TEACHER BACKDOOR PANEL
// =========================================================
function teacherPanel() {
  let pass = prompt("Enter Teacher Security PIN:");
  if (pass === "1234") {
    let action = prompt("Type 'set' to adjust total class points, or 'reset' to completely clear the app cache:");
    if (action === "set") {
      let val = prompt("Enter new absolute total class points:");
      if (val !== null && !isNaN(val)) {
        localStorage.setItem('lit_class_total', parseInt(val));
        updateDisplays();
      }
    } else if (action === "reset") {
      if (confirm("Are you absolutely sure you want to clear all student wallets and progress metrics?")) {
        localStorage.clear();
        updateDisplays();
      }
    }
  } else {
    alert("Incorrect PIN access denied.");
  }
}
</script>
</body>
</html>
