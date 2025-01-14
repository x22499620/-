<!DOCTYPE html>
<html lang="zh-Hant">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>隨機抽獎產生器</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin: 20px;
        }
        #results {
            margin-top: 20px;
            font-size: 18px;
        }
        .number {
            display: inline-block;
            margin: 5px;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 5px;
            background-color: #f0f8ff;
            font-size: 20px;
        }
        button {
            margin: 10px;
            padding: 10px 20px;
            font-size: 16px;
            cursor: pointer;
        }
    </style>
</head>
<body>
    <h1>隨機抽獎產生器</h1>
    <p>按下按鈕生成 1-75 的隨機號碼</p>
    <button id="generate">抽獎</button>
    <button id="clear">清除結果</button>
    <div id="results"></div>

    <script>
        const generatedNumbers = new Set();
        const maxNumber = 75;

        function generateRandomNumber() {
            if (generatedNumbers.size >= maxNumber) {
                alert("所有號碼都已經抽取完畢！");
                return;
            }

            let number;
            do {
                number = Math.floor(Math.random() * maxNumber) + 1;
            } while (generatedNumbers.has(number));

            generatedNumbers.add(number);
            displayNumber(number);
        }

        function displayNumber(number) {
            const resultsDiv = document.getElementById("results");
            const numberDiv = document.createElement("div");
            numberDiv.className = "number";
            numberDiv.textContent = number;
            resultsDiv.appendChild(numberDiv);
        }

        function clearResults() {
            generatedNumbers.clear();
            const resultsDiv = document.getElementById("results");
            resultsDiv.innerHTML = "";
        }

        document.getElementById("generate").addEventListener("click", generateRandomNumber);
        document.getElementById("clear").addEventListener("click", clearResults);
    </script>
</body>
</html>
