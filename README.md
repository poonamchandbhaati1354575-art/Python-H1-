<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Vedic Math Magic Kingdom 🌟 Mental Math Superpowers for Kids</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- FontAwesome Icons -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <!-- Google Fonts: Fredoka & Comic Neue for friendly child-oriented typography -->
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Comic+Neue:wght@700&family=Fredoka:wght@400;500;600;700&display=swap" rel="stylesheet">
    <!-- Canvas Confetti -->
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>

    <style>
        * {
            font-family: 'Fredoka', cursive, sans-serif;
            user-select: none;
        }

        body {
            background: linear-gradient(135deg, #FFF9E6 0%, #E6F7FF 50%, #F3E8FF 100%);
            min-height: 100vh;
        }

        /* Fun bounce and pulse keyframe animations */
        @keyframes floatSlow {
            0%, 100% { transform: translateY(0px) rotate(0deg); }
            50% { transform: translateY(-12px) rotate(2deg); }
        }

        @keyframes pulseGlow {
            0%, 100% { box-shadow: 0 0 15px rgba(255, 193, 7, 0.6); }
            50% { box-shadow: 0 0 30px rgba(255, 193, 7, 1); }
        }

        @keyframes popIn {
            0% { transform: scale(0.8); opacity: 0; }
            80% { transform: scale(1.05); }
            100% { transform: scale(1); opacity: 1; }
        }

        .animate-float {
            animation: floatSlow 4s ease-in-out infinite;
        }

        .animate-pulse-glow {
            animation: pulseGlow 2s infinite;
        }

        .animate-pop {
            animation: popIn 0.3s cubic-bezier(0.175, 0.885, 0.32, 1.275) forwards;
        }

        /* Tactile pushable button styles */
        .btn-bounce {
            transition: all 0.15s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            box-shadow: 0 6px 0 rgba(0,0,0,0.15);
        }
        .btn-bounce:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 0 rgba(0,0,0,0.15);
        }
        .btn-bounce:active {
            transform: translateY(4px);
            box-shadow: 0 2px 0 rgba(0,0,0,0.15);
        }

        /* Custom Scrollbars */
        ::-webkit-scrollbar {
            width: 10px;
        }
        ::-webkit-scrollbar-track {
            background: #FFE8AC;
            border-radius: 10px;
        }
        ::-webkit-scrollbar-thumb {
            background: #FF8A00;
            border-radius: 10px;
        }

        .badge-card {
            transition: transform 0.3s ease;
        }
        .badge-card:hover {
            transform: scale(1.08) rotate(2deg);
        }
    </style>
