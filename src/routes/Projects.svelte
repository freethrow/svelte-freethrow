<script>
  import Header from '../components/Header.svelte'
  import Navbar from '../components/Navbar.svelte'
  import What from '../components/What.svelte'
  import ProjectsGrid from '../components/ProjectsGrid.svelte'
  import Footer from '../components/Footer.svelte'
  import Card from '../components/Card.svelte'
  import Waiting from '../components/Waiting.svelte'

  import { onMount } from 'svelte'

  let title = 'Portfolio'

  const apiUrl = 'https://freethrow-api.herokuapp.com/projects'

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
      entity: 'project',
    }))

    console.log('WebData:', webData)
    return webData
  }

  let portfolioItems = getProjects()
</script>

<div id="portfolio">
  {#await portfolioItems}
    <Waiting
      title="Fetching projects..."
      message="Please hold on, Heroku is waking up." />
  {:then result}
    <div class="container">
      <ProjectsGrid portfolioItems={result} {title} />
    </div>
  {:catch error}
    <p style="color: red">{error}</p>
  {/await}

</div>
