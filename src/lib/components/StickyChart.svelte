<script>
  import { onMount } from 'svelte';
  export let current = 0;
  let canvas;
  let dpr = 1;
  let data = [12, 28, 45, 30, 52, 61, 40, 70, 68, 85];

  function draw() {
    if (!canvas) return;          // <-- evita l'errore se canvas è ancora undefined
    const ctx = canvas.getContext('2d');
    const w = canvas.clientWidth * dpr;
    const h = canvas.clientHeight * dpr;
    canvas.width = w; canvas.height = h;

    ctx.fillStyle = '#ffffff';
    ctx.fillRect(0, 0, w, h);

    ctx.strokeStyle = '#e5e7eb';
    ctx.lineWidth = 1 * dpr;
    ctx.beginPath();
    ctx.moveTo(40 * dpr, 20 * dpr);
    ctx.lineTo(40 * dpr, h - 40 * dpr);
    ctx.lineTo(w - 20 * dpr, h - 40 * dpr);
    ctx.stroke();

    const max = Math.max(...data);
    const min = 0;
    const x = i => 40 * dpr + i * ((w - 60 * dpr) / (data.length - 1));
    const y = v => (h - 40 * dpr) - (v - min) / (max - min) * (h - 60 * dpr);

    const highlight = current % data.length;

    ctx.strokeStyle = '#1c7ed6';
    ctx.lineWidth = 2 * dpr;
    ctx.beginPath();
    data.forEach((v, i) => { i === 0 ? ctx.moveTo(x(i), y(v)) : ctx.lineTo(x(i), y(v)); });
    ctx.stroke();

    data.forEach((v, i) => {
      ctx.fillStyle = i === highlight ? '#ff7a59' : '#1c7ed6';
      ctx.beginPath();
      ctx.arc(x(i), y(v), i === highlight ? 6 * dpr : 4 * dpr, 0, Math.PI * 2);
      ctx.fill();
    });

    ctx.fillStyle = '#6b7280';
    ctx.font = `${12 * dpr}px Inter`;
    ctx.fillText('Valori simulati, punto evidenziato segue lo step', 46 * dpr, h - 16 * dpr);
  }

  onMount(() => {
    dpr = Math.min(2, window.devicePixelRatio || 1);
    const ro = new ResizeObserver(draw);
    if (canvas) ro.observe(canvas); // osserva il canvas solo se esiste
    draw();                          // disegna solo dopo che canvas è montato
    return () => ro.disconnect();
  });

  $: if (canvas) draw(); // riesegue draw quando cambia current e canvas è pronto
</script>

<div style="inline-size:100%; block-size:100%; display:grid; place-items:center; padding:1rem">
  <canvas bind:this={canvas} style="width:100%;height:100%;border-radius:16px"></canvas>
</div>

<style>
canvas {
  width: 100%;
  height: auto;
  max-width: 100%;
}
</style>

