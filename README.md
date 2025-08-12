# baitaptienganh.github.io
Luyện chuyên anh
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Baitap.com - Luyện Viết Lại Câu Nâng Cao</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&family=Press+Start+2P&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background: linear-gradient(135deg, #a7e6ff, #d0b8ff); /* Anime-inspired gradient */
            display: flex;
            justify-content: center;
            align-items: flex-start;
            min-height: 100vh;
            padding: 20px;
            box-sizing: border-box;
            overflow-y: auto; /* Enable scrolling for long content */
        }
        .quiz-container {
            background-color: #ffffff;
            padding: 30px;
            border-radius: 20px; /* More rounded */
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.2); /* Deeper shadow for 3D feel */
            max-width: 800px;
            width: 100%;
            display: flex;
            flex-direction: column;
            gap: 20px;
            transition: all 0.5s ease-in-out;
            border: 3px solid #6c5ce7; /* Purple accent border */
            position: relative;
            z-index: 1;
        }
        .quiz-container::before {
            content: '';
            position: absolute;
            top: -10px;
            left: -10px;
            right: -10px;
            bottom: -10px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 25px;
            z-index: -1;
            filter: blur(8px);
        }
        .quiz-header {
            text-align: center;
            margin-bottom: 20px;
        }
        .quiz-header h1 {
            font-family: 'Press Start 2P', cursive; /* Retro game font */
            color: #6c5ce7; /* Purple */
            font-size: 2.5rem;
            text-shadow: 3px 3px 0 #ff79c6; /* Pink shadow */
            margin-bottom: 10px;
            animation: bounceIn 1s ease-out;
        }
        .quiz-header p {
            color: #4a4a68;
            font-size: 1.1rem;
        }
        .question-box {
            background-color: #f7f9fb; /* Lighter background */
            padding: 25px;
            border-radius: 15px;
            margin-bottom: 15px;
            box-shadow: inset 0 3px 8px rgba(0, 0, 0, 0.1); /* Subtle inner shadow */
            border: 1px solid #e0e6ed;
            position: relative;
            animation: fadeIn 0.8s ease-out;
        }
        .question-text {
            font-size: 1.15rem;
            margin-bottom: 12px;
            color: #2c3e50;
            line-height: 1.6;
        }
        .input-area {
            display: flex;
            flex-direction: column;
            gap: 10px;
        }
        input[type="text"] {
            padding: 14px 18px;
            border: 2px solid #a7d9f7;
            border-radius: 10px; /* More rounded input */
            font-size: 1.05rem;
            width: 100%;
            box-sizing: border-box;
            transition: border-color 0.3s ease, box-shadow 0.3s ease;
            background-color: #fcfdff;
            color: #333;
        }
        input[type="text"]:focus {
            outline: none;
            border-color: #ff79c6; /* Pink on focus */
            box-shadow: 0 0 0 4px rgba(255, 121, 198, 0.3);
        }
        .action-buttons {
            display: flex;
            gap: 20px; /* Increased gap */
            justify-content: center;
            margin-top: 20px;
        }
        button {
            padding: 14px 30px; /* Larger buttons */
            border-radius: 10px; /* More rounded buttons */
            font-size: 1.1rem;
            font-weight: 700;
            cursor: pointer;
            transition: background-color 0.3s ease, transform 0.2s ease, box-shadow 0.3s ease;
            box-shadow: 0 6px 15px rgba(0, 0, 0, 0.15); /* Stronger shadow */
            position: relative;
            overflow: hidden;
        }
        button:active {
            transform: translateY(1px);
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
        }
        button.primary {
            background-color: #8be9fd; /* Cyan */
            color: #282a36; /* Dark */
            border: none;
        }
        button.primary:hover:not(:disabled) {
            background-color: #62d8f7;
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.25);
        }
        button.secondary {
            background-color: #ff79c6; /* Pink */
            color: white;
            border: none;
        }
        button.secondary:hover:not(:disabled) {
            background-color: #e65fa8;
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.25);
        }
        button:disabled {
            opacity: 0.5;
            cursor: not-allowed;
            box-shadow: 0 3px 8px rgba(0, 0, 0, 0.1);
        }
        .feedback-area {
            margin-top: 20px;
            padding: 18px;
            border-radius: 12px;
            font-size: 1.05rem;
            line-height: 1.6;
            font-weight: 600;
            text-align: center;
            animation: fadeIn 0.5s ease-out;
        }
        .feedback-correct {
            background-color: #e6ffe6;
            color: #27ae60;
            border: 2px solid #27ae60;
        }
        .feedback-incorrect {
            background-color: #ffe6e6;
            color: #e74c3c;
            border: 2px solid #e74c3c;
        }
        .explanation {
            margin-top: 15px;
            font-size: 1rem;
            color: #555;
            background-color: #f7f9fb;
            padding: 20px;
            border-radius: 12px;
            border-left: 5px solid #bd93f9; /* Lavender accent */
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
            animation: slideInUp 0.6s ease-out;
        }
        .explanation strong {
            color: #6c5ce7; /* Purple for emphasis */
        }
        .score-display {
            text-align: center;
            font-size: 1.3rem;
            font-weight: 700;
            color: #4a4a68;
            margin-top: 20px;
        }
        .final-message {
            text-align: center;
            font-size: 1.5rem;
            font-weight: 700;
            color: #27ae60;
            animation: tada 1s ease-out;
        }
        .fill-in-the-blank {
            font-weight: bold;
            color: #e74c3c;
            transition: color 0.3s ease;
        }
        .ask-ai-section {
            margin-top: 30px; /* More spacing */
            padding: 25px;
            background-color: #effaff; /* Very light blue */
            border-radius: 15px;
            border: 2px solid #8be9fd; /* Cyan border */
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
            animation: fadeIn 0.8s ease-out;
        }
        .ask-ai-section h3 {
            font-family: 'Press Start 2P', cursive;
            font-size: 1.1rem;
            font-weight: 600;
            color: #6c5ce7;
            margin-bottom: 15px;
            text-align: center;
            text-shadow: 1px 1px 0 #ff79c6;
        }
        textarea {
            width: 100%;
            padding: 12px 15px;
            border: 2px solid #8be9fd; /* Cyan border */
            border-radius: 10px;
            font-size: 1rem;
            min-height: 90px;
            box-sizing: border-box;
            resize: vertical;
            transition: border-color 0.3s ease, box-shadow 0.3s ease;
            background-color: #fcfdff;
            color: #333;
        }
        textarea:focus {
            outline: none;
            border-color: #ff79c6;
            box-shadow: 0 0 0 4px rgba(255, 121, 198, 0.3);
        }
        .ai-response {
            margin-top: 18px;
            padding: 18px;
            background-color: #f5faff; /* Lighter background for response */
            border-radius: 12px;
            border: 1px solid #c8e1f5;
            color: #333;
            line-height: 1.6;
            box-shadow: inset 0 2px 5px rgba(0, 0, 0, 0.05);
            font-style: italic;
            animation: fadeIn 0.6s ease-out;
        }
        .loading-indicator {
            text-align: center;
            margin-top: 10px;
            font-style: italic;
            color: #555;
            animation: pulse 1.5s infinite;
        }
        .question-progress {
            text-align: center;
            font-size: 1.05rem;
            color: #777;
            margin-top: 5px;
            font-weight: 600;
        }

        /* Keyframe Animations */
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }
        @keyframes slideInUp {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        @keyframes bounceIn {
            0%, 20%, 40%, 60%, 80%, 100% {
                transition-timing-function: cubic-bezier(0.215, 0.610, 0.355, 1.000);
            }
            0% { opacity: 0; transform: scale3d(0.3, 0.3, 0.3); }
            20% { transform: scale3d(1.1, 1.1, 1.1); }
            40% { transform: scale3d(0.9, 0.9, 0.9); }
            60% { opacity: 1; transform: scale3d(1.03, 1.03, 1.03); }
            80% { transform: scale3d(0.97, 0.97, 0.97); }
            100% { opacity: 1; transform: scale3d(1, 1, 1); }
        }
        @keyframes tada {
            from {
                transform: scale3d(1, 1, 1);
            }

            10%, 20% {
                transform: scale3d(0.9, 0.9, 0.9) rotate3d(0, 0, 1, -3deg);
            }

            30%, 50%, 70%, 90% {
                transform: scale3d(1.1, 1.1, 1.1) rotate3d(0, 0, 1, 3deg);
            }

            40%, 60%, 80% {
                transform: scale3d(1.1, 1.1, 1.1) rotate3d(0, 0, 1, -3deg);
            }

            to {
                transform: scale3d(1, 1, 1);
            }
        }
        @keyframes pulse {
            0% { opacity: 1; }
            50% { opacity: 0.6; }
            100% { opacity: 1; }
        }

        /* Responsive adjustments */
        @media (max-width: 768px) {
            .quiz-container {
                padding: 20px;
                margin: 10px;
            }
            .quiz-header h1 {
                font-size: 2rem;
            }
            .question-text {
                font-size: 1rem;
            }
            input[type="text"], textarea {
                font-size: 0.95rem;
                padding: 10px 12px;
            }
            .action-buttons {
                flex-direction: column;
                gap: 10px;
            }
            button {
                width: 100%;
                font-size: 1rem;
                padding: 10px 15px;
            }
            .feedback-area, .explanation, .ask-ai-section {
                padding: 15px;
            }
            .final-message {
                font-size: 1.2rem;
            }
        }
    </style>
</head>
<body>
    <div class="quiz-container">
        <div class="quiz-header">
            <h1>Baitap.com</h1>
            <p>Khám phá thế giới ngữ pháp cùng AI!</p>
            <p class="text-lg font-semibold text-purple-700 mt-2">Bài Tập Viết Lại Câu Nâng Cao (HSGQG - Phần 2)</p>
            <p class="text-gray-600 text-sm">Mức độ B2-C2, tập trung vào Idiom, Phrasal Verb và cấu trúc khó.</p>
        </div>

        <div class="score-display">
            Điểm: <span id="score">0</span> / <span id="total-questions-overall">0</span>
        </div>
        <div class="question-progress">
            Câu <span id="current-question-number">1</span> / <span id="total-questions-in-part">20</span>
        </div>

        <div class="question-box">
            <p class="question-text" id="original-sentence"></p>
            <p class="question-text">
                **Viết lại:** <span id="transformed-prefix"></span><span class="fill-in-the-blank">..................................................</span><span id="transformed-suffix"></span>
            </p>
            <div class="input-area">
                <input type="text" id="user-answer" placeholder="Nhập câu trả lời của bạn vào đây..." autocomplete="off">
            </div>
        </div>

        <div class="action-buttons">
            <button id="check-btn" class="primary">Kiểm tra</button>
            <button id="next-btn" class="secondary" disabled>Câu tiếp theo</button>
        </div>

        <div id="feedback-area" class="feedback-area hidden"></div>
        <div id="explanation-area" class="explanation hidden"></div>

        <div id="ask-ai-section" class="ask-ai-section">
            <h3>✨ Bạn có câu hỏi gì không? ✨</h3>
            <textarea id="ai-question-input" placeholder="Gõ câu hỏi của bạn về câu này vào đây (ví dụ: 'Tại sao lại dùng 'such' ở đây?', 'Giải thích idiom này?')..."></textarea>
            <button id="ask-ai-btn" class="primary w-full mt-3">Hỏi AI</button>
            <div id="ai-response-area" class="ai-response hidden"></div>
            <div id="loading-indicator" class="loading-indicator hidden">Đang tải câu trả lời...</div>
        </div>

        <div id="final-message" class="final-message hidden"></div>
    </div>

    <script>
        // Array of quiz questions (Part 2: Questions 21-40)
        const questions = [
            {
                originalSentence: "It's a waste of time to try and persuade him; he won't change his mind.",
                transformedPrefix: "There's no ",
                transformedSuffix: " him; he won't change his mind.",
                correctAnswer: "point in trying to persuade",
                explanation: "Cấu trúc 'There's no point in doing something' có nghĩa là 'Thật vô ích khi làm gì đó'. Đây là một collocation rất hữu ích."
            },
            {
                originalSentence: "The problem was so complicated that the experts couldn't solve it.",
                transformedPrefix: "Such was the ",
                transformedSuffix: " that the experts couldn't solve it.",
                correctAnswer: "complexity of the problem",
                explanation: "Đây là cấu trúc đảo ngữ với 'Such'. Cấu trúc: 'Such + be + Noun Phrase + that...'. 'Complexity of the problem' là cụm danh từ để thay thế cho 'so complicated', nhấn mạnh mức độ phức tạp."
            },
            {
                originalSentence: "You should not tell anyone about our secret plan under any circumstances.",
                transformedPrefix: "Under no ",
                transformedSuffix: " tell anyone about our secret plan.",
                correctAnswer: "circumstances should you",
                explanation: "Đây là cấu trúc đảo ngữ với 'Under no circumstances'. Cấu trúc: 'Under no circumstances + trợ động từ + S + V...'. Nó mang nghĩa 'không trong bất cứ hoàn cảnh nào'."
            },
            {
                originalSentence: "I think you should apologize for your rude comments.",
                transformedPrefix: "If I ",
                transformedSuffix: ", I would apologize for your rude comments.",
                correctAnswer: "were you",
                explanation: "Đây là câu điều kiện loại 2 dùng để đưa ra lời khuyên hoặc gợi ý. Cấu trúc 'If I were you, I would...' là cách diễn đạt phổ biến."
            },
            {
                originalSentence: "His behavior was so unpredictable that we never knew what to expect.",
                transformedPrefix: "So unpredictable ",
                transformedSuffix: " that we never knew what to expect.",
                correctAnswer: "was his behavior",
                explanation: "Đây là cấu trúc đảo ngữ với 'So + tính từ'. Cấu trúc: 'So + tính từ + be + Chủ ngữ + that...'. Nó được dùng để nhấn mạnh tính chất của chủ ngữ."
            },
            {
                originalSentence: "She didn't want to get involved in their argument.",
                transformedPrefix: "She wanted to steer ",
                transformedSuffix: " of their argument.",
                correctAnswer: "clear",
                explanation: "Idiom 'steer clear of something' có nghĩa là 'tránh xa, không dính líu đến cái gì đó'. Nó thể hiện ý muốn giữ khoảng cách, không muốn vướng vào rắc rối."
            },
            {
                originalSentence: "It is essential that all students submit their assignments by Friday.",
                transformedPrefix: "It is of the ",
                transformedSuffix: " that all students submit their assignments by Friday.",
                correctAnswer: "utmost importance",
                explanation: "Cấu trúc nhấn mạnh 'It is of the utmost importance that...' tương đương với 'It is essential that...'. Sau đó là mệnh đề với động từ ở dạng nguyên thể (subjunctive mood) để diễn tả sự bắt buộc, quan trọng."
            },
            {
                originalSentence: "I really regret not having studied harder for the exam.",
                transformedPrefix: "If only ",
                transformedSuffix: " harder for the exam.",
                correctAnswer: "I had studied",
                explanation: "Cấu trúc 'If only + S + Past Perfect' được dùng để diễn tả sự hối tiếc về một điều gì đó đã xảy ra (hoặc không xảy ra) trong quá khứ."
            },
            {
                originalSentence: "The new regulations will be implemented next month.",
                transformedPrefix: "The new regulations will come ",
                transformedSuffix: " next month.",
                correctAnswer: "into effect",
                explanation: "Collocation 'come into effect' có nghĩa là 'bắt đầu có hiệu lực', tương đương với 'be implemented'. Đây là một cụm từ rất phổ biến trong các văn bản pháp lý, quy định."
            },
            {
                originalSentence: "He is very likely to win the competition.",
                transformedPrefix: "He stands a ",
                transformedSuffix: " of winning the competition.",
                correctAnswer: "good chance",
                explanation: "Idiom 'stand a good chance of doing something' có nghĩa là 'có khả năng cao làm được việc gì đó'. Nó diễn tả sự lạc quan về một kết quả tích cực."
            },
            {
                originalSentence: "His behavior was so strange that I began to get worried.",
                transformedPrefix: "His strange behavior set ",
                transformedSuffix: " for me.",
                correctAnswer: "alarm bells ringing",
                explanation: "Idiom 'set alarm bells ringing' có nghĩa là 'làm ai đó lo lắng, cảnh giác vì có điều gì đó không ổn'. Nó mô tả một tình huống gây ra sự bất an."
            },
            {
                originalSentence: "The government's proposal has been criticized by many people.",
                transformedPrefix: "There has been a great ",
                transformedSuffix: " of the government's proposal.",
                correctAnswer: "deal of criticism",
                explanation: "Để viết lại câu này bằng cách dùng danh từ 'criticism', chúng ta dùng 'a great deal of' có nghĩa là 'rất nhiều'. Đây là một collocation thường dùng với các danh từ không đếm được."
            },
            {
                originalSentence: "She is famous for her ability to solve complex problems.",
                transformedPrefix: "She has a ",
                transformedSuffix: " for solving complex problems.",
                correctAnswer: "reputation",
                explanation: "Collocation 'have a reputation for doing something' có nghĩa là 'nổi tiếng về việc gì'. Nó thể hiện danh tiếng hoặc uy tín của một người."
            },
            {
                originalSentence: "I didn't know that he was the CEO of the company.",
                transformedPrefix: "Little ",
                transformedSuffix: " that he was the CEO of the company.",
                correctAnswer: "did I know",
                explanation: "Đây là cấu trúc đảo ngữ với 'Little'. Cấu trúc: 'Little + trợ động từ + S + V...'. Nó được dùng để nhấn mạnh sự ngạc nhiên, không biết trước một điều gì đó."
            },
            {
                originalSentence: "He finally admitted that he had made a mistake.",
                transformedPrefix: "He finally owned ",
                transformedSuffix: " that he had made a mistake.",
                correctAnswer: "up to the fact",
                explanation: "Phrasal verb 'own up to something' có nghĩa là 'thú nhận, thừa nhận' điều gì đó sai trái. 'The fact that...' là một cấu trúc phổ biến theo sau khi bạn muốn làm rõ sự thật đó."
            },
            {
                originalSentence: "You must do exactly what the manager tells you.",
                transformedPrefix: "You must carry ",
                transformedSuffix: " instructions exactly.",
                correctAnswer: "out the manager's",
                explanation: "Phrasal verb 'carry out something' có nghĩa là 'thực hiện, thi hành' (thường dùng cho các mệnh lệnh, chỉ thị, kế hoạch). Nó thay thế cho 'do'."
            },
            {
                originalSentence: "The project was not successful because of a lack of communication.",
                transformedPrefix: "The project fell ",
                transformedSuffix: " because of a lack of communication.",
                correctAnswer: "through",
                explanation: "Phrasal verb 'fall through' có nghĩa là 'thất bại, không thành công' (thường dùng cho kế hoạch, dự án, thỏa thuận). Nó ngụ ý rằng một điều gì đó đã không đi đến đích như mong đợi."
            },
            {
                originalSentence: "It's very important for you to be on time for the interview.",
                transformedPrefix: "It is of the ",
                transformedSuffix: " that you be on time for the interview.",
                correctAnswer: "utmost importance",
                explanation: "Tương tự như câu 27, đây là một cấu trúc nhấn mạnh sự quan trọng, cần thiết. 'Utmost importance' là collocation cố định."
            },
            {
                originalSentence: "He is not a very good liar; you can always tell when he's not being honest.",
                transformedPrefix: "He is a ",
                transformedSuffix: "; you can always tell when he's not being honest.",
                correctAnswer: "bad liar",
                explanation: "Đây là một cách diễn đạt trực tiếp để chỉ người nói dối không giỏi. Kiểm tra khả năng nhận biết collocation đơn giản."
            },
            {
                originalSentence: "She was the only one who didn't approve of the plan.",
                transformedPrefix: "Everyone approved of the plan ",
                transformedSuffix: " her.",
                correctAnswer: "apart from",
                explanation: "'Apart from' là một giới từ có nghĩa là 'ngoại trừ'. Nó đồng nghĩa với 'except for' và thường được dùng để chỉ ra một ngoại lệ."
            }
        ];

        let currentQuestionIndex = 0;
        let score = 0;

        const originalSentenceEl = document.getElementById('original-sentence');
        const transformedPrefixEl = document.getElementById('transformed-prefix');
        const transformedSuffixEl = document.getElementById('transformed-suffix');
        const userAnswerEl = document.getElementById('user-answer');
        const checkBtn = document.getElementById('check-btn');
        const nextBtn = document.getElementById('next-btn');
        const feedbackArea = document.getElementById('feedback-area');
        const explanationArea = document.getElementById('explanation-area');
        const scoreDisplay = document.getElementById('score');
        const totalQuestionsOverallDisplay = document.getElementById('total-questions-overall'); // Overall total
        const finalMessageEl = document.getElementById('final-message');
        const fillInTheBlankEl = document.querySelector('.fill-in-the-blank');
        const currentQuestionNumberEl = document.getElementById('current-question-number');
        const totalQuestionsInPartEl = document.getElementById('total-questions-in-part'); // Total in current part

        const askAiSection = document.getElementById('ask-ai-section');
        const aiQuestionInput = document.getElementById('ai-question-input');
        const askAiBtn = document.getElementById('ask-ai-btn');
        const aiResponseArea = document.getElementById('ai-response-area');
        const loadingIndicator = document.getElementById('loading-indicator');

        // Function to display the current question
        function displayQuestion() {
            if (currentQuestionIndex < questions.length) {
                const q = questions[currentQuestionIndex];
                originalSentenceEl.textContent = "Câu gốc: " + q.originalSentence;
                transformedPrefixEl.textContent = q.transformedPrefix;
                transformedSuffixEl.textContent = q.transformedSuffix;
                userAnswerEl.value = '';
                feedbackArea.classList.add('hidden');
                explanationArea.classList.add('hidden');
                checkBtn.disabled = false;
                nextBtn.disabled = true;
                fillInTheBlankEl.textContent = '..................................................';
                fillInTheBlankEl.style.color = '#e74c3c';
                userAnswerEl.focus();

                askAiSection.classList.remove('hidden'); // Ensure AI section is visible
                aiQuestionInput.value = '';
                aiResponseArea.classList.add('hidden');
                loadingIndicator.classList.add('hidden');

                currentQuestionNumberEl.textContent = currentQuestionIndex + 1;
                totalQuestionsInPartEl.textContent = questions.length; // Number of questions in this part
                totalQuestionsOverallDisplay.textContent = questions.length; // For the "Score" line
            } else {
                originalSentenceEl.textContent = "🎉 Bạn đã hoàn thành phần này! 🎉";
                transformedPrefixEl.textContent = "";
                transformedSuffixEl.textContent = "";
                userAnswerEl.style.display = 'none';
                checkBtn.style.display = 'none';
                nextBtn.style.display = 'none';
                feedbackArea.classList.add('hidden');
                explanationArea.classList.add('hidden');
                askAiSection.style.display = 'none';
                finalMessageEl.classList.remove('hidden');
                finalMessageEl.textContent = `Tuyệt vời! Bạn đã hoàn thành phần này với ${score} trên ${questions.length} câu đúng! Hãy sẵn sàng cho phần tiếp theo nhé!`;
            }
            updateScoreDisplay();
        }

        // Function to update score display
        function updateScoreDisplay() {
            scoreDisplay.textContent = score;
            totalQuestionsOverallDisplay.textContent = questions.length;
        }

        // Function to check user's answer
        function checkAnswer() {
            const userAnswer = userAnswerEl.value.trim().toLowerCase();
            const correctAnswer = questions[currentQuestionIndex].correctAnswer.toLowerCase();
            const explanation = questions[currentQuestionIndex].explanation;

            feedbackArea.classList.remove('hidden');
            explanationArea.classList.remove('hidden');

            if (userAnswer === correctAnswer) {
                feedbackArea.textContent = 'Chính xác! 🎉';
                feedbackArea.className = 'feedback-area feedback-correct';
                score++;
            } else {
                feedbackArea.textContent = 'Chưa đúng. 😕';
                feedbackArea.className = 'feedback-area feedback-incorrect';
            }
            
            explanationArea.innerHTML = `**Đáp án đúng:** ${questions[currentQuestionIndex].correctAnswer}<br>${explanation}`;
            
            fillInTheBlankEl.textContent = questions[currentQuestionIndex].correctAnswer;
            fillInTheBlankEl.style.color = feedbackArea.classList.contains('feedback-correct') ? '#27ae60' : '#e74c3c';

            checkBtn.disabled = true;
            nextBtn.disabled = false;
            updateScoreDisplay();
        }

        // Function to call LLM for explanation
        async function askAI() {
            const userQuestion = aiQuestionInput.value.trim();
            if (!userQuestion) {
                aiResponseArea.classList.remove('hidden');
                aiResponseArea.textContent = "Vui lòng nhập câu hỏi của bạn!";
                aiResponseArea.className = 'ai-response feedback-incorrect';
                return;
            }

            loadingIndicator.classList.remove('hidden');
            aiResponseArea.classList.add('hidden');
            aiResponseArea.textContent = '';
            askAiBtn.disabled = true;

            const currentQuestion = questions[currentQuestionIndex];
            const prompt = `Tôi đang làm bài tập viết lại câu nâng cao.
            Đây là câu gốc: "${currentQuestion.originalSentence}"
            Đây là phần câu đã viết lại: "${currentQuestion.transformedPrefix} ... ${currentQuestion.transformedSuffix}"
            Đây là đáp án đúng: "${currentQuestion.correctAnswer}"
            Đây là giải thích của hệ thống: "${currentQuestion.explanation}"
            Câu hỏi của tôi về câu này là: "${userQuestion}"
            Hãy giải thích chi tiết và rõ ràng cho câu hỏi của tôi, tập trung vào ngữ cảnh thi HSGQG.`;

            let chatHistory = [];
            chatHistory.push({ role: "user", parts: [{ text: prompt }] });
            const payload = { contents: chatHistory };
            const apiKey = "";
            const apiUrl = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-05-20:generateContent?key=${apiKey}`;

            let retries = 0;
            const MAX_RETRIES = 5;
            let delay = 1000;

            while (retries < MAX_RETRIES) {
                try {
                    const response = await fetch(apiUrl, {
                        method: 'POST',
                        headers: { 'Content-Type': 'application/json' },
                        body: JSON.stringify(payload)
                    });

                    if (response.status === 429) {
                        retries++;
                        await new Promise(res => setTimeout(res, delay));
                        delay *= 2;
                        continue;
                    }

                    const result = await response.json();
                    if (result.candidates && result.candidates.length > 0 &&
                        result.candidates[0].content && result.candidates[0].content.parts &&
                        result.candidates[0].content.parts.length > 0) {
                        const text = result.candidates[0].content.parts[0].text;
                        aiResponseArea.classList.remove('hidden');
                        aiResponseArea.textContent = text;
                        aiResponseArea.className = 'ai-response';
                    } else {
                        aiResponseArea.classList.remove('hidden');
                        aiResponseArea.textContent = 'Rất tiếc, không thể lấy được câu trả lời. Vui lòng thử lại sau.';
                        aiResponseArea.className = 'ai-response feedback-incorrect';
                    }
                    break;
                } catch (error) {
                    retries++;
                    if (retries < MAX_RETRIES) {
                        await new Promise(res => setTimeout(res, delay));
                        delay *= 2;
                    } else {
                        aiResponseArea.classList.remove('hidden');
                        aiResponseArea.textContent = `Đã xảy ra lỗi khi gọi AI: ${error.message}. Vui lòng thử lại sau.`;
                        aiResponseArea.className = 'ai-response feedback-incorrect';
                    }
                }
            }

            loadingIndicator.classList.add('hidden');
            askAiBtn.disabled = false;
        }

        // Event listeners for buttons
        checkBtn.addEventListener('click', checkAnswer);
        nextBtn.addEventListener('click', () => {
            currentQuestionIndex++;
            displayQuestion();
        });
        askAiBtn.addEventListener('click', askAI);

        // Allow pressing Enter to check answer
        userAnswerEl.addEventListener('keypress', (event) => {
            if (event.key === 'Enter' && !checkBtn.disabled) {
                checkAnswer();
            } else if (event.key === 'Enter' && !nextBtn.disabled) {
                currentQuestionIndex++;
                displayQuestion();
            }
        });

        // Initialize quiz
        displayQuestion();
    </script>
</body>
</html>
