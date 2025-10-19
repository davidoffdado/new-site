<script>
  export let project;
</script>


  <ul class="project-list">
    <li>
      <a href={project.url} target="_blank" rel="noopener">
        {project.title}
      </a>
    </li>
</ul>




<style>
.project-list {
  list-style-type: none;
  padding: 0;
  margin: 0;
}

.project-list li {
  margin: 0.5rem 0;
}

.project-list a {
  text-decoration: underline;
  text-decoration-thickness: 2px;
  text-decoration-color: black;
  color: black;
  transition: color 0.3s, background-color 0.3s;
}

.project-list a:hover {
  background-color: black;
  color: white;
}

</style>

