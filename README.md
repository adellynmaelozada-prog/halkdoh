<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lozada's Hub</title>
    <style>
        
        body, html {
            height: 100%;
            margin: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            color: #fff; 
            background-color: #0d1117; 
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            overflow: hidden;
            position: relative; 
        }

        body::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(45deg, #ff10f0, #f535aa, #36f57f); 
            background-size: 400% 400%;
            animation: neon-animation 20s ease infinite; 
            z-index: -1; 
            filter: blur(100px); 
            opacity: 0.7; 
        }

        @keyframes neon-animation {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        h1 {
            font-size: 5em;
            text-shadow: 0 0 10px #fff, 0 0 20px #fff, 0 0 40px #ff10f0, 0 0 80px #ff10f0; 
            animation: neon-text-flicker 2s ease-in-out infinite alternate;
            margin-bottom: 20px;
        }

        @keyframes neon-text-flicker {
            from { text-shadow: 0 0 10px #fff, 0 0 20px #fff, 0 0 40px #ff10f0, 0 0 80px #ff10f0; }
            to { text-shadow: 0 0 20px #fff, 0 0 30px #ff10f0, 0 0 60px #ff10f0, 0 0 100px #ff10f0; }
        }

        .calculator {
            padding: 20px;
            background: rgba(0, 0, 0, 0.5);
            border-radius: 10px;
            border: 2px solid #ff10f0;
            box-shadow: 0 0 20px #ff10f0, inset 0 0 10px #ff10f0;
            z-index: 1;
            backdrop-filter: blur(5px);
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 10px;
            max-width: 320px;
        }
        
        .calculator .display {
            grid-column: 1 / -1; 
            background: rgba(255, 255, 255, 0.1);
            color: #ffffff;
            padding: 15px;
            font-size: 2em;
            text-align: right;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: inset 0 0 10px #000;
            text-shadow: 0 0 5px #ff10f0;
        }
        
       
        .calculator button {
            padding: 20px;
            font-size: 1.5em;
            background: rgba(255, 255, 255, 0.1);
            color: #ffffff;
            border: 1px solid rgba(255, 255, 255, 0.2);
            border-radius: 8px;
            cursor: pointer;
            box-shadow: 0 0 5px #ff10f0, inset 0 0 5px #ee87e7;
            transition: all 0.2s ease;
        }
        
        .calculator button:hover {
            background: rgba(255, 255, 255, 0.2);
            box-shadow: 0 0 15px #ff10f0, inset 0 0 10px #ff10f0;
        }
        
        .calculator .operator {
            background-color: #ff10f0;
            color: #0d1117;
            text-shadow: none;
            box-shadow: 0 0 5px #ff10f0;
        }
        
        .calculator .operator:hover {
            background-color: #f535aa;
            box-shadow: 0 0 15px #ff10f0;
        }
        
        .calculator .equals {
            grid-column: span 2;
            background-color: #36f57f;
            color: #0d1117;
            text-shadow: none;
            box-shadow: 0 0 5px #36f57f;
        }
        
        .calculator .equals:hover {
            background-color: #2ecf6b;
            box-shadow: 0 0 15px #36f57f;
        }

        footer {
            margin-top: 40px;
            z-index: 1;
        }
    </style>
</head>
<body>

    <header>
        <h1>Lozada's Hub</h1>
    </header>

    <main>
        <div class="calculator">
            <div class="display" id="display">0</div>
            <button class="operator" onclick="clearDisplay()">C</button>
            <button class="operator" onclick="deleteLast()">DEL</button>
            <button class="operator" onclick="appendToDisplay('/')">/</button>
            <button class="operator" onclick="appendToDisplay('*')">*</button>
            
            <button onclick="appendToDisplay('7')">7</button>
            <button onclick="appendToDisplay('8')">8</button>
            <button onclick="appendToDisplay('9')">9</button>
            <button class="operator" onclick="appendToDisplay('-')">-</button>
            
            <button onclick="appendToDisplay('4')">4</button>
            <button onclick="appendToDisplay('5')">5</button>
            <button onclick="appendToDisplay('6')">6</button>
            <button class="operator" onclick="appendToDisplay('+')">+</button>
            
            <button onclick="appendToDisplay('1')">1</button>
            <button onclick="appendToDisplay('2')">2</button>
            <button onclick="appendToDisplay('3')">3</button>
            <button onclick="appendToDisplay('.')">.</button>
            
            <button onclick="appendToDisplay('0')">0</button>
            <button class="equals" onclick="calculateResult()">=</button>
        </div>
    </main>

    <footer>
        <p>&copy; 2025 Lozada's Hub</p>
    </footer>
    
    <script>
        const display = document.getElementById('display');
        
        function appendToDisplay(input) {
            if (display.innerText === '0' && input !== '.') {
                display.innerText = input;
            } else {
                display.innerText += input;
            }
        }
        
        function clearDisplay() {
            display.innerText = '0';
        }
        
        function deleteLast() {
            if (display.innerText.length > 1) {
                display.innerText = display.innerText.slice(0, -1);
            } else {
                display.innerText = '0';
            }
        }
        
        function calculateResult() {
            try {
                display.innerText = eval(display.innerText);
            } catch (error) {
                display.innerText = 'Error';
            }
        }
    </script>
</body>
</html>
