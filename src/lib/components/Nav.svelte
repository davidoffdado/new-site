<script>
  export let active = 'work'
</script>
<nav class="container" aria-label="Primary">
  <div class="grid" style="grid-template-columns:auto 1fr auto;align-items:center;padding:1.2rem 0">
    <a href="#top" class="h2" style="text-decoration:none;color:var(--ink)">
<span style="color:var(--accent)">●</span> David Ruffini

</a>
    <div></div>
    <div style="display:flex;gap:.8rem;align-items:center">
      <a href="#work" aria-current={active==='work'} class="badge">Lavori</a>
      <a href="#about" aria-current={active==='about'} class="badge">Chi sono</a>
      <a href="#methods" aria-current={active==='methods'} class="badge">Metodologia</a>
      <a href="#contact" aria-current={active==='contact'} class="badge">Contatti</a>
    </div>
  </div>
</nav>
<style>
  a[aria-current="true"]{color:var(--ink);font-weight:600}
</style>