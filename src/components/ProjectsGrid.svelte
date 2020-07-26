<script>
  import Card from '../components/Card.svelte'
  export let portfolioItems = []
  export let title = ''
</script>

<section id="portfolio">
  <div class="container">
    <h2 class="text-center">{title}</h2>
    <div id="portfolio-grid">
      {#each portfolioItems as item}
        <Card
          title={item.title}
          imageUrl={item.imageUrl}
          brief={item.brief}
          slug={item.slug}
          webUrl={item.webUrl}
          entity={item.entity} />
      {/each}
    </div>
  </div>
</section>