</head>
<body class="text-slate-800 pb-12 flex flex-col min-h-screen">

    <!-- TOP NAVIGATION & HUD -->
    <header class="sticky top-0 z-50 bg-white/90 backdrop-blur-md border-b-4 border-amber-300 shadow-md">
        <div class="max-w-6xl mx-auto px-4 py-3 flex items-center justify-between flex-wrap gap-2">
            
            <!-- Logo & Mascot Branding -->
            <div class="flex items-center space-x-3 cursor-pointer" onclick="switchTab('tricks')">
                <div class="w-12 h-12 bg-gradient-to-tr from-amber-400 to-orange-400 rounded-full flex items-center justify-center text-white text-2xl shadow-lg animate-float">
                    🐘
                </div>
                <div>
                    <h1 class="text-2xl md:text-3xl font-extrabold text-orange-600 leading-none">VedicMath<span class="text-amber-500">Magic!</span></h1>
                    <p class="text-xs font-semibold text-slate-500">Math Superpowers for Young Genius Kids 🚀</p>
                </div>
            </div>

            <!-- Navigation Tabs -->
            <nav class="flex items-center space-x-2 md:space-x-3">
                <button onclick="switchTab('tricks')" id="nav-tricks" class="px-4 py-2 rounded-2xl font-bold text-sm md:text-base flex items-center gap-2 transition-all bg-amber-400 text-slate-900 shadow-md btn-bounce">
                    <i class="fa-solid fa-wand-magic-sparkles text-orange-700"></i> Tricks Hub
                </button>
                <button onclick="switchTab('quiz')" id="nav-quiz" class="px-4 py-2 rounded-2xl font-bold text-sm md:text-base flex items-center gap-2 transition-all bg-white text-slate-700 hover:bg-amber-100 btn-bounce">
                    <i class="fa-solid fa-gamepad text-purple-600"></i> Quiz Zone
                </button>
                <button onclick="switchTab('story')" id="nav-story" class="px-4 py-2 rounded-2xl font-bold text-sm md:text-base flex items-center gap-2 transition-all bg-white text-slate-700 hover:bg-amber-100 btn-bounce">
                    <i class="fa-solid fa-book-open-reader text-emerald-600"></i> Vedic Lore
                </button>
            </nav>

            <!-- Rewards Counters (Stars & Sound Toggle) -->
            <div class="flex items-center gap-3">
                <!-- Star Counter -->
                <div class="flex items-center gap-2 bg-amber-100 border-2 border-amber-400 px-3 py-1.5 rounded-full shadow-inner">
                    <i class="fa-solid fa-star text-amber-500 text-xl animate-bounce"></i>
                    <span id="global-star-count" class="font-black text-xl text-amber-700">0</span>
                </div>

                <!-- Sound Toggle Button -->
                <button onclick="toggleAudio()" id="audio-btn" class="w-10 h-10 bg-slate-100 border-2 border-slate-300 rounded-full flex items-center justify-center text-slate-700 hover:bg-slate-200 btn-bounce" title="Toggle Sound">
                    <i id="audio-icon" class="fa-solid fa-volume-high text-lg"></i>
                </button>
            </div>
        </div>
    </header>

    <!-- MAIN CONTAINER AREA -->
    <main class="max-w-6xl mx-auto px-4 py-6 flex-grow w-full">

        <!-- MASCOT WELCOME BANNER -->
        <div class="bg-gradient-to-r from-orange-400 via-amber-300 to-yellow-300 rounded-3xl p-5 md:p-6 mb-8 border-4 border-white shadow-xl flex flex-col md:flex-row items-center gap-4 relative overflow-hidden">
            <div class="text-6xl md:text-7xl bg-white p-3 rounded-full shadow-md animate-bounce">
                🐘
            </div>
            <div class="flex-grow text-center md:text-left">
                <h2 class="text-2xl md:text-3xl font-extrabold text-slate-900 mb-1">Namaste, Little Math Explorer! 🙏</h2>
                <p id="mascot-speech" class="text-slate-800 text-base md:text-lg font-medium">
                    I'm <span class="font-extrabold text-orange-800">Ganesha the Wise</span>! Vedic Math turns giant numbers into tiny puzzle pieces. Pick a magical trick below to start your adventure!
                </p>
            </div>
            <div class="flex gap-2 bg-white/70 backdrop-blur-sm p-3 rounded-2xl border border-white text-center shadow-inner">
                <div>
                    <span id="badges-unlocked-count" class="text-2xl font-black text-purple-600 block">0/5</span>
                    <span class="text-xs font-bold text-slate-600 uppercase">Badges</span>
                </div>
            </div>
        </div>

        <!-- ==================== TAB 1: TRICKS HUB ==================== -->
        <section id="tab-tricks" class="space-y-8">
            
            <!-- TRICK SELECTOR CARDS GRID -->
            <div>
                <h3 class="text-2xl font-black text-slate-800 mb-4 flex items-center gap-2">
                    <i class="fa-solid fa-bolt text-yellow-500"></i> Choose a Vedic Shortcut:
                </h3>
                <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4" id="trick-cards-grid">
                    <!-- Cards will be dynamically injected or rendered -->
                </div>
            </div>

            <!-- INTERACTIVE MAGIC BOX VISUALIZER -->
            <div id="interactive-visualizer" class="bg-white rounded-3xl border-4 border-amber-300 shadow-2xl p-6 md:p-8 animate-pop">
                <!-- Visualizer Header -->
                <div class="flex flex-col md:flex-row md:items-center justify-between gap-4 border-b-2 border-dashed border-amber-200 pb-4 mb-6">
                    <div>
                        <span id="current-sutra-tag" class="bg-amber-100 text-amber-800 font-extrabold text-xs px-3 py-1 rounded-full uppercase tracking-wider">
                            Sutra: Ekadhikena Purvena
                        </span>
                        <h3 id="current-trick-title" class="text-2xl md:text-3xl font-black text-orange-600 mt-1">
                            Squaring Numbers Ending in 5
                        </h3>
                        <p id="current-trick-desc" class="text-slate-600 font-medium text-sm md:text-base">
                            Multiply the first number by its next integer, then add 25 at the end!
                        </p>
                    </div>

                    <!-- Custom Input Box for Dynamic Calculations -->
                    <div class="bg-amber-50 p-3 rounded-2xl border-2 border-amber-300 flex items-center gap-2">
                        <label for="user-number-input" class="text-xs font-bold text-amber-900 uppercase">Try your own number:</label>
                        <input type="text" id="user-number-input" class="w-24 text-center font-black text-xl py-1 px-2 rounded-xl border-2 border-amber-400 text-slate-800 focus:outline-none focus:ring-2 focus:ring-amber-500" value="25">
                        <button onclick="calculateCustomInput()" class="bg-amber-500 text-white font-bold px-3 py-1.5 rounded-xl hover:bg-amber-600 btn-bounce text-sm">
                            Magic! ✨
                        </button>
                    </div>
                </div>

                <!-- STEP-BY-STEP VISUAL DISPLAY AREA -->
                <div class="grid grid-cols-1 lg:grid-cols-12 gap-6 items-center">
                    <!-- Steps Dynamic Visual Box -->
                    <div class="lg:col-span-8 bg-slate-50 rounded-2xl p-6 border-2 border-slate-200 min-h-[320px] flex flex-col justify-between" id="visualizer-steps-container">
                        <!-- Dynamic visual elements will load here -->
                    </div>

                    <!-- Interactive Mascot Helper & Quiz Shortcut -->
                    <div class="lg:col-span-4 bg-gradient-to-b from-orange-50 to-amber-100 rounded-2xl p-6 border-2 border-amber-300 flex flex-col items-center text-center justify-between h-full space-y-4">
                        <div class="text-6xl animate-bounce">
                            🧙‍♂️
                        </div>
                        <div>
                            <h4 class="font-extrabold text-amber-900 text-lg mb-1">Why does this work?</h4>
                            <p id="trick-explanation-text" class="text-xs md:text-sm text-slate-700">
                                In ancient India, scholars found that patterns in base-10 math let us bypass long multiplication!
                            </p>
                        </div>
                        <button onclick="startQuizForCurrentTrick()" class="w-full bg-emerald-500 hover:bg-emerald-600 text-white font-bold py-3 px-4 rounded-2xl shadow-lg btn-bounce text-sm flex items-center justify-center gap-2">
                            <i class="fa-solid fa-circle-play"></i> Practice This Trick!
                        </button>
                    </div>
                </div>
            </div>

        </section>

        <!-- ==================== TAB 2: QUIZ ZONE ==================== -->
        <section id="tab-quiz" class="hidden space-y-6">
            <div class="bg-white rounded-3xl border-4 border-purple-300 shadow-2xl p-6 md:p-8">
                
                <!-- Quiz Controls Header -->
                <div class="flex flex-col md:flex-row items-center justify-between gap-4 border-b-2 border-purple-100 pb-4 mb-6">
                    <div>
                        <h2 class="text-2xl md:text-3xl font-black text-purple-700 flex items-center gap-2">
                            <i class="fa-solid fa-trophy text-amber-400"></i> Math Superpowers Quiz Arena
                        </h2>
                        <p class="text-slate-600 text-sm">Solve questions using your Vedic shortcuts to earn magical stars and badges!</p>
                    </div>

                    <!-- Mode Toggle & Timer Settings -->
                    <div class="flex items-center gap-4 bg-purple-50 p-3 rounded-2xl border border-purple-200">
                        <div class="flex items-center gap-2">
                            <i class="fa-solid fa-stopwatch text-purple-600"></i>
                            <span class="text-xs font-bold text-slate-700">Timer Mode:</span>
                            <button id="timer-toggle-btn" onclick="toggleQuizTimer()" class="bg-purple-200 text-purple-800 text-xs font-bold px-3 py-1 rounded-full btn-bounce">
                                OFF ☕ (Casual)
                            </button>
                        </div>
                    </div>
                </div>

                <!-- Quiz Main Game Screen -->
                <div id="quiz-game-screen" class="max-w-2xl mx-auto text-center space-y-6 py-4">
                    
                    <!-- Progress Bar & Score HUD -->
                    <div class="flex items-center justify-between text-sm font-bold text-slate-600">
                        <span>Question <span id="quiz-question-number" class="text-purple-700 text-lg">1</span> / 5</span>
                        <span id="quiz-timer-display" class="hidden text-red-500 font-extrabold text-lg">⏱️ 15s</span>
                        <span class="text-amber-600 font-extrabold">Score: <span id="quiz-current-score" class="text-xl">0</span></span>
                    </div>

                    <!-- Progress Bar Track -->
                    <div class="w-full bg-slate-200 h-3 rounded-full overflow-hidden">
                        <div id="quiz-progress-bar" class="bg-gradient-to-r from-purple-500 to-amber-400 h-full w-1/5 transition-all duration-300"></div>
                    </div>

                    <!-- Question Card -->
                    <div class="bg-gradient-to-b from-purple-50 to-indigo-50 border-4 border-purple-200 rounded-3xl p-8 shadow-inner relative">
                        <span id="quiz-sutra-hint" class="bg-purple-200 text-purple-900 text-xs font-bold px-3 py-1 rounded-full uppercase tracking-wider">
                            Trick: Squaring ending in 5
                        </span>
                        <h3 id="quiz-question-text" class="text-4xl md:text-5xl font-black text-slate-800 my-6">
                            35 × 35 = ?
                        </h3>

                        <!-- Option Buttons Container -->
                        <div id="quiz-options-grid" class="grid grid-cols-1 sm:grid-cols-2 gap-4 mt-6">
                            <!-- Option Buttons generated dynamically -->
                        </div>
                    </div>

                    <!-- Feedback Banner -->
                    <div id="quiz-feedback" class="hidden p-4 rounded-2xl font-extrabold text-lg animate-pop">
                        <!-- Dynamic Feedback Message -->
                    </div>

                    <!-- Next Question Button -->
                    <button id="quiz-next-btn" onclick="nextQuizQuestion()" class="hidden w-full bg-amber-500 hover:bg-amber-600 text-white font-black text-lg py-4 rounded-2xl shadow-xl btn-bounce">
                        Next Question! 🚀
                    </button>
                </div>

                <!-- Quiz Results / Completion Overlay -->
                <div id="quiz-results-screen" class="hidden text-center py-8 space-y-6 animate-pop">
                    <div class="text-7xl">🎉</div>
                    <h3 class="text-3xl font-black text-purple-800">Awesome Job, Math Superhero!</h3>
                    <p class="text-slate-600 font-medium">You completed the quiz challenge with flying colors!</p>
                    
                    <div class="flex justify-center items-center gap-6 my-4">
                        <div class="bg-amber-100 p-4 rounded-2xl border-2 border-amber-300 text-center">
                            <span class="text-xs text-amber-800 uppercase font-bold block">Stars Earned</span>
                            <span id="quiz-final-stars" class="text-3xl font-black text-amber-600">0 ⭐</span>
                        </div>
                        <div class="bg-purple-100 p-4 rounded-2xl border-2 border-purple-300 text-center">
                            <span class="text-xs text-purple-800 uppercase font-bold block">Accuracy</span>
                            <span id="quiz-final-accuracy" class="text-3xl font-black text-purple-600">100%</span>
                        </div>
                    </div>

                    <button onclick="resetQuiz()" class="bg-purple-600 hover:bg-purple-700 text-white font-black text-lg px-8 py-4 rounded-2xl shadow-xl btn-bounce">
                        Play Again! 🔄
                    </button>
                </div>

            </div>

            <!-- UNLOCKED BADGES & ACHIEVEMENTS SECTION -->
            <div class="bg-white rounded-3xl border-4 border-amber-200 p-6 shadow-xl">
                <h3 class="text-xl font-black text-slate-800 mb-4 flex items-center gap-2">
                    <i class="fa-solid fa-award text-amber-500"></i> Math Superpower Badges
                </h3>
                <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-5 gap-4" id="badges-container">
                    <!-- Badges rendered via JavaScript -->
                </div>
            </div>
        </section>

        <!-- ==================== TAB 3: VEDIC LORE / STORY ==================== -->
        <section id="tab-story" class="hidden space-y-6">
            <div class="bg-white rounded-3xl border-4 border-emerald-300 shadow-2xl p-6 md:p-8 space-y-6">
                
                <div class="text-center max-w-2xl mx-auto space-y-2">
                    <span class="bg-emerald-100 text-emerald-800 font-black text-xs px-3 py-1 rounded-full uppercase">
                        Ancient India Secrets
                    </span>
                    <h2 class="text-3xl md:text-4xl font-black text-emerald-700">
                        The Ancient Story of Vedic Math 📜✨
                    </h2>
                    <p class="text-slate-600 font-medium">Discover how ancient sages solved huge math problems in their heads like magical wizards!</p>
                </div>

                <!-- Story Cards Grid -->
                <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                    <!-- Card 1 -->
                    <div class="bg-emerald-50 rounded-2xl p-5 border-2 border-emerald-200 flex flex-col justify-between space-y-3">
                        <div class="text-4xl">🏛️</div>
                        <h4 class="font-extrabold text-emerald-900 text-lg">1. What is Vedic Math?</h4>
                        <p class="text-xs text-slate-700 leading-relaxed">
                            Vedic Math comes from ancient Indian texts called the <b>Vedas</b>. Hundreds of years ago, mathematicians discovered 16 simple word-rules called <i>Sutras</i> that make math super fast!
                        </p>
                    </div>

                    <!-- Card 2 -->
                    <div class="bg-amber-50 rounded-2xl p-5 border-2 border-amber-200 flex flex-col justify-between space-y-3">
                        <div class="text-4xl">🧠</div>
                        <h4 class="font-extrabold text-amber-900 text-lg">2. Why use Math Shortcuts?</h4>
                        <p class="text-xs text-slate-700 leading-relaxed">
                            Instead of doing tedious long multiplication on paper, Vedic math lets you solve calculations in your head using fun visual patterns and mental symmetry!
                        </p>
                    </div>

                    <!-- Card 3 -->
                    <div class="bg-purple-50 rounded-2xl p-5 border-2 border-purple-200 flex flex-col justify-between space-y-3">
                        <div class="text-4xl">🦸‍♂️</div>
                        <h4 class="font-extrabold text-purple-900 text-lg">3. Become a Math Wizard!</h4>
                        <p class="text-xs text-slate-700 leading-relaxed">
                            Practicing Vedic math boosts your memory, speed, and confidence. You can impress your teachers and friends by solving math problems faster than a calculator!
                        </p>
                    </div>
                </div>

                <!-- Interactive Sutra Mini-Dictionary -->
                <div class="bg-slate-50 rounded-2xl p-6 border-2 border-slate-200">
                    <h3 class="font-black text-slate-800 text-lg mb-3 flex items-center gap-2">
                        <i class="fa-solid fa-scroll text-amber-600"></i> Ancient Vedic Sutras Dictionary:
                    </h3>
                    <div class="grid grid-cols-1 sm:grid-cols-2 gap-4 text-xs font-medium">
                        <div class="p-3 bg-white rounded-xl border border-slate-200">
                            <span class="font-extrabold text-orange-600 block text-sm">1. Ekadhikena Purvena</span>
                            <span class="text-slate-500">"By one more than the previous one" (Used for fast squares ending in 5)</span>
                        </div>
                        <div class="p-3 bg-white rounded-xl border border-slate-200">
                            <span class="font-extrabold text-purple-600 block text-sm">2. Nikhilam Navatashcaramam Dashatah</span>
                            <span class="text-slate-500">"All from 9 and the last from 10" (Used for fast subtraction from 100/1000)</span>
                        </div>
                        <div class="p-3 bg-white rounded-xl border border-slate-200">
                            <span class="font-extrabold text-emerald-600 block text-sm">3. Urdhva-Tiryagbhyam</span>
                            <span class="text-slate-500">"Vertically and Crosswise" (Criss-cross multiplication for any numbers)</span>
                        </div>
                        <div class="p-3 bg-white rounded-xl border border-slate-200">
                            <span class="font-extrabold text-blue-600 block text-sm">4. Antyayordashake'pi</span>
                            <span class="text-slate-500">"Numbers close to bases" (Fast base-10 multiplication shortcuts)</span>
                        </div>
                    </div>
                </div>

            </div>
        </section>

    </main>

    <!-- FOOTER -->
    <footer class="mt-auto text-center py-4 text-xs text-slate-500 font-semibold">
        <p>Vedic Math Magic Kingdom 🌟 Created with ❤️ for Kids & Young Learners</p>
    </footer>

    <script>
        /* ==================== APP STATE & SOUND SYSTEM ==================== */
        const state = {
            activeTab: 'tricks',
            selectedTrickId: 0,
            stars: 0,
            soundEnabled: true,
            timerEnabled: false,
            quizIndex: 0,
            quizScore: 0,
            timerInterval: null,
            timeLeft: 15,
            unlockedBadges: [false, false, false, false, false]
        };

        // Web Audio API Synthesizer for Fun Kid SFX
        const audioCtx = new (window.AudioContext || window.webkitAudioContext)();

        function playSound(type) {
            if (!state.soundEnabled) return;
            try {
                const osc = audioCtx.createOscillator();
                const gain = audioCtx.createGain();
                osc.connect(gain);
                gain.connect(audioCtx.destination);

                if (type === 'correct') {
                    osc.type = 'triangle';
                    osc.frequency.setValueAtTime(523.25, audioCtx.currentTime); // C5
                    osc.frequency.exponentialRampToValueAtTime(880, audioCtx.currentTime + 0.3); // A5
                    gain.gain.setValueAtTime(0.2, audioCtx.currentTime);
                    gain.gain.exponentialRampToValueAtTime(0.01, audioCtx.currentTime + 0.3);
                    osc.start();
                    osc.stop(audioCtx.currentTime + 0.3);
                } else if (type === 'wrong') {
                    osc.type = 'sawtooth';
                    osc.frequency.setValueAtTime(200, audioCtx.currentTime);
                    osc.frequency.exponentialRampToValueAtTime(120, audioCtx.currentTime + 0.25);
                    gain.gain.setValueAtTime(0.2, audioCtx.currentTime);
                    gain.gain.exponentialRampToValueAtTime(0.01, audioCtx.currentTime + 0.25);
                    osc.start();
                    osc.stop(audioCtx.currentTime + 0.25);
                } else if (type === 'click') {
                    osc.type = 'sine';
                    osc.frequency.setValueAtTime(400, audioCtx.currentTime);
                    gain.gain.setValueAtTime(0.1, audioCtx.currentTime);
                    gain.gain.exponentialRampToValueAtTime(0.01, audioCtx.currentTime + 0.08);
                    osc.start();
                    osc.stop(audioCtx.currentTime + 0.08);
                }
            } catch(e) {
                console.log("Audio play suppressed");
            }
        }

        function toggleAudio() {
            state.soundEnabled = !state.soundEnabled;
            const icon = document.getElementById('audio-icon');
            if (state.soundEnabled) {
                icon.className = 'fa-solid fa-volume-high text-lg text-slate-700';
            } else {
                icon.className = 'fa-solid fa-volume-xmark text-lg text-red-500';
            }
        }

        /* ==================== VEDIC TRICKS DATA & SHORTCUTS ==================== */
        const tricksData = [
            {
                id: 0,
                title: "Squaring Numbers Ending in 5",
                sutra: "Ekadhikena Purvena",
                shortDesc: "Easily square 15, 25, 35, 85, 95 in seconds!",
                color: "orange",
                icon: "fa-superscript",
                defaultInput: "35",
                explanation: "Take the tens digit, multiply it by (itself + 1), then tack '25' on the end!",
                calculate: (val) => {
                    let num = parseInt(val) || 25;
                    if (num % 10 !== 5) num = 25; // fallback
                    const tens = Math.floor(num / 10);
                    const nextTens = tens + 1;
                    const tensProd = tens * nextTens;
                    const finalAns = num * num;

                    return {
                        input: num,
                        steps: [
                            { label: "Step 1: Separate the Digits", detail: `Number: <span class="text-orange-600 font-extrabold">${tens}</span> | <span class="text-emerald-600 font-extrabold">5</span>` },
                            { label: "Step 2: Multiply First Digit by Next Number", detail: `${tens} × (${tens} + 1) = ${tens} × ${nextTens} = <span class="text-orange-600 font-extrabold text-xl">${tensProd}</span>` },
                            { label: "Step 3: Always write 25 at the end!", detail: `5² = <span class="text-emerald-600 font-extrabold text-xl">25</span>` },
                            { label: "Final Result!", detail: `<span class="text-orange-600 font-black text-2xl">${tensProd}</span><span class="text-emerald-600 font-black text-2xl">25</span> = <span class="text-purple-700 font-black text-3xl">${finalAns}</span>` }
                        ]
                    };
                }
            },
            {
                id: 1,
                title: "Multiply Any 2-Digit Number by 11",
                sutra: "Sandhi & Antyayordashake",
                shortDesc: "Just split the digits and place their sum in the middle!",
                color: "blue",
                icon: "fa-bolt",
                defaultInput: "45",
                explanation: "Pull the two digits apart like rubber bands and drop their sum right between them!",
                calculate: (val) => {
                    let num = parseInt(val) || 45;
                    if (num < 10 || num > 99) num = 45;
                    const d1 = Math.floor(num / 10);
                    const d2 = num % 10;
                    const sum = d1 + d2;
                    const finalAns = num * 11;

                    let step2Detail = `${d1} + ${d2} = <span class="text-purple-600 font-extrabold text-xl">${sum}</span>`;
                    if (sum >= 10) {
                        step2Detail += ` (Carry over 1 to first digit: ${d1}+1 = ${d1+1})`;
                    }

                    return {
                        input: num,
                        steps: [
                            { label: "Step 1: Split the Digits Apart", detail: `Digit 1: <span class="text-blue-600 font-extrabold">${d1}</span> , Digit 2: <span class="text-emerald-600 font-extrabold">${d2}</span>` },
                            { label: "Step 2: Add the Two Digits Together", detail: step2Detail },
                            { label: "Step 3: Put the Sum in the Middle!", detail: `${d1} _ ${d2} ➔ ${d1} [${sum}] ${d2}` },
                            { label: "Final Result!", detail: `<span class="font-black text-3xl text-indigo-700">${num} × 11 = ${finalAns}</span>` }
                        ]
                    };
                }
            },
            {
                id: 2,
                title: "Subtracting from 100, 1000, 10000",
                sutra: "Nikhilam Navatashcaramam Dashatah",
                shortDesc: "Subtract all numbers from 9, and the last number from 10!",
                color: "emerald",
                icon: "fa-minus",
                defaultInput: "346",
                explanation: "No borrowing needed! Just subtract every digit from 9, except the very last one which you subtract from 10.",
                calculate: (val) => {
                    let num = parseInt(val) || 346;
                    if (num < 1 || num > 999) num = 346;
                    const str = num.toString().padStart(3, '0');
                    const base = Math.pow(10, str.length);
                    const d1 = parseInt(str[0]);
                    const d2 = parseInt(str[1]);
                    const d3 = parseInt(str[2]);

                    const r1 = 9 - d1;
                    const r2 = 9 - d2;
                    const r3 = 10 - d3;
                    const finalAns = base - num;

                    return {
                        input: num,
                        steps: [
                            { label: "Step 1: Problem Setup", detail: `Calculate: <span class="font-black text-slate-800">${base} - ${num}</span>` },
                            { label: "Step 2: First digits from 9", detail: `9 - ${d1} = <span class="text-emerald-600 font-bold">${r1}</span> | 9 - ${d2} = <span class="text-emerald-600 font-bold">${r2}</span>` },
                            { label: "Step 3: Last digit from 10", detail: `10 - ${d3} = <span class="text-amber-600 font-bold text-xl">${r3}</span>` },
                            { label: "Final Magic Answer!", detail: `<span class="text-emerald-700 font-black text-3xl">${r1}${r2}${r3}</span>` }
                        ]
                    };
                }
            },
            {
                id: 3,
                title: "Multiply Numbers Close to 10 (e.g. 12 × 14)",
                sutra: "Anurupyena Base Trick",
                shortDesc: "Cross-add deviations and multiply surpluses!",
                color: "purple",
                icon: "fa-star",
                defaultInput: "13",
                explanation: "Find how much bigger each number is than 10. Cross-add one surplus, then multiply the surpluses!",
                calculate: (val) => {
                    let num1 = parseInt(val) || 12;
                    if (num1 < 10 || num1 > 19) num1 = 12;
                    const num2 = 14;
                    const dev1 = num1 - 10;
                    const dev2 = num2 - 10;
                    const leftPart = num1 + dev2;
                    const rightPart = dev1 * dev2;
                    const finalAns = num1 * num2;

                    return {
                        input: num1,
                        steps: [
                            { label: "Step 1: Find Deviation from 10", detail: `${num1} (+${dev1}) | ${num2} (+${dev2})` },
                            { label: "Step 2: Cross Add Number + Other Deviation", detail: `${num1} + ${dev2} = <span class="text-purple-600 font-extrabold text-xl">${leftPart}</span>` },
                            { label: "Step 3: Multiply the Deviations", detail: `${dev1} × ${dev2} = <span class="text-amber-600 font-extrabold text-xl">${rightPart}</span>` },
                            { label: "Final Result!", detail: `<span class="text-purple-700 font-black text-3xl">${leftPart}${rightPart}</span> (${num1} × ${num2} = ${finalAns})` }
                        ]
                    };
                }
            },
            {
                id: 4,
                title: "Criss-Cross Multiplication (2-Digit)",
                sutra: "Urdhva-Tiryagbhyam",
                shortDesc: "Vertically up, crosswise, and vertically down!",
                color: "rose",
                icon: "fa-xmark",
                defaultInput: "21",
                explanation: "Vertical left product | Cross multiply sum | Vertical right product!",
                calculate: (val) => {
                    let a = parseInt(val) || 21;
                    if (a < 10 || a > 99) a = 21;
                    const b = 31;
                    
                    const a1 = Math.floor(a/10), a2 = a%10;
                    const b1 = Math.floor(b/10), b2 = b%10;

                    const step1 = a1 * b1;
                    const step2 = (a1 * b2) + (a2 * b1);
                    const step3 = a2 * b2;
                    const finalAns = a * b;

                    return {
                        input: a,
                        steps: [
                            { label: "Step 1: Vertical Left Digits", detail: `${a1} × ${b1} = <span class="text-rose-600 font-bold">${step1}</span>` },
                            { label: "Step 2: Criss-Cross & Add", detail: `(${a1}×${b2}) + (${a2}×${b1}) = ${a1*b2} + ${a2*b1} = <span class="text-amber-600 font-bold text-xl">${step2}</span>` },
                            { label: "Step 3: Vertical Right Digits", detail: `${a2} × ${b2} = <span class="text-blue-600 font-bold">${step3}</span>` },
                            { label: "Final Result!", detail: `<span class="text-rose-700 font-black text-3xl">${finalAns}</span>` }
                        ]
                    };
                }
            }
        ];

        /* ==================== QUIZ QUESTIONS DATASET ==================== */
        const quizQuestions = [
            {
                trickId: 0,
                question: "What is 25 × 25?",
                sutraHint: "Squaring numbers ending in 5",
                options: ["525", "625", "650", "725"],
                correct: 1
            },
            {
                trickId: 1,
                question: "What is 53 × 11?",
                sutraHint: "Multiply by 11: 5 _ 3 (5+3=8)",
                options: ["583", "538", "853", "553"],
                correct: 0
            },
            {
                trickId: 2,
                question: "What is 1000 - 432?",
                sutraHint: "All from 9 and last from 10!",
                options: ["568", "668", "578", "567"],
                correct: 0
            },
            {
                trickId: 0,
                question: "What is 65 × 65?",
                sutraHint: "6 × 7 = 42, then attach 25!",
                options: ["4225", "3625", "4255", "4825"],
                correct: 0
            },
            {
                trickId: 3,
                question: "What is 12 × 13?",
                sutraHint: "12 + 3 = 15, and 2 × 3 = 6!",
                options: ["146", "156", "166", "153"],
                correct: 1
            }
        ];

        /* ==================== BADGES DATASET ==================== */
        const badgesData = [
            { id: 0, name: "Vedic Initiate", desc: "Selected your first trick!", icon: "🌱" },
            { id: 1, name: "Star Collector", desc: "Earned 5 total stars!", icon: "⭐" },
            { id: 2, name: "Speed Demon", desc: "Completed Quiz with Timer!", icon: "⚡" },
            { id: 3, name: "Math Magician", desc: "Scored 100% in a quiz!", icon: "🎩" },
            { id: 4, name: "Vedic Scholar", desc: "Unlocked all badges!", icon: "👑" }
        ];

        /* ==================== TAB SWITCHING & INITIALIZATION ==================== */
        function switchTab(tabName) {
            playSound('click');
            state.activeTab = tabName;

            ['tricks', 'quiz', 'story'].forEach(t => {
                const el = document.getElementById(`tab-${t}`);
                const nav = document.getElementById(`nav-${t}`);
                if (t === tabName) {
                    el.classList.remove('hidden');
                    nav.className = 'px-4 py-2 rounded-2xl font-bold text-sm md:text-base flex items-center gap-2 transition-all bg-amber-400 text-slate-900 shadow-md btn-bounce';
                } else {
                    el.classList.add('hidden');
                    nav.className = 'px-4 py-2 rounded-2xl font-bold text-sm md:text-base flex items-center gap-2 transition-all bg-white text-slate-700 hover:bg-amber-100 btn-bounce';
                }
            });

            if (tabName === 'quiz') {
                resetQuiz();
            }
        }

        /* ==================== TRICKS HUB RENDERERS ==================== */
        function renderTrickCards() {
            const grid = document.getElementById('trick-cards-grid');
            grid.innerHTML = tricksData.map((trick, index) => {
                const isSelected = state.selectedTrickId === trick.id;
                return `
                    <div onclick="selectTrick(${trick.id})" class="cursor-pointer bg-white rounded-2xl p-5 border-4 ${isSelected ? 'border-amber-400 shadow-xl scale-105' : 'border-slate-100 shadow-md hover:border-amber-200'} transition-all btn-bounce">
                        <div class="flex items-center justify-between mb-3">
                            <span class="w-10 h-10 rounded-xl bg-amber-100 flex items-center justify-center text-amber-600 text-lg">
                                <i class="fa-solid ${trick.icon}"></i>
                            </span>
                            <span class="text-xs font-black text-amber-800 bg-amber-100 px-2.5 py-1 rounded-full uppercase">Trick #${index + 1}</span>
                        </div>
                        <h4 class="font-black text-slate-800 text-base mb-1">${trick.title}</h4>
                        <p class="text-xs text-slate-500 font-medium line-clamp-2">${trick.shortDesc}</p>
                    </div>
                `;
            }).join('');
        }

        function selectTrick(id) {
            playSound('click');
            state.selectedTrickId = id;
            renderTrickCards();
            updateVisualizer();
            unlockBadge(0); // Unlock "Vedic Initiate"
        }

        function updateVisualizer() {
            const trick = tricksData[state.selectedTrickId];
            document.getElementById('current-sutra-tag').innerText = `Sutra: ${trick.sutra}`;
            document.getElementById('current-trick-title').innerText = trick.title;
            document.getElementById('current-trick-desc').innerText = trick.shortDesc;
            document.getElementById('trick-explanation-text').innerText = trick.explanation;
            
            const inputEl = document.getElementById('user-number-input');
            inputEl.value = trick.defaultInput;

            calculateCustomInput();
        }

        function calculateCustomInput() {
            const trick = tricksData[state.selectedTrickId];
            const val = document.getElementById('user-number-input').value;
            const res = trick.calculate(val);

            const stepsContainer = document.getElementById('visualizer-steps-container');
            stepsContainer.innerHTML = res.steps.map((step, idx) => `
                <div class="bg-white p-4 rounded-2xl border-2 border-slate-100 shadow-sm flex flex-col md:flex-row md:items-center justify-between gap-2 animate-pop" style="animation-delay: ${idx * 0.1}s">
                    <span class="font-extrabold text-xs text-amber-800 bg-amber-100 px-3 py-1 rounded-lg uppercase self-start md:self-auto">${step.label}</span>
                    <div class="text-base md:text-lg font-bold text-slate-700">${step.detail}</div>
                </div>
            `).join('');
        }

        /* ==================== QUIZ ZONE LOGIC ==================== */
        function toggleQuizTimer() {
            playSound('click');
            state.timerEnabled = !state.timerEnabled;
            const btn = document.getElementById('timer-toggle-btn');
            const timerDisplay = document.getElementById('quiz-timer-display');

            if (state.timerEnabled) {
                btn.className = 'bg-red-500 text-white text-xs font-bold px-3 py-1 rounded-full btn-bounce';
                btn.innerText = 'ON ⚡ (15s Challenge)';
                timerDisplay.classList.remove('hidden');
            } else {
                btn.className = 'bg-purple-200 text-purple-800 text-xs font-bold px-3 py-1 rounded-full btn-bounce';
                btn.innerText = 'OFF ☕ (Casual)';
                timerDisplay.classList.add('hidden');
            }
            resetQuiz();
        }

        function startQuizForCurrentTrick() {
            switchTab('quiz');
        }

        function resetQuiz() {
            state.quizIndex = 0;
            state.quizScore = 0;
            clearInterval(state.timerInterval);

            document.getElementById('quiz-game-screen').classList.remove('hidden');
            document.getElementById('quiz-results-screen').classList.add('hidden');
            
            renderQuizQuestion();
        }

        function renderQuizQuestion() {
            clearInterval(state.timerInterval);
            const q = quizQuestions[state.quizIndex];

            document.getElementById('quiz-question-number').innerText = state.quizIndex + 1;
            document.getElementById('quiz-current-score').innerText = state.quizScore;
            document.getElementById('quiz-sutra-hint').innerText = q.sutraHint;
            document.getElementById('quiz-question-text').innerText = q.question;
            
            // Update progress bar
            const pct = ((state.quizIndex + 1) / quizQuestions.length) * 100;
            document.getElementById('quiz-progress-bar').style.width = `${pct}%`;

            // Reset options & feedback
            const feedback = document.getElementById('quiz-feedback');
            feedback.className = 'hidden p-4 rounded-2xl font-extrabold text-lg animate-pop';
            document.getElementById('quiz-next-btn').classList.add('hidden');

            const grid = document.getElementById('quiz-options-grid');
            grid.innerHTML = q.options.map((opt, idx) => `
                <button onclick="checkAnswer(${idx})" class="quiz-opt-btn bg-white hover:bg-purple-100 text-slate-800 border-2 border-purple-200 font-black text-xl py-4 px-6 rounded-2xl shadow-sm transition-all btn-bounce">
                    ${opt}
                </button>
            `).join('');

            if (state.timerEnabled) {
                state.timeLeft = 15;
                document.getElementById('quiz-timer-display').innerText = `⏱️ ${state.timeLeft}s`;
                state.timerInterval = setInterval(() => {
                    state.timeLeft--;
                    document.getElementById('quiz-timer-display').innerText = `⏱️ ${state.timeLeft}s`;
                    if (state.timeLeft <= 0) {
                        clearInterval(state.timerInterval);
                        checkAnswer(-1); // Time out
                    }
                }, 1000);
            }
        }

        function checkAnswer(selectedIdx) {
            clearInterval(state.timerInterval);
            const q = quizQuestions[state.quizIndex];
            const options = document.querySelectorAll('.quiz-opt-btn');
            const feedback = document.getElementById('quiz-feedback');

            // Disable buttons
            options.forEach(btn => btn.setAttribute('disabled', 'true'));

            if (selectedIdx === q.correct) {
                playSound('correct');
                state.quizScore += 10;
                addStars(2);
                
                feedback.classList.remove('hidden');
                feedback.className = 'p-4 rounded-2xl font-extrabold text-lg bg-emerald-100 text-emerald-800 border-2 border-emerald-300 animate-pop';
                feedback.innerHTML = '🎉 Super Duper! That is Correct! (+2 Stars)';

                // Confetti animation
                confetti({ particleCount: 50, spread: 60, origin: { y: 0.7 } });

                if (state.timerEnabled) {
                    unlockBadge(2); // Speed demon
                }
            } else {
                playSound('wrong');
                feedback.classList.remove('hidden');
                feedback.className = 'p-4 rounded-2xl font-extrabold text-lg bg-rose-100 text-rose-800 border-2 border-rose-300 animate-pop';
                feedback.innerHTML = `Oopsie! The correct answer was <span class="underline">${q.options[q.correct]}</span>. You'll get it next time! 💪`;
            }

            document.getElementById('quiz-next-btn').classList.remove('hidden');
        }

        function nextQuizQuestion() {
            playSound('click');
            state.quizIndex++;
            if (state.quizIndex < quizQuestions.length) {
                renderQuizQuestion();
            } else {
                finishQuiz();
            }
        }

        function finishQuiz() {
            document.getElementById('quiz-game-screen').classList.add('hidden');
            document.getElementById('quiz-results-screen').classList.remove('hidden');

            const totalPossible = quizQuestions.length * 10;
            const accuracy = Math.round((state.quizScore / totalPossible) * 100);

            document.getElementById('quiz-final-stars').innerText = `+${state.quizScore / 5} ⭐`;
            document.getElementById('quiz-final-accuracy').innerText = `${accuracy}%`;

            if (accuracy === 100) {
                unlockBadge(3); // Math Magician badge
            }

            confetti({ particleCount: 100, spread: 80, origin: { y: 0.5 } });
        }

        /* ==================== BADGES & REWARDS SYSTEM ==================== */
        function addStars(count) {
            state.stars += count;
            document.getElementById('global-star-count').innerText = state.stars;

            if (state.stars >= 5) {
                unlockBadge(1); // Star Collector
            }
        }

        function unlockBadge(badgeId) {
            if (!state.unlockedBadges[badgeId]) {
                state.unlockedBadges[badgeId] = true;
                renderBadges();

                // Check if all unlocked
                if (state.unlockedBadges.every(b => b === true)) {
                    state.unlockedBadges[4] = true; // Vedic Scholar
                }
            }
        }

        function renderBadges() {
            const unlockedCount = state.unlockedBadges.filter(Boolean).length;
            document.getElementById('badges-unlocked-count').innerText = `${unlockedCount}/${badgesData.length}`;

            const container = document.getElementById('badges-container');
            container.innerHTML = badgesData.map((b, idx) => {
                const isUnlocked = state.unlockedBadges[idx];
                return `
                    <div class="badge-card p-3 rounded-2xl border-2 ${isUnlocked ? 'bg-gradient-to-b from-amber-50 to-orange-50 border-amber-300' : 'bg-slate-100 border-slate-200 grayscale opacity-60'} text-center space-y-1">
                        <div class="text-3xl">${b.icon}</div>
                        <h5 class="font-black text-xs text-slate-800">${b.name}</h5>
                        <p class="text-[10px] text-slate-500 leading-tight">${b.desc}</p>
                    </div>
                `;
            }).join('');
        }

        /* ==================== WINDOW ONLOAD ==================== */
        window.onload = function() {
            renderTrickCards();
            updateVisualizer();
            renderBadges();
        };
    </script>
</body>
</html># Python-H1-
Python repository in The repository we have A lot of project we build and work on this.
