# sor123.github.io
SoR practice
<!DOCTYPE html>
<html lang="zh-TW">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
  <title>五色金字塔英語智慧學習平台</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;600;700&display=swap');
    body { font-family: 'Plus Jakarta Sans', system-ui, -apple-system, sans-serif; background-color: #f3f4f6; }
    .pyramid-stage { transition: all 0.3s ease; }
    .active-stage { transform: scale(1.02); ring: 4px; }
  </style>
</head>
<body class="flex justify-center min-h-screen bg-slate-100">

  <!-- Mobile App Container -->
  <div class="w-full max-w-md bg-white min-h-screen flex flex-col shadow-2xl relative overflow-hidden">
    
    <!-- Top Header & Timer -->
    <header class="bg-slate-900 text-white p-4 flex justify-between items-center sticky top-0 z-50">
      <div>
        <h1 class="text-xs text-slate-400 font-bold uppercase tracking-wider">五色金字塔英語平台</h1>
        <div id="word-title" class="text-lg font-extrabold text-amber-400">001. a</div>
      </div>
      <div class="flex items-center space-x-3">
        <div class="text-right">
          <div class="text-[10px] text-slate-400">闖關剩餘時間</div>
          <div id="timer" class="text-sm font-mono font-bold text-red-400">25:00</div>
        </div>
        <div class="bg-amber-500/20 border border-amber-500/40 px-2 py-1 rounded-lg text-amber-300 font-bold text-xs">
          ⭐ <span id="star-count">0</span>
        </div>
      </div>
    </header>

    <!-- Visual Pyramid Navigation Map -->
    <div class="bg-slate-800 p-3 text-white flex justify-between items-stretch gap-1 text-[11px] font-bold">
      <div id="nav-s5" class="flex-1 py-1 text-center rounded bg-slate-700 opacity-50">🔵 5.文意</div>
      <div id="nav-s4" class="flex-1 py-1 text-center rounded bg-slate-700 opacity-50">🟢 4.識別</div>
      <div id="nav-s3" class="flex-1 py-1 text-center rounded bg-slate-700 opacity-50">🟡 3.流暢</div>
      <div id="nav-s2" class="flex-1 py-1 text-center rounded bg-slate-700 opacity-50">🟠 2.拼讀</div>
      <div id="nav-s1" class="flex-1 py-1 text-center rounded bg-rose-600 border border-rose-400">🔴 1.音素</div>
    </div>

    <!-- Main Content Area -->
    <main class="flex-1 p-5 overflow-y-auto">
      
      <!-- STAGE 1: 音素覺察 -->
      <section id="stage-1" class="space-y-5">
        <div class="bg-rose-50 border-l-4 border-rose-500 p-4 rounded-r-xl">
          <span class="text-xs font-bold text-rose-600 uppercase">🔴 第 1 關：音素覺察</span>
          <h2 class="text-xl font-bold text-slate-800 mt-1">聽音辨音節 (Syllables)</h2>
        </div>
        <div class="text-center py-6 bg-slate-50 rounded-2xl border border-slate-200">
          <div class="text-3xl font-extrabold text-slate-800" id="s1-word">a</div>
          <div class="text-slate-500 mt-1 font-mono" id="s1-phonetic">/ə/</div>
          <button onclick="playAudio(currentWord.target_word)" class="mt-4 bg-rose-500 hover:bg-rose-600 text-white px-5 py-2 rounded-full font-bold shadow-md active:scale-95 transition">
            🔊 播放發音
          </button>
        </div>
        <div class="space-y-3">
          <p class="text-sm font-semibold text-slate-700">請問該單字共有幾個音節？</p>
          <button onclick="checkStage1(1)" class="w-full py-3 bg-white border-2 border-slate-200 rounded-xl font-bold text-slate-700 hover:border-rose-500 active:bg-rose-50 transition">A. 1 個音節</button>
          <button onclick="checkStage1(2)" class="w-full py-3 bg-white border-2 border-slate-200 rounded-xl font-bold text-slate-700 hover:border-rose-500 active:bg-rose-50 transition">B. 2 個音節</button>
          <button onclick="checkStage1(3)" class="w-full py-3 bg-white border-2 border-slate-200 rounded-xl font-bold text-slate-700 hover:border-rose-500 active:bg-rose-50 transition">C. 3 個音節</button>
        </div>
      </section>

      <!-- STAGE 2: 自然拼讀 -->
      <section id="stage-2" class="space-y-5 hidden">
        <div class="bg-orange-50 border-l-4 border-orange-500 p-4 rounded-r-xl">
          <span class="text-xs font-bold text-orange-600 uppercase">🟠 第 2 關：自然拼讀</span>
          <h2 class="text-xl font-bold text-slate-800 mt-1">聽音律聽寫拼音</h2>
        </div>
        <div class="bg-amber-50 border border-amber-200 p-4 rounded-xl text-center">
          <p class="text-xs text-amber-800 mb-2">🎧 系統正在自動連播 2 次字母拆解...</p>
          <button onclick="playSpellingBreakdown()" class="bg-orange-500 text-white px-4 py-2 rounded-lg font-bold text-sm shadow">
            🔁 再次重播 (2次連播)
          </button>
        </div>
        <div class="space-y-3">
          <label class="text-sm font-semibold text-slate-700">請拼寫出正確的單字：</label>
          <input type="text" id="s2-input" placeholder="在此輸入拼字..." class="w-full p-3 border-2 border-slate-300 rounded-xl font-bold text-lg focus:border-orange-500 outline-none">
          <button onclick="checkStage2()" class="w-full py-3 bg-orange-500 text-white rounded-xl font-bold shadow-lg active:scale-95 transition">確認送出</button>
        </div>
      </section>

      <!-- STAGE 3: 流暢準確 -->
      <section id="stage-3" class="space-y-5 hidden">
        <div class="bg-amber-50 border-l-4 border-amber-500 p-4 rounded-r-xl">
          <span class="text-xs font-bold text-amber-600 uppercase">🟡 第 3 關：流暢準確</span>
          <h2 class="text-xl font-bold text-slate-800 mt-1">朗讀流暢度評測</h2>
        </div>
        <div class="p-4 bg-slate-50 border border-slate-200 rounded-xl space-y-3">
          <p class="text-xs text-slate-500 font-bold">示範例句：</p>
          <p id="s3-sentence" class="text-lg font-extrabold text-slate-800">This is a book.</p>
          <div class="flex items-center justify-between pt-2 border-t border-slate-200">
            <span class="text-xs text-slate-500">語速選擇：</span>
            <div class="space-x-1">
              <button onclick="playSentence(0.75)" class="px-2 py-1 bg-slate-200 rounded text-xs font-bold">0.75x</button>
              <button onclick="playSentence(1.0)" class="px-2 py-1 bg-amber-500 text-white rounded text-xs font-bold">1.0x</button>
            </div>
          </div>
        </div>
        <div class="text-center py-4 space-y-3">
          <button id="record-btn" onclick="simulateRecording()" class="w-20 h-20 bg-rose-500 rounded-full text-white font-bold shadow-xl border-4 border-rose-200 active:scale-90 transition">
            🎙️<br><span class="text-xs">錄音挑戰</span>
          </button>
          <p id="s3-status" class="text-xs text-slate-500">點擊麥克風開始錄音（需達到 95% 通關）</p>
        </div>
      </section>

      <!-- STAGE 4: 單字識別 -->
      <section id="stage-4" class="space-y-5 hidden">
        <div class="bg-emerald-50 border-l-4 border-emerald-500 p-4 rounded-r-xl">
          <span class="text-xs font-bold text-emerald-600 uppercase">🟢 第 4 關：單字識別</span>
          <h2 class="text-xl font-bold text-slate-800 mt-1">重組與語意選填</h2>
        </div>
        
        <!-- Q1: Drag/Tap unscramble -->
        <div class="space-y-2">
          <p class="text-xs font-bold text-slate-600">Q1. 點擊卡片重組句子：</p>
          <div id="unscramble-target" class="min-h-[50px] p-2 bg-slate-100 border-2 border-dashed border-slate-300 rounded-xl flex flex-wrap gap-2 items-center">
            <!-- Selected words appear here -->
          </div>
          <div id="unscramble-source" class="flex flex-wrap gap-2 pt-2">
            <!-- Source words -->
          </div>
          <button onclick="resetUnscramble()" class="text-xs text-slate-400 underline">重置卡片</button>
        </div>

        <hr class="my-4">

        <!-- Q2: Multiple Choice -->
        <div class="space-y-3">
          <p class="text-xs font-bold text-slate-600">Q2. 選出最適合填入空格的單字：</p>
          <p id="s4-q2-text" class="text-sm font-bold text-slate-800">This ________ a book.</p>
          <div id="s4-options" class="space-y-2">
            <!-- Options injected by JS -->
          </div>
        </div>

        <button onclick="checkStage4()" class="w-full py-3 bg-emerald-500 text-white rounded-xl font-bold shadow-lg active:scale-95 transition">提交第 4 關答案</button>
      </section>

      <!-- STAGE 5: 文意理解 -->
      <section id="stage-5" class="space-y-5 hidden">
        <div class="bg-blue-50 border-l-4 border-blue-500 p-4 rounded-r-xl">
          <span class="text-xs font-bold text-blue-600 uppercase">🔵 第 5 關：文意理解</span>
          <h2 class="text-xl font-bold text-slate-800 mt-1">60秒限時默寫與翻譯</h2>
        </div>
        <div class="space-y-3">
          <label class="text-xs font-bold text-slate-600">Part 1. 全句默寫（播放例句 2 次）：</label>
          <button onclick="playSentence(1.0)" class="text-xs bg-blue-100 text-blue-700 px-3 py-1 rounded-full font-bold">🎧 播放例句</button>
          <input type="text" id="s5-dictation" placeholder="請在此默寫出完整英文例句..." class="w-full p-3 border-2 border-slate-300 rounded-xl font-bold text-sm focus:border-blue-500 outline-none">
        </div>
        <div class="space-y-3">
          <label class="text-xs font-bold text-slate-600">Part 2. 請輸入繁體中文意譯：</label>
          <textarea id="s5-translation" rows="2" placeholder="請輸入中文翻譯..." class="w-full p-3 border-2 border-slate-300 rounded-xl text-sm focus:border-blue-500 outline-none"></textarea>
        </div>
        <button onclick="finishCard()" class="w-full py-4 bg-blue-600 text-white rounded-xl font-extrabold text-lg shadow-xl active:scale-95 transition">🎉 完成本單字卡闖關</button>
      </section>

    </main>

    <!-- Modal / Audio Feedback Notice -->
    <div id="modal" class="fixed inset-0 bg-black/60 z-50 flex items-center justify-center p-4 hidden">
      <div class="bg-white rounded-2xl p-6 max-w-sm w-full space-y-4 text-center">
        <div id="modal-icon" class="text-4xl">🎉</div>
        <h3 id="modal-title" class="text-xl font-bold text-slate-800">闖關成功</h3>
        <p id="modal-msg" class="text-sm text-slate-600">獲得 5 顆星！</p>
        <button onclick="closeModal()" class="w-full py-3 bg-slate-900 text-white font-bold rounded-xl">繼續下一關</button>
      </div>
    </div>

  </div>

  <script>
    // --- Data Definition (Sample Dataset matching User's 700 Word List) ---
    const vocabularyList = [
      {
        id: "ELEM_001",
        target_word: "a",
        kk_phonetic: "/ə/",
        syllables: 1,
        spelling_breakdown: "a",
        example_sentence: "This is a book.",
        scrambled: ["book.", "a", "This", "is"],
        q2_text: "This ________ a book.",
        q2_options: [
          { text: "a (正確答案)", correct: true },
          { text: "an", correct: false },
          { text: "the", correct: false },
          { text: "and", correct: false }
        ],
        chinese: "這是一本書。"
      },
      {
        id: "ELEM_002",
        target_word: "able",
        kk_phonetic: "/ˈeɪ.bəl/",
        syllables: 2,
        spelling_breakdown: "a - b - l - e",
        example_sentence: "He is able to swim fast.",
        scrambled: ["fast.", "to", "He", "able", "swim", "is"],
        q2_text: "He is ________ to swim fast.",
        q2_options: [
          { text: "able (正確答案)", correct: true },
          { text: "ability", correct: false },
          { text: "ably", correct: false },
          { text: "disable", correct: false }
        ],
        chinese: "他能夠游泳游得很快。"
      }
    ];

    let currentIndex = 0;
    let currentWord = vocabularyList[currentIndex];
    let totalStars = 0;
    let selectedScramble = [];
    let stage4Answer = null;

    // --- Web Speech API (TTS) ---
    function playAudio(text, rate = 1.0) {
      if ('speechSynthesis' in window) {
        window.speechSynthesis.cancel();
        const utterance = new SpeechSynthesisUtterance(text);
        utterance.lang = 'en-US';
        utterance.rate = rate;
        window.speechSynthesis.speak(utterance);
      }
    }

    function speakDiagnostic(text) {
      if ('speechSynthesis' in window) {
        const utterance = new SpeechSynthesisUtterance(text);
        utterance.lang = 'zh-TW';
        window.speechSynthesis.speak(utterance);
      }
    }

    function playSpellingBreakdown() {
      const letters = currentWord.target_word.split('').join(' - ');
      playAudio(`${currentWord.target_word}. ${letters}.`, 0.8);
      setTimeout(() => {
        playAudio(`${currentWord.target_word}. ${letters}.`, 0.8);
      }, 3000);
    }

    function playSentence(rate) {
      playAudio(currentWord.example_sentence, rate);
    }

    // --- Stage Controllers ---
    function loadWord(index) {
      currentWord = vocabularyList[index];
      document.getElementById('word-title').innerText = `${currentWord.id.replace('ELEM_','')} ${currentWord.target_word}`;
      document.getElementById('s1-word').innerText = currentWord.target_word;
      document.getElementById('s1-phonetic').innerText = currentWord.kk_phonetic;
      document.getElementById('s3-sentence').innerText = currentWord.example_sentence;
      document.getElementById('s4-q2-text').innerText = currentWord.q2_text;
      
      // Init Stage 4 Q1 Cards
      resetUnscramble();
      
      // Init Stage 4 Q2 Options
      const optContainer = document.getElementById('s4-options');
      optContainer.innerHTML = '';
      currentWord.q2_options.forEach((opt, idx) => {
        const btn = document.createElement('button');
        btn.className = "w-full py-2 px-3 bg-white border border-slate-200 rounded-lg text-left text-sm font-semibold hover:border-emerald-500 focus:bg-emerald-50";
        btn.innerText = `${String.fromCharCode(65 + idx)}. ${opt.text}`;
        btn.onclick = () => { stage4Answer = opt.correct; };
        optContainer.appendChild(btn);
      });
    }

    function checkStage1(ans) {
      if (ans === currentWord.syllables) {
        addStars(5);
        showModal('🎉 答對了！', '獲贈 5 顆星，進入第 2 關自然拼讀！', () => {
          switchStage(1, 2);
          playSpellingBreakdown();
        });
      } else {
        alert('解答不正確，請再聽一次發音！');
      }
    }

    function checkStage2() {
      const val = document.getElementById('s2-input').value.trim().toLowerCase();
      if (val === currentWord.target_word.toLowerCase()) {
        addStars(5);
        showModal('🎉 拼寫完全正確！', '進入第 3 關流暢準確評測！', () => {
          switchStage(2, 3);
        });
      } else {
        alert('拼寫有誤，請再聽一次語音拆解提示！');
      }
    }

    function simulateRecording() {
      document.getElementById('s3-status').innerText = "AI 辨識中...";
      setTimeout(() => {
        const accuracy = 96; // Simulated 96% accuracy
        addStars(5);
        speakDiagnostic("太棒了！你的發音與節奏非常完美，達標 96%，順利通過第 3 關！");
        showModal('💯 流暢度達標 96%', 'AI 語音 diagnostic 反饋已播報，解鎖第 4 關！', () => {
          switchStage(3, 4);
        });
      }, 1500);
    }

    function resetUnscramble() {
      selectedScramble = [];
      const targetDiv = document.getElementById('unscramble-target');
      const sourceDiv = document.getElementById('unscramble-source');
      targetDiv.innerHTML = '';
      sourceDiv.innerHTML = '';

      currentWord.scrambled.forEach((word) => {
        const card = document.createElement('span');
        card.className = "px-3 py-1 bg-white border border-slate-300 shadow-sm rounded-lg text-sm font-bold cursor-pointer active:scale-95";
        card.innerText = word;
        card.onclick = () => handleCardTap(card, word);
        sourceDiv.appendChild(card);
      });
    }

    function handleCardTap(cardElement, word) {
      const targetDiv = document.getElementById('unscramble-target');
      if (cardElement.parentElement.id === 'unscramble-source') {
        targetDiv.appendChild(cardElement);
        selectedScramble.push(word);
      } else {
        document.getElementById('unscramble-source').appendChild(cardElement);
        selectedScramble = selectedScramble.filter(w => w !== word);
      }
    }

    function checkStage4() {
      if (stage4Answer === true) {
        addStars(5);
        showModal('🎉 識別關全對！', '解鎖第 5 關文意理解！', () => {
          switchStage(4, 5);
        });
      } else {
        alert('題目回答有誤，請重新檢查選擇題！');
      }
    }

    function finishCard() {
      addStars(4);
      showModal('🏆 恭喜完成單字卡！', `累計星幣：${totalStars} 顆星！`, () => {
        if (currentIndex + 1 < vocabularyList.length) {
          currentIndex++;
          loadWord(currentIndex);
          switchStage(5, 1);
        } else {
          alert('恭喜完成本單字庫所有測試！');
        }
      });
    }

    // --- Helpers ---
    function switchStage(from, to) {
      document.getElementById(`stage-${from}`).classList.add('hidden');
      document.getElementById(`stage-${to}`).classList.remove('hidden');
      
      const navFrom = document.getElementById(`nav-s${from}`);
      const navTo = document.getElementById(`nav-s${to}`);
      
      navFrom.className = "flex-1 py-1 text-center rounded bg-slate-700 opacity-50";
      navTo.className = "flex-1 py-1 text-center rounded bg-rose-600 border border-rose-400";
    }

    function addStars(count) {
      totalStars += count;
      document.getElementById('star-count').innerText = totalStars;
    }

    function showModal(title, msg, callback) {
      document.getElementById('modal-title').innerText = title;
      document.getElementById('modal-msg').innerText = msg;
      document.getElementById('modal').classList.remove('hidden');
      window.modalCallback = callback;
    }

    function closeModal() {
      document.getElementById('modal').classList.add('hidden');
      if (window.modalCallback) window.modalCallback();
    }

    // Timer Init
    let timeLeft = 1500;
    setInterval(() => {
      if (timeLeft > 0) {
        timeLeft--;
        const m = String(Math.floor(timeLeft / 60)).padStart(2, '0');
        const s = String(timeLeft % 60).padStart(2, '0');
        document.getElementById('timer').innerText = `${m}:${s}`;
      }
    }, 1000);

    // Init App
    loadWord(0);
  </script>
</body>
</html>
