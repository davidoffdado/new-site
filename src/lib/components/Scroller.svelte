<script>
  import { onMount } from 'svelte'
  export let steps = [] // [{title, text}]
  export let current = 0
  let stepEls = []
  const setCurrent = (i)=> current = i

  onMount(()=>{
    const io = new IntersectionObserver((entries)=>{
      entries.forEach(e=>{ if(e.isIntersecting){ current = +e.target.dataset.idx } })
    },{root:null,rootMargin:'-40% 0px -50% 0px',threshold:0})
    stepEls.forEach(el=>io.observe(el))
    return ()=> io.disconnect()
  })
</script>
<div class="scrolly">
  <div class="sticky" aria-live="polite">
    <slot name="graphic" {current}></slot>
  </div>
  <div>
    {#each steps as s, i}
      <section bind:this={stepEls[i]} class="step card" data-idx={i} aria-current={current===i}>
        <h4 class="h2" style="margin:.2rem 0">{s.title}</h4>
        <p class="subtle" style="margin:0">{s.text}</p>
      </section>
    {/each}
  </div>
</div>

