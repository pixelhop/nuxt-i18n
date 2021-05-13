<template>
  <nav>
    <ul class="flex">
      <li
        v-for="locale in availableLocales"
        :key="locale"
        class="py-4 px-4 text-xl font-bold"
      >
        <nuxt-link :to="switchLocalePath(locale)">
          {{ locale }}
        </nuxt-link>
      </li>
    </ul>
  </nav>
</template>

<script>
export default {
  computed: {
    availableLocales () {
      return this.$i18n.locales.filter(i => i.code !== this.$i18n.locale)
    }
  }
}
</script>
