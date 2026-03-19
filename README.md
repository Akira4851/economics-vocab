<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Economics Vocabulary Master</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&family=Playfair+Display:wght@400;600;700&display=swap" rel="stylesheet">
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
    <style type="text/tailwindcss">
        @layer base {
            body {
                font-family: 'Inter', sans-serif;
                background: #0f172a;
                color: #e2e8f0;
            }
            h1, h2, h3 {
                font-family: 'Playfair Display', serif;
            }
        }
        @layer components {
            .glass-card {
                background: rgba(30, 41, 59, 0.7);
                backdrop-filter: blur(12px);
                border: 1px solid rgba(255, 255, 255, 0.1);
                box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.5);
            }
            .neon-glow {
                box-shadow: 0 0 20px rgba(99, 102, 241, 0.5), 0 0 40px rgba(99, 102, 241, 0.3);
            }
            .gradient-text {
                background: linear-gradient(135deg, #818cf8 0%, #c084fc 50%, #f472b6 100%);
                -webkit-background-clip: text;
                -webkit-text-fill-color: transparent;
                background-clip: text;
            }
            .card-flip {
                perspective: 1000px;
            }
            .card-inner {
                position: relative;
                width: 100%;
                height: 100%;
                text-align: center;
                transition: transform 0.6s;
                transform-style: preserve-3d;
            }
            .card-flip.flipped .card-inner {
                transform: rotateY(180deg);
            }
            .card-front, .card-back {
                position: absolute;
                width: 100%;
                height: 100%;
                backface-visibility: hidden;
                border-radius: 1rem;
            }
            .card-back {
                transform: rotateY(180deg);
            }
            .progress-ring {
                transform: rotate(-90deg);
                transform-origin: 50% 50%;
            }
            .progress-ring-circle {
                transition: stroke-dashoffset 0.35s;
                transform-origin: 50% 50%;
            }
            .particle {
                position: absolute;
                pointer-events: none;
                border-radius: 50%;
                animation: float 3s ease-in-out infinite;
            }
            @keyframes float {
                0%, 100% { transform: translateY(0) rotate(0deg); opacity: 0; }
                10% { opacity: 1; }
                90% { opacity: 1; }
                100% { transform: translateY(-100px) rotate(360deg); opacity: 0; }
            }
            .shake {
                animation: shake 0.5s cubic-bezier(.36,.07,.19,.97) both;
            }
            @keyframes shake {
                10%, 90% { transform: translate3d(-1px, 0, 0); }
                20%, 80% { transform: translate3d(2px, 0, 0); }
                30%, 50%, 70% { transform: translate3d(-4px, 0, 0); }
                40%, 60% { transform: translate3d(4px, 0, 0); }
            }
            .pulse-success {
                animation: pulseSuccess 0.6s ease-out;
            }
            @keyframes pulseSuccess {
                0% { transform: scale(1); box-shadow: 0 0 0 0 rgba(34, 197, 94, 0.7); }
                70% { transform: scale(1.05); box-shadow: 0 0 0 20px rgba(34, 197, 94, 0); }
                100% { transform: scale(1); box-shadow: 0 0 0 0 rgba(34, 197, 94, 0); }
            }
        }
    </style>
