<script>
  import { onMount, onDestroy } from 'svelte';

  // Frasi che cambiano
  const rotating = [
    'uno statistico',
    'un data journalist',
    'un divulgatore della probabilità'
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
    <a href="#about" class="badge">Chi sono</a>
    <a href="#methods" class="badge">Cosa faccio</a>
    <a href="#contact" class="badge">Contatti</a>
  </div>
</nav>

<style>
.nav-bar {
  display: grid;
  grid-template-columns: 1fr auto 1fr; /* sinistra-centro-destra */
  align-items: center;
  gap: 1rem;
  padding: 1rem 2rem;
}

/* 🔸 Sinistra */
.left-text {
	  justify-self: start;   /* allinea a sinistra */
  font-size: 1rem;
  color: var(--ink);
  white-space: normal;   /* consente il ritorno a capo */	

}

/* 🔸 Centro */
.center-logo {
  justify-self: center;  /* mantiene il logo centrato */
  font-size: 1.4rem;
  font-weight: bold;
  color: var(--ink);
}

/* 🔸 Destra */
.links {
  justify-self: end;
  display: flex;
  gap: 0.8rem;
  flex-wrap: wrap; /* Avvolge su mobile */
}

strong {
  color: var(--accent);
}

/* ✅ Mobile: nav verticale */
@media (max-width: 768px) {
  .nav-bar {
    grid-template-columns: 1fr auto;
    grid-template-rows: auto auto;
  }
  .center-logo {
    grid-column: 1 / -1;
    justify-self: center;
    margin-bottom: 0.5rem;
  }
  .links {
    grid-column: 1 / -1;
    justify-self: center;
  }
}
</style>
