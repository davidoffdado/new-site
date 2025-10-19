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

<header class="container" id="top">
  <!-- <p class="badge">Portfolio</p> -->
  <h1 class="h0 typing-cursor" style="margin: 0.2rem 0 1rem;">ciao :)</h1>

  <p class="subtle" style="max-width: 100%;"> Sono David Ruffini, uno statistico interessato alla data visualization e alla probabilità. Lavoro come data analyst e data journalist; ho scritto per Il Sole 24 Ore, Wired Italia e Aliseo Editoriale.</p>
   
   <p class="subtle" style="max-width: 100%;"> Se non sono al computer, sono probabilmente a leggere, ad allenarmi, a cucinare, al cinema, in campagna o in giro.</p>

  <p class="subtle" style="max-width: 100%;"> Per qualsiasi richiesta, puoi contattatarmi via <a href="mailto:davidruffini98@email.com"> mail</a>! </p>


   <p class="subtle" style="max-width: 100%;"> 	<a href="https://drive.google.com/file/d/1vNtAIv2O_r0Xsiw0KSw2aWvwWDvdc7AP/view?usp=sharing" target="_blank" rel="noopener"> cv</a>
												<a href="https://aalea.substack.com/" target="_blank" rel="noopener"> newsletter </a>
												<a href="#all-projects"> progetti </a> 
												<a href="#all-articles"> articoli </a>
												<a href="https://linktr.ee/davidruffini" target="_blank" rel="noopener"> social </a>
												
	</p>


  <!-- Blocco dinamico 
  <p class="intro">Sono…</p>
  <p class="rotating"><strong>{rotating[index]}</strong></p> -->

<!-- Pulsanti sezioni
  <div style="margin-top: 1.25rem; display: flex; gap: 0.75rem; flex-wrap: wrap;">
    <a class="button" href="#newsletter"> <b> Sfoglia la mia newsletter </b> </a>
    <a class="button" href="#projects"> <b> Guarda i miei progetti </b> </a>
    <a class="button" href="#articles"> <b> Leggi i miei articoli </b> </a>
  </div> -->
</header>

<style>

.container {margin-top: 40px;}

a {
  text-decoration: underline;
  text-decoration-thickness: 2px;
  text-decoration-color: black;
  color: black;
  transition: color 0.3s, background-color 0.3s;
}

a:hover {
  background-color: black;
  color: white;
}

.intro {
  font-size: 0.5rem;
  color: var(--ink);
  margin-top: 1rem;
  margin-bottom: 0.3rem;
  text-align: center;
}

.rotating {
  font-size: 0.5rem;
  color: var(--accent);
  text-align: center;
  transition: opacity 0.5s ease-in-out;
}

.hero {
  text-align: center;
  padding: 2rem 1rem 2rem;
}

.button {
  padding: 0.5rem 1rem;
  font-size: 0.5rem;
  color: var(--accent);
  background-color: lightgray;
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
    font-size: 0.5rem;
	color: var(--accent);
	background-color: lightgray;
  }
}

</style>

