<script>
  import Header from '../components/Header.svelte'
  import Navbar from '../components/Navbar.svelte'
  import What from '../components/What.svelte'
  import ProjectsGrid from '../components/ProjectsGrid.svelte'
  import Footer from '../components/Footer.svelte'
  import Card from '../components/Card.svelte'

  import { onMount } from 'svelte'

  let data = []

  const apiUrl = 'https://freethrow-api.herokuapp.com/projects?featured=true'
  let portfolioItems = []

  onMount(async () => {
    const response = await fetch(apiUrl)
    data = await response.json()
    console.log(data)

    let webData = await data.map((item) => ({
      brief: item.brief,
      title: item.title,
      imageUrl: item.images[0].picture.url,
      webUrl: item.web_url,
      slug: item.slug,
    }))
    console.log(webData)
    portfolioItems = webData
  })
</script>

<div>
  <Header />
  <What />
  <div class="divider" />

  <ProjectsGrid {portfolioItems} title="Recent Projects" />

</div>
