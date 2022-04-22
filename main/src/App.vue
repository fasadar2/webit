<template>
  <div id = "app">
  <Head></Head>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import Head from '../../head/src/components/head.vue';

export default Vue.extend({
  name: 'App',
  components: {
    Head,
  },
});
</script>
