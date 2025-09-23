<script>
  import './lib/styles/typography.css';
  import Nav from './lib/components/Nav.svelte';
  import Hero from './lib/components/Hero.svelte';
  import ProjectCard from './lib/components/ProjectCard.svelte';
  import Scroller from './lib/components/Scroller.svelte';
  import StickyChart from './lib/components/StickyChart.svelte';
  import MethodBox from './lib/components/MethodBox.svelte';
  import { articles } from './data/articles.js';
  import { projects } from './data/projects.js';
  import { newsletter } from './data/newsletter.js';
  import Typewriter from './lib/components/Typewriter.svelte';


    import { onMount } from 'svelte';
  import { tick } from 'svelte';

  let view = 'home'; // 'home' | 'all-articles' | 'all-projects'

  async function syncViewWithHash() {
    const h = (location.hash || '').slice(1); // senza '#'

    if (h === 'all-articles' || h === 'all-projects') {
      view = h;
      return;
    }

    // per qualunque altro hash (about, methods, contact, o stringa vuota) torniamo alla home
    view = 'home';
    await tick(); // aspetta che la home sia renderizzata

    if (h) {
      const el = document.getElementById(h);
      if (el) el.scrollIntoView({ behavior: 'smooth', block: 'start' });
    } else {
      // nessun hash: torna in cima
      window.scrollTo({ top: 0, behavior: 'smooth' });
    }
  }

  onMount(() => {
    syncViewWithHash(); // all’avvio (gestisce accesso diretto a /#all-articles ecc.)
    window.addEventListener('hashchange', syncViewWithHash);
  });



</script>

<Nav />
<Hero />

