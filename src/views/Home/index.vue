<template>
  <div class="home">
    <banner-box></banner-box>
    <div class="center">
      <popular-open-classes></popular-open-classes>
      <popular-products></popular-products>
    </div>
  </div>
</template>

<script>
import BannerBox from "@/views/Home/BannerBox";
import PopularOpenClasses from "@/views/Home/PopularOpenClasses";
import PopularProducts from "@/views/Home/PopularProducts";

export default {
  name: "Home",
  components: {PopularProducts, PopularOpenClasses, BannerBox},
  mounted() {

  },
  methods: {

  }
}
</script>

<style scoped lang="scss">
@import "~@/assets/style/base";
.center {
  width: $content-width;
  margin: 0 auto;
}
</style>