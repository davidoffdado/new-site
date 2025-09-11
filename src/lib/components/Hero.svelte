<script>
  import { onMount, onDestroy } from 'svelte';

  // Frasi che ruotano sotto "Sono…"
  const rotating = [
    'un data journalist appassionato di visualizzazione.',
    'uno statistico che ama raccontare storie con i numeri.',
    'un creativo che trasforma dataset complessi in esperienze interattive.',
    'alla costante ricerca della migliore narrazione visiva.'
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

<header class="container" id="top" style="padding: 4rem 0 2rem;">
  <p class="badge">Portfolio</p>
  <h1 class="h0" style="margin: 0.2rem 0 1rem;">Raccontare una storia, partendo dai dati</h1>
  <p class="subtle" style="max-width: 100%;">
    I numeri non sono noiosi e, anzi, ci aiutano a capire meglio la realtà che ci circonda; il nostro mondo, però, ha poche certezze e ciascun dato deve essere interpretato al meglio, non solo proiettato in un grafico. Fortunatamente, hanno inventato la Statistica.
  </p>

  <p class="subtle" style="max-width: 100%;">
   La sezione relativa agli articoli contiene tutti i miei lavori pubblicati dalle testate giornalistiche, mentre i progetti si riferiscono a quelle attività che hanno richiesto (e richiedono) un maggiore impegno in termini di tempo e risorse dedicate. Infine, la mia opera più recente: una newsletter che parla di probabilità e incertezza, per cercare di mostrare le situazioni in cui i numeri sembrano volerci ingannare.
  </p>

  <!-- Blocco dinamico 
  <p class="intro">Sono…</p>
  <p class="rotating"><strong>{rotating[index]}</strong></p> -->

  <div style="margin-top: 1.25rem; display: flex; gap: 0.75rem; flex-wrap: wrap;">
    <a class="button" href="#articles"> <b> Leggi i miei articoli </b> </a>
    <a class="button" href="#projects"> <b> Guarda i miei progetti </b> </a>
    <a class="button" href="#newsletter"> <b> Sfoglia la mia newsletter </b> </a>
  </div>
</header>

<style>
.intro {
  font-size: 1.8rem;
  color: var(--ink);
  margin-top: 1rem;
  margin-bottom: 0.3rem;
  text-align: center;
}

.rotating {
  font-size: 1.4rem;
  color: var(--accent);
  text-align: center;
  transition: opacity 0.5s ease-in-out;
}

.hero {
  text-align: center;
  padding: 4rem 1rem 2rem;
}

.button {
  padding: 0.5rem 1rem;
  font-size: 1rem;
  color: var(--accent);
}

.button:hover {
  background-color: var(--accent);
  color: white;                 /* Inverti colori al passaggio del mouse */
}

@media (max-width: 768px) {
  .hero {
    padding: 2rem 1rem;
  }
  .button {
    padding: 0.4rem 0.8rem;
    font-size: 0.9rem;
	color: var(--accent);
  }
}

</style>

