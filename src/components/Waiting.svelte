<script>
  export let message = 'Please hold on: heroku is waking up...'
  export let title = ''
</script>

<style>
  .waiting {
    height: 70vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
  .waiting p {
    margin: 3rem 0;
  }
</style>

<div class="waiting">
  <h2>{title}</h2>
  <p>{message}</p>
  <i class="fas fa-cog fa-spin fa-7x" />
  <p>
    If it doesn't work, hit refresh: it's a free dyno and it might need a little
    push in order to wake up
  </p>
</div>
