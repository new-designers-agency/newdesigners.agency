<template>
  <main>
    <!-- Hero -->
    <section id="hero">
      <div class="container">
        <h1>{{ project.title }}</h1>
      </div>
    </section>

    <article>
      <p>{{ formatDate(project["publish-date"]) }}</p>
      <p>{{ project.categories }}</p>
      <p>{{ project.languages }}</p>
      <Project />
    </article>
  </main>
</template>

<script>
export default {
  data() {
    return {
      project: []
    };
  },

  async fetch() {
    this.project = await this.$content(this.$route.path).fetch();
    console.log(this.$route.path);
    console.log(this.project);
  },

  methods: {
    formatDate(date) {
      const options = { year: "numeric", month: "long", day: "numeric" };
      return new Date(date).toLocaleDateString("nl", options);
    }
  }
};
</script>
