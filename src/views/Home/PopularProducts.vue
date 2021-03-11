<template>
  <section>
    <section-title>热销产品</section-title>
    <div class="left-introduction">
      <div class="title">互联网</div>
      <div class="detail">
        <p>数据可视化入门到精通</p>
        <p>打造前端差异化竞争力体系课</p>
        <p>数据可视化入门到精通</p>
      </div>
      <div class="learn-more">了解更多</div>
    </div>
  </section>
</template>

<script>
import SectionTitle from "@/components/SectionTitle";

export default {
  name: "HotProducts",
  components: {SectionTitle}
}
</script>

<style lang="scss" scoped>
@import "~@/assets/style/base";

$product-height: 310px;
.left-introduction {
  height: $product-height * 2;
  width: 285px;
  background-color: $base-color;
  padding-top: 35px;
  .title {
    width: 215px;
    height: 90px;
    line-height: 90px;
    margin-left: 35px;
    border-top: 1px solid #fff;
    border-bottom: 1px solid #fff;
    text-align: center;
    font-size: 36px;
    color: #fff;
  }
  .detail {
    font-size: 16px;
    color: #fff;
    text-align: center;
    padding-top: 25px;

    p{
      line-height: 1.8em;
    }
  }
  .learn-more {
    width: 170px;
    height: 45px;
    background-color: mix(#fff, $base-color, 40%);
    border-radius: 23px;
    line-height: 45px;
    text-align: center;
    color: #fff;
    margin: 30px auto 80px;
    user-select: none;
    cursor: pointer;
  }
}
</style>