<base target="_blank">
</head>
<body class="min-h-screen overflow-x-hidden">
    <!-- Animated Background -->
    <div id="particles-container" class="fixed inset-0 pointer-events-none z-0"></div>

    <!-- Navigation -->
    <nav class="fixed top-0 w-full z-50 glass-card border-b border-white/10">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex items-center justify-between h-16">
                <div class="flex items-center gap-3">
                    <div class="w-10 h-10 rounded-xl bg-gradient-to-br from-indigo-500 to-purple-600 flex items-center justify-center">
                        <span class="text-white font-bold text-xl">E</span>
                    </div>
                    <span class="text-xl font-bold gradient-text">EconVocab</span>
                </div>
                <div class="flex items-center gap-4">
                    <div class="hidden md:flex items-center gap-2 text-sm text-slate-400">
                        <span id="progress-text">0/50 mastered</span>
                    </div>
                    <div class="w-32 h-2 bg-slate-700 rounded-full overflow-hidden">
                        <div id="nav-progress" class="h-full bg-gradient-to-r from-indigo-500 to-purple-500 transition-all duration-500" style="width: 0%"></div>
                    </div>
                </div>
            </div>
        </div>
    </nav>

    <!-- Main Content -->
    <main class="relative z-10 pt-24 pb-12 px-4 sm:px-6 lg:px-8 max-w-7xl mx-auto">

        <!-- Welcome Section -->
        <section id="welcome-section" class="text-center py-20">
            <h1 class="text-5xl md:text-7xl font-bold mb-6 gradient-text">Master Economics Vocabulary</h1>
            <p class="text-xl text-slate-400 mb-12 max-w-2xl mx-auto">Interactive flashcards, quizzes, and spaced repetition to help you learn 50+ essential economics terms in English and Russian.</p>

            <div class="grid md:grid-cols-3 gap-6 max-w-4xl mx-auto mb-12">
                <div class="glass-card p-6 rounded-2xl hover:scale-105 transition-transform cursor-pointer" onclick="app.startFlashcards()">
                    <div class="w-14 h-14 rounded-full bg-indigo-500/20 flex items-center justify-center mb-4 mx-auto">
                        <svg class="w-7 h-7 text-indigo-400" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 11H5m14 0a2 2 0 012 2v6a2 2 0 01-2 2H5a2 2 0 01-2-2v-6a2 2 0 012-2m14 0V9a2 2 0 00-2-2M5 11V9a2 2 0 012-2m0 0V5a2 2 0 012-2h6a2 2 0 012 2v2M7 7h10"></path></svg>
                    </div>
                    <h3 class="text-lg font-semibold mb-2">Flashcards</h3>
                    <p class="text-sm text-slate-400">Flip cards to learn terms and definitions</p>
                </div>

                <div class="glass-card p-6 rounded-2xl hover:scale-105 transition-transform cursor-pointer" onclick="app.startQuiz()">
                    <div class="w-14 h-14 rounded-full bg-purple-500/20 flex items-center justify-center mb-4 mx-auto">
                        <svg class="w-7 h-7 text-purple-400" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"></path></svg>
                    </div>
                    <h3 class="text-lg font-semibold mb-2">Quiz Mode</h3>
                    <p class="text-sm text-slate-400">Test your knowledge with multiple choice</p>
                </div>

                <div class="glass-card p-6 rounded-2xl hover:scale-105 transition-transform cursor-pointer" onclick="app.startMatching()">
                    <div class="w-14 h-14 rounded-full bg-pink-500/20 flex items-center justify-center mb-4 mx-auto">
                        <svg class="w-7 h-7 text-pink-400" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 7h12m0 0l-4-4m4 4l-4 4m0 6H4m0 0l4 4m-4-4l4-4"></path></svg>
                    </div>
                    <h3 class="text-lg font-semibold mb-2">Matching</h3>
                    <p class="text-sm text-slate-400">Match terms with their definitions</p>
                </div>
            </div>

            <button onclick="app.startFlashcards()" class="px-8 py-4 bg-gradient-to-r from-indigo-600 to-purple-600 rounded-full font-semibold text-lg hover:scale-105 transition-transform neon-glow">
                Start Learning
            </button>
        </section>

        <!-- Flashcards Section -->
        <section id="flashcards-section" class="hidden">
            <div class="flex items-center justify-between mb-8">
                <button onclick="app.showWelcome()" class="flex items-center gap-2 text-slate-400 hover:text-white transition-colors">
                    <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7"></path></svg>
                    Back
                </button>
                <div class="flex items-center gap-4">
                    <span class="text-sm text-slate-400">Card <span id="card-current">1</span> of <span id="card-total">50</span></span>
                    <button onclick="app.shuffleCards()" class="p-2 rounded-lg bg-slate-800 hover:bg-slate-700 transition-colors">
                        <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 4v5h.582m15.356 2A8.001 8.001 0 004.582 9m0 0H9m11 11v-5h-.581m0 0a8.003 8.003 0 01-15.357-2m15.357 2H15"></path></svg>
                    </button>
                </div>
            </div>

            <div class="max-w-2xl mx-auto">
                <div class="card-flip h-96 cursor-pointer" id="flashcard" onclick="app.flipCard()">
                    <div class="card-inner">
                        <div class="card-front glass-card flex flex-col items-center justify-center p-8">
                            <span class="text-sm text-indigo-400 uppercase tracking-wider mb-4">English</span>
                            <h2 id="card-term" class="text-4xl font-bold text-center mb-4">Activities</h2>
                            <p class="text-slate-400 text-center">Click to reveal translation</p>
                            <div class="mt-6 flex gap-2">
                                <span id="card-category" class="px-3 py-1 rounded-full text-xs bg-indigo-500/20 text-indigo-300">Noun</span>
                            </div>
                        </div>
                        <div class="card-back glass-card flex flex-col items-center justify-center p-8 bg-gradient-to-br from-slate-800 to-slate-900">
                            <span class="text-sm text-purple-400 uppercase tracking-wider mb-4">Russian</span>
                            <h2 id="card-translation" class="text-3xl font-bold text-center mb-4">деятельность, активность</h2>
                            <p id="card-context" class="text-slate-300 text-center text-sm">economic activities</p>
                            <div class="mt-6 flex gap-2">
                                <span class="px-3 py-1 rounded-full text-xs bg-purple-500/20 text-purple-300">Translation</span>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="flex justify-center gap-4 mt-8">
                    <button onclick="app.prevCard()" class="p-4 rounded-full bg-slate-800 hover:bg-slate-700 transition-colors">
                        <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7"></path></svg>
                    </button>
                    <button onclick="app.markKnown()" class="px-6 py-3 rounded-full bg-green-600/20 text-green-400 hover:bg-green-600/30 transition-colors flex items-center gap-2">
                        <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 13l4 4L19 7"></path></svg>
                        I Know This
                    </button>
                    <button onclick="app.markUnknown()" class="px-6 py-3 rounded-full bg-red-600/20 text-red-400 hover:bg-red-600/30 transition-colors flex items-center gap-2">
                        <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path></svg>
                        Study Again
                    </button>
                    <button onclick="app.nextCard()" class="p-4 rounded-full bg-slate-800 hover:bg-slate-700 transition-colors">
                        <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"></path></svg>
                    </button>
                </div>
            </div>
        </section>

        <!-- Quiz Section -->
        <section id="quiz-section" class="hidden max-w-3xl mx-auto">
            <div class="flex items-center justify-between mb-8">
                <button onclick="app.showWelcome()" class="flex items-center gap-2 text-slate-400 hover:text-white transition-colors">
                    <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7"></path></svg>
                    Back
                </button>
                <div class="flex items-center gap-4">
                    <div class="flex items-center gap-2">
                        <span class="text-green-400 font-semibold" id="quiz-correct">0</span>
                        <span class="text-slate-400">/</span>
                        <span class="text-red-400 font-semibold" id="quiz-wrong">0</span>
                    </div>
                    <div class="w-32 h-2 bg-slate-700 rounded-full overflow-hidden">
                        <div id="quiz-progress" class="h-full bg-gradient-to-r from-indigo-500 to-purple-500 transition-all duration-500" style="width: 0%"></div>
                    </div>
                </div>
            </div>

            <div class="glass-card rounded-2xl p-8 mb-6">
                <div class="mb-8">
                    <span class="text-sm text-indigo-400 uppercase tracking-wider">Question <span id="question-number">1</span></span>
                    <h2 id="question-text" class="text-2xl font-bold mt-2">What is the Russian translation of "Activities"?</h2>
                </div>

                <div id="quiz-options" class="grid gap-4">
                    <!-- Options will be inserted here -->
                </div>
            </div>

            <div id="quiz-feedback" class="hidden glass-card rounded-2xl p-6 text-center">
                <div id="feedback-icon" class="w-16 h-16 rounded-full flex items-center justify-center mx-auto mb-4"></div>
                <h3 id="feedback-title" class="text-xl font-bold mb-2"></h3>
                <p id="feedback-text" class="text-slate-400 mb-4"></p>
                <button onclick="app.nextQuestion()" class="px-6 py-3 bg-indigo-600 hover:bg-indigo-700 rounded-full transition-colors">
                    Next Question
                </button>
            </div>
        </section>

        <!-- Matching Section -->
        <section id="matching-section" class="hidden">
            <div class="flex items-center justify-between mb-8">
                <button onclick="app.showWelcome()" class="flex items-center gap-2 text-slate-400 hover:text-white transition-colors">
                    <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7"></path></svg>
                    Back
                </button>
                <div class="flex items-center gap-4">
                    <span class="text-sm text-slate-400">Matches: <span id="match-score">0</span>/<span id="match-total">8</span></span>
                    <span id="match-timer" class="text-xl font-mono text-indigo-400">00:00</span>
                </div>
            </div>

            <div class="grid md:grid-cols-2 gap-8 max-w-5xl mx-auto">
                <div>
                    <h3 class="text-lg font-semibold mb-4 text-indigo-400">English Terms</h3>
                    <div id="match-terms" class="grid gap-3">
                        <!-- Terms will be inserted here -->
                    </div>
                </div>
                <div>
                    <h3 class="text-lg font-semibold mb-4 text-purple-400">Russian Definitions</h3>
                    <div id="match-definitions" class="grid gap-3">
                        <!-- Definitions will be inserted here -->
                    </div>
                </div>
            </div>

            <div id="match-complete" class="hidden fixed inset-0 bg-black/80 backdrop-blur-sm z-50 flex items-center justify-center">
                <div class="glass-card rounded-3xl p-8 max-w-md w-full mx-4 text-center">
                    <div class="w-20 h-20 rounded-full bg-gradient-to-br from-green-400 to-emerald-600 flex items-center justify-center mx-auto mb-6">
                        <svg class="w-10 h-10 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="3" d="M5 13l4 4L19 7"></path></svg>
                    </div>
                    <h2 class="text-3xl font-bold mb-2">Excellent!</h2>
                    <p class="text-slate-400 mb-6">You completed the matching game in <span id="final-time" class="text-white font-semibold"></span></p>
                    <div class="flex gap-3 justify-center">
                        <button onclick="app.startMatching()" class="px-6 py-3 bg-indigo-600 hover:bg-indigo-700 rounded-full transition-colors">
                            Play Again
                        </button>
                        <button onclick="app.showWelcome()" class="px-6 py-3 bg-slate-700 hover:bg-slate-600 rounded-full transition-colors">
                            Menu
                        </button>
                    </div>
                </div>
            </div>
        </section>

        <!-- Dictionary Section -->
        <section id="dictionary-section" class="hidden">
            <div class="flex items-center justify-between mb-8">
                <button onclick="app.showWelcome()" class="flex items-center gap-2 text-slate-400 hover:text-white transition-colors">
                    <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7"></path></svg>
                    Back
                </button>
                <div class="relative">
                    <input type="text" id="search-input" placeholder="Search terms..." 
                        class="w-64 px-4 py-2 rounded-full bg-slate-800 border border-slate-700 focus:border-indigo-500 focus:outline-none text-sm"
                        oninput="app.searchDictionary(this.value)">
                    <svg class="w-5 h-5 text-slate-400 absolute right-3 top-2.5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"></path></svg>
                </div>
            </div>

            <div class="flex gap-2 mb-6 overflow-x-auto pb-2">
                <button onclick="app.filterCategory('all')" class="px-4 py-2 rounded-full text-sm bg-indigo-600 text-white whitespace-nowrap">All</button>
                <button onclick="app.filterCategory('noun')" class="px-4 py-2 rounded-full text-sm bg-slate-800 hover:bg-slate-700 whitespace-nowrap">Nouns</button>
                <button onclick="app.filterCategory('verb')" class="px-4 py-2 rounded-full text-sm bg-slate-800 hover:bg-slate-700 whitespace-nowrap">Verbs</button>
                <button onclick="app.filterCategory('mastered')" class="px-4 py-2 rounded-full text-sm bg-slate-800 hover:bg-slate-700 whitespace-nowrap">Mastered</button>
                <button onclick="app.filterCategory('learning')" class="px-4 py-2 rounded-full text-sm bg-slate-800 hover:bg-slate-700 whitespace-nowrap">Learning</button>
            </div>

            <div id="dictionary-grid" class="grid md:grid-cols-2 lg:grid-cols-3 gap-4">
                <!-- Dictionary items will be inserted here -->
            </div>
        </section>
    </main>

    <!-- Floating Action Button -->
    <button onclick="app.toggleDictionary()" class="fixed bottom-8 right-8 w-14 h-14 rounded-full bg-gradient-to-r from-indigo-600 to-purple-600 flex items-center justify-center shadow-lg hover:scale-110 transition-transform z-40">
        <svg class="w-6 h-6 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3 6.253v13C4.168 18.477 5.754 18 7.5 18s3.332.477 4.5 1.253m0-13C13.168 5.477 14.754 5 16.5 5c1.747 0 3.332.477 4.5 1.253v13C19.832 18.477 18.247 18 16.5 18c-1.746 0-3.332.477-4.5 1.253"></path></svg>
    </button>

    <script>
        // Vocabulary Data
        const vocabulary = [
            { term: "Activities", translation: "деятельность, активность", context: "economic activities", category: "noun", subcategory: "general" },
            { term: "Area", translation: "площадь, пространство; район, область; область, сфера деятельности", context: "area of economics, remote area, rural area", category: "noun", subcategory: "general" },
            { term: "Approach", translation: "подход (к решению проблемы)", context: "different approaches to, main approaches to", category: "noun", subcategory: "general" },
            { term: "Benefit", translation: "выгода, польза, прибыль", context: "", category: "noun", subcategory: "general" },
            { term: "Branch", translation: "отрасль, подразделение; отделение, филиал", context: "branch of economy, branch of enterprise", category: "noun", subcategory: "general" },
            { term: "Commodity", translation: "предмет потребления, товар", context: "commodities, commodity production", category: "noun", subcategory: "general" },
            { term: "Consumption", translation: "потребление", context: "consumption of commodities, consumption of goods and services", category: "noun", subcategory: "general" },
            { term: "Demand", translation: "официальное требование; потребность; спрос", context: "demand for goods and services, demand for money", category: "noun", subcategory: "general" },
            { term: "Distribution", translation: "распределение", context: "distribution of products, distribution of income", category: "noun", subcategory: "general" },
            { term: "Economics", translation: "экономика (как наука)", context: "", category: "noun", subcategory: "academic" },
            { term: "Economy", translation: "экономика (как система народного хозяйства), хозяйство; бережливость, расчетливость, экономия", context: "type of economy, country's economy", category: "noun", subcategory: "general" },
            { term: "Employment", translation: "служба, занятие, работа; ремесло, профессия; занятость; использование, применение", context: "full employment, employment of natural resources", category: "noun", subcategory: "general", antonym: "Unemployment" },
            { term: "Entrepreneur", translation: "предприниматель", context: "entrepreneurial talent", category: "noun", subcategory: "business" },
            { term: "Enterprise", translation: "промышленное предприятие; предпринимательство", context: "private enterprise, public enterprise, commercial enterprise, free enterprise", category: "noun", subcategory: "business" },
            { term: "Expenditure", translation: "расходы, затраты", context: "government expenditure, production expenditures", category: "noun", subcategory: "finance" },
            { term: "Force", translation: "сила, насилие; (мн.) войска", context: "economic forces, market forces, labour forces, productive forces", category: "noun", subcategory: "general" },
            { term: "Goods", translation: "товары", context: "consumer goods, goods and services", category: "noun", subcategory: "general" },
            { term: "Household", translation: "семейство, семья, домашнее хозяйство", context: "household goods, household appliances, household management", category: "noun", subcategory: "general" },
            { term: "Income", translation: "прибыль, доход, заработок", context: "", category: "noun", subcategory: "finance" },
            { term: "Institution", translation: "общество, организация, учреждение, ведомство", context: "financial institution, social institution, state-supported institution", category: "noun", subcategory: "general" },
            { term: "Manufacture", translation: "производство, изготовление", context: "", category: "noun", subcategory: "production", synonym: "Production" },
            { term: "Ownership", translation: "собственность", context: "joint ownership, private ownership, public ownership, state ownership", category: "noun", subcategory: "legal" },
            { term: "Production", translation: "производство", context: "means of production, factors of production", category: "noun", subcategory: "production", synonym: "Manufacture" },
            { term: "Resources", translation: "запасы, ресурсы, средства", context: "available resources, economic resources, natural resources, scarce resources", category: "noun", subcategory: "general" },
            { term: "Service", translation: "служба, занятие, работа; учреждение, подразделение; обслуживание, оказание услуг", context: "service industry, catering services, government services, medical services", category: "noun", subcategory: "general" },
            { term: "Supply", translation: "снабжение, поставка; ресурсы, припасы, запас; предложение", context: "labour supply, supply and demand", category: "noun", subcategory: "general" },
            { term: "Wealth", translation: "богатство, состояние; материальные ценности", context: "natural wealth, mineral wealth", category: "noun", subcategory: "finance" },
            { term: "Unemployment", translation: "безработица", context: "antonym to employment", category: "noun", subcategory: "general" },
            // Verbs
            { term: "To affect", translation: "затрагивать, оказывать влияние", context: "to affect prices, to affect market, to be affected by", category: "verb", subcategory: "action" },
            { term: "To avoid", translation: "избегать, остерегаться, уклоняться", context: "to avoid unnecessary expenditures, to avoid the disadvantages", category: "verb", subcategory: "action" },
            { term: "To concern", translation: "касаться, относиться; заниматься, интересоваться", context: "to concern everybody, to be concerned with", category: "verb", subcategory: "action" },
            { term: "To consume", translation: "потреблять, расходовать, тратить", context: "to consume goods and services, to consume natural resources", category: "verb", subcategory: "action" },
            { term: "To carry out", translation: "выполнять, совершать, осуществлять", context: "to carry out economic policy, to carry out economic activities", category: "verb", subcategory: "action" },
            { term: "To deal with", translation: "вести дело, заниматься, рассматривать вопрос", context: "to deal with economic problems, to deal with production, distribution and consumption", category: "verb", subcategory: "action" },
            { term: "To define", translation: "определять, давать определение, определять границы", context: "to define a problem, to define an area of study, to define the economy", category: "verb", subcategory: "cognitive" },
            { term: "To distribute", translation: "распределять", context: "to distribute commodities, to distribute resources", category: "verb", subcategory: "action" },
            { term: "To determine", translation: "определять, устанавливать, регулировать; решать, разрешать", context: "to determine the way of using resources, to determine inflation and unemployment", category: "verb", subcategory: "cognitive" },
            { term: "To develop", translation: "развивать", context: "to develop the economy, to develop certain industries", category: "verb", subcategory: "action" },
            { term: "To employ", translation: "принимать на работу, нанимать; употреблять, использовать", context: "to employ workers, to employ factors of production", category: "verb", subcategory: "action" },
            { term: "To enable", translation: "давать возможность, делать возможным", context: "to enable smb. to do smth.", category: "verb", subcategory: "modal" },
            { term: "To encourage", translation: "поощрять, поддерживать, содействовать", context: "to encourage trade, to encourage production and employment", category: "verb", subcategory: "action" },
            { term: "To enjoy", translation: "пользоваться (правами, преимуществами)", context: "to enjoy advantages, to enjoy the benefits", category: "verb", subcategory: "stative" },
            { term: "To exercise", translation: "пользоваться, осуществлять", context: "to exercise a right", category: "verb", subcategory: "action" },
            { term: "To extract", translation: "добывать, извлекать, получать", context: "to extract information, to extract goods from natural environment", category: "verb", subcategory: "action" },
            { term: "To involve", translation: "вовлекать, впутывать", context: "to involve in the process of production", category: "verb", subcategory: "action" },
            { term: "To manufacture", translation: "производить, выпускать", context: "to manufacture equipment", category: "verb", subcategory: "production", synonym: "To produce, To make" },
            { term: "To obtain", translation: "получать, добывать", context: "to obtain natural resources", category: "verb", subcategory: "action" },
            { term: "To produce", translation: "производить", context: "to produce goods and services, to produce commodities", category: "verb", subcategory: "production", synonym: "To manufacture" },
            { term: "To provide", translation: "давать, предоставлять, обеспечивать, снабжать", context: "to provide smb with goods, to provide a service", category: "verb", subcategory: "action" },
            { term: "To refer", translation: "иметь отношение, относиться, касаться; ссылаться, упоминать", context: "to refer to the problem, to refer to the information", category: "verb", subcategory: "cognitive" },
            { term: "To satisfy", translation: "удовлетворять; возмещать (убытки)", context: "to satisfy the demand, to satisfy needs and wants", category: "verb", subcategory: "action" },
            { term: "To supply", translation: "снабжать, доставлять, поставлять", context: "to supply an industry with raw materials, to supply the goods from the market", category: "verb", subcategory: "action" }
        ];

        // Application State
        const app = {
            currentCard: 0,
            shuffledIndices: [],
            mastered: new Set(),
            learning: new Set(),
            quizScore: { correct: 0, wrong: 0, current: 0 },
            matchState: { selected: null, matches: 0, total: 8, startTime: null },
            currentFilter: 'all',

            init() {
                this.shuffledIndices = [...Array(vocabulary.length).keys()];
                this.createParticles();
                this.updateProgress();

                // Load saved progress
                const saved = localStorage.getItem('econVocabProgress');
                if (saved) {
                    const data = JSON.parse(saved);
                    this.mastered = new Set(data.mastered || []);
                    this.learning = new Set(data.learning || []);
                }
            },

            createParticles() {
                const container = document.getElementById('particles-container');
                for (let i = 0; i < 20; i++) {
                    const particle = document.createElement('div');
                    particle.className = 'particle';
                    particle.style.width = Math.random() * 4 + 2 + 'px';
                    particle.style.height = particle.style.width;
                    particle.style.background = `rgba(${100 + Math.random() * 155}, ${100 + Math.random() * 155}, 255, ${Math.random() * 0.5})`;
                    particle.style.left = Math.random() * 100 + '%';
                    particle.style.top = Math.random() * 100 + '%';
                    particle.style.animationDelay = Math.random() * 3 + 's';
                    particle.style.animationDuration = (3 + Math.random() * 4) + 's';
                    container.appendChild(particle);
                }
            },

            showWelcome() {
                this.hideAllSections();
                document.getElementById('welcome-section').classList.remove('hidden');
                this.updateProgress();
            },

            hideAllSections() {
                ['welcome-section', 'flashcards-section', 'quiz-section', 'matching-section', 'dictionary-section'].forEach(id => {
                    document.getElementById(id).classList.add('hidden');
                });
            },

            // Flashcard Methods
            startFlashcards() {
                this.hideAllSections();
                document.getElementById('flashcards-section').classList.remove('hidden');
                this.currentCard = 0;
                this.updateCard();
                document.getElementById('card-total').textContent = vocabulary.length;
            },

            updateCard() {
                const card = vocabulary[this.shuffledIndices[this.currentCard]];
                document.getElementById('card-current').textContent = this.currentCard + 1;
                document.getElementById('card-term').textContent = card.term;
                document.getElementById('card-translation').textContent = card.translation;
                document.getElementById('card-context').textContent = card.context || 'No example context';
                document.getElementById('card-category').textContent = card.category;

                // Reset flip
                document.getElementById('flashcard').classList.remove('flipped');

                // Visual feedback for mastered/learning
                const flashcardEl = document.getElementById('flashcard');
                flashcardEl.classList.remove('pulse-success', 'shake');
                if (this.mastered.has(this.shuffledIndices[this.currentCard])) {
                    flashcardEl.querySelector('.card-front').classList.add('border-green-500/50');
                }
            },

            flipCard() {
                document.getElementById('flashcard').classList.toggle('flipped');
            },

            nextCard() {
                if (this.currentCard < vocabulary.length - 1) {
                    this.currentCard++;
                    this.animateCardChange('next');
                } else {
                    this.showFlashcardComplete();
                }
            },

            prevCard() {
                if (this.currentCard > 0) {
                    this.currentCard--;
                    this.animateCardChange('prev');
                }
            },

            animateCardChange(direction) {
                const card = document.getElementById('flashcard');
                gsap.to(card, {
                    x: direction === 'next' ? -50 : 50,
                    opacity: 0,
                    duration: 0.2,
                    onComplete: () => {
                        this.updateCard();
                        gsap.fromTo(card, 
                            { x: direction === 'next' ? 50 : -50, opacity: 0 },
                            { x: 0, opacity: 1, duration: 0.3 }
                        );
                    }
                });
            },

            markKnown() {
                const idx = this.shuffledIndices[this.currentCard];
                this.mastered.add(idx);
                this.learning.delete(idx);
                this.saveProgress();

                const card = document.getElementById('flashcard');
                card.classList.add('pulse-success');

                setTimeout(() => this.nextCard(), 600);
            },

            markUnknown() {
                const idx = this.shuffledIndices[this.currentCard];
                this.learning.add(idx);
                this.saveProgress();

                const card = document.getElementById('flashcard');
                card.classList.add('shake');

                setTimeout(() => {
                    card.classList.remove('shake');
                    this.nextCard();
                }, 500);
            },

            shuffleCards() {
                this.shuffledIndices.sort(() => Math.random() - 0.5);
                this.currentCard = 0;
                this.updateCard();
            },

            showFlashcardComplete() {
                const container = document.querySelector('#flashcards-section .max-w-2xl');
                const originalContent = container.innerHTML;

                // Calculate stats
                const mastered = this.mastered.size;
                const total = vocabulary.length;
                const percentage = Math.round((mastered / total) * 100);

                container.innerHTML = `
                    <div class="glass-card rounded-3xl p-8 text-center">
                        <div class="w-20 h-20 rounded-full bg-gradient-to-br from-indigo-500 to-purple-600 flex items-center justify-center mx-auto mb-6">
                            <svg class="w-10 h-10 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="3" d="M5 13l4 4L19 7"></path>
                            </svg>
                        </div>
                        <h2 class="text-3xl font-bold mb-2 gradient-text">Session Complete!</h2>
                        <p class="text-slate-400 mb-6">You've reviewed all ${total} cards</p>

                        <div class="grid grid-cols-3 gap-4 mb-8">
                            <div class="bg-slate-800/50 rounded-xl p-4">
                                <div class="text-2xl font-bold text-green-400">${mastered}</div>
                                <div class="text-xs text-slate-400">Mastered</div>
                            </div>
                            <div class="bg-slate-800/50 rounded-xl p-4">
                                <div class="text-2xl font-bold text-yellow-400">${this.learning.size}</div>
                                <div class="text-xs text-slate-400">Learning</div>
                            </div>
                            <div class="bg-slate-800/50 rounded-xl p-4">
                                <div class="text-2xl font-bold text-indigo-400">${percentage}%</div>
                                <div class="text-xs text-slate-400">Progress</div>
                            </div>
                        </div>

                        <div class="flex gap-3 justify-center">
                            <button onclick="app.restartFlashcards()" class="px-6 py-3 bg-indigo-600 hover:bg-indigo-700 rounded-full transition-colors flex items-center gap-2">
                                <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 4v5h.582m15.356 2A8.001 8.001 0 004.582 9m0 0H9m11 11v-5h-.581m0 0a8.003 8.003 0 01-15.357-2m15.357 2H15"></path>
                                </svg>
                                Study Again
                            </button>
                            <button onclick="app.showWelcome()" class="px-6 py-3 bg-slate-700 hover:bg-slate-600 rounded-full transition-colors flex items-center gap-2">
                                <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M3 12l2-2m0 0l7-7 7 7M5 10v10a1 1 0 001 1h3m10-11l2 2m-2-2v10a1 1 0 01-1 1h-3m-6 0a1 1 0 001-1v-4a1 1 0 011-1h2a1 1 0 011 1v4a1 1 0 001 1m-6 0h6"></path>
                                </svg>
                                Main Menu
                            </button>
                        </div>
                    </div>
                `;

                // Store original content for restart
                container.dataset.originalContent = originalContent;
            },

            restartFlashcards() {
                const container = document.querySelector('#flashcards-section .max-w-2xl');
                if (container.dataset.originalContent) {
                    container.innerHTML = container.dataset.originalContent;
                }
                this.currentCard = 0;
                this.shuffleCards();
            },

            // Quiz Methods
            startQuiz() {
                this.hideAllSections();
                document.getElementById('quiz-section').classList.remove('hidden');
                this.quizScore = { correct: 0, wrong: 0, current: 0 };
                this.updateQuizProgress();
                this.generateQuestion();
            },

            generateQuestion() {
                const questionTypes = ['translation', 'context', 'term'];
                const type = questionTypes[Math.floor(Math.random() * questionTypes.length)];
                const correctIdx = Math.floor(Math.random() * vocabulary.length);
                const correct = vocabulary[correctIdx];

                let question, options;

                if (type === 'translation') {
                    question = `What is the Russian translation of "${correct.term}"?`;
                    options = this.generateOptions(correctIdx, 'translation');
                } else if (type === 'context') {
                    question = `Which term matches the context: "${correct.context || correct.translation}"?`;
                    options = this.generateOptions(correctIdx, 'term');
                } else {
                    question = `What is the English term for "${correct.translation.split(';')[0].trim()}"?`;
                    options = this.generateOptions(correctIdx, 'term');
                }

                document.getElementById('question-number').textContent = this.quizScore.current + 1;
                document.getElementById('question-text').textContent = question;

                const optionsContainer = document.getElementById('quiz-options');
                optionsContainer.innerHTML = '';

                options.forEach((opt, idx) => {
                    const btn = document.createElement('button');
                    btn.className = 'w-full text-left p-4 rounded-xl bg-slate-800 hover:bg-slate-700 transition-colors border border-slate-700 hover:border-indigo-500';
                    btn.textContent = opt.text;
                    btn.onclick = () => this.selectAnswer(idx, options, correctIdx);
                    optionsContainer.appendChild(btn);
                });

                document.getElementById('quiz-feedback').classList.add('hidden');
            },

            generateOptions(correctIdx, field) {
                const options = [{ idx: correctIdx, text: vocabulary[correctIdx][field] }];
                const used = new Set([correctIdx]);

                while (options.length < 4) {
                    const idx = Math.floor(Math.random() * vocabulary.length);
                    if (!used.has(idx)) {
                        used.add(idx);
                        let text = vocabulary[idx][field];
                        if (field === 'translation' && text.length > 50) {
                            text = text.split(';')[0].trim();
                        }
                        options.push({ idx, text });
                    }
                }

                return options.sort(() => Math.random() - 0.5);
            },

            selectAnswer(selectedIdx, options, correctIdx) {
                const selected = options[selectedIdx];
                const isCorrect = selected.idx === correctIdx;

                if (isCorrect) {
                    this.quizScore.correct++;
                    this.mastered.add(correctIdx);
                } else {
                    this.quizScore.wrong++;
                    this.learning.add(correctIdx);
                }

                this.saveProgress();
                this.updateQuizProgress();

                // Show feedback
                const feedback = document.getElementById('quiz-feedback');
                const icon = document.getElementById('feedback-icon');
                const title = document.getElementById('feedback-title');
                const text = document.getElementById('feedback-text');

                feedback.classList.remove('hidden');

                if (isCorrect) {
                    icon.className = 'w-16 h-16 rounded-full flex items-center justify-center mx-auto mb-4 bg-green-500';
                    icon.innerHTML = '<svg class="w-8 h-8 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="3" d="M5 13l4 4L19 7"></path></svg>';
                    title.textContent = 'Correct!';
                    title.className = 'text-xl font-bold mb-2 text-green-400';
                    text.textContent = `"${vocabulary[correctIdx].term}" = "${vocabulary[correctIdx].translation}"`;
                } else {
                    icon.className = 'w-16 h-16 rounded-full flex items-center justify-center mx-auto mb-4 bg-red-500';
                    icon.innerHTML = '<svg class="w-8 h-8 text-white" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="3" d="M6 18L18 6M6 6l12 12"></path></svg>';
                    title.textContent = 'Incorrect';
                    title.className = 'text-xl font-bold mb-2 text-red-400';
                    text.textContent = `The correct answer was: "${vocabulary[correctIdx].translation}"`;
                }

                // Disable all buttons
                document.querySelectorAll('#quiz-options button').forEach(btn => {
                    btn.disabled = true;
                    btn.classList.add('opacity-50', 'cursor-not-allowed');
                });
            },

            nextQuestion() {
                this.quizScore.current++;
                if (this.quizScore.current < 10) {
                    this.generateQuestion();
                } else {
                    this.showQuizResults();
                }
            },

            updateQuizProgress() {
                document.getElementById('quiz-correct').textContent = this.quizScore.correct;
                document.getElementById('quiz-wrong').textContent = this.quizScore.wrong;
                const pct = (this.quizScore.current / 10) * 100;
                document.getElementById('quiz-progress').style.width = pct + '%';
            },

            showQuizResults() {
                const container = document.getElementById('quiz-options').parentElement;
                container.innerHTML = `
                    <div class="text-center py-12">
                        <div class="w-24 h-24 rounded-full bg-gradient-to-br from-indigo-500 to-purple-600 flex items-center justify-center mx-auto mb-6">
                            <span class="text-3xl font-bold text-white">${this.quizScore.correct}/10</span>
                        </div>
                        <h2 class="text-2xl font-bold mb-4">Quiz Complete!</h2>
                        <p class="text-slate-400 mb-8">You got ${this.quizScore.correct} correct and ${this.quizScore.wrong} wrong.</p>
                        <div class="flex gap-4 justify-center">
                            <button onclick="app.startQuiz()" class="px-6 py-3 bg-indigo-600 hover:bg-indigo-700 rounded-full transition-colors">Try Again</button>
                            <button onclick="app.showWelcome()" class="px-6 py-3 bg-slate-700 hover:bg-slate-600 rounded-full transition-colors">Back to Menu</button>
                        </div>
                    </div>
                `;
            },

            // Matching Game
            startMatching() {
                this.hideAllSections();
                document.getElementById('matching-section').classList.remove('hidden');
                this.matchState = { selected: null, matches: 0, total: 8, startTime: Date.now() };
                this.setupMatching();
                this.startMatchTimer();
            },

            setupMatching() {
                // Select 8 random terms
                const indices = [...Array(vocabulary.length).keys()].sort(() => Math.random() - 0.5).slice(0, 8);
                const selected = indices.map(i => vocabulary[i]);

                const termsContainer = document.getElementById('match-terms');
                const defsContainer = document.getElementById('match-definitions');

                termsContainer.innerHTML = '';
                defsContainer.innerHTML = '';

                // Create term buttons
                selected.forEach((item, idx) => {
                    const btn = document.createElement('button');
                    btn.className = 'match-item w-full p-4 rounded-xl bg-slate-800 border-2 border-slate-700 hover:border-indigo-500 transition-all text-left';
                    btn.textContent = item.term;
                    btn.dataset.index = indices[idx];
                    btn.dataset.type = 'term';
                    btn.onclick = () => this.selectMatchItem(btn, indices[idx]);
                    termsContainer.appendChild(btn);
                });

                // Create definition buttons (shuffled)
                const shuffledDefs = [...selected].sort(() => Math.random() - 0.5);
                shuffledDefs.forEach(item => {
                    const originalIdx = vocabulary.indexOf(item);
                    const btn = document.createElement('button');
                    btn.className = 'match-item w-full p-4 rounded-xl bg-slate-800 border-2 border-slate-700 hover:border-purple-500 transition-all text-left text-sm';
                    btn.textContent = item.translation.split(';')[0].trim();
                    btn.dataset.index = originalIdx;
                    btn.dataset.type = 'def';
                    btn.onclick = () => this.selectMatchItem(btn, originalIdx);
                    defsContainer.appendChild(btn);
                });

                document.getElementById('match-score').textContent = '0';
                document.getElementById('match-total').textContent = '8';
                document.getElementById('match-complete').classList.add('hidden');
            },

            selectMatchItem(btn, index) {
                if (btn.classList.contains('matched') || btn.classList.contains('selected')) return;

                if (!this.matchState.selected) {
                    // First selection
                    this.matchState.selected = { btn, index };
                    btn.classList.add('selected', 'border-indigo-500', 'bg-indigo-500/20');
                } else {
                    // Second selection
                    const first = this.matchState.selected;

                    if (first.index === index && first.btn !== btn) {
                        // Match!
                        first.btn.classList.remove('selected', 'border-indigo-500', 'bg-indigo-500/20');
                        first.btn.classList.add('matched', 'border-green-500', 'bg-green-500/20');
                        btn.classList.add('matched', 'border-green-500', 'bg-green-500/20');

                        this.matchState.matches++;
                        document.getElementById('match-score').textContent = this.matchState.matches;

                        // Animation
                        gsap.fromTo([first.btn, btn], 
                            { scale: 1 },
                            { scale: 1.05, duration: 0.2, yoyo: true, repeat: 1 }
                        );

                        if (this.matchState.matches === this.matchState.total) {
                            setTimeout(() => this.completeMatching(), 500);
                        }
                    } else {
                        // No match
                        first.btn.classList.remove('selected', 'border-indigo-500', 'bg-indigo-500/20');
                        btn.classList.add('shake');
                        first.btn.classList.add('shake');

                        setTimeout(() => {
                            btn.classList.remove('shake');
                            first.btn.classList.remove('shake');
                        }, 500);
                    }

                    this.matchState.selected = null;
                }
            },

            startMatchTimer() {
                const update = () => {
                    if (this.matchState.matches === this.matchState.total) return;
                    const elapsed = Math.floor((Date.now() - this.matchState.startTime) / 1000);
                    const mins = Math.floor(elapsed / 60).toString().padStart(2, '0');
                    const secs = (elapsed % 60).toString().padStart(2, '0');
                    document.getElementById('match-timer').textContent = `${mins}:${secs}`;
                    requestAnimationFrame(update);
                };
                update();
            },

            completeMatching() {
                const elapsed = Math.floor((Date.now() - this.matchState.startTime) / 1000);
                const mins = Math.floor(elapsed / 60).toString().padStart(2, '0');
                const secs = (elapsed % 60).toString().padStart(2, '0');
                document.getElementById('final-time').textContent = `${mins}:${secs}`;
                document.getElementById('match-complete').classList.remove('hidden');
            },

            // Dictionary Methods
            toggleDictionary() {
                const dictSection = document.getElementById('dictionary-section');
                if (dictSection.classList.contains('hidden')) {
                    this.hideAllSections();
                    dictSection.classList.remove('hidden');
                    this.renderDictionary();
                } else {
                    this.showWelcome();
                }
            },

            renderDictionary() {
                const grid = document.getElementById('dictionary-grid');
                grid.innerHTML = '';

                const filtered = vocabulary.filter((item, idx) => {
                    if (this.currentFilter === 'all') return true;
                    if (this.currentFilter === 'mastered') return this.mastered.has(idx);
                    if (this.currentFilter === 'learning') return this.learning.has(idx);
                    return item.category === this.currentFilter;
                });

                filtered.forEach((item, idx) => {
                    const originalIdx = vocabulary.indexOf(item);
                    const card = document.createElement('div');
                    card.className = 'glass-card rounded-xl p-4 hover:scale-105 transition-transform cursor-pointer';

                    const isMastered = this.mastered.has(originalIdx);
                    const isLearning = this.learning.has(originalIdx);

                    card.innerHTML = `
                        <div class="flex items-start justify-between mb-2">
                            <h3 class="font-bold text-lg">${item.term}</h3>
                            ${isMastered ? '<span class="text-green-400 text-xs">✓ Mastered</span>' : ''}
                            ${isLearning ? '<span class="text-yellow-400 text-xs">📖 Learning</span>' : ''}
                        </div>
                        <p class="text-sm text-slate-300 mb-2">${item.translation}</p>
                        ${item.context ? `<p class="text-xs text-slate-500 italic">${item.context}</p>` : ''}
                        <div class="mt-3 flex gap-2">
                            <span class="px-2 py-1 rounded text-xs bg-slate-700">${item.category}</span>
                            ${item.subcategory ? `<span class="px-2 py-1 rounded text-xs bg-slate-800">${item.subcategory}</span>` : ''}
                        </div>
                    `;

                    card.onclick = () => {
                        this.currentCard = originalIdx;
                        this.shuffledIndices = [...Array(vocabulary.length).keys()];
                        this.startFlashcards();
                    };

                    grid.appendChild(card);
                });
            },

            filterCategory(cat) {
                this.currentFilter = cat;
                // Update button styles
                document.querySelectorAll('#dictionary-section button').forEach(btn => {
                    if (btn.textContent.toLowerCase().includes(cat) || (cat === 'all' && btn.textContent === 'All')) {
                        btn.classList.remove('bg-slate-800');
                        btn.classList.add('bg-indigo-600');
                    } else if (btn.onclick && btn.onclick.toString().includes('filterCategory')) {
                        btn.classList.add('bg-slate-800');
                        btn.classList.remove('bg-indigo-600');
                    }
                });
                this.renderDictionary();
            },

            searchDictionary(query) {
                const grid = document.getElementById('dictionary-grid');
                const cards = grid.children;

                Array.from(cards).forEach(card => {
                    const text = card.textContent.toLowerCase();
                    card.style.display = text.includes(query.toLowerCase()) ? 'block' : 'none';
                });
            },

            // Utility Methods
            updateProgress() {
                const mastered = this.mastered.size;
                const total = vocabulary.length;
                const pct = (mastered / total) * 100;

                document.getElementById('progress-text').textContent = `${mastered}/${total} mastered`;
                document.getElementById('nav-progress').style.width = pct + '%';
            },

            saveProgress() {
                const data = {
                    mastered: Array.from(this.mastered),
                    learning: Array.from(this.learning)
                };
                localStorage.setItem('econVocabProgress', JSON.stringify(data));
                this.updateProgress();
            }
        };

        // Initialize
        document.addEventListener('DOMContentLoaded', () => {
            app.init();
        });

        // Keyboard shortcuts
        document.addEventListener('keydown', (e) => {
            if (document.getElementById('flashcards-section').classList.contains('hidden')) return;

            if (e.key === 'ArrowRight') app.nextCard();
            if (e.key === 'ArrowLeft') app.prevCard();
            if (e.key === ' ') {
                e.preventDefault();
                app.flipCard();
            }
            if (e.key === '1') app.markKnown();
            if (e.key === '2') app.markUnknown();
        });
    </script>
</body>
</html>
