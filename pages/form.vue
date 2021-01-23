<template>
  <form
    name="contactus"
    action="/thanks"
    method="post"
    netlify
    netlify-honeypot="bot-field"
  >
    <input type="hidden" name="form-name" value="contactus" />
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
  </form>
</template>
