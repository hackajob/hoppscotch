<template>
  <footer class="flex-col flex-no-wrap">
    <div class="row-wrapper">
      <span v-if="version.name" class="font-mono">
        <a
          class="footer-link"
          :href="'https://github.com/hoppscotch/hoppscotch/releases/tag/' + version.name"
          target="_blank"
          rel="noopener"
          v-tooltip="'GitHub'"
        >
          {{ version.name }}
        </a>
        <a
          class="footer-link hide-on-small-screen"
          href="https://www.netlify.com"
          target="_blank"
          rel="noopener"
        >
          Powered by Netlify
        </a>
        <!-- <span v-if="version.hash">
          -
          <a
            :href="'https://github.com/hoppscotch/hoppscotch/commit/' + version.hash"
            target="_blank"
            rel="noopener"
          >{{version.hash}}</a>
        </span> -->
        <!-- <span v-if="version.variant">({{version.variant}})</span> -->
      </span>
    </div>
  </footer>
</template>

<style scoped lang="scss">
.footer-link {
  @apply my-2;
  @apply mx-4;
  @apply text-fgLightColor;

  &:hover {
    @apply text-fgColor;
  }
}
</style>

<script>
import * as version from "../../.hoppscotch/version.json"

export default {
  data() {
    return {
      version: {},
    }
  },

  beforeMount() {
    // Set version data
    this.version = version.default
  },

  computed: {
    availableLocales() {
      return this.$i18n.locales.filter(({ code }) => code !== this.$i18n.locale)
    },
  },
}
</script>
