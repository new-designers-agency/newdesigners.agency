<template>
  <main>
    <!-- Hero -->
    <section id="hero">
      <div class="container">
        <h1>{{ project[`title`] }}</h1>
      </div>
    </section>

    <!-- Project -->
    <section id="project">
      <div class="container flex justify-between max-w-6xl">
        <article class="pr-2 text-justify flex-1">
          <p class="mb-1">
            Posted at: {{ formatDate(project[`publish-date`]) }}
          </p>

          <p class="mb-1 whitespace-pre-line">
            {{ project[`project-description`] }}
          </p>
        </article>

        <aside class="bg-gray shadow-md p-1 w-20">
          <h2 class="text-left mb-1">Project info</h2>

          <!-- Categories -->
          <div class="mb-1">
            <h4>Categories</h4>
            <template v-for="(categorie, name, index) in project[`categories`]">
              <span
                v-if="categorie === true"
                :key="index"
                class="badge badge-primary"
              >
                {{ capitalize(name) }}</span
              >
            </template>
          </div>

          <!-- Languages -->
          <div class="mb-1">
            <h4>Languages</h4>
            <template v-for="(language, name, index) in project[`languages`]">
              <span v-if="language === true" :key="index">
                {{ capitalize(name) }}</span
              >
            </template>
          </div>

          <!-- Estimated duration -->
          <div class="mb-1">
            <h4>Estimated duration</h4>
            <span>{{ project[`estimated-duration`] }}</span>
          </div>

          <h2 class="text-left mb-1">Company info</h2>

          <!-- Company name -->
          <div class="mb-1">
            <h4>Company name</h4>
            <span>{{ project[`company-name`] }}</span>
          </div>

          <!-- Company website -->
          <div class="mb-1">
            <h4>Company website</h4>
            <span>{{ project[`company-website`] }}</span>
          </div>
        </aside>
      </div>
    </section>
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
  },

  methods: {
    formatDate(date) {
      const options = { year: "numeric", month: "long", day: "numeric" };
      return new Date(date).toLocaleDateString("nl", options);
    },
    capitalize(value) {
      if (!value) return "";
      value = value.toString();
      value = value.charAt(0).toUpperCase() + value.slice(1);
      return value.replace(/-/g, " ");
    }
  }
};
</script>
