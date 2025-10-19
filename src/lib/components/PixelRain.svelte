<script>
  import { onMount } from 'svelte';

  let canvas;
  let ctx;
  let width, height;

  const pixels = [];
  const pixelSize = 3;       // grandezza pixel
  const gravity = 0.05;      // 👈 caduta lenta
  const friction = 0.2;      // 👈 rimbalzo minimo
  const spawnRate = 5;       // quanti pixel generare ogni ciclo
  const maxPixels = 5000;    // per non appesantire troppo

  function resize() {
    width = canvas.width = window.innerWidth;
    height = canvas.height = window.innerHeight;
  }

  onMount(() => {
    ctx = canvas.getContext('2d');
    resize();
    window.addEventListener('resize', resize);

    // genera continuamente nuovi pixel
    const spawnInterval = setInterval(() => {
      if (pixels.length < maxPixels) {
        for (let i = 0; i < spawnRate; i++) {
          pixels.push({
            x: Math.random() * width,
            y: 0,
            vy: 0,
          });
        }
      }
    }, 100);

    // piccola griglia per accumulo "fisico"
    const gridCols = Math.floor(width / pixelSize);
    const gridRows = Math.floor(height / pixelSize);
    const grid = Array.from({ length: gridCols }, () => Array(gridRows).fill(false));

    function animate() {
      ctx.clearRect(0, 0, width, height);

      for (let p of pixels) {
        const gridX = Math.floor(p.x / pixelSize);
        const gridY = Math.floor(p.y / pixelSize);

        if (gridY < gridRows - 1 && !grid[gridX]?.[gridY + 1]) {
          // caduta
          p.vy += gravity;
          p.y += p.vy;
        } else {
          // si ferma o rimbalza poco
          if (p.vy > 0.2) {
            p.vy *= -friction;
          } else {
            p.vy = 0;
            grid[gridX][gridY] = true;
          }
        }

        // disegna pixel
        ctx.fillStyle = 'black';
        ctx.fillRect(p.x, p.y, pixelSize, pixelSize);
      }

      requestAnimationFrame(animate);
    }

    animate();
  });
</script>

<canvas bind:this={canvas} class="pixel-rain"></canvas>

<style>
.pixel-rain {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
}
</style>
