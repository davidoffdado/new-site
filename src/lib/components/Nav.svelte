<script>
  import { onMount, onDestroy } from 'svelte';

  // Frasi che cambiano
  const rotating = [
    'uno statistico',
    'un data journalist',
    'un appassionato di probabilità',
    'un feroce lettore'
  ];

  let index = 0;
  let interval;

  onMount(() => {
    interval = setInterval(() => {
      index = (index + 1) % rotating.length;
    }, 2000);
  });

  onDestroy(() => {
    clearInterval(interval);
  });
</script>

<nav class="container nav-bar" aria-label="Primary">
  <!-- 🔸 Sinistra: frasi che cambiano -->
  <div class="left-text">
    Sono… <br> <strong>{rotating[index]}</strong>
  </div>

  <!-- 🔸 Centro: Data Stories -->
  <div class="center-logo">
    David Ruffini
  </div>

  <!-- 🔸 Destra: link di navigazione -->
  <div class="links">
    <a href="#articles" class="badge">Articoli</a>
    <a href="#projects" class="badge">Progetti</a>
    <a href="#about" class="badge">Chi sono</a>
    <a href="#methods" class="badge">Metodologia</a>
    <a href="#contact" class="badge">Contatti</a>
  </div>
</nav>

<style>
.nav-bar {
  display: grid;
  grid-template-columns: auto 1fr 1fr;
  align-items: center;
  padding: 1rem 0;
}

/* 🔸 Sinistra */
.left-text {
  font-size: 1rem;
  color: var(--ink);
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  max-width: 250px;
  position: absolute;
  left: 12%;
top: 20px;
}

/* 🔸 Centro */
.center-logo {
  text-align: center;
  font-size: 1.4rem;
  font-weight: bold;
  color: var(--ink);
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
	top: 20px;
}

/* 🔸 Destra */
.links {
  display: flex;
  gap: .8rem;
  justify-content: flex-end;
  align-items: center;
  position: absolute;
  left: 70%;
top: 20px;
}

strong {
  color: var(--accent);
}
</style>
