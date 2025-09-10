<script>
  export let items = [] // [{label, text}]
</script>
<div class="card" style="padding:1rem 1.25rem">
  <h3 class="h2" style="margin:0 0 .5rem">Metodologia</h3>
  <ul style="margin:0;padding-left:1rem">
    {#each items as m}
      <li style="margin:.35rem 0"><strong>{m.label}:</strong> <span class="subtle">{m.text}</span></li>
    {/each}
  </ul>
</div>