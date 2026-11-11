<!DOCTYPE html>

<html lang="vi">

<head>

    <meta charset="UTF-8">

    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>English Learning Hub - Học Tiếng Anh Cùng Panda 🐼</title>

    <script src="https://cdn.tailwindcss.com"></script>

    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">

    <style>

        body { font-family: 'Poppins', sans-serif; }

        .gradient-bg { background: linear-gradient(135deg, #6366f1 0%, #a855f7 100%); }

    </style>

</head>

<body class="bg-slate-50 text-slate-800 min-h-screen flex flex-col">

⁢

    <!-- Header -->

    <header class="gradient-bg text-white shadow-lg py-6 px-4">

        <div class="max-w-4xl mx-auto flex flex-col sm:flex-row justify-between items-center gap-4">

            <div class="flex items-center gap-3">

                <span class="text-4xl">🐼</span>

                <div>

                    <h1 class="text-2xl font-bold">English Hub cho Panda</h1>

                    <p class="text-indigo-100 text-sm">Học mỗi ngày, giỏi mỗi giây! 🚀</p>

                </div>

            </div>

            <nav class="flex gap-2 bg-white/10 p-1 rounded-xl backdrop-blur-md">

                <button onclick="switchTab('vocab')" id="btn-vocab" class="px-4 py-2 rounded-lg font-medium transition bg-white text-indigo-600 shadow">📚 Từ Vựng</button>

                <button onclick="switchTab('listening')" id="btn-listening" class="px-4 py-2 rounded-lg font-medium transition text-white hover:bg-white/20">🎧 Luyện Nghe</button>

                <button onclick="switchTab('quiz')" id="btn-quiz" class="px-4 py-2 rounded-lg font-medium transition text-white hover:bg-white/20">🎮 Mini Quiz</button>

            </nav>

        </div>

    </header>

⁢

    <!-- Main Content -->

    <main class="max-w-4xl w-full mx-auto p-4 sm:p-6 flex-grow">

⁢

        <!-- TAB 1: TỪ VỰNG -->

        <section id="tab-vocab" class="space-y-6">

            <div class="flex flex-col sm:flex-row justify-between gap-4">

                <input type="text" id="searchInput" placeholder="🔍 Tìm kiếm từ vựng..." onkeyup="filterVocab()" 

                    class="w-full sm:w-72 px-4 py-3 rounded-xl border border-slate-200 focus:outline-none focus:ring-2 focus:ring-indigo-500 shadow-sm">

                <div class="flex gap-2 overflow-x-auto pb-2">

                    <button onclick="filterCategory('all')" class="px-4 py-2 rounded-xl bg-indigo-600 text-white font-medium text-sm whitespace-nowrap shadow">Tất cả</button>

                    <button onclick="filterCategory('tech')" class="px-4 py-2 rounded-xl bg-white text-slate-600 font-medium text-sm whitespace-nowrap border border-slate-200 hover:bg-slate-100">💻 Công nghệ</button>

                    <button onclick="filterCategory('travel')" class="px-4 py-2 rounded-xl bg-white text-slate-600 font-medium text-sm whitespace-nowrap border border-slate-200 hover:bg-slate-100">✈️ Du lịch</button>

                    <button onclick="filterCategory('life')" class="px-4 py-2 rounded-xl bg-white text-slate-600 font-medium text-sm whitespace-nowrap border border-slate-200 hover:bg-slate-100">🌿 Đời sống</button>

                </div>

            </div>

⁢

            <div id="vocab-grid" class="grid grid-cols-1 sm:grid-cols-2 gap-4">

                <!-- Javascript sẽ render từ vựng ở đây -->

            </div>

        </section>

⁢

        <!-- TAB 2: LUYỆN NGHE -->

        <section id="tab-listening" class="hidden space-y-6">

            <div class="bg-white p-6 rounded-2xl shadow-sm border border-slate-100 space-y-4">

                <h2 class="text-xl font-bold text-slate-800">🎧 Luyện Nghe & Phát Âm Giao Tiếp</h2>

                <p class="text-slate-600 text-sm">Bấm nút loa để nghe câu thoại, thử luyện tập tốc độ chậm hoặc chuẩn nhé Panda!</p>

                

                <div id="listening-list" class="space-y-4 mt-4">

                    <!-- Danh sách câu luyện nghe -->

                </div>

            </div>

        </section>

⁢

        <!-- TAB 3: MINI QUIZ -->

        <section id="tab-quiz" class="hidden">

            <div class="bg-white p-6 sm:p-8 rounded-2xl shadow-sm border border-slate-100 max-w-xl mx-auto text-center space-y-6">

                <div id="quiz-start-screen" class="space-y-4">

                    <span class="text-6xl">🎯</span>

                    <h2 class="text-2xl font-bold">Thử Thách Từ Vựng</h2>

                    <p class="text-slate-600 text-sm">Kiểm tra ngay trí nhớ siêu phàm của Panda với 5 câu hỏi trắc nghiệm nhanh!</p>

                    <button onclick="startQuiz()" class="px-6 py-3 bg-indigo-600 text-white font-semibold rounded-xl shadow-lg hover:bg-indigo-700 transition">Bắt Đầu Ngay 🚀</button>

                </div>

⁢

                <div id="quiz-question-screen" class="hidden space-y-6 text-left">

                    <div class="flex justify-between text-sm font-semibold text-slate-400">

                        <span id="quiz-progress">Câu 1/5</span>

                        <span id="quiz-score">Điểm: 0</span>

                    </div>

                    <h3 id="quiz-question" class="text-xl font-bold text-slate-800"></h3>

                    <div id="quiz-options" class="space-y-3">

                        <!-- Các lựa chọn đáp án -->

                    </div>

                </div>

⁢

                <div id="quiz-result-screen" class="hidden space-y-4">

                    <span class="text-6xl">🏆</span>

                    <h2 class="text-2xl font-bold">Hoàn Thành Xuất Sắc!</h2>

                    <p id="quiz-final-score" class="text-lg font-medium text-indigo-600"></p>

                    <button onclick="resetQuiz()" class="px-6 py-3 bg-indigo-600 text-white font-semibold rounded-xl shadow-lg hover:bg-indigo-700 transition">Làm Lại Quiz 🔄</button>

                </div>

            </div>

        </section>

⁢

    </main>

⁢

    <!-- Footer -->

    <footer class="text-center py-6 text-sm text-slate-400 border-t border-slate-200 mt-10">

        Made with 💖 for Panda by Panh - 2026

    </footer>

⁢

    <!-- JavaScript Xử Lý -->

    <script>

        // Dữ liệu từ vựng

        const vocabData = \[

            { word: "Developer", ipa: "/dɪˈveləpər/", meaning: "Lập trình viên", example: "Panda is a awesome web developer.", category: "tech", emoji: "💻" },

            { word: "Artificial Intelligence", ipa: "/ˌɑːrtɪˈfɪʃl ɪnˈtelɪdʒəns/", meaning: "Trí tuệ nhân tạo", example: "AI helps Panda code faster.", category: "tech", emoji: "🤖" },

            { word: "Adventure", ipa: "/ədˈventʃər/", meaning: "Cuộc phiêu lưu", example: "Life is a great adventure.", category: "travel", emoji: "🌍" },

            { word: "Destination", ipa: "/ˌdestɪˈneɪʃn/", meaning: "Điểm đến", example: "Choose your next travel destination.", category: "travel", emoji: "✈️" },

            { word: "Coffee", ipa: "/ˈkɑːfi/", meaning: "Cà phê", example: "Start a morning with hot coffee.", category: "life", emoji: "☕" },

            { word: "Happiness", ipa: "/ˈhæpinəs/", meaning: "Sự hạnh phúc", example: "Happiness is key to success.", category: "life", emoji: "😊" }

        \];

⁢

        // Dữ liệu luyện nghe

        const listeningData = \[

            { text: "Hello Panda, how are you doing today?", meaning: "Xin chào Panda, hôm nay bạn thế nào?" },

            { text: "Let's build an amazing web application together.", meaning: "Hãy cùng nhau xây dựng một ứng dụng web tuyệt vời nhé." },

            { text: "Practice makes perfect, keep going!", meaning: "Có công mài sắt có ngày nên kim, cứ tiếp tục cố gắng nhé!" }

        \];

⁢

        // Dữ liệu Quiz

        const quizData = \[

            { q: "Từ nào có nghĩa là 'Lập trình viên'?", options: \["Developer", "Designer", "Manager", "Engineer"\], correct: 0 },

            { q: "Phiên âm chuẩn của từ 'Coffee' là gì?", options: \["/kɑːfi/", "/kʌfi/", "/koʊfi/", "/kæfi/"\], correct: 0 },

            { q: "Đâu là nghĩa của từ 'Artificial Intelligence'?", options: \["Du lịch mạo hiểm", "Trí tuệ nhân tạo", "Lập trình web", "Hạnh phúc"\], correct: 1 },

            { q: "Từ nào có nghĩa là 'Cuộc phiêu lưu'?", options: \["Destination", "Journey", "Adventure", "Trip"\], correct: 2 },

            { q: "Chọn câu ví dụ đúng với từ 'Happiness':", options: \["Happiness is key to success.", "Coffee is a great language.", "AI is flying high."\], correct: 0 }

        \];

⁢

        // Phát âm thanh SpeechSynthesis

        function speakText(text, rate = 1.0) {

            if ('speechSynthesis' in window) {

                window.speechSynthesis.cancel(); // Dừng âm thanh cũ nếu đang đọc

                const utterance = new SpeechSynthesisUtterance(text);

                utterance.lang = 'en-US';

                utterance.rate = rate;

                window.speechSynthesis.speak(utterance);

            } else {

                alert("Trình duyệt của Panda chưa hỗ trợ phát âm thanh trực tiếp rồi! Hãy thử dùng Chrome hoặc Safari bản mới nhất nhé.");

            }

        }

⁢

        // Chuyển Tab

        function switchTab(tab) {

            \['vocab', 'listening', 'quiz'\].forEach(t => {

                document.getElementById(\`tab-${t}\`).classList.add('hidden');

                document.getElementById(\`btn-${t}\`).className = "px-4 py-2 rounded-lg font-medium transition text-white hover:bg-white/20";

            });

            document.getElementById(\`tab-${tab}\`).classList.remove('hidden');

            document.getElementById(\`btn-${tab}\`).className = "px-4 py-2 rounded-lg font-medium transition bg-white text-indigo-600 shadow";

            

            if(tab \=== 'listening') renderListening();

            if(tab \=== 'vocab') renderVocab(vocabData);

        }

⁢

        // Render Từ Vựng

        function renderVocab(data) {

            const grid = document.getElementById('vocab-grid');

            grid.innerHTML = data.map(item => \`

                <div class="bg-white p-5 rounded-2xl shadow-sm border border-slate-100 flex flex-col justify-between hover:shadow-md transition">

                    <div>

                        <div class="flex justify-between items-start">

                            <span class="text-3xl">${item.emoji}</span>

                            <button onclick="speakText('${item.word}')" class="p-2 bg-indigo-50 text-indigo-600 rounded-xl hover:bg-indigo-100 transition">🔊 Phát âm</button>

                        </div>

                        <h3 class="text-xl font-bold text-slate-800 mt-3">${item.word}</h3>

                        <p class="text-indigo-500 font-mono text-sm">${item.ipa}</p>

                        <p class="text-slate-600 font-medium mt-1">${item.meaning}</p>

                    </div>

                    <div class="mt-4 pt-3 border-t border-slate-100 text-sm text-slate-500 italic">

                        "${item.example}"

                    </div>

                </div>

            \`).join('');

        }

⁢

        function filterCategory(cat) {

            if(cat \=== 'all') renderVocab(vocabData);

            else renderVocab(vocabData.filter(i => i.category \=== cat));

        }

⁢

        function filterVocab() {

            const keyword = document.getElementById('searchInput').value.toLowerCase();

            renderVocab(vocabData.filter(i => i.word.toLowerCase().includes(keyword) || i.meaning.toLowerCase().includes(keyword)));

        }

⁢

        // Render Luyện Nghe

        function renderListening() {

            const list = document.getElementById('listening-list');

            list.innerHTML = listeningData.map((item, index) => \`

                <div class="p-4 rounded-xl bg-slate-50 border border-slate-200 flex flex-col sm:flex-row justify-between items-start sm:items-center gap-3">

                    <div>

                        <p class="font-semibold text-slate-800 text-lg">${item.text}</p>

                        <p class="text-slate-500 text-sm">${item.meaning}</p>

                    </div>

                    <div class="flex gap-2">

                        <button onclick="speakText('${item.text}', 0.7)" class="px-3 py-1.5 bg-amber-100 text-amber-700 rounded-lg text-sm font-medium hover:bg-amber-200 transition">🐢 Chậm (0.7x)</button>

                        <button onclick="speakText('${item.text}', 1.0)" class="px-3 py-1.5 bg-indigo-600 text-white rounded-lg text-sm font-medium hover:bg-indigo-700 transition">🔊 Chuẩn</button>

                    </div>

                </div>

            \`).join('');

        }

⁢

        // Xử lý Quiz

        let currentQuestion = 0;

        let score = 0;

⁢

        function startQuiz() {

            currentQuestion = 0;

            score = 0;

            document.getElementById('quiz-start-screen').classList.add('hidden');

            document.getElementById('quiz-result-screen').classList.add('hidden');

            document.getElementById('quiz-question-screen').classList.remove('hidden');

            loadQuestion();

        }

⁢

        function loadQuestion() {

            if(currentQuestion >= quizData.length) {

                showQuizResult();

                return;

            }

            const q = quizData\[currentQuestion\];

            document.getElementById('quiz-progress').innerText = \`Câu ${currentQuestion + 1}/${quizData.length}\`;

            document.getElementById('quiz-score').innerText = \`Điểm: ${score}\`;

            document.getElementById('quiz-question').innerText = q.q;

            

            const optionsDiv = document.getElementById('quiz-options');

            optionsDiv.innerHTML = q.options.map((opt, idx) => \`

                <button onclick="selectAnswer(${idx})" class="w-full text-left p-4 rounded-xl border border-slate-200 font-medium hover:bg-indigo-50 hover:border-indigo-500 transition">${opt}</button>

            \`).join('');

        }

⁢

        function selectAnswer(selectedIdx) {

            const q = quizData\[currentQuestion\];

            if(selectedIdx \=== q.correct) {

                score += 20;

            }

            currentQuestion++;

            loadQuestion();

        }

⁢

        function showQuizResult() {

            document.getElementById('quiz-question-screen').classList.add('hidden');

            document.getElementById('quiz-result-screen').classList.remove('hidden');

            document.getElementById('quiz-final-score').innerText = \`Panda đạt được ${score}/100 điểm tuyệt vời! 🎉\`;

        }

⁢

        function resetQuiz() {

            startQuiz();

        }

⁢

        // Chạy mặc định tab đầu tiên

        renderVocab(vocabData);

    </script>

</body>

</html>

⁢