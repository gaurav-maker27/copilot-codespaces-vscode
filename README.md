<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Birthday Khushi! 🎉</title>
    <style>
        body {
            text-align: center;
            font-family: Arial, sans-serif;
            background-color: #000;
            color: white;
            overflow: hidden;
            position: relative;
        }
        h1 {
            font-size: 50px;
            color: #ffcc00;
            margin-top: 20px;
        }
        p {
            font-size: 24px;
        }
        .wish {
            font-size: 28px;
            font-weight: bold;
            color: #ff4500;
        }
        .boy {
            font-size: 22px;
            margin-top: 20px;
        }
        canvas {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
        }
    </style>
</head>
<body>

    <canvas id="fireworks"></canvas>

    <h1>🎂 Happy Birthday, Khushi! 🎉</h1>
    <p>Wishing you a day filled with love, laughter, and all your favorite things! 💖</p>
    <p class="wish">May all your dreams come true! 🎁</p>
    <p class="boy">With lots of love, <br> ❤️ Your Brother, Gaurav ❤️</p>

    <script>
        // Fireworks Animation
        const canvas = document.getElementById("fireworks");
        const ctx = canvas.getContext("2d");
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        const particles = [];
        function createFirework(x, y) {
            for (let i = 0; i < 50; i++) {
                particles.push({
                    x: x,
                    y: y,
                    size: Math.random() * 5 + 1,
                    speedX: (Math.random() - 0.5) * 4,
                    speedY: (Math.random() - 1.5) * 4,
                    color: `hsl(${Math.random() * 360}, 100%, 50%)`,
                    opacity: 1
                });
            }
        }

        function animate() {
            ctx.fillStyle = "rgba(0, 0, 0, 0.2)";
            ctx.fillRect(0, 0, canvas.width, canvas.height);
            for (let i = 0; i < particles.length; i++) {
                let p = particles[i];
                p.x += p.speedX;
                p.y += p.speedY;
                p.opacity -= 0.02;
                ctx.fillStyle = p.color;
                ctx.globalAlpha = p.opacity;
                ctx.beginPath();
                ctx.arc(p.x, p.y, p.size, 0, Math.PI * 2);
                ctx.fill();
                ctx.globalAlpha = 1;
                if (p.opacity <= 0) {
                    particles.splice(i, 1);
                    i--;
                }
            }
            requestAnimationFrame(animate);
        }

        canvas.addEventListener("click", (e) => {
            createFirework(e.clientX, e.clientY);
        });

        animate();
    </script>

</body>
</html>
