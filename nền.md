<!DOCTYPE html>
<html lang="vi">
<head>
  <meta charset="UTF-8">
  <title>Nền chuyển động phân tử</title>
  <style>
    body, html {
      margin: 0;
      padding: 0;
      overflow: hidden;
      background: #000; /* Nền đen */
    }

    canvas {
      display: block;
    }
  </style>
</head>
<body>
  <canvas id="moleculeCanvas"></canvas>

  <script>
    const canvas = document.getElementById('moleculeCanvas');
    const ctx = canvas.getContext('2d');
    let width, height;

    function resizeCanvas() {
      width = canvas.width = window.innerWidth;
      height = canvas.height = window.innerHeight;
    }

    window.addEventListener('resize', resizeCanvas);
    resizeCanvas();

    const moleculeCount = 100;
    const molecules = [];

    for (let i = 0; i < moleculeCount; i++) {
      molecules.push({
        x: Math.random() * width,
        y: Math.random() * height,
        vx: (Math.random() - 0.5) * 2, // tốc độ x (-1 đến 1)
        vy: (Math.random() - 0.5) * 2, // tốc độ y (-1 đến 1)
        radius: 2 + Math.random() * 2
      });
    }

    function animate() {
      ctx.fillStyle = 'rgba(0, 0, 0, 0.2)'; // tạo hiệu ứng mờ mờ phía sau
      ctx.fillRect(0, 0, width, height);

      for (let i = 0; i < molecules.length; i++) {
        const m = molecules[i];

        m.x += m.vx;
        m.y += m.vy;

        // Va chạm với biên
        if (m.x < 0 || m.x > width) m.vx *= -1;
        if (m.y < 0 || m.y > height) m.vy *= -1;

        // Vẽ phân tử
        ctx.beginPath();
        ctx.arc(m.x, m.y, m.radius, 0, Math.PI * 2);
        ctx.fillStyle = '#00ffff'; // màu cyan
        ctx.fill();
      }

      requestAnimationFrame(animate);
    }

    animate();
  </script>
</body>
</html>
