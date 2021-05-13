<template>
  <div class="container flex flex-col items-center">
    <div class="flex flex-col items-center">
      <h1 class="mb-4 text-pink-700 font-bold">
        {{ home.Title }}
      </h1>
      <div class="mb-4 text-green-700">
        {{ home.Body }}
      </div>
      <img :src="`http://localhost:1337${home.Image.url}`" class="w-1/4 mb-6" alt="Featured Image">
      <LocaleSwitcher />
    </div>
  </div>
</template>

<script>
import LocaleSwitcher from '~/components/LocaleSwitcher.vue'
export default {
  components: {
    LocaleSwitcher
  },
  async asyncData ({ $strapi, i18n }) {
    const home = await $strapi.$home.find({ _locale: i18n.locale })
    return {
      home
    }
  }
}
</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
@apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
