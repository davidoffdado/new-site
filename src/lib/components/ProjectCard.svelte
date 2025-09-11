<script>
  export let project;
</script>

<a class="card" href={project.link} target="_blank" rel="noopener">
  <!-- Immagine in alto -->
  {#if project.cover}
    <div class="image-container">
      <img src={project.cover} alt={project.title} />
    </div>
  {/if}

  <!-- Titolo e descrizione -->
  <div class="content">
    <h3 class="title">{project.title}</h3>
    {#if project.dek}
      <p class="dek">{project.dek}</p>
    {/if}

    <!-- Tag o categorie -->
    {#if project.tags}
      <div class="tags">
        {#each project.tags as tag}
          <span class="tag">{tag}</span>
        {/each}
      </div>
    {/if}
  </div>
</a>

<style>
.card {
  display: flex;
  flex-direction: column;
  border-radius: 12px;
  overflow: hidden;
  background: var(--surface);
  text-decoration: none;
  color: inherit;
  box-shadow: 0 2px 8px rgba(0,0,0,0.08);
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.card:hover {
  transform: translateY(-4px);
  box-shadow: 0 6px 16px rgba(0,0,0,0.12);
}

.image-container {
  width: 100%;
  aspect-ratio: 16/9;       /* Mantiene proporzioni coerenti */
  overflow: hidden;
  background: #eee;
}

.image-container img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
  transition: transform 0.3s ease;
}

.card:hover img {
  transform: scale(1.05);
}

.content {
  padding: 1rem;
}

.title {
  font-size: 1.2rem;
  font-weight: 600;
  margin: 0 0 0.5rem;
}

.dek {
  font-size: 0.95rem;
  color: var(--dim);
  margin: 0 0 0.75rem;
}

.tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.4rem;
}

.tag {
  background: var(--accent);
  color: #fff;
  padding: 0.2rem 0.6rem;
  font-size: 0.75rem;
  border-radius: 4px;
}
</style>
