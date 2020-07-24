<script>
  import Header from '../components/Header.svelte'
  import Navbar from '../components/Navbar.svelte'

  import ProjectsGrid from '../components/ProjectsGrid.svelte'
  import Footer from '../components/Footer.svelte'
  import Card from '../components/Card.svelte'

  import { onMount } from 'svelte'

  export let params

  const apiUrl = 'https://jsonplaceholder.typicode.com/posts/'
  let data = []
  let webData

  const randInt = () => {
    return Math.floor(Math.random() * Math.floor(250))
  }

  let portfolioItems = []
  let title = 'Articles, snippets, thoughts and Stuff - in progress'

  onMount(async () => {
    const response = await fetch(apiUrl)
    data = await response.json()

    let webData = await data.map((item, index) => ({
      brief: item.body.split(' ').slice(0, 12).join(' '),
      title: item.title.split(' ').slice(0, 3).join(' '),
      imageUrl: `https://picsum.photos/id/${index}/400/300`,
    }))

    portfolioItems = webData
  })
</script>

<style>
  #articles {
  }
</style>

<section id="articles">
  <div class="container">

    <ProjectsGrid {portfolioItems} {title} } />

  </div>
</section>
