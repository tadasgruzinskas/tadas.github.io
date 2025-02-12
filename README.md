<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Valentine's Quiz 💖</title>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; background-color: #ffe6e6; }
        .container { width: 50%; margin: auto; background: white; padding: 20px; border-radius: 10px; box-shadow: 0px 0px 10px gray; }
        button { padding: 10px; background: red; color: white; border: none; cursor: pointer; font-size: 18px; border-radius: 5px; }
        button:hover { background: darkred; }
        h2 { color: #ff3366; }
        label { font-size: 18px; }
        .success { color: green; font-size: 18px; font-weight: bold; }
    </style>
</head>
<body>
    <div class="container">
        <h2>💘 Valentine's Quiz for You 💘</h2>
        <form id="quizForm">
            <label>What's your favorite flower? 🌸</label><br>
            <input type="radio" name="flower" value="Roses"> Roses 🌹<br>
            <input type="radio" name="flower" value="Tulips"> Tulips 🌷<br>
            <input type="radio" name="flower" value="Lilies"> Lilies 🌼<br>
            <br>
            <label>What's your favorite chocolate? 🍫</label><br>
            <input type="radio" name="chocolate" value="Dark"> Dark Chocolate 🍫<br>
            <input type="radio" name="chocolate" value="Milk"> Milk Chocolate 🍫<br>
            <input type="radio" name="chocolate" value="White"> White Chocolate 🍫<br>
            <br>
            <label>What's your favorite romantic date? ❤️</label><br>
            <input type="radio" name="date" value="Dinner"> Candlelight Dinner 🍽️<br>
            <input type="radio" name="date" value="Beach"> Beach Walk 🌊<br>
            <input type="radio" name="date" value="Movie"> Movie Night 🎬<br>
            <br>
            <button type="submit">Submit 💌</button>
        </form>
        <p id="responseMessage"></p>
    </div>

    <script>
        document.getElementById("quizForm").addEventListener("submit", function(event) {
            event.preventDefault();
            
            const formData = new FormData(this);
            const data = {};
            formData.forEach((value, key) => { data[key] = value; });

            fetch("https://formspree.io/f/mnnjbbez", { // Your Formspree endpoint
                method: "POST",
                headers: { 
                    "Content-Type": "application/json",
                    "Accept": "application/json"
                },
                body: JSON.stringify(data)
            })
            .then(response => response.ok ? "Thank you, my love! ❤️ Your answers have been sent!" : "Oops! Something went wrong 😢")
            .then(message => {
                document.getElementById("responseMessage").innerText = message;
                document.getElementById("responseMessage").className = "success";
            })
            .catch(error => console.error("Error:", error));
        });
    </script>
</body>
</html>
