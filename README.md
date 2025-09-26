<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Game Komposisi Fungsi - Makanan & Minuman</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background: linear-gradient(135deg, #ffecd2 0%, #fcb69f 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }
        
        .container {
            max-width: 900px;
            width: 100%;
            background-color: rgba(255, 255, 255, 0.9);
            border-radius: 20px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            overflow: hidden;
        }
        
        header {
            background: linear-gradient(to right, #ff9a9e, #fad0c4);
            padding: 20px;
            text-align: center;
            color: #5a3e36;
        }
        
        h1 {
            font-size: 2.5rem;
            margin-bottom: 10px;
            text-shadow: 1px 1px 3px rgba(0, 0, 0, 0.1);
        }
        
        .subtitle {
            font-size: 1.2rem;
            color: #7d5d4f;
        }
        
        .game-area {
            display: flex;
            flex-wrap: wrap;
            padding: 20px;
            gap: 20px;
        }
        
        .info-panel {
            flex: 1;
            min-width: 300px;
            background-color: #fff9f2;
            border-radius: 15px;
            padding: 20px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
        }
        
        .info-panel h2 {
            color: #e67e22;
            margin-bottom: 15px;
            border-bottom: 2px dashed #fad0c4;
            padding-bottom: 10px;
        }
        
        .functions {
            margin-bottom: 20px;
        }
        
        .function {
            background-color: #fff;
            padding: 15px;
            border-radius: 10px;
            margin-bottom: 15px;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.05);
        }
        
        .function h3 {
            color: #e67e22;
            margin-bottom: 10px;
        }
        
        .function-display {
            font-size: 1.5rem;
            text-align: center;
            margin: 10px 0;
            font-family: 'Courier New', monospace;
            color: #5a3e36;
        }
        
        .visualization {
            flex: 2;
            min-width: 300px;
            background-color: #fff9f2;
            border-radius: 15px;
            padding: 20px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
            display: flex;
            flex-direction: column;
        }
        
        .machine {
            display: flex;
            justify-content: space-around;
            align-items: center;
            margin: 20px 0;
            flex-wrap: wrap;
        }
        
        .machine-part {
            text-align: center;
            position: relative;
            margin: 10px;
        }
        
        .machine-box {
            width: 120px;
            height: 120px;
            background: linear-gradient(to bottom, #ff9a9e, #fad0c4);
            border-radius: 15px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            position: relative;
            overflow: hidden;
        }
        
        .machine-box::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            height: 10px;
            background: linear-gradient(to right, #ff9a9e, #fad0c4);
        }
        
        .machine-label {
            margin-top: 10px;
            font-weight: bold;
            color: #5a3e36;
        }
        
        .arrow {
            font-size: 2rem;
            color: #e67e22;
            margin: 0 10px;
        }
        
        .item {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 2rem;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            transition: all 0.5s ease;
            z-index: 10;
        }
        
        .food {
            background-color: #ff9a9e;
            box-shadow: 0 5px 15px rgba(255, 154, 158, 0.5);
        }
        
        .drink {
            background-color: #a1c4fd;
            box-shadow: 0 5px 15px rgba(161, 196, 253, 0.5);
        }
        
        .combo {
            background: linear-gradient(135deg, #ff9a9e 0%, #a1c4fd 100%);
            box-shadow: 0 5px 15px rgba(255, 154, 158, 0.5);
        }
        
        .input-area {
            background-color: #fff;
            padding: 20px;
            border-radius: 15px;
            margin-top: 20px;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.05);
        }
        
        .input-area h3 {
            color: #e67e22;
            margin-bottom: 15px;
        }
        
        .input-group {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            margin-bottom: 15px;
        }
        
        input {
            flex: 1;
            min-width: 150px;
            padding: 12px;
            border: 2px solid #fad0c4;
            border-radius: 8px;
            font-size: 1rem;
            outline: none;
            transition: border-color 0.3s;
        }
        
        input:focus {
            border-color: #ff9a9e;
        }
        
        button {
            background: linear-gradient(to right, #ff9a9e, #fad0c4);
            border: none;
            padding: 12px 25px;
            border-radius: 8px;
            color: #5a3e36;
            font-size: 1rem;
            font-weight: bold;
            cursor: pointer;
            transition: transform 0.3s, box-shadow 0.3s;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.1);
        }
        
        button:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.15);
        }
        
        button:active {
            transform: translateY(0);
        }
        
        .result {
            margin-top: 20px;
            padding: 15px;
            border-radius: 10px;
            text-align: center;
            font-size: 1.2rem;
            min-height: 60px;
            display: flex;
            justify-content: center;
            align-items: center;
            transition: all 0.3s;
        }
        
        .correct {
            background-color: #d4edda;
            color: #155724;
            border: 1px solid #c3e6cb;
        }
        
        .incorrect {
            background-color: #f8d7da;
            color: #721c24;
            border: 1px solid #f5c6cb;
        }
        
        .score-panel {
            display: flex;
            justify-content: space-between;
            margin-top: 20px;
            padding: 15px;
            background-color: #fff;
            border-radius: 10px;
            box-shadow: 0 3px 10px rgba(0, 0, 0, 0.05);
        }
        
        .score-item {
            text-align: center;
        }
        
        .score-value {
            font-size: 1.5rem;
            font-weight: bold;
            color: #e67e22;
        }
        
        .explanation {
            margin-top: 20px;
            padding: 15px;
            background-color: #f8f9fa;
            border-radius: 10px;
            border-left: 5px solid #e67e22;
        }
        
        @media (max-width: 768px) {
            .game-area {
                flex-direction: column;
            }
            
            .machine {
                flex-direction: column;
            }
            
            .arrow {
                transform: rotate(90deg);
                margin: 10px 0;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>Komposisi Fungsi: Makanan & Minuman</h1>
            <p class="subtitle">Belajar matematika dengan cara yang menyenangkan!</p>
        </header>
        
        <div class="game-area">
            <div class="info-panel">
                <h2>Fungsi Makanan & Minuman</h2>
                
                <div class="functions">
                    <div class="function">
                        <h3>Fungsi Makanan (f)</h3>
                        <p>Mengubah minuman (x) menjadi makanan:</p>
                        <div class="function-display" id="function-f">f(x) = 2x + 3</div>
                    </div>
                    
                    <div class="function">
                        <h3>Fungsi Minuman (g)</h3>
                        <p>Mengubah makanan (x) menjadi minuman:</p>
                        <div class="function-display" id="function-g">g(x) = x - 1</div>
                    </div>
                </div>
                
                <div class="explanation">
                    <h3>Apa itu Komposisi Fungsi?</h3>
                    <p>Komposisi fungsi adalah penggabungan dua fungsi, di mana hasil dari fungsi pertama menjadi input untuk fungsi kedua.</p>
                    <p>Contoh: (f ∘ g)(x) = f(g(x))</p>
                </div>
            </div>
            
            <div class="visualization">
                <h2>Mesin Komposisi</h2>
                
                <div class="machine">
                    <div class="machine-part">
                        <div class="machine-box">
                            <div class="item drink" id="input-item">🥤</div>
                        </div>
                        <div class="machine-label">Input (x)</div>
                    </div>
                    
                    <div class="arrow">➡</div>
                    
                    <div class="machine-part">
                        <div class="machine-box">
                            <div class="item drink" id="after-g">🥤</div>
                        </div>
                        <div class="machine-label">Fungsi g</div>
                    </div>
                    
                    <div class="arrow">➡</div>
                    
                    <div class="machine-part">
                        <div class="machine-box">
                            <div class="item food" id="after-f">🍕</div>
                        </div>
                        <div class="machine-label">Fungsi f</div>
                    </div>
                    
                    <div class="arrow">➡</div>
                    
                    <div class="machine-part">
                        <div class="machine-box">
                            <div class="item combo" id="output-item">🍹</div>
                        </div>
                        <div class="machine-label">Output</div>
                    </div>
                </div>
                
                <div class="input-area">
                    <h3>Hitung Komposisi Fungsi</h3>
                    <p id="question">Berapakah nilai dari (f ∘ g)(2)?</p>
                    
                    <div class="input-group">
                        <input type="number" id="answer-input" placeholder="Masukkan jawaban">
                        <button id="check-button">Periksa Jawaban</button>
                    </div>
                    
                    <div class="result" id="result"></div>
                </div>
                
                <div class="score-panel">
                    <div class="score-item">
                        <div>Skor</div>
                        <div class="score-value" id="score">0</div>
                    </div>
                    <div class="score-item">
                        <div>Level</div>
                        <div class="score-value" id="level">1</div>
                    </div>
                    <div class="score-item">
                        <div>Soal</div>
                        <div class="score-value" id="question-count">1/10</div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        // Data fungsi makanan dan minuman
        const functions = [
            { f: "2x + 3", g: "x - 1", fFunc: x => 2*x + 3, gFunc: x => x - 1 },
            { f: "3x - 2", g: "x + 4", fFunc: x => 3*x - 2, gFunc: x => x + 4 },
            { f: "x² + 1", g: "2x", fFunc: x => x*x + 1, gFunc: x => 2*x },
            { f: "4x + 5", g: "x/2", fFunc: x => 4*x + 5, gFunc: x => x/2 },
            { f: "x - 3", g: "x + 7", fFunc: x => x - 3, gFunc: x => x + 7 }
        ];
        
        // Variabel game
        let currentFunctionIndex = 0;
        let currentX = 2;
        let currentComposition = "f∘g"; // atau "g∘f"
        let score = 0;
        let level = 1;
        let questionNumber = 1;
        const totalQuestions = 10;
        
        // Elemen DOM
        const functionFElement = document.getElementById('function-f');
        const functionGElement = document.getElementById('function-g');
        const questionElement = document.getElementById('question');
        const answerInput = document.getElementById('answer-input');
        const checkButton = document.getElementById('check-button');
        const resultElement = document.getElementById('result');
        const scoreElement = document.getElementById('score');
        const levelElement = document.getElementById('level');
        const questionCountElement = document.getElementById('question-count');
        const inputItem = document.getElementById('input-item');
        const afterG = document.getElementById('after-g');
        const afterF = document.getElementById('after-f');
        const outputItem = document.getElementById('output-item');
        
        // Inisialisasi game
        function initGame() {
            updateFunctions();
            updateQuestion();
            updateScorePanel();
            animateVisualization();
        }
        
        // Memperbarui fungsi yang ditampilkan
        function updateFunctions() {
            const func = functions[currentFunctionIndex];
            functionFElement.textContent = `f(x) = ${func.f}`;
            functionGElement.textContent = `g(x) = ${func.g}`;
        }
        
        // Memperbarui pertanyaan
        function updateQuestion() {
            const func = functions[currentFunctionIndex];
            currentX = Math.floor(Math.random() * 10) + 1; // Nilai x antara 1-10
            currentComposition = Math.random() > 0.5 ? "f∘g" : "g∘f";
            
            if (currentComposition === "f∘g") {
                questionElement.textContent = `Berapakah nilai dari (f ∘ g)(${currentX})?`;
            } else {
                questionElement.textContent = `Berapakah nilai dari (g ∘ f)(${currentX})?`;
            }
            
            answerInput.value = '';
            resultElement.textContent = '';
            resultElement.className = 'result';
        }
        
        // Memperbarui panel skor
        function updateScorePanel() {
            scoreElement.textContent = score;
            levelElement.textContent = level;
            questionCountElement.textContent = `${questionNumber}/${totalQuestions}`;
        }
        
        // Animasi visualisasi
        function animateVisualization() {
            // Reset posisi
            inputItem.style.transform = 'translate(-50%, -50%)';
            afterG.style.transform = 'translate(-50%, -50%) scale(0)';
            afterF.style.transform = 'translate(-50%, -50%) scale(0)';
            outputItem.style.transform = 'translate(-50%, -50%) scale(0)';
            
            // Animasi input
            setTimeout(() => {
                inputItem.style.transform = 'translate(-50%, -50%) scale(1.2)';
                setTimeout(() => {
                    inputItem.style.transform = 'translate(-50%, -50%) scale(1)';
                    
                    // Animasi setelah g
                    setTimeout(() => {
                        afterG.style.transform = 'translate(-50%, -50%) scale(1)';
                        
                        // Animasi setelah f
                        setTimeout(() => {
                            afterF.style.transform = 'translate(-50%, -50%) scale(1)';
                            
                            // Animasi output
                            setTimeout(() => {
                                outputItem.style.transform = 'translate(-50%, -50%) scale(1)';
                            }, 500);
                        }, 500);
                    }, 500);
                }, 300);
            }, 300);
        }
        
        // Memeriksa jawaban
        function checkAnswer() {
            const userAnswer = parseFloat(answerInput.value);
            if (isNaN(userAnswer)) {
                resultElement.textContent = "Masukkan jawaban yang valid!";
                resultElement.className = 'result incorrect';
                return;
            }
            
            const func = functions[currentFunctionIndex];
            let correctAnswer;
            
            if (currentComposition === "f∘g") {
                correctAnswer = func.fFunc(func.gFunc(currentX));
            } else {
                correctAnswer = func.gFunc(func.fFunc(currentX));
            }
            
            if (Math.abs(userAnswer - correctAnswer) < 0.001) {
                resultElement.textContent = "Jawaban benar! 🎉";
                resultElement.className = 'result correct';
                score += 10;
                
                // Naik level setiap 30 poin
                if (score >= level * 30) {
                    level++;
                }
            } else {
                resultElement.textContent = `Jawaban salah. Yang benar adalah ${correctAnswer}`;
                resultElement.className = 'result incorrect';
            }
            
            questionNumber++;
            updateScorePanel();
            
            if (questionNumber > totalQuestions) {
                setTimeout(() => {
                    alert(`Permainan selesai! Skor akhir Anda: ${score}`);
                    // Reset game
                    score = 0;
                    level = 1;
                    questionNumber = 1;
                    currentFunctionIndex = 0;
                    updateScorePanel();
                }, 1000);
            } else {
                // Pindah ke fungsi berikutnya
                setTimeout(() => {
                    currentFunctionIndex = (currentFunctionIndex + 1) % functions.length;
                    updateFunctions();
                    updateQuestion();
                    animateVisualization();
                }, 2000);
            }
        }
        
        // Event listener
        checkButton.addEventListener('click', checkAnswer);
        answerInput.addEventListener('keypress', function(e) {
            if (e.key === 'Enter') {
                checkAnswer();
            }
        });
        
        // Mulai game
        initGame();
    </script>
</body>
</html>
