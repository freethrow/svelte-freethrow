<script>
  import marked from 'marked'
  import { onMount } from 'svelte'

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

<style>
  .spinner {
    margin: 100px auto;
    width: 40px;
    height: 80vh;
    position: relative;
    text-align: center;

    -webkit-animation: sk-rotate 2s infinite linear;
    animation: sk-rotate 2s infinite linear;
  }

  .dot1,
  .dot2 {
    width: 60%;
    height: 60%;
    display: inline-block;
    position: absolute;
    top: 0;
    background-color: #333;
    border-radius: 100%;

    -webkit-animation: sk-bounce 2s infinite ease-in-out;
    animation: sk-bounce 2s infinite ease-in-out;
  }

  .dot2 {
    top: auto;
    bottom: 0;
    -webkit-animation-delay: -1s;
    animation-delay: -1s;
  }

  @-webkit-keyframes sk-rotate {
    100% {
      -webkit-transform: rotate(360deg);
    }
  }
  @keyframes sk-rotate {
    100% {
      transform: rotate(360deg);
      -webkit-transform: rotate(360deg);
    }
  }

  @-webkit-keyframes sk-bounce {
    0%,
    100% {
      -webkit-transform: scale(0);
    }
    50% {
      -webkit-transform: scale(1);
    }
  }

  @keyframes sk-bounce {
    0%,
    100% {
      transform: scale(0);
      -webkit-transform: scale(0);
    }
    50% {
      transform: scale(1);
      -webkit-transform: scale(1);
    }
  }

  img.featured {
    width: 100%;
    max-height: 300px;
    object-fit: cover;
  }

  .project {
    font-weight: 200;
  }
</style>

<div class="container">
  {#await promise}
    <div class="spinner">
      <div class="dot1" />
      <div class="dot2" />
    </div>
  {:then project}
    <div class="project">
      <h2>{project.title}</h2>
      <p class="url">
        <a href={project.web_url}>live link</a>
      </p>
      {@html marked(project.brief)}
      <img class="featured" src={project.images[0].picture.url} alt="" />
      <hr />
      {@html marked(project.description)}
    </div>
  {:catch error}
    <p style="color: red">Error</p>
  {/await}
</div>
