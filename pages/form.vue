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
          <!-- Project title -->
          <div class="form-group">
            <label for="project-title">Project title *</label>
            <input
              type="text"
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
