<template>
  <v-app-bar
    app
    color="primary"
    dark
    src="../assets/background.png"
    flat
    absolute
  >
    <v-btn
      href="/"
      text
    >
      <v-toolbar-title>
        {{ $t('hero.title') }}
      </v-toolbar-title>
    </v-btn>

    <v-spacer />

    <v-toolbar-items
      v-if="$vuetify.breakpoint.mdAndUp"
      class="d-flex align-center"
    >
      <div
        v-for="item in filteredItems"
        :key="item.title"
      >
        <v-btn
          text
          :href="item.path"
        >
          {{ item.title }}
        </v-btn>
      </div>
      <v-divider
        class="mx-4"
        inset
        vertical
      />
      <locale-switcher />
    </v-toolbar-items>
    <v-toolbar-items v-else>
      <v-btn
        text
        @click="$emit('click-menu')"
      >
        <!--eslint-disable-next-line @intlify/vue-i18n/no-raw-text -->
        <v-icon>menu</v-icon>
      </v-btn>
    </v-toolbar-items>
  </v-app-bar>
</template>

<script>

import LocaleSwitcher from './LocaleSwitcher.vue';

export default {
  components: {
    LocaleSwitcher,
  },
  props: {
    items: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
    };
  },
  computed: {
    // some navigation items aren't meant for display in the toolbar, so filter
    // them out
    filteredItems() {
      return this.items.filter((item) => !item.hideInToolbar);
    },
  },
};
</script>
