<template>
  <div id="app">
      <header>
        <page-header></page-header>
      </header>
      <main>
        <router-view/>
      </main>
  </div>
</template>
<script>
import PageHeader from "@/components/PageHeader";

export default {
  components: {
    PageHeader
  }
}
</script>
<style lang="scss">
@import "~@/assets/style/base";
#app {
  background-color: $bg-color;
  height: 2000px;
}
header {
  position: fixed;
  top: 0;
  left: 0;
  z-index: 999;
}
main {
  margin-top: $header-height;
}
</style>
