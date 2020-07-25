<style scoped>
  #about {
    min-height: 100vh;
    padding: 3rem 1rem;
    margin-top: 0rem;
  }

  #about > .container {
    background-color: #fff;
    opacity: 0.9;
    padding: 1rem;
  }

  #contact {
    margin: 2rem 0;
  }
</style>

<section id="about">
  <div class="container">

    <h2>Freethrow?</h2>

    <p>
      I am a control systems engineer with a PhD in Systems Automation, trade
      analyst, freelance developer, former energy scientist, and data analyst.
    </p>
    <p>
      My curriculum is available in PDF, but I tend to write here about
      interesting things and projects.
    </p>

    <h3>What can I do for you?</h3>
    <p>Web Development Projects from start to finish:</p>
    <ol>
      <li>Project requirements analysis</li>
      <li>Discussion and details</li>
      <li>Features (data flow, data endpoints, connections, ETL)</li>
      <li>SQL or NoSQL database design (MongoDB, PostgreSQL, Firebase)</li>
      <li>
        Technology Stack (Node.js, python, Express.js, Koa.js, Django, Flask,
        Vue.js, Svelte.js etc)
      </li>
      <li>Fully Responsive and mobile or desktop first</li>
      <li>CSS3 or SASS design (Flexbox, Grid, with or without frameworks)</li>
    </ol>
    <p>Data Science Projects from start to finish</p>
    <ol>
      <li>Data gathering and organization</li>
      <li>Data cleaning</li>
      <li>Exploratory Data Analysis</li>
      <li>Machine Learning Algorithms</li>
      <li>Data Visualization (D3.js, python, Tableau)</li>
      <li>Data Driven Product Design</li>
    </ol>

  </div>

</section>

<section id="contact">
  <div class="container">
    <div class="row justify-content-lg-center">
      <form autocomplete="off" name="contact" data-netlify="true">

        <div class="form-group">
          <label for="email">Email</label>
          <input
            type="email"
            name="email"
            class="form-control"
            id="email"
            placeholder="Email" />
        </div>

        <div class="form-group">
          <label for="name">Name</label>
          <input
            type="text"
            class="form-control"
            id="name"
            name="name"
            placeholder="Your name" />
        </div>

        <div class="form-group">
          <textarea
            style="min-width: 100%"
            name="content"
            class="form-control"
            id="content"
            cols="30"
            rows="10" />
        </div>

        <button type="submit" class="btn btn-outline-dark">Send</button>
      </form>
    </div>

  </div>

</section>
