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
Database
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Vedic Math Magic Realm 🌟 Realtime Firebase Learning Adventure</title>
    <!-- Tailwind CSS -->
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

        /* Tactile bounce and glowing keyframe animations */
        @keyframes floatSlow {
            0%, 100% { transform: translateY(0px) rotate(0deg); }
            50% { transform: translateY(-10px) rotate(2deg); }
        }

        @keyframes popIn {
            0% { transform: scale(0.85); opacity: 0; }
            100% { transform: scale(1); opacity: 1; }
        }

        .animate-float {
            animation: floatSlow 4s ease-in-out infinite;
        }

        .animate-pop {
            animation: popIn 0.25s cubic-bezier(0.175, 0.885, 0.32, 1.275) forwards;
        }

        /* Button pushable depth */
        .btn-bounce {
            transition: all 0.15s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            box-shadow: 0 5px 0 rgba(0,0,0,0.12);
        }
        .btn-bounce:hover {
            transform: translateY(-2px);
            box-shadow: 0 7px 0 rgba(0,0,0,0.12);
        }
        .btn-bounce:active {
            transform: translateY(3px);
            box-shadow: 0 2px 0 rgba(0,0,0,0.12);
        }

        /* Custom Scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            background: #FFE8AC;
            border-radius: 8px;
        }
        ::-webkit-scrollbar-thumb {
            background: #FF8A00;
            border-radius: 8px;
        }
    </style>
</head>
<body class="text-slate-800 pb-12 flex flex-col min-h-screen">

    <!-- NAVIGATION HEADER & USER HUD -->
    <header class="sticky top-0 z-50 bg-white/90 backdrop-blur-md border-b-4 border-amber-300 shadow-md">
        <div class="max-w-6xl mx-auto px-4 py-3 flex items-center justify-between flex-wrap gap-3">
            
            <!-- Logo Branding -->
            <div class="flex items-center space-x-3 cursor-pointer" onclick="switchTab('tricks')">
                <div class="w-12 h-12 bg-gradient-to-tr from-amber-400 to-orange-400 rounded-full flex items-center justify-center text-white text-2xl shadow-lg animate-float">
                    🐘
                </div>
                <div>
                    <h1 class="text-2xl md:text-3xl font-black text-orange-600 leading-none">Vedic<span class="text-amber-500">Realm!</span></h1>
                    <p class="text-xs font-semibold text-slate-500">Mental Math Magic with Firebase Cloud Savings ☁️</p>
                </div>
            </div>

            <!-- Navigation Tabs -->
            <nav class="flex items-center space-x-1.5 md:space-x-3">
                <button onclick="switchTab('tricks')" id="nav-tricks" class="px-3 md:px-4 py-2 rounded-2xl font-bold text-xs md:text-sm flex items-center gap-1.5 bg-amber-400 text-slate-900 shadow-md btn-bounce">
                    <i class="fa-solid fa-wand-magic-sparkles text-orange-700"></i> Tricks
                </button>
                <button onclick="switchTab('quiz')" id="nav-quiz" class="px-3 md:px-4 py-2 rounded-2xl font-bold text-xs md:text-sm flex items-center gap-1.5 bg-white text-slate-700 hover:bg-amber-100 btn-bounce">
                    <i class="fa-solid fa-gamepad text-purple-600"></i> Quiz Arena
                </button>
                <button onclick="switchTab('leaderboard')" id="nav-leaderboard" class="px-3 md:px-4 py-2 rounded-2xl font-bold text-xs md:text-sm flex items-center gap-1.5 bg-white text-slate-700 hover:bg-amber-100 btn-bounce">
                    <i class="fa-solid fa-trophy text-yellow-500"></i> Leaderboard
                </button>
                <button onclick="switchTab('notes')" id="nav-notes" class="px-3 md:px-4 py-2 rounded-2xl font-bold text-xs md:text-sm flex items-center gap-1.5 bg-white text-slate-700 hover:bg-amber-100 btn-bounce">
                    <i class="fa-solid fa-bookmark text-emerald-600"></i> My Notes
                </button>
            </nav>

            <!-- User Auth HUD & Star counter -->
            <div class="flex items-center gap-3">
                <!-- Stars HUD -->
                <div class="flex items-center gap-1.5 bg-amber-100 border-2 border-amber-400 px-3 py-1 rounded-full shadow-inner" title="Total Stars Saved to Firestore Database">
                    <i class="fa-solid fa-star text-amber-500 text-lg"></i>
                    <span id="user-stars-display" class="font-black text-lg text-amber-700">0</span>
                </div>

                <!-- User Profile / Auth Button -->
                <div id="auth-status-container" class="flex items-center gap-2">
                    <!-- Dynamic auth state rendered via JS -->
                </div>
            </div>
        </div>
    </header>

    <!-- MAIN APP CONTENT -->
    <main class="max-w-6xl mx-auto px-4 py-6 flex-grow w-full">

        <!-- USER WELCOME BANNER -->
        <div class="bg-gradient-to-r from-orange-400 via-amber-300 to-yellow-300 rounded-3xl p-5 md:p-6 mb-8 border-4 border-white shadow-xl flex flex-col md:flex-row items-center gap-4">
            <div class="text-6xl bg-white p-3 rounded-full shadow-md animate-bounce">
                🧙‍♂️
            </div>
            <div class="flex-grow text-center md:text-left">
                <h2 class="text-2xl md:text-3xl font-extrabold text-slate-900">
                    Welcome, <span id="banner-user-name" class="text-orange-900 underline decoration-wavy">Young Wizard</span>! ✨
                </h2>
                <p id="banner-auth-info" class="text-slate-800 text-sm font-medium mt-1">
                    Your progress, stars, and saved notes are synchronized to the Cloud Firestore database!
                </p>
            </div>
            <div class="flex items-center gap-3 bg-white/80 backdrop-blur-sm p-3 rounded-2xl border border-white text-center shadow-inner">
                <div>
                    <span id="user-level-badge" class="text-xl font-black text-purple-700 block">Level 1</span>
                    <span class="text-[10px] font-extrabold text-slate-500 uppercase tracking-wider">Math Rank</span>
                </div>
            </div>
        </div>

        <!-- ================= TAB 1: TRICKS & LIVE SOLVER ================= -->
        <section id="tab-tricks" class="space-y-8">
            <!-- TRICKS GRID -->
            <div>
                <h3 class="text-2xl font-black text-slate-800 mb-4 flex items-center gap-2">
                    <i class="fa-solid fa-lightbulb text-amber-500"></i> Select a Vedic Shortcut:
                </h3>
                <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4" id="tricks-selector-grid">
                    <!-- Cards rendered via JS -->
                </div>
            </div>

            <!-- INTERACTIVE SOLVER / VISUALIZER -->
            <div class="bg-white rounded-3xl border-4 border-amber-300 shadow-2xl p-6 md:p-8 animate-pop">
                <div class="flex flex-col md:flex-row md:items-center justify-between gap-4 border-b-2 border-dashed border-amber-200 pb-4 mb-6">
                    <div>
                        <span id="active-sutra-name" class="bg-amber-100 text-amber-800 font-black text-xs px-3 py-1 rounded-full uppercase tracking-wider">
                            Sutra: Ekadhikena Purvena
                        </span>
                        <h3 id="active-trick-title" class="text-2xl md:text-3xl font-black text-orange-600 mt-1">
                            Multiply Any 2-Digit Number by 11
                        </h3>
                        <p id="active-trick-desc" class="text-slate-600 font-medium text-sm">
                            Pull the digits apart and place their sum right in the middle!
                        </p>
                    </div>

                    <!-- Custom Number Input Sandbox -->
                    <div class="bg-amber-50 p-3 rounded-2xl border-2 border-amber-300 flex items-center gap-2">
                        <label for="custom-math-input" class="text-xs font-black text-amber-900 uppercase">Test Number:</label>
                        <input type="text" id="custom-math-input" class="w-24 text-center font-black text-xl py-1.5 px-2 rounded-xl border-2 border-amber-400 text-slate-800 focus:outline-none focus:ring-2 focus:ring-amber-500" value="45">
                        <button onclick="calculateCustomInput()" class="bg-amber-500 hover:bg-amber-600 text-white font-bold px-3 py-2 rounded-xl btn-bounce text-xs">
                            Solve! ✨
                        </button>
                    </div>
                </div>

                <!-- Visual Step-by-Step Output -->
                <div class="grid grid-cols-1 lg:grid-cols-12 gap-6 items-center">
                    <div class="lg:col-span-8 bg-slate-50 rounded-2xl p-6 border-2 border-slate-200 min-h-[300px] flex flex-col justify-between space-y-4" id="visualizer-steps-box">
                        <!-- Dynamic step cards load here -->
                    </div>

                    <!-- Save Note & Practice Actions -->
                    <div class="lg:col-span-4 bg-gradient-to-b from-amber-50 to-orange-100 rounded-2xl p-5 border-2 border-amber-300 flex flex-col justify-between h-full space-y-4 text-center">
                        <div class="text-5xl animate-bounce">
                            💡
                        </div>
                        <div>
                            <h4 class="font-extrabold text-amber-900 text-base mb-1">Save to Cloud Notes?</h4>
                            <p class="text-xs text-slate-600">Bookmark this technique into your Cloud Firestore database notebook to read later!</p>
                        </div>
                        <button onclick="saveCurrentTrickAsNote()" class="w-full bg-emerald-500 hover:bg-emerald-600 text-white font-black py-3 px-4 rounded-xl shadow-md btn-bounce text-xs flex items-center justify-center gap-2">
                            <i class="fa-solid fa-cloud-arrow-up"></i> Save Note to Database
                        </button>
                    </div>
                </div>
            </div>
        </section>

        <!-- ================= TAB 2: QUIZ ARENA ================= -->
        <section id="tab-quiz" class="hidden space-y-6">
            <div class="bg-white rounded-3xl border-4 border-purple-300 shadow-2xl p-6 md:p-8">
                <div class="flex flex-col md:flex-row items-center justify-between gap-4 border-b-2 border-purple-100 pb-4 mb-6">
                    <div>
                        <h2 class="text-2xl md:text-3xl font-black text-purple-700 flex items-center gap-2">
                            <i class="fa-solid fa-gamepad text-amber-400"></i> Vedic Speed Arena
                        </h2>
                        <p class="text-slate-600 text-xs md:text-sm">Answer correctly to earn +10 stars saved automatically to your profile!</p>
                    </div>

                    <div class="flex items-center gap-3 bg-purple-50 p-2.5 rounded-2xl border border-purple-200">
                        <span class="text-xs font-bold text-slate-700">Timer Mode:</span>
                        <button id="timer-toggle-btn" onclick="toggleQuizTimer()" class="bg-purple-200 text-purple-800 text-xs font-bold px-3 py-1 rounded-full btn-bounce">
                            OFF ☕ (Relaxed)
                        </button>
                    </div>
                </div>

                <!-- Quiz Main Play Container -->
                <div id="quiz-main-view" class="max-w-2xl mx-auto text-center space-y-6 py-2">
                    <div class="flex items-center justify-between text-xs md:text-sm font-bold text-slate-600">
                        <span>Question <span id="quiz-q-num" class="text-purple-700 text-base font-black">1</span> / 5</span>
                        <span id="quiz-timer-counter" class="hidden text-red-500 font-black text-base">⏱️ 15s</span>
                        <span class="text-amber-600 font-extrabold">Score: <span id="quiz-score-val" class="text-lg">0</span></span>
                    </div>

                    <div class="w-full bg-slate-200 h-3 rounded-full overflow-hidden">
                        <div id="quiz-progress-fill" class="bg-purple-500 h-full w-1/5 transition-all duration-300"></div>
                    </div>

                    <div class="bg-gradient-to-b from-purple-50 to-indigo-50 border-4 border-purple-200 rounded-3xl p-6 md:p-8 shadow-inner">
                        <span id="quiz-hint-tag" class="bg-purple-200 text-purple-900 text-xs font-black px-3 py-1 rounded-full uppercase">
                            Trick: Multiply by 11
                        </span>
                        <h3 id="quiz-q-text" class="text-3xl md:text-5xl font-black text-slate-800 my-6">
                            45 × 11 = ?
                        </h3>

                        <div id="quiz-answers-grid" class="grid grid-cols-1 sm:grid-cols-2 gap-4 mt-4">
                            <!-- Answer option buttons -->
                        </div>
                    </div>

                    <div id="quiz-feedback-box" class="hidden p-4 rounded-2xl font-extrabold text-base animate-pop"></div>

                    <button id="quiz-next-btn" onclick="nextQuizQuestion()" class="hidden w-full bg-amber-500 hover:bg-amber-600 text-white font-black text-lg py-3.5 rounded-2xl shadow-lg btn-bounce">
                        Next Question 🚀
                    </button>
                </div>

                <!-- Quiz Results Overlay -->
                <div id="quiz-results-view" class="hidden text-center py-6 space-y-6 animate-pop">
                    <div class="text-6xl">🏆</div>
                    <h3 class="text-3xl font-black text-purple-800">Quiz Completed!</h3>
                    <p class="text-slate-600 text-sm">Your score and earned stars have been persisted to the Cloud Firestore database!</p>

                    <div class="flex justify-center items-center gap-4 my-2">
                        <div class="bg-amber-100 p-4 rounded-2xl border-2 border-amber-300 min-w-[120px]">
                            <span class="text-[10px] text-amber-800 uppercase font-black block">Stars Earned</span>
                            <span id="res-stars-val" class="text-2xl font-black text-amber-600">+0 ⭐</span>
                        </div>
                        <div class="bg-purple-100 p-4 rounded-2xl border-2 border-purple-300 min-w-[120px]">
                            <span class="text-[10px] text-purple-800 uppercase font-black block">Accuracy</span>
                            <span id="res-accuracy-val" class="text-2xl font-black text-purple-600">0%</span>
                        </div>
                    </div>

                    <button onclick="resetQuiz()" class="bg-purple-600 hover:bg-purple-700 text-white font-black text-base px-8 py-3.5 rounded-2xl shadow-lg btn-bounce">
                        Play Again! 🔄
                    </button>
                </div>
            </div>
        </section>

        <!-- ================= TAB 3: LEADERBOARD ================= -->
        <section id="tab-leaderboard" class="hidden space-y-6">
            <div class="bg-white rounded-3xl border-4 border-yellow-300 shadow-2xl p-6 md:p-8">
                <div class="flex items-center justify-between border-b-2 border-yellow-100 pb-4 mb-6">
                    <div>
                        <h2 class="text-2xl md:text-3xl font-black text-amber-600 flex items-center gap-2">
                            <i class="fa-solid fa-trophy text-yellow-500"></i> Top Math Magicians (Realtime Leaderboard)
                        </h2>
                        <p class="text-slate-600 text-xs md:text-sm">Live scores retrieved from Cloud Firestore Database!</p>
                    </div>
                </div>

                <!-- Leaderboard Table Container -->
                <div class="overflow-x-auto">
                    <table class="w-full text-left border-collapse">
                        <thead>
                            <tr class="bg-amber-100 text-amber-900 text-xs font-black uppercase border-b-2 border-amber-200">
                                <th class="p-3 rounded-l-xl">Rank</th>
                                <th class="p-3">Wizard Name</th>
                                <th class="p-3">Total Stars</th>
                                <th class="p-3 rounded-r-xl">Quiz High Score</th>
                            </tr>
                        </thead>
                        <tbody id="leaderboard-tbody" class="text-sm font-bold divide-y divide-slate-100">
                            <!-- Realtime Firestore leaderboard rows load here -->
                        </tbody>
                    </table>
                </div>
            </div>
        </section>

        <!-- ================= TAB 4: FIRESTORE SAVED NOTES ================= -->
        <section id="tab-notes" class="hidden space-y-6">
            <div class="bg-white rounded-3xl border-4 border-emerald-300 shadow-2xl p-6 md:p-8">
                <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-4 border-b-2 border-emerald-100 pb-4 mb-6">
                    <div>
                        <h2 class="text-2xl md:text-3xl font-black text-emerald-700 flex items-center gap-2">
                            <i class="fa-solid fa-book-bookmark text-emerald-500"></i> My Cloud Notes Notebook
                        </h2>
                        <p class="text-slate-600 text-xs md:text-sm">Tricks & custom notes stored safely in `/artifacts/{appId}/users/{userId}/notes`</p>
                    </div>

                    <!-- Manual Note Creator Modal trigger -->
                    <button onclick="openCustomNoteModal()" class="bg-emerald-500 hover:bg-emerald-600 text-white font-black text-xs px-4 py-2.5 rounded-xl btn-bounce flex items-center gap-1.5 self-start sm:self-auto">
                        <i class="fa-solid fa-plus"></i> Write Custom Note
                    </button>
                </div>

                <!-- Notes Cards Grid -->
                <div id="notes-grid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
                    <!-- Dynamic notes load here -->
                </div>
            </div>
        </section>

    </main>

    <!-- CUSTOM NOTE MODAL -->
    <div id="note-modal" class="hidden fixed inset-0 z-50 bg-black/50 backdrop-blur-sm flex items-center justify-center p-4">
        <div class="bg-white rounded-3xl border-4 border-emerald-400 p-6 max-w-md w-full space-y-4 shadow-2xl animate-pop">
            <div class="flex items-center justify-between">
                <h3 class="text-xl font-black text-emerald-800">New Vedic Math Note 📝</h3>
                <button onclick="closeCustomNoteModal()" class="text-slate-400 hover:text-slate-600 font-bold text-xl">&times;</button>
            </div>
            <div>
                <label class="text-xs font-bold text-slate-600 uppercase block mb-1">Title / Technique:</label>
                <input type="text" id="modal-note-title" class="w-full p-2.5 border-2 border-slate-200 rounded-xl font-bold focus:outline-none focus:border-emerald-500 text-sm" placeholder="e.g. My Favorite 11s Trick">
            </div>
            <div>
                <label class="text-xs font-bold text-slate-600 uppercase block mb-1">Note Details / Example:</label>
                <textarea id="modal-note-body" rows="3" class="w-full p-2.5 border-2 border-slate-200 rounded-xl font-bold focus:outline-none focus:border-emerald-500 text-sm" placeholder="Write down your steps or observations..."></textarea>
            </div>
            <div class="flex justify-end gap-2 pt-2">
                <button onclick="closeCustomNoteModal()" class="px-4 py-2 rounded-xl text-xs font-bold text-slate-600 hover:bg-slate-100">Cancel</button>
                <button onclick="submitCustomNote()" class="px-5 py-2 rounded-xl text-xs font-black bg-emerald-500 hover:bg-emerald-600 text-white btn-bounce">Save Note</button>
            </div>
        </div>
    </div>

    <!-- FIREBASE MODULE SCRIPTS & APPLICATION LOGIC -->
    <script type="module">
        import { initializeApp } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-app.js";
        import { 
            getAuth, 
            signInAnonymously, 
            signInWithCustomToken, 
            onAuthStateChanged,
            GoogleAuthProvider,
            signInWithPopup,
            signOut
        } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-auth.js";
        import { 
            getFirestore, 
            doc, 
            getDoc, 
            setDoc, 
            updateDoc, 
            collection, 
            onSnapshot, 
            addDoc, 
            deleteDoc,
            query
        } from "https://www.gstatic.com/firebasejs/11.6.1/firebase-firestore.js";

        // Global Firebase Environment Config
        const appId = typeof __app_id !== 'undefined' ? __app_id : 'vedic-math-app';
        const firebaseConfig = typeof __firebase_config !== 'undefined' ? JSON.parse(__firebase_config) : {
            apiKey: "dummy-key",
            authDomain: "dummy.firebaseapp.com",
            projectId: "dummy-project"
        };

        const app = initializeApp(firebaseConfig);
        const auth = getAuth(app);
        const db = getFirestore(app);

        // Application Global State
        window.appState = {
            currentUser: null,
            userProfile: {
                displayName: "Guest Explorer",
                stars: 0,
                highScore: 0,
                avatar: "🐘"
            },
            selectedTrickId: 0,
            activeTab: 'tricks',
            quizIndex: 0,
            quizScore: 0,
            timerEnabled: false,
            timeLeft: 15,
            timerInterval: null,
            savedNotes: [],
            leaderboardData: []
        };

        /* ================= MANDATORY RULE 1, 2, 3: AUTHENTICATION ================= */
        async function initAuth() {
            try {
                if (typeof __initial_auth_token !== 'undefined' && __initial_auth_token) {
                    await signInWithCustomToken(auth, __initial_auth_token);
                } else {
                    await signInAnonymously(auth);
                }
            } catch (err) {
                console.warn("Auth initial attempt fallback:", err);
                try {
                    await signInAnonymously(auth);
                } catch(e) {
                    console.error("Anonymous auth failed", e);
                }
            }
        }

        onAuthStateChanged(auth, async (user) => {
            window.appState.currentUser = user;
            renderAuthHUD(user);

            if (user) {
                // Initialize/Listen to User Document
                setupUserFirestoreListeners(user.uid);
                // Listen to Global Leaderboard
                setupLeaderboardListener();
                // Listen to Saved Notes
                setupNotesListener(user.uid);
            }
        });

        function renderAuthHUD(user) {
            const container = document.getElementById('auth-status-container');
            const nameBanner = document.getElementById('banner-user-name');

            if (user) {
                const name = user.displayName || (user.isAnonymous ? `Guest Wizard (${user.uid.substring(0, 4)})` : "Math Wizard");
                nameBanner.innerText = name;

                container.innerHTML = `
                    <div class="flex items-center gap-2">
                        <span class="text-xs font-black text-slate-700 bg-slate-100 px-2.5 py-1 rounded-full border border-slate-300 hidden sm:inline">
                            ${user.isAnonymous ? '👤 Guest' : '⭐ Google User'}
                        </span>
                        <button onclick="handleGoogleSignIn()" class="bg-blue-500 hover:bg-blue-600 text-white font-black text-xs px-3 py-1.5 rounded-xl btn-bounce ${user.isAnonymous ? '' : 'hidden'}">
                            Google Login
                        </button>
                    </div>
                `;
            }
        }

        window.handleGoogleSignIn = async function() {
            try {
                const provider = new GoogleAuthProvider();
                await signInWithPopup(auth, provider);
            } catch (e) {
                console.error("Google sign in error", e);
            }
        };

        /* ================= FIRESTORE DATABASE LISTENERS ================= */
        // RULE 1: Private Path: /artifacts/{appId}/users/{userId}/profile/data
        // RULE 1: Public Leaderboard Path: /artifacts/{appId}/public/data/leaderboard
        function setupUserFirestoreListeners(userId) {
            if (!userId) return;

            const userDocRef = doc(db, 'artifacts', appId, 'users', userId, 'profile', 'user_data');

            // RULE 2: Simple snapshot, no complex index queries
            onSnapshot(userDocRef, (snap) => {
                if (snap.exists()) {
                    const data = snap.data();
                    window.appState.userProfile = data;
                    document.getElementById('user-stars-display').innerText = data.stars || 0;
                    
                    // Level calculation
                    const lvl = Math.floor((data.stars || 0) / 30) + 1;
                    document.getElementById('user-level-badge').innerText = `Level ${lvl}`;
                } else {
                    // Create default user profile in Firestore
                    const defaultProfile = {
                        displayName: auth.currentUser?.displayName || "Young Wizard",
                        stars: 0,
                        highScore: 0,
                        uid: userId
                    };
                    setDoc(userDocRef, defaultProfile);
                }
            }, (error) => {
                console.error("User profile snapshot error:", error);
            });
        }

        function setupLeaderboardListener() {
            // RULE 1: /artifacts/{appId}/public/data/leaderboard
            const lbCol = collection(db, 'artifacts', appId, 'public', 'data', 'leaderboard');

            onSnapshot(lbCol, (snapshot) => {
                const list = [];
                snapshot.forEach(docSnap => {
                    list.push({ id: docSnap.id, ...docSnap.data() });
                });

                // Sort in memory (Rule 2)
                list.sort((a, b) => (b.stars || 0) - (a.stars || 0));
                window.appState.leaderboardData = list;
                renderLeaderboard();
            }, (err) => {
                console.error("Leaderboard error:", err);
            });
        }

        function setupNotesListener(userId) {
            // RULE 1: /artifacts/{appId}/users/{userId}/notes
            const notesCol = collection(db, 'artifacts', appId, 'users', userId, 'notes');

            onSnapshot(notesCol, (snapshot) => {
                const notes = [];
                snapshot.forEach(docSnap => {
                    notes.push({ id: docSnap.id, ...docSnap.data() });
                });
                window.appState.savedNotes = notes;
                renderSavedNotes();
            }, (err) => {
                console.error("Notes snapshot error:", err);
            });
        }

        /* ================= VEDIC MATH TRICKS ENGINE & SOLVER ================= */
        const tricksDatabase = [
            {
                id: 0,
                title: "Multiply Any 2-Digit Number by 11",
                sutra: "Sandhi & Antyayordashake",
                desc: "Split the two digits and put their sum right in the center!",
                defaultVal: "45",
                icon: "fa-bolt",
                calc: (val) => {
                    let num = parseInt(val) || 45;
                    if (num < 10 || num > 99) num = 45;
                    const d1 = Math.floor(num / 10);
                    const d2 = num % 10;
                    const sum = d1 + d2;
                    const finalAns = num * 11;

                    return [
                        { step: "Step 1: Pull Digits Apart", detail: `Digit 1 = <span class="text-orange-600 font-extrabold text-lg">${d1}</span> , Digit 2 = <span class="text-emerald-600 font-extrabold text-lg">${d2}</span>` },
                        { step: "Step 2: Add Digits Together", detail: `${d1} + ${d2} = <span class="text-purple-600 font-black text-xl">${sum}</span>` },
                        { step: "Step 3: Drop Sum in Middle!", detail: `${d1} _ ${d2} ➔ ${d1} [<span class="text-purple-600">${sum}</span>] ${d2}` },
                        { step: "Final Result!", detail: `<span class="text-purple-700 font-black text-3xl">${num} × 11 = ${finalAns}</span>` }
                    ];
                }
            },
            {
                id: 1,
                title: "Squaring Numbers Ending in 5",
                sutra: "Ekadhikena Purvena",
                desc: "Multiply tens digit by (tens + 1), then write 25 at the end!",
                defaultVal: "35",
                icon: "fa-superscript",
                calc: (val) => {
                    let num = parseInt(val) || 35;
                    if (num % 10 !== 5) num = 35;
                    const tens = Math.floor(num / 10);
                    const next = tens + 1;
                    const prod = tens * next;
                    const finalAns = num * num;

                    return [
                        { step: "Step 1: Identify Tens Digit", detail: `First digit: <span class="text-orange-600 font-black text-xl">${tens}</span>` },
                        { step: "Step 2: Multiply by Next Integer", detail: `${tens} × (${tens} + 1) = ${tens} × ${next} = <span class="text-orange-600 font-black text-2xl">${prod}</span>` },
                        { step: "Step 3: Append 25 at the End!", detail: `5² = <span class="text-emerald-600 font-black text-2xl">25</span>` },
                        { step: "Final Magic Result!", detail: `<span class="text-orange-600 font-black text-3xl">${prod}</span><span class="text-emerald-600 font-black text-3xl">25</span> = <span class="text-purple-700 font-black text-3xl">${finalAns}</span>` }
                    ];
                }
            },
            {
                id: 2,
                title: "Nikhilam Subtraction (Base 100/1000)",
                sutra: "Nikhilam Navatashcaramam Dashatah",
                desc: "Subtract all digits from 9, and the last digit from 10!",
                defaultVal: "346",
                icon: "fa-minus",
                calc: (val) => {
                    let num = parseInt(val) || 346;
                    if (num < 1 || num > 999) num = 346;
                    const str = num.toString().padStart(3, '0');
                    const d1 = parseInt(str[0]), d2 = parseInt(str[1]), d3 = parseInt(str[2]);
                    const r1 = 9 - d1, r2 = 9 - d2, r3 = 10 - d3;
                    const finalAns = 1000 - num;

                    return [
                        { step: "Step 1: Problem Target", detail: `<span class="font-extrabold text-slate-800">1000 - ${num}</span>` },
                        { step: "Step 2: Subtract first two digits from 9", detail: `9 - ${d1} = <span class="text-emerald-600 font-black">${r1}</span> | 9 - ${d2} = <span class="text-emerald-600 font-black">${r2}</span>` },
                        { step: "Step 3: Subtract final digit from 10", detail: `10 - ${d3} = <span class="text-amber-600 font-black text-xl">${r3}</span>` },
                        { step: "Final Result!", detail: `<span class="text-emerald-700 font-black text-3xl">${r1}${r2}${r3}</span>` }
                    ];
                }
            },
            {
                id: 3,
                title: "Multiply Numbers Close to Base 100",
                sutra: "Anurupyena Base Method",
                desc: "Cross-subtract deficits and multiply surplus/deficits!",
                defaultVal: "96",
                icon: "fa-star",
                calc: (val) => {
                    let n1 = parseInt(val) || 96;
                    let n2 = 94;
                    const d1 = 100 - n1;
                    const d2 = 100 - n2;
                    const left = n1 - d2;
                    const right = d1 * d2;
                    const rightStr = right.toString().padStart(2, '0');
                    const finalAns = n1 * n2;

                    return [
                        { step: "Step 1: Deficits from 100", detail: `${n1} (-${d1}) | ${n2} (-${d2})` },
                        { step: "Step 2: Cross Subtract Deficits", detail: `${n1} - ${d2} = <span class="text-purple-600 font-black text-2xl">${left}</span>` },
                        { step: "Step 3: Multiply Deficits Together", detail: `${d1} × ${d2} = <span class="text-amber-600 font-black text-2xl">${rightStr}</span>` },
                        { step: "Final Result!", detail: `<span class="text-purple-700 font-black text-3xl">${left}${rightStr}</span> (${n1} × ${n2} = ${finalAns})` }
                    ];
                }
            }
        ];

        /* ================= QUIZ QUESTIONS DATASET ================= */
        const quizQuestions = [
            { q: "What is 35 × 11?", hint: "Split 3 and 5, put (3+5=8) in middle!", opts: ["385", "358", "388", "835"], correct: 0 },
            { q: "What is 45 × 45?", hint: "4 × 5 = 20, attach 25!", opts: ["2025", "1625", "2055", "2525"], correct: 0 },
            { q: "What is 1000 - 245?", hint: "All from 9, last from 10!", opts: ["755", "855", "745", "655"], correct: 0 },
            { q: "What is 75 × 75?", hint: "7 × 8 = 56, attach 25!", opts: ["5625", "4925", "5655", "6425"], correct: 0 },
            { q: "What is 82 × 11?", hint: "8 _ 2 with (8+2=10 carry 1)", opts: ["902", "802", "812", "920"], correct: 0 }
        ];

        /* ================= UI RENDER FUNCTIONS ================= */
        window.switchTab = function(tabName) {
            window.appState.activeTab = tabName;
            ['tricks', 'quiz', 'leaderboard', 'notes'].forEach(t => {
                const el = document.getElementById(`tab-${t}`);
                const nav = document.getElementById(`nav-${t}`);
                if (t === tabName) {
                    el.classList.remove('hidden');
                    nav.className = 'px-3 md:px-4 py-2 rounded-2xl font-bold text-xs md:text-sm flex items-center gap-1.5 bg-amber-400 text-slate-900 shadow-md btn-bounce';
                } else {
                    el.classList.add('hidden');
                    nav.className = 'px-3 md:px-4 py-2 rounded-2xl font-bold text-xs md:text-sm flex items-center gap-1.5 bg-white text-slate-700 hover:bg-amber-100 btn-bounce';
                }
            });

            if (tabName === 'quiz') resetQuiz();
        };

        function renderTricksGrid() {
            const grid = document.getElementById('tricks-selector-grid');
            grid.innerHTML = tricksDatabase.map((t) => {
                const isSelected = window.appState.selectedTrickId === t.id;
                return `
                    <div onclick="selectTrick(${t.id})" class="cursor-pointer bg-white rounded-2xl p-4 border-4 ${isSelected ? 'border-amber-400 shadow-xl scale-105' : 'border-slate-100 shadow-sm hover:border-amber-200'} transition-all btn-bounce">
                        <div class="flex items-center justify-between mb-2">
                            <span class="w-9 h-9 rounded-xl bg-amber-100 flex items-center justify-center text-amber-600 text-base">
                                <i class="fa-solid ${t.icon}"></i>
                            </span>
                            <span class="text-[10px] font-black text-amber-800 bg-amber-100 px-2 py-0.5 rounded-full uppercase">Trick #${t.id + 1}</span>
                        </div>
                        <h4 class="font-black text-slate-800 text-sm mb-1">${t.title}</h4>
                        <p class="text-xs text-slate-500 font-medium line-clamp-2">${t.desc}</p>
                    </div>
                `;
            }).join('');
        }

        window.selectTrick = function(id) {
            window.appState.selectedTrickId = id;
            renderTricksGrid();
            updateSolverView();
        };

        function updateSolverView() {
            const trick = tricksDatabase[window.appState.selectedTrickId];
            document.getElementById('active-sutra-name').innerText = `Sutra: ${trick.sutra}`;
            document.getElementById('active-trick-title').innerText = trick.title;
            document.getElementById('active-trick-desc').innerText = trick.desc;
            document.getElementById('custom-math-input').value = trick.defaultVal;

            calculateCustomInput();
        }

        window.calculateCustomInput = function() {
            const trick = tricksDatabase[window.appState.selectedTrickId];
            const val = document.getElementById('custom-math-input').value;
            const steps = trick.calc(val);

            const stepsBox = document.getElementById('visualizer-steps-box');
            stepsBox.innerHTML = steps.map((s, idx) => `
                <div class="bg-white p-3.5 rounded-2xl border-2 border-slate-100 shadow-sm flex flex-col md:flex-row md:items-center justify-between gap-2 animate-pop" style="animation-delay: ${idx * 0.08}s">
                    <span class="font-extrabold text-xs text-amber-800 bg-amber-100 px-2.5 py-1 rounded-lg uppercase self-start md:self-auto">${s.step}</span>
                    <div class="text-sm md:text-base font-bold text-slate-700">${s.detail}</div>
                </div>
            `).join('');
        };

        /* ================= FIRESTORE WRITE OPERATIONS ================= */
        window.saveCurrentTrickAsNote = async function() {
            const user = window.appState.currentUser;
            if (!user) return;

            const trick = tricksDatabase[window.appState.selectedTrickId];
            const currentVal = document.getElementById('custom-math-input').value;

            try {
                // RULE 1: /artifacts/{appId}/users/{userId}/notes
                const notesCol = collection(db, 'artifacts', appId, 'users', user.uid, 'notes');
                await addDoc(notesCol, {
                    title: trick.title,
                    sutra: trick.sutra,
                    example: `Solved with input: ${currentVal}`,
                    createdAt: new Date().toISOString()
                });

                alert("✨ Note saved successfully to your Cloud Firestore database!");
            } catch (err) {
                console.error("Error saving note:", err);
            }
        };

        window.openCustomNoteModal = function() {
            document.getElementById('note-modal').classList.remove('hidden');
        };

        window.closeCustomNoteModal = function() {
            document.getElementById('note-modal').classList.add('hidden');
        };

        window.submitCustomNote = async function() {
            const user = window.appState.currentUser;
            if (!user) return;

            const title = document.getElementById('modal-note-title').value;
            const body = document.getElementById('modal-note-body').value;

            if (!title) return;

            try {
                const notesCol = collection(db, 'artifacts', appId, 'users', user.uid, 'notes');
                await addDoc(notesCol, {
                    title: title,
                    sutra: "Custom Technique",
                    example: body,
                    createdAt: new Date().toISOString()
                });

                closeCustomNoteModal();
                document.getElementById('modal-note-title').value = '';
                document.getElementById('modal-note-body').value = '';
            } catch (err) {
                console.error("Custom note error:", err);
            }
        };

        window.deleteNote = async function(noteId) {
            const user = window.appState.currentUser;
            if (!user) return;

            try {
                const noteRef = doc(db, 'artifacts', appId, 'users', user.uid, 'notes', noteId);
                await deleteDoc(noteRef);
            } catch (err) {
                console.error("Delete note error:", err);
            }
        };

        function renderSavedNotes() {
            const container = document.getElementById('notes-grid');
            const notes = window.appState.savedNotes;

            if (notes.length === 0) {
                container.innerHTML = `
                    <div class="col-span-full text-center py-8 text-slate-400">
                        <i class="fa-solid fa-note-sticky text-4xl mb-2"></i>
                        <p class="font-bold text-sm">No notes saved yet. Click "Save Note to Database" from any trick!</p>
                    </div>
                `;
                return;
            }

            container.innerHTML = notes.map((n) => `
                <div class="bg-emerald-50 rounded-2xl p-4 border-2 border-emerald-200 flex flex-col justify-between space-y-3 relative shadow-sm">
                    <button onclick="deleteNote('${n.id}')" class="absolute top-3 right-3 text-slate-400 hover:text-rose-600 font-bold text-sm">
                        <i class="fa-solid fa-trash"></i>
                    </button>
                    <div>
                        <span class="bg-emerald-200 text-emerald-900 font-black text-[10px] px-2.5 py-0.5 rounded-full uppercase">${n.sutra || 'Vedic Note'}</span>
                        <h4 class="font-black text-slate-800 text-base mt-1">${n.title}</h4>
                        <p class="text-xs text-slate-600 font-medium mt-2">${n.example || ''}</p>
                    </div>
                    <div class="text-[10px] text-slate-400 font-extrabold pt-2 border-t border-emerald-200">
                        Saved in Firestore
                    </div>
                </div>
            `).join('');
        }

        /* ================= QUIZ & LEADERBOARD LOGIC ================= */
        window.toggleQuizTimer = function() {
            window.appState.timerEnabled = !window.appState.timerEnabled;
            const btn = document.getElementById('timer-toggle-btn');
            const counter = document.getElementById('quiz-timer-counter');

            if (window.appState.timerEnabled) {
                btn.className = 'bg-red-500 text-white text-xs font-bold px-3 py-1 rounded-full btn-bounce';
                btn.innerText = 'ON ⚡ (15s Speed)';
                counter.classList.remove('hidden');
            } else {
                btn.className = 'bg-purple-200 text-purple-800 text-xs font-bold px-3 py-1 rounded-full btn-bounce';
                btn.innerText = 'OFF ☕ (Relaxed)';
                counter.classList.add('hidden');
            }
            resetQuiz();
        };

        window.resetQuiz = function() {
            window.appState.quizIndex = 0;
            window.appState.quizScore = 0;
            clearInterval(window.appState.timerInterval);

            document.getElementById('quiz-main-view').classList.remove('hidden');
            document.getElementById('quiz-results-view').classList.add('hidden');

            renderQuizQuestion();
        };

        function renderQuizQuestion() {
            clearInterval(window.appState.timerInterval);
            const q = quizQuestions[window.appState.quizIndex];

            document.getElementById('quiz-q-num').innerText = window.appState.quizIndex + 1;
            document.getElementById('quiz-score-val').innerText = window.appState.quizScore;
            document.getElementById('quiz-hint-tag').innerText = q.hint;
            document.getElementById('quiz-q-text').innerText = q.q;

            const pct = ((window.appState.quizIndex + 1) / quizQuestions.length) * 100;
            document.getElementById('quiz-progress-fill').style.width = `${pct}%`;

            document.getElementById('quiz-feedback-box').classList.add('hidden');
            document.getElementById('quiz-next-btn').classList.add('hidden');

            const grid = document.getElementById('quiz-answers-grid');
            grid.innerHTML = q.opts.map((opt, idx) => `
                <button onclick="checkAnswer(${idx})" class="quiz-ans-btn bg-white hover:bg-purple-100 text-slate-800 border-2 border-purple-200 font-black text-lg py-3.5 px-4 rounded-2xl shadow-sm btn-bounce">
                    ${opt}
                </button>
            `).join('');

            if (window.appState.timerEnabled) {
                window.appState.timeLeft = 15;
                document.getElementById('quiz-timer-counter').innerText = `⏱️ ${window.appState.timeLeft}s`;
                window.appState.timerInterval = setInterval(() => {
                    window.appState.timeLeft--;
                    document.getElementById('quiz-timer-counter').innerText = `⏱️ ${window.appState.timeLeft}s`;
                    if (window.appState.timeLeft <= 0) {
                        clearInterval(window.appState.timerInterval);
                        checkAnswer(-1);
                    }
                }, 1000);
            }
        }

        window.checkAnswer = function(selectedIdx) {
            clearInterval(window.appState.timerInterval);
            const q = quizQuestions[window.appState.quizIndex];
            const btns = document.querySelectorAll('.quiz-ans-btn');
            const feedback = document.getElementById('quiz-feedback-box');

            btns.forEach(b => b.setAttribute('disabled', 'true'));

            if (selectedIdx === q.correct) {
                window.appState.quizScore += 10;
                feedback.classList.remove('hidden');
                feedback.className = 'p-3.5 rounded-2xl font-extrabold text-sm bg-emerald-100 text-emerald-800 border-2 border-emerald-300 animate-pop';
                feedback.innerHTML = '🎉 Excellent Job! That is Correct! (+10 Stars)';
                confetti({ particleCount: 40, spread: 50, origin: { y: 0.7 } });
            } else {
                feedback.classList.remove('hidden');
                feedback.className = 'p-3.5 rounded-2xl font-extrabold text-sm bg-rose-100 text-rose-800 border-2 border-rose-300 animate-pop';
                feedback.innerHTML = `Incorrect! The correct answer was <b>${q.opts[q.correct]}</b>.`;
            }

            document.getElementById('quiz-next-btn').classList.remove('hidden');
        };

        window.nextQuizQuestion = function() {
            window.appState.quizIndex++;
            if (window.appState.quizIndex < quizQuestions.length) {
                renderQuizQuestion();
            } else {
                finishQuiz();
            }
        };

        async function finishQuiz() {
            document.getElementById('quiz-main-view').classList.add('hidden');
            document.getElementById('quiz-results-view').classList.remove('hidden');

            const earnedStars = window.appState.quizScore;
            const accuracy = Math.round((window.appState.quizScore / (quizQuestions.length * 10)) * 100);

            document.getElementById('res-stars-val').innerText = `+${earnedStars} ⭐`;
            document.getElementById('res-accuracy-val').innerText = `${accuracy}%`;

            // Persist stars and update profile in Firestore
            const user = window.appState.currentUser;
            if (user) {
                const userDocRef = doc(db, 'artifacts', appId, 'users', user.uid, 'profile', 'user_data');
                const newStars = (window.appState.userProfile.stars || 0) + earnedStars;
                const newHigh = Math.max(window.appState.userProfile.highScore || 0, window.appState.quizScore);

                await updateDoc(userDocRef, {
                    stars: newStars,
                    highScore: newHigh
                });

                // Also update public leaderboard doc
                const lbDocRef = doc(db, 'artifacts', appId, 'public', 'data', 'leaderboard', user.uid);
                await setDoc(lbDocRef, {
                    displayName: user.displayName || (user.isAnonymous ? `Guest (${user.uid.substring(0,4)})` : "Wizard"),
                    stars: newStars,
                    highScore: newHigh,
                    uid: user.uid
                }, { merge: true });
            }

            confetti({ particleCount: 80, spread: 70, origin: { y: 0.5 } });
        }

        function renderLeaderboard() {
            const tbody = document.getElementById('leaderboard-tbody');
            const data = window.appState.leaderboardData;

            if (data.length === 0) {
                tbody.innerHTML = `<tr><td colspan="4" class="text-center p-4 text-slate-400">No leaderboard entries yet. Be the first to play!</td></tr>`;
                return;
            }

            tbody.innerHTML = data.map((item, idx) => `
                <tr class="hover:bg-amber-50">
                    <td class="p-3 font-black text-amber-700">#${idx + 1}</td>
                    <td class="p-3 font-extrabold text-slate-800">${item.displayName || 'Anonymous Wizard'}</td>
                    <td class="p-3 text-amber-600 font-black">${item.stars || 0} ⭐</td>
                    <td class="p-3 text-purple-600 font-black">${item.highScore || 0} pts</td>
                </tr>
            `).join('');
        }

        /* ================= INITIALIZATION ================= */
        window.addEventListener('DOMContentLoaded', async () => {
            renderTricksGrid();
            updateSolverView();
            await initAuth();
        });
    </script>
</body>
</html>
