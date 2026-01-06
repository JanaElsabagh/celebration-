<html>
<head>
<title>Celebration</title>
<style>
body {
  display:flex;
  justify-content:center;
  align-items:center;
  height:100vh;
  font-family:Arial;
  font-size:28px;
  background:white;
  overflow:hidden;
  margin:0;
}
p {
  z-index:10;
  position:relative;
}
canvas {
  position:absolute;
  top:0;
  left:0;
}
</style>
</head>
<body>

<p>Congratulations, you have been hacked by Jana Elsabagh 😘😘</p>

<canvas id="confetti"></canvas>

<script>
const canvas = document.getElementById("confetti");
const ctx = canvas.getContext("2d");
canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

let particles = [];

for (let i = 0; i < 150; i++) {
  particles.push({
    x: Math.random() * canvas.width,
    y: Math.random() * canvas.height,
    r: Math.random() * 6 + 2,
    d: Math.random() * 150,
    color: "hsl(" + Math.random() * 360 + ",100%,50%)"
  });
}

function draw() {
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  particles.forEach(p => {
    ctx.beginPath();
    ctx.fillStyle = p.color;
    ctx.arc(p.x, p.y, p.r, 0, Math.PI * 2);
    ctx.fill();
    p.y += Math.cos(p.d) + 1;
    p.x += Math.sin(p.d);
    if (p.y > canvas.height) {
      p.y = 0;
      p.x = Math.random() * canvas.width;
    }
  });
  requestAnimationFrame(draw);
}

draw();
</script>

</body>
</html>
