<template>
  <div id="app">
    <global-layout>
      <router-view/>
    </global-layout>
  </div>
</template>
<script>
import GlobalLayout from './components/global-layout';

export default {
  components: {
    GlobalLayout
  }
};
</script>

<style lang="scss">
body {
  margin: 0;
  padding: 0;
  height: 100vh;

  & #app {
    height: 100%;
  }
}
</style>
