<script>
  export let project
</script>
<article class="card fade-in" style="overflow:hidden">
  <a href={project.url} target="_blank" rel="noopener" style="display:grid;grid-template-columns:1.2fr 1fr;gap:0">
    <div style="padding:1rem 1rem 0">
      <img src={project.cover} alt={project.title} style="border-radius:14px;border:1px solid var(--line)"/>
    </div>
    <div style="padding:1rem 1.25rem">
      <p class="badge">{project.year} · {project.role}</p>
      <h3 class="h2" style="margin:.25rem 0 .25rem">{project.title}</h3>
      <p class="subtle" style="margin:0 0 .8rem">{project.dek}</p>
      <div style="display:flex;flex-wrap:wrap;gap:.4rem">
        {#each project.tags as t}
          <span class="badge" style="background:#f8fafc;border:1px solid var(--line);padding:.25rem .5rem;border-radius:999px">{t}</span>
        {/each}
      </div>
    </div>
  </a>
</article>
<style>
  article:hover img{transform:scale(1.02);transition:transform .3s ease}
</style>