<script>
  import { onMount, onDestroy } from 'svelte';

  // Frasi che cambiano
  const rotating = [
    '> uno statistico',
    '> un data journalist',
    '> uno studioso dell\'incertezza'
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
    > sono… <br> <strong>{rotating[index]}</strong>
  </div>

  <!-- 🔸 Centro: Data Stories -->
  <div class="center-logo">
      <a href="https://www.davidruffini.com/">
    <img src="/davidruffini.png" alt="David Ruffini">
  </a>
  </div>

  <!-- 🔸 Destra: link di navigazione -->
  <div class="links">
    <a href="#about" class="badge" ><img src="/chisono.png" alt="Chi sono" /></a>
    <a href="#methods" class="badge"><img src="/cosa-faccio.png" alt="Cosa faccio" /></a>
    <a href="#contact" class="badge"><img src="/contatti.png" alt="Contatti" /></a>
  </div>
</nav>

<style>
.nav-bar {
  display: grid;
  grid-template-columns: 1fr auto 1fr; /* sinistra-centro-destra */
  align-items: center;
  gap: 1rem;
  
	
}

/* 🔸 Sinistra */
.left-text {
  justify-self: start;
  font-size: 1rem;
  color: #000000;       
  white-space: normal;
  /* background-color: #1e1e1e;   sfondo scuro */
  padding: 0.5rem 1rem;       /* spazio interno */
  border-radius: 6px;         /* angoli arrotondati */
  font-family: 'Fira Code', monospace; /* font tipo IDE */
  /* box-shadow: 0 0 10px rgba(0,0,0,0.5);	*/

}

.left-text::after {
  content: '|';
  margin-left: -4px;
  animation: blink 1s step-start infinite;
}

@keyframes blink {
  50% { opacity: 0; }
}

/* 🔸 Centro */
.center-logo {
  justify-self: center;  /* mantiene il logo centrato */
  font-size: 1.4rem;
  font-weight: bold;
  color: var(--ink);
  border-radius: 6px;         /* angoli arrotondati */	

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

.links img {
  width: 110px;       /* 🔹 Aumenta la larghezza */
  height: 110px;      /* 🔹 Aumenta l’altezza */
  display: block;
  transition: transform 0.2s ease;
	gap: 0.1rem; 
}

.links a {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 0.1rem;   /* Spazio intorno alle icone */
}

.links a:hover img {
  transform: scale(1.1);
}

/* 📱 Su mobile: leggermente più piccole */
@media (max-width: 768px) {
  .links img {
    width: 80px;
    height: 80px;
  }
}

.center-logo img {
  height: 250px;           /* 🔹 Altezza del logo */
  width: auto;            /* Mantiene le proporzioni */
  display: block;
  transition: transform 0.2s ease;
}

.center-logo img:hover {
  transform: scale(1.05); /* Leggero zoom al passaggio */
}

/* 📱 Su mobile: leggermente più piccolo */
@media (max-width: 768px) {
  .center-logo img {
    height: 200px;
  }
}
</style>
