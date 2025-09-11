<script>
  import './lib/styles/typography.css';
  import Nav from './lib/components/Nav.svelte';
  import Hero from './lib/components/Hero.svelte';
  import ProjectCard from './lib/components/ProjectCard.svelte';
  import Scroller from './lib/components/Scroller.svelte';
  import StickyChart from './lib/components/StickyChart.svelte';
  import MethodBox from './lib/components/MethodBox.svelte';
  import { articles, projects } from './data/projects.js';

  let view = 'home';

  const steps = [
    { title: 'Contesto', text: 'Inizio con una domanda chiara e un dataset pulito.' },
    { title: 'Analisi', text: 'Esploro pattern con notebook e prototipi rapidi.' },
    { title: 'Narrazione', text: 'Scelgo la visualizzazione più onesta ed efficace.' },
    { title: 'Interazione', text: 'Aggiungo micro-interazioni utili, mai gratuite.' }
  ];

  const methods = [
    { label: 'Dati', text: 'CSV/Parquet; pulizia con Python + Pandas/Polars.' },
    { label: 'Analisi', text: 'Notebook riproducibili; versioning su Git.' },
    { label: 'Viz', text: 'Svelte + Canvas/SVG; accessibile e responsivo.' },
    { label: 'Etica', text: 'Preferisco semplicità e trasparenza a effetti speciali.' }
  ];
</script>

<Nav />
<Hero />

{#if view === 'home'}
  <main class="container" id="articles" style="padding:2rem 0">
    <h2 class="h1" style="margin:0 0 1rem">Gli ultimi articoli</h2>
    <div class="grid" style="grid-template-columns:repeat(auto-fit,minmax(320px,1fr));gap:1rem">
      {#each articles.slice(0,3) as a}
        <ProjectCard project={a} />
      {/each}
    </div>
    <p style="margin-top:1rem">
      <a class="button" on:click={() => view = 'all-articles'}>Vedi tutti gli articoli →</a>
    </p>
  </main>

<main class="container" id="projects" style="padding:2rem 0">
  <h2 class="h1" style="margin:0 0 1rem">Gli ultimi progetti</h2>
  <div class="grid" style="grid-template-columns:repeat(auto-fit,minmax(320px,1fr));gap:1rem">
    {#each projects.slice(0,3) as p}
      <ProjectCard project={p} />
    {/each}
  </div>
  <p style="margin-top:1rem">
    <a class="button" on:click={() => view = 'all-projects'}>Vedi tutti i progetti →</a>
  </p>
</main>

<main class="container" id="newsletter" style="padding:2rem 0">
  <h2 class="h1" style="margin:0 0 1rem">Una newsletter sull'incertezza</h2>
  <div class="grid" style="grid-template-columns:repeat(auto-fit,minmax(320px,1fr));gap:1rem">
    {#each projects.slice(0,3) as p}
      <ProjectCard project={p} />
    {/each}
  </div>
  <p style="margin-top:1rem">
    <a class="button" on:click={() => view = 'all-projects'}>Vedi tutti i progetti →</a>
  </p>
</main>


  <section class="container" aria-labelledby="scrolly">
    <h2 id="scrolly" class="h1" style="margin:1rem 0">Processo, passo dopo passo</h2>
    <Scroller {steps} let:current>
      <div slot="graphic" let:current>
        <StickyChart {current} />
      </div>
    </Scroller>
  </section>

<section class="container about-section" id="about">
  <div class="about-text">
    <h2 class="h1">Chi sono</h2>
    <p>
      Sono un data journalist appassionato di visualizzazione e narrazione con i dati.
      Uso design e codice per trasformare informazioni complesse in storie chiare e coinvolgenti.
    </p>
  </div>

  <div class="about-photo">
    <img src="/new-site/IMG-20250309-WA0129.jpg" alt="Foto di David Ruffini">
  </div>
</section>



  <section class="container" id="methods" style="margin-top:2rem">
    <h2 class="h1">Cosa faccio</h2>
    <div class="card" style="padding:1rem 1.25rem">
      <p class="subtle">David Ruffini — Statistico e data journalist, principalmente per Il Sole 24 Ore. Esperienza con Python, SQL, Svelte, D3 e grafica su Canvas/SVG.</p>
      <p class="subtle">Premi/menzioni, collaborazioni e contatti media su richiesta.</p>
    </div>
  </section>


  <section class="container" id="contact" style="margin-top:2rem">
    <h2 class="h1">Contatti</h2>
    <div class="card" style="padding:1rem 1.25rem">
      <p>Email: <a href="mailto:davidruffini@email.com">davidruffini@email.com</a></p>
      <p>GitHub: <a href="https://github.com/davidoffdado" target="_blank" rel="noopener">@davidoffdado</a></p>
      <p>Twitter: <a href="https://twitter.com/davidruffini_" target="_blank" rel="noopener">@davidruffini_</a></p>
      <p class="caption">Portfolio open-source. Puoi clonarlo e adattarlo liberamente.</p>
    </div>
  </section>
{/if}

{#if view === 'all-articles'}
  <section class="container" style="padding:2rem 0">
    <h1 class="h1">Tutti gli articoli</h1>
    <div class="grid" style="grid-template-columns:repeat(auto-fit,minmax(320px,1fr));gap:1rem">
      {#each articles as a}
        <ProjectCard project={a} />
      {/each}
    </div>
    <p style="text-align:center;margin-top:2rem">
      <a class="button" on:click={() => view = 'home'}>← Torna alla home</a>
    </p>
  </section>
{/if}

{#if view === 'all-projects'}
  <section class="container" style="padding:2rem 0">
    <h1 class="h1">Tutti i progetti</h1>
    <div class="grid" style="grid-template-columns:repeat(auto-fit,minmax(320px,1fr));gap:1rem">
      {#each projects as p}
        <ProjectCard project={p} />
      {/each}
    </div>
    <p style="text-align:center;margin-top:2rem">
      <a class="button" on:click={() => view = 'home'}>← Torna alla home</a>
    </p>
  </section>
{/if}

<footer class="container">
  <p class="caption">© {new Date().getFullYear()} — Costruito con Svelte · Ispirato a The Pudding</p>
</footer>

<style>
  #articles .grid, #projects .grid {grid-template-columns:repeat(auto-fit,minmax(320px,1fr))}

.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 1rem;
}

@media (max-width: 480px) {
  .grid {
    grid-template-columns: 1fr; /* Una colonna sui telefoni */
  }
}

.about-section {
  display: grid;
  grid-template-columns: 1fr;     /* Mobile: una colonna */
  gap: 2rem;
  align-items: center;
  margin-top: 2rem;
  text-align: center;
}

/* Foto di default su mobile */
.about-photo img {
  width: 100%;
  max-width: 300px;
  border-radius: 12px;
  box-shadow: 0 4px 12px rgba(0,0,0,0.1);
}

/* 📺 Su schermi grandi (desktop), due colonne 50/50 */
@media (min-width: 992px) {
  .about-section {
    grid-template-columns: 1fr 1fr; /* due colonne uguali */
    text-align: left;
  }

  .about-photo img {
    width: 100%;         /* Occupa tutta la metà destra */
    max-width: none;     /* Rimuove il limite di 300px */
    border-radius: 12px;
  }
}

</style>