{#if view === 'home'}

<main class="container" id="newsletter" style="padding:2rem 0">
  <h2 class="h1" style="margin:0 0 1rem">La newsletter</h2>
  <div class="grid" style="grid-template-columns:repeat(auto-fit,minmax(320px,1fr));gap:1rem">
    {#each newsletter.slice(0,3) as p}
      <ProjectCard project={p} />
    {/each}
  </div>
  <p style="margin-top:1rem">
      <a
    	class="button"
    	href="https://aalea.substack.com/"  
    	target="_blank"
    	rel="noopener"
  	> 
	<b> Vai alla newsletter → </b> 
	</a>
  </p>
</main>

<main class="container" id="projects" style="padding:2rem 0">
  <h2 class="h1" style="margin:0 0 1rem">I progetti</h2>
  <div class="grid" style="grid-template-columns:repeat(auto-fit,minmax(320px,1fr));gap:1rem">
    {#each projects.slice(0,3) as p}
      <ProjectCard project={p} />
    {/each}
  </div>
  <p style="margin-top:1rem">
    <a class="button" href="#all-projects"> <b> Vedi tutti i progetti → </b></a>
  </p>
</main>

  <main class="container" id="articles" style="padding:2rem 0">
    <h2 class="h1" style="margin:0 0 1rem">Gli articoli</h2>
    <div class="grid" style="grid-template-columns:repeat(auto-fit,minmax(320px,1fr));gap:1rem">
      {#each articles.slice(0,3) as a}
        <ProjectCard project={a} />
      {/each}
    </div>
    <p style="margin-top:1rem">
      <a class="button" href="#all-articles"> <b> Vedi tutti gli articoli → </b> </a>
    </p>
  </main>







<section class="container about-section" id="about">
  <div class="about-text">
    <h2 class="h1">Chi sono</h2>
  <b>nome:</b> <Typewriter text="david" speed={250}/> <br>
  <b>cognome:</b> <Typewriter text="ruffini" speed={250} /> <br>
  <b>data di nascita:</b> <Typewriter text="22 settembre 1998" speed={150} /> <br>
  <b>luogo di nascita:</b> <Typewriter text="macerata" speed={150} /> <br>
  <b>laurea:</b> <Typewriter text="statistica e data science" speed={150} /> <br>
  <b>interessi:</b> <Typewriter text="libri, cinema, cucina, ..." speed={150} /><br>
  <b>lavoro:</b> <Typewriter text="data analyst, data journalist" speed={150} /><br>
    <p>
  </div>

  <div class="about-photo">
    <img src="./IMG-20250309-WA0129.jpg" alt="Foto di David Ruffini">
  </div>
</section>



  <section class="container" id="methods" style="margin-top:2rem">
    <h2 class="h1">Cosa faccio</h2>
    <div class="about-text">
<p> Provo a fare il data journalist. </p>
      <p> Durante i miei studi universitari mi sono avvicinato al mondo della probabilità e del data journalism, convinto che nell’informazione di oggi ci sia spazio (e sia esso necessario) per una comunicazione basata sui dati e sulla cultura dell’incertezza. Ho quindi iniziato a coltivare un portfolio di analisi e a collaborare con Il Sole 24 Ore, contribuendo al blog <a href="https://www.infodata.ilsole24ore.com/"> Info Data</a>. Successivamente, ho lanciato una newsletter: si chiama <a href="https://aalea.substack.com/"> àlea </a> e parla di probabilità. </p>

<p> Finora mi sono occupato di argomenti trasversali tra di loro, ma spesso mi ritrovo a scrivere di conflitti o di temi legati all'incertezza. Qualche tempo fa ho realizzato uno <a href="https://www.davidruffini.com/stato-delle-carceri"> scraper </a> che aggiorna quotidianamente, in maniera automatica, i dati relativi all’affollamento carcerario in Italia; il progetto è stato selezionato dal <a href="https://gijn.org/stories/europes-deadly-heatwave-middle-east-ceasefires/"> Global Investigative Journalism Network </a> tra i migliori dieci lavori di data journalism realizzati nelle prime settimane di luglio 2025. </p>

<p>
Nel frattempo, lavoro come data analyst in una società di consulenza.
</p>

<b>keywords:</b> <Typewriter text="data journalism, data visualization, data analysis, probabilità, sviluppo web" speed={100} /><br>
<b>tecnologie:</b> <Typewriter text="R, Python, Flourish, Datawrapper, HTML, CSS, JavaScript, Svelte, SQL" speed={100} /><br>
    </div>
  </section>


  <section class="container" id="contact" style="margin-top:2rem">
    <h2 class="h1">Contatti</h2>
    <div class="about-text">
<p> Lavoro su tutto ciò che può essere rappresentato in una dimensione numerica o che può essere visto sotto la lente dell'incertezza. </p>
<p>
Ti serve una mano per un progetto, un articolo o un’inchiesta che richiede analisi e visualizzazioni? <br>
Pensi che quel numero letto nei giornali nasconda altro o sia sbagliato? <br>
Parliamone!
</p>
<p>  Scrivimi sulla mail <a href="mailto:davidruffini98@gmail.com">davidruffini98@gmail.com </a> o tramite i social presenti in fondo alla pagina. Ci sentiamo :) </p>


<div class="social-icons">
  <ul>

	    <!-- Email -->
    <li>
      <a href="mailto:davidruffini98@email.com">
        <i class="fa fa-envelope fa-2x"></i>
      </a>
    </li>

    <!-- Instagram -->
    <li>
      <a href="https://www.instagram.com/david_ruffini/" target="_blank" rel="noopener">
        <i class="fa fa-instagram fa-2x"></i>
      </a>
    </li>

    <!-- LinkedIn -->
    <li>
      <a href="https://www.linkedin.com/in/david-ruffini-56a5a1161/" target="_blank" rel="noopener">
        <i class="fa fa-linkedin fa-2x"></i>
      </a>
    </li>

    <!-- Substack -->
    <li>
      <a href="https://substack.com/@davidruffini1" target="_blank" rel="noopener">
        <i class="fa fa-rss fa-2x"></i>
      </a>
    </li>

	    <!-- Twitter -->
    <li>
      <a href="https://twitter.com/davidruffini_" target="_blank" rel="noopener">
        <i class="fa fa-twitter fa-2x"></i>
      </a>
    </li>

	    <!-- GitHub -->
    <li>
      <a href="https://github.com/davidoffdado" target="_blank" rel="noopener">
        <i class="fa fa-github fa-2x"></i>
      </a>
    </li>
	
  </ul>
</div>
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
  <p class="caption">© David Ruffini, {new Date().getFullYear()} · Realizzato con Svelte · L'header è ispirato a quello di <a href="https://pudding.cool/"> The Pudding </a> </p>
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
  text-align: left;
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
