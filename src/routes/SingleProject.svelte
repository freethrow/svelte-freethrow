<script>
  import marked from 'marked'
  import { onMount } from 'svelte'

  import { Highlight } from 'svelte-highlight'
  import { python } from 'svelte-highlight/languages'
  import { github } from 'svelte-highlight/styles'

  export let params

  let slug = params.slug

  const apiUrl = `https://freethrow-api.herokuapp.com/projects?slug=${slug}`
  let data = []

  const getProject = async () => {
    const response = await fetch(apiUrl)
    data = await response.json()
    return data[0]
  }

  let promise = getProject()
</script>

<style scoped>
  img.featured {
    width: 100%;
    max-height: 300px;
    object-fit: cover;
  }

  .project {
    font-weight: 200;
  }

  .waiting {
    height: 70vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }

  .project-content img {
    display: block;
    margin-left: auto;
    margin-right: auto;
    width: 100%;
    border: 4px solid black;
  }
</style>

<div class="container">
  {#await promise}
    <div class="waiting">
      <h2>Loading project...</h2>
      <p>Please hold on: heroku is waking up...</p>
      <i class="fas fa-cog fa-spin fa-7x" />
      <p>
        If it doesn't work, hit refresh: it's a free dyno and it might need a
        little push in order to wake up
      </p>
    </div>
  {:then project}
    <div class="project">
      <h2>{project.title}</h2>
      {#if project.web_url}
        <p class="url">
          <a href={project.web_url}>live link</a>
        </p>
      {/if}

      {@html marked(project.brief)}
      <img class="featured" src={project.images[0].picture.url} alt="" />
      <hr />
      <div class="project-content">
        {@html marked(project.description)}
      </div>
    </div>
  {:catch error}
    <p style="color: red">Error</p>
  {/await}
</div>
