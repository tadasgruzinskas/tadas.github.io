<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Valentine's Day Gift</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #ffe6e6;
            padding: 20px;
        }
        .container {
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.1);
            display: inline-block;
        }
        input, select, button {
            margin: 10px;
            padding: 10px;
            font-size: 16px;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Happy Valentine's Day!</h1>
        <p>Choose your favorite things and pick a date:</p>
        
        <label for="favorite">Your Favorite Thing:</label>
        <select id="favorite">
            <option value="chocolates">Chocolates</option>
            <option value="flowers">Flowers</option>
            <option value="jewelry">Jewelry</option>
            <option value="date-night">Date Night</option>
        </select>
        
        <br>
        <label for="date">Select a Date:</label>
        <input type="date" id="date">
        
        <br>
        <button onclick="submitChoice()">Submit</button>
        
        <p id="result"></p>
    </div>
    
    <script>
        function submitChoice() {
            const favorite = document.getElementById("favorite").value;
            const date = document.getElementById("date").value;
            
            if (!date) {
                alert("Please select a date!");
                return;
            }
            
            document.getElementById("result").innerHTML = `You chose ${favorite} on ${date}! ❤️`;
        }
    </script>
</body>
</html>

