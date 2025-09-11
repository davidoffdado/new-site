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
</script>

<Nav />
<Hero />

{#if view === 'home'}
  <main class="container" id="articles" style="padding:2rem 0">
    <h2 class="h1" style="margin:0 0 1rem">Gli articoli</h2>
    <div class="grid" style="grid-template-columns:repeat(auto-fit,minmax(320px,1fr));gap:1rem">
      {#each articles.slice(0,3) as a}
        <ProjectCard project={a} />
      {/each}
    </div>
    <p style="margin-top:1rem">
      <a class="button" on:click={() => view = 'all-articles'}> <b> Vedi tutti gli articoli → </b> </a>
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
    <a class="button" on:click={() => view = 'all-projects'}> <b> Vedi tutti i progetti → </b></a>
  </p>
</main>

<main class="container" id="newsletter" style="padding:2rem 0">
  <h2 class="h1" style="margin:0 0 1rem">La newsletter</h2>
  <div class="grid" style="grid-template-columns:repeat(auto-fit,minmax(320px,1fr));gap:1rem">
    {#each projects.slice(0,3) as p}
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
	<b> Vai alla mia newsletter → </b> 
	</a>
  </p>
</main>



<section class="container about-section" id="about">
  <div class="about-text">
    <h2 class="h1">Chi sono</h2>
    <p>
      Ciao, chi sono? :) <br>
	Sono David Ruffini, un classe 1998 di Macerata interessato al giornalismo, ai dati e alla probabilità. </p>

<p> Sono laureato in Scienze Statistiche e lavoro con i dati, ma soprattutto cerco di dare loro un senso, in modo da capire meglio ciò che ci circonda. Per altri dettagli su ciò che ho studiato e sulle mie esperienze lavorative vi rimando a <a href="https://www.linkedin.com/in/david-ruffini-56a5a1161/"> LinkedIn</a>.
</p> 

<p> 
L’incertezza mi ha sempre incuriosito. Entrambe le mie tesi hanno avuto a che fare con la probabilità e con i comportamenti delle persone, ma il caso è sempre stato qualcosa che mi ha dato molto da pensare (o forse sto semplicemente razionalizzando ex-post).
</p>

<p> Fortunatamente, siamo altro oltre il lavoro. Qualche parola a caso per dire altro su di me: libri, film, allenamento, cucina e tante altre. </p>
  </div>

  <div class="about-photo">
    <img src="/new-site/IMG-20250309-WA0129.jpg" alt="Foto di David Ruffini">
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
<p>  Scrivimi sulla mail <a href="mailto:davidruffini98@email.com">davidruffini98@email.com </a> o tramite i social presenti in fondo alla pagina. Ci sentiamo :) </p>


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
