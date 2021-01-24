<template>
  <main>
    <!-- Hero -->
    <section id="hero">
      <div class="container">
        <h1>{{ project[`title`] }}</h1>
      </div>
    </section>

    <article>
      <p class="mb-1">Posted at: {{ formatDate(project[`publish-date`]) }}</p>

      <div class="mb-1">
        <p
          v-for="(categorie, name, index) in project[`categories`]"
          :key="index"
        >
          <span v-if="categorie === true"> {{ capitalize(name) }}</span>
        </p>
      </div>

      <div class="mb-1">
        <p v-for="(language, name, index) in project[`languages`]" :key="index">
          <span v-if="language === true"> {{ capitalize(name) }}</span>
        </p>
      </div>

      <p class="mb-1 whitespace-pre-line">
        {{ project[`project-description`] }}
      </p>

      <p class="mb-1">
        {{ project[`estimated-duration`] }}
      </p>

      <p class="mb-1">{{ project[`company-name`] }}</p>

      <p class="mb-1">{{ project[`company-website`] }}</p>

      <p class="mb-1">{{ project[`contact-name`] }}</p>

      <p class="mb-1">{{ project[`contact-email`] }}</p>

      <p>{{ project[`contact-phone-number`] }}</p>
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
