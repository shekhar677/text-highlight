<template>
  <div class="max-w-screen-2xl mx-auto font-tinos">
    <app-header/>
    <div class="bg-bg-gray min-h-screen">
      <Nuxt />
    </div>
    <app-footer/>
  </div>
</template>

<script>
import AppFooter from '~/components/appFooter.vue';
import AppHeader from '~/components/appHeader.vue';

export default {
  components: {
    AppFooter,
    AppHeader
  }
}
</script>

<style>

html {
  font-family: 'Tinos', serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
}

body {
  background: #E5E5E5;
}
</style>
