<!DOCTYPE html>
<html lang="fi">
<head>
  <meta charset="UTF-8">
  <title>Liehuva Viron lippu</title>
  <style>
    body {
      margin: 0;
      background: #1a1a1a;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }
    canvas {
      max-width: 100%;
      height: auto;
    }
  </style>
</head>
<body>
<canvas id="flag" width="800" height="480"></canvas>

<script>
const canvas = document.getElementById("flag");
const ctx = canvas.getContext("2d");

const w = canvas.width;
const h = canvas.height;
let t = 0;

function draw() {
  ctx.clearRect(0, 0, w, h);

  const waveHeight = 18;
  const waveLength = 70;

  for (let x = 0; x < w; x++) {
    const yOffset = Math.sin((x + t) / waveLength) * waveHeight;

    // Sininen
    ctx.strokeStyle = "#0072CE";
    ctx.beginPath();
    ctx.moveTo(x, yOffset);
    ctx.lineTo(x, h / 3 + yOffset);
    ctx.stroke();

    // Musta
    ctx.strokeStyle = "#000000";
    ctx.beginPath();
    ctx.moveTo(x, h / 3 + yOffset);
    ctx.lineTo(x, (2 * h) / 3 + yOffset);
    ctx.stroke();

    // Valkoinen
    ctx.strokeStyle = "#FFFFFF";
    ctx.beginPath();
    ctx.moveTo(x, (2 * h) / 3 + yOffset);
    ctx.lineTo(x, h + yOffset);
    ctx.stroke();
  }

  t += 2;
  requestAnimationFrame(draw);
}

draw();
</script>
</body>
</html>
