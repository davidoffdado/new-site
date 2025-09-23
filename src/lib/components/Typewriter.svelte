<script>
  export let text = "";
  export let speed = 80;

  let displayed = "";
  let index = 0;
  let visible = false; // diventa true quando l’elemento entra in viewport
  let container;

  const write = async () => {
    while (index < text.length) {
      await new Promise(r => setTimeout(r, speed));
      displayed += text[index];
      index += 1;
    }
  };

  // IntersectionObserver: parte solo quando entra in viewport
  const observer = new IntersectionObserver(
    entries => {
      if (entries[0].isIntersecting) {
        visible = true;
        write();
        observer.disconnect(); // evita di riscrivere più volte
      }
    },
    { threshold: 0.3 } // parte quando il 30% è visibile
  );

  // attivo observer su mount
  import { onMount } from "svelte";
  onMount(() => {
    if (container) observer.observe(container);
  });
</script>

<span bind:this={container}>{visible ? displayed : ""}</span>

<style>
span {
  font-family: 'Fira Code', monospace;
  white-space: normal;    /* consente il ritorno a capo */
  word-wrap: break-word;  /* spezza se necessario */
}
</style>
