<script>
  export let imageUrl
  export let title
  export let brief
  export let webUrl
  export let slug
</script>

<style scoped>
  .card-img-top {
    max-height: 300px;
    width: 100%;
    object-fit: cover;
  }

  .card {
    display: flex;
    flex-direction: column;
    justify-content: space-around;
  }

  .card-body {
    flex: 0;
  }
  img {
    flex: 1;
    opacity: 0.4;
    transition-property: all;
    transition-duration: 1s;
    transition-delay: 0.2s;
    transition-timing-function: linear;
    filter: grayscale(100%) contrast(180%);
  }

  img:hover {
    opacity: 1;
    filter: none;
  }

  .btn-primary {
    background-color: #f7d705;
  }
</style>

<div class="card">

  <img class="card-img-top" src={imageUrl} alt={title} />

  <div class="card-body">
    <h5 class="card-title">{title}</h5>
    <p class="card-text">{brief}</p>
    <p class="card-text">
      <small class="text-muted">
        <a class="btn btn-primary btn-sm" href="/project/{slug}">
          project link
        </a>
      </small>
    </p>
  </div>
</div>
