<script>
  import Header from '../components/Header.svelte'
  import Navbar from '../components/Navbar.svelte'
  import What from '../components/What.svelte'
  import ProjectsGrid from '../components/ProjectsGrid.svelte'
  import Footer from '../components/Footer.svelte'
  import Card from '../components/Card.svelte'

  import { onMount } from 'svelte'

  let title = 'Portfolio'

  const apiUrl = 'http://freethrow-api.herokuapp.com/projects'

  const getProjects = async () => {
    const response = await fetch(apiUrl)
    let data = await response.json()
    console.log(data)
    let webData = await data.map((item) => ({
      brief: item.brief,
      title: item.title,
      imageUrl: item.images[0].picture.url,
      webUrl: item.web_url,
      slug: item.slug,
    }))

    console.log('WebData:', webData)
    return webData
  }

  let portfolioItems = getProjects()
</script>

<style>
  .waiting {
    height: 70vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
</style>

<div id="portfolio">
  {#await portfolioItems}
    <div class="waiting">
      <h2>Loading projects...</h2>
      <p>Please hold on: heroku is waking up...</p>
    </div>
  {:then result}
    <div class="container">
      <ProjectsGrid portfolioItems={result} {title} />
    </div>
  {:catch error}
    <p style="color: red">{error}</p>
  {/await}

</div>
