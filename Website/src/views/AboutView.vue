<template>
  <div class="about">
    <section class="about-content">
      <h1>About Me</h1>
      <p>
        Welcome to my website's about page. It displays different concepts and information I have been working on for tasks over the weeks
      </p>
      <p>
        Hopefully Over the weeks to come I will change the ui and add more pages for all the new stuff I learn which will be memorialised here
      </p>
      <p>
        Take a look around!
      </p>
    </section>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    display: flex;
    align-items: center;
    padding: 20px;
  }
}
.about-content {
  max-width: 800px;
  margin: 0 auto;
  text-align: center;
}

h1 {
  font-size: 2rem;
  margin-bottom: 20px;
}

p {
  font-size: 1.2rem;
  line-height: 1.5;
  margin-bottom: 20px;
}
</style>