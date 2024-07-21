<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Age Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f0f0f0;
            margin: 0;
        }
        .age-calculator {
            background-color: #fff;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            text-align: center;
        }
        input[type="number"], button {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 5px;
            font-size: 1.2rem;
        }
        button {
            background-color: #007bff;
            color: #fff;
            border: none;
            cursor: pointer;
        }
        button:hover {
            background-color: #0056b3;
        }
        .result {
            font-size: 1.5rem;
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <div class="age-calculator">
        <br/>
        <h1>Age Calculator</h1>
        <input type="number" id="day" placeholder="Day" min="1" max="31">
        <input type="number" id="month" placeholder="Month" min="1" max="12">
        <input type="number" id="year" placeholder="Year" min="1900" max="2100">
        <button onclick="calculateAge()">Calculate Age</button>
        <div class="result" id="result"></div>
    </div>
    <script>
        function calculateAge() {
            var day = parseInt(document.getElementById('day').value);
            var month = parseInt(document.getElementById('month').value);
            var year = parseInt(document.getElementById('year').value);

            if (!day || !month || !year) {
                document.getElementById('result').innerHTML = "Please enter a valid date of birth.";
                return;
            }

            var today = new Date();
            var birthDate = new Date(year, month - 1, day);
            var age = today.getFullYear() - birthDate.getFullYear();
            var monthDifference = today.getMonth() - birthDate.getMonth();

            if (monthDifference < 0 || (monthDifference === 0 && today.getDate() < birthDate.getDate())) {
                age--;
            }

            document.getElementById('result').innerHTML = "Your age is " + age + " years.";
        }
    </script>
</body>
</html>
