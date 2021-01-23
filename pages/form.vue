<template>
  <main>
    <!-- Hero -->
    <section id="hero">
      <div class="container">
        <h1 class="mb-2">Post a design project</h1>
      </div>
    </section>
    <form
      name="post-a-design-project"
      action="/thanks"
      method="post"
      netlify
      netlify-honeypot="bot-field"
    >
      <input type="hidden" name="form-name" value="post-a-design-project" />

      <!-- Project info -->
      <section>
        <div class="container max-w-3xl">
          <h2 class="text-left mb-1">What kind of project is it?</h2>

          <!-- Categories -->
          <div id="categories" class="form-group">
            <span>Please check all categories that may apply.</span>

            <div class="flex flex-col flex-wrap sm:flex-row">
              <div
                class="form-check"
                v-for="category in categories"
                :key="category"
              >
                <input
                  class="form-check-input"
                  type="checkbox"
                  :name="category"
                  :id="category"
                />

                <label class="form-check-label" :for="category">
                  {{ category | capitalize }}
                </label>
              </div>
            </div>
          </div>

          <!-- Language -->
          <div class="form-group">
            <span>Project language preference.</span>

            <div
              class="form-check"
              v-for="language in languages"
              :key="language"
            >
              <input
                class="form-check-input"
                type="radio"
                name="language"
                :id="language | lowercase"
              />

              <label class="form-check-label" :for="language | lowercase">
                {{ language }}
              </label>
            </div>
          </div>

          <!-- Project title -->
          <div class="form-group">
            <label for="project-title">Project title *</label>
            <input
              type="text"
              name="project-title"
              class="form-control"
              id="project-title"
              required
            />
          </div>
          <div>
            <label for="name" class="block">Name:</label>
            <input type="text" name="name" class="border" required />
          </div>
          <div>
            <label for="email" class="block">Email:</label>
            <input type="email" name="email" class="border" required />
          </div>
          <div>
            <label for="message" class="block">Message:</label>
            <textarea name="message" class="border" required></textarea>
          </div>
          <button type="submit" value="Send message" class="btn btn-primary">
            Send
          </button>
        </div>
      </section>
    </form>
  </main>
</template>

<script>
export default {
  data() {
    return {
      categories: [
        "internship",
        "graduation-project",
        "freelance",
        "paid",
        "unpaid",
        "research",
        "design",
        "development"
      ],
      languages: ["English or Dutch", "Only English", "Only Dutch"]
    };
  },
  filters: {
    capitalize: function(value) {
      if (!value) return "";
      value = value.toString();
      value = value.charAt(0).toUpperCase() + value.slice(1);
      return value.replace("-", " ");
    },
    lowercase: function(value) {
      if (!value) return "";
      value = value.toString();
      return value.replace(/\s+/g, "-").toLowerCase();
    }
  }
};
</script>
