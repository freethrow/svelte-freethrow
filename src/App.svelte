<script>
  import router from 'page'

  // Include our Routes
  import Home from './routes/Home.svelte'
  import Projects from './routes/Projects.svelte'
  import SingleProject from './routes/SingleProject.svelte'
  import Articles from './routes/Articles.svelte'
  import Navbar from './components/Navbar.svelte'
  import Footer from './components/Footer.svelte'
  import About from './routes/About.svelte'
  let page
  let params

  // Set up the pages to watch for
  router('/', () => (page = Home))
  router('/about', () => (page = About))
  router('/projects', () => (page = Projects))
  router(
    '/project/:slug',
    // Before we set the component
    (ctx, next) => {
      params = ctx.params
      next()
    },

    // Finally set the component
    () => (page = SingleProject)
  )
  router('/articles', () => (page = Articles))
  router(
    '/article/:id',

    // Before we set the component
    (ctx, next) => {
      params = ctx.params
      next()
    },

    // Finally set the component
    () => (page = SingleArticle)
  )

  router.start()
</script>

<style>

</style>

<main>
  <Navbar />
  <svelte:component this={page} {params} />
  <Footer />
</main>
