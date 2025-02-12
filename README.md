<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Valentine's Quiz</title>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; }
        .container { width: 50%; margin: auto; }
        button { padding: 10px; background: red; color: white; border: none; cursor: pointer; }
    </style>
</head>
<body>
    <div class="container">
        <h2>Valentine's Quiz 💖</h2>
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
            <button type="submit">Submit</button>
        </form>
        <p id="responseMessage"></p>
    </div>

    <script>
        document.getElementById("quizForm").addEventListener("submit", function(event) {
            event.preventDefault();
            const formData = new FormData(this);
            const data = {};
            formData.forEach((value, key) => { data[key] = value; });

            fetch("https://formspree.io/YOUR_EMAIL", { // Replace YOUR_EMAIL with your email
                method: "POST",
                headers: { "Content-Type": "application/json" },
                body: JSON.stringify(data)
            })
            .then(response => response.ok ? "Thank you! ❤️" : "Oops! Something went wrong 😢")
            .then(message => document.getElementById("responseMessage").innerText = message)
            .catch(error => console.error("Error:", error));
        });
    </script>
</body>
</html>
