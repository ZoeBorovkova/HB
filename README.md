С днём рождения


<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Бегающие котики</title>
    <style>
        body {
            background-color: #ffffff;
            overflow: hidden;
            margin: 0;
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
        }
        .cat {
            position: absolute;
            width: 100px;
            height: auto;
        }
    </style>
</head>
<body>
    <script>
        const numCats = 15;
        const cats = [];
        const screenWidth = window.innerWidth;
        const screenHeight = window.innerHeight;
        
        for (let i = 0; i < numCats; i++) {
            let cat = document.createElement("img");
            cat.src = "https://i.pinimg.com/736x/2a/d9/27/2ad9278233e9f4d41d0a7dd92495fdb3--animated-gif-gifs.jpg";
            cat.className = "cat";
            cat.style.top = Math.random() * screenHeight * 0.8 + "px";
            cat.style.left = Math.random() * screenWidth + "px";
            cat.speedX = (Math.random() * 4 + 2) * (Math.random() > 0.5 ? 1 : -1);
            cat.speedY = (Math.random() * 4 + 2) * (Math.random() > 0.5 ? 1 : -1);
            document.body.appendChild(cat);
            cats.push(cat);
        }
        
        function moveCats() {
            cats.forEach(cat => {
                let left = parseFloat(cat.style.left);
                let top = parseFloat(cat.style.top);
                
                left += cat.speedX;
                top += cat.speedY;
                
                if (left > screenWidth || left < 0) {
                    cat.speedX *= -1;
                }
                if (top > screenHeight || top < 0) {
                    cat.speedY *= -1;
                }
                
                cat.style.left = left + "px";
                cat.style.top = top + "px";
            });
            requestAnimationFrame(moveCats);
        }
        
        moveCats();
    </script>
</body>
</html>
