# MWAD-EXP_04-Simple-caluculator
## Date:21-09-2025

## AIM
To  develop a Simple Calculator using React.js with clean and responsive design, ensuring a smooth user experience across different screen sizes.

## ALGORITHM
### STEP 1
Create a React App.

### STEP 2
Open a terminal and run:
  <ul><li>npx create-react-app simple-calculator</li>
  <li>cd simple-calculator</li>
  <li>npm start</li></ul>

### STEP 3
Inside the src/ folder, create a new file Calculator.js and define the basic structure.

### STEP 4
Plan the UI: Display screen, number buttons (0-9), operators (+, -, *, /), clear (C), and equal (=).

### STEP 5
Create a new file Calculator.css in src/ and add the styling.

### STEP 6
Open src/App.js and modify it.

### STEP 7
Start the development server.
  npm start

### STEP 8
Open http://localhost:3000/ in the browser.

### STEP 9
Test the calculator by entering numbers and operations.

### STEP 10
Fix styling issues and refine content placement.

### STEP 11
Deploy the website.

### STEP 12
Upload to GitHub Pages for free hosting.

## PROGRAM

## index.html:
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Advanced Simple Calculator</title>
  <link rel="stylesheet" href="calc.css">
</head>
<body>
  <div class="calculator-container">
    <header>
      <h1>Simple Calculator</h1>
      <p>Built with HTML, CSS & JavaScript</p>
    </header>

    <div class="display">
      <div id="expression">0</div>
      <div id="result">= 0</div>
    </div>

    <div class="buttons">
      <!-- Row 1 -->
      <button class="btn operator" data-value="C">C</button>
      <button class="btn operator" data-value="(">(</button>
      <button class="btn operator" data-value=")">)</button>
      <button class="btn operator" data-value="⌫">⌫</button>

      <!-- Row 2 -->
      <button class="btn" data-value="7">7</button>
      <button class="btn" data-value="8">8</button>
      <button class="btn" data-value="9">9</button>
      <button class="btn operator" data-value="/">÷</button>

      <!-- Row 3 -->
      <button class="btn" data-value="4">4</button>
      <button class="btn" data-value="5">5</button>
      <button class="btn" data-value="6">6</button>
      <button class="btn operator" data-value="*">×</button>

      <!-- Row 4 -->
      <button class="btn" data-value="1">1</button>
      <button class="btn" data-value="2">2</button>
      <button class="btn" data-value="3">3</button>
      <button class="btn operator" data-value="-">−</button>

      <!-- Row 5 -->
      <button class="btn" data-value="0">0</button>
      <button class="btn" data-value=".">.</button>
      <button class="btn operator" data-value="%">%</button>
      <button class="btn operator" data-value="+">+</button>

      <!-- Row 6 -->
      <button class="btn operator" data-value="+/-">+/-</button>
      <button class="btn equal" data-value="=">=</button>
      <button class="btn operator" data-value="ANS">ANS</button>
      <button class="btn operator" data-value="CLR">CLR</button>
    </div>

    <footer>
      <p><strong>Name:Sharon Harshini Reg No:212223040193</strong></p>
    </footer>
  </div>

  <script src="calc.js"></script>
</body>
</html>

```
## styles.css:
```
body {
  font-family: Arial, sans-serif;
  background: linear-gradient(135deg, #f5f7fa, #c3cfe2);
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  margin: 0;
}

.calculator-container {
  background: #fff;
  padding: 20px;
  border-radius: 16px;
  box-shadow: 0 8px 20px rgba(0,0,0,0.2);
  width: 320px;
}

header {
  text-align: center;
  margin-bottom: 15px;
}

header h1 {
  margin: 0;
  font-size: 1.4rem;
}

header p {
  font-size: 0.85rem;
  color: #555;
}

.display {
  background: #111;
  color: #0f0;
  padding: 10px;
  border-radius: 8px;
  margin-bottom: 15px;
  font-family: monospace;
}

#expression {
  font-size: 1.3rem;
  min-height: 28px;
  text-align: right;
}

#result {
  font-size: 0.9rem;
  text-align: right;
  color: #aaa;
}

.buttons {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 10px;
}

.btn {
  padding: 15px;
  font-size: 1.1rem;
  border: none;
  border-radius: 8px;
  background: #f1f1f1;
  cursor: pointer;
  transition: background 0.2s;
}

.btn:hover {
  background: #ddd;
}

.operator {
  background: #ffc107;
}

.operator:hover {
  background: #e0a800;
}

.equal {
  background: #007bff;
  color: #fff;
}

.equal:hover {
  background: #0056b3;
}

footer {
  text-align: center;
  font-size: 0.8rem;
  color: #444;
  margin-top: 15px;
  border-top: 1px solid #eee;
  padding-top: 8px;
}

```
## script.js:
```
let expressionDisplay = document.getElementById("expression");
let resultDisplay = document.getElementById("result");
let buttons = document.querySelectorAll(".btn");

let expression = "";
let lastAnswer = 0;

buttons.forEach(button => {
  button.addEventListener("click", () => {
    let value = button.getAttribute("data-value");

    if (value === "C" || value === "CLR") {
      expression = "";
      resultDisplay.innerText = "= 0";
    } 
    else if (value === "⌫") {
      expression = expression.slice(0, -1);
    } 
    else if (value === "=") {
      try {
        lastAnswer = eval(expression);
        resultDisplay.innerText = "= " + lastAnswer;
      } catch {
        resultDisplay.innerText = "Error";
      }
    } 
    else if (value === "ANS") {
      expression += lastAnswer;
    } 
    else if (value === "+/-") {
      if (expression.startsWith("-")) {
        expression = expression.substring(1);
      } else {
        expression = "-" + expression;
      }
    } 
    else {
      expression += value;
    }

    if (expression === "") {
      expressionDisplay.innerText = "0";
    } else {
      expressionDisplay.innerText = expression;
    }
  });
});

```
## OUTPUT
<img width="1919" height="1063" alt="image" src="https://github.com/user-attachments/assets/20afe0d2-ae23-4cbb-af36-d648e70ef43f" />


## RESULT
The program for developing a simple calculator in React.js is executed successfully.
