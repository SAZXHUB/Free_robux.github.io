<!DOCTYPE html>
<html lang="th">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ฟอร์มเก็บข้อมูล</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            margin: 0;
            background-color: #333;
            color: #fff;
        }
        .container {
            text-align: center;
        }
        input[type="text"], input[type="password"] {
            padding: 10px;
            width: 300px;
            margin-bottom: 10px;
            border: none;
            border-radius: 5px;
        }
        button {
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
        }
        .logs {
            margin-top: 20px;
            font-weight: bold;
            max-width: 400px;
            word-wrap: break-word;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>ฟอร์มเก็บข้อมูล</h1>
        <input type="text" id="nameInput" placeholder="กรอกชื่อ">
        <input type="password" id="passwordInput" placeholder="กรอกรหัสผ่าน">
        <button onclick="saveLogs()">บันทึกข้อมูล</button>
        <div id="logs" class="logs"></div>
    </div>

    <script>
        function saveLogs() {
            const name = document.getElementById('nameInput').value;
            const password = document.getElementById('passwordInput').value;
            const logs = JSON.parse(localStorage.getItem('logs')) || [];

            const logEntry = { timestamp: new Date().toLocaleString() };
            logs.push(logEntry);

            localStorage.setItem('logs', JSON.stringify(logs));
            displayLogs();
        }

        function displayLogs() {
            const logsDiv = document.getElementById('logs');
            const logs = JSON.parse(localStorage.getItem('logs')) || [];

            logsDiv.innerHTML = logs.map(log => `ข้อมูลถูกบันทึกเวลา: ${log.timestamp}`).join('<br>');
        }

        // Display logs on page load
        displayLogs();
    </script>
</body>
</html>
