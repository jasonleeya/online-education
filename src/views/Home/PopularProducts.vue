<template>
  <section>
    <section-title>热门产品</section-title>
    <div class="content">
      <div class="product-category" v-for="(category,cIndex) in product" :key="cIndex">
        <div class="left-introduction">
          <div class="title">{{ category.name }}</div>
          <div class="detail">
            <p v-for="(desc,dIndex) in category.desc" :key="dIndex">{{ desc }}</p>
          </div>
          <div class="learn-more">了解更多</div>
          <img alt="" class="picture" :src="category.picture">
        </div>
        <div class="products">
          <div class="product" v-for="(item,index) in category.list" :key="index">
            <div class="discount">
              <span>{{ calculateDiscount(item.price, item.originalPrice) }}</span>
            </div>
            <img class="cover" :src="item.cover" alt="">
            <div class="name">{{ item.name }}</div>
            <div class="desc">{{ item.desc }}</div>
            <div class="lesson-count-and-tags"><span>共{{ item.lessonCount }}课时</span><span
                v-for="(tag,tIndex) in item.tags" :key="tIndex"> | {{ tag }}</span></div>
            <div class="price">
              <span class="now">￥ {{ Number(item.price).toFixed(2) }}</span>
              <span class="original">￥ {{ Number(item.originalPrice).toFixed(2) }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import SectionTitle from "@/components/SectionTitle";

export default {
  name: "PopularProducts",
  components: {SectionTitle},
  data() {
    return {
      product: [
        {
          name: '互联网',
          desc: ['数据可视化入门到精通', '打造前端差异化竞争力体系课', '数据可视化入门到精通'],
          picture: require('@/assets/images/network.png'),
          list: [
            {
              name: '自媒体运营|新媒体运营|微信公众号',
              desc: '教你5个提升卡片式UI设计质量的小细节',
              cover: require('@/assets/images/product_cover1.jpg'),
              tags: ['随到随学', '入门'],
              lessonCount: 30,
              price: 980,
              originalPrice: 1980,
            }, {
              name: '短视频剪辑自媒体爆文吸粉VLOG引流',
              desc: '教你5个提升卡片式UI设计质量的小细节',
              cover: require('@/assets/images/product_cover2.jpg'),
              tags: ['随到随学', '入门'],
              lessonCount: 30,
              price: 1980,
              originalPrice: 2580,
            }, {
              name: '自媒体运营|新媒体运营|微信公众号',
              desc: '教你5个提升卡片式UI设计质量的小细节',
              cover: require('@/assets/images/product_cover3.jpg'),
              tags: ['随到随学', '入门'],
              lessonCount: 30,
              price: 2580,
              originalPrice: 3600,
            }, {
              name: '自媒体运营|新媒体运营|微信公众号',
              desc: '教你5个提升卡片式UI设计质量的小细节',
              cover: require('@/assets/images/product_cover1.jpg'),
              tags: ['随到随学', '入门'],
              lessonCount: 30,
              price: 980,
              originalPrice: 1980,
            }, {
              name: '短视频剪辑自媒体爆文吸粉VLOG引流',
              desc: '教你5个提升卡片式UI设计质量的小细节',
              cover: require('@/assets/images/product_cover2.jpg'),
              tags: ['随到随学', '入门'],
              lessonCount: 30,
              price: 1980,
              originalPrice: 2580,
            }, {
              name: '自媒体运营|新媒体运营|微信公众号',
              desc: '教你5个提升卡片式UI设计质量的小细节',
              cover: require('@/assets/images/product_cover3.jpg'),
              tags: ['随到随学', '入门'],
              lessonCount: 30,
              price: 2580,
              originalPrice: 3600,
            },
          ]
        }
      ]
    }
  },
  computed: {
    calculateDiscount() {
      return (now, org) => {
        if (!now || !org) {
          return '10.0';
        } else {
          return (parseFloat(now) / parseFloat(org) * 10).toFixed(1) + '折'

        }
      }
    }
  }
}
</script>

<style lang="scss" scoped>
@import "~@/assets/style/base";

$product-height: 310px;
.product-category {
  display: flex;
}

.left-introduction {
  height: $product-height * 2;
  min-width: 285px;
  background-color: $base-color;
  padding-top: 35px;
  box-sizing: border-box;

  .title {
    width: 215px;
    height: 90px;
    line-height: 90px;
    margin-left: 35px;
    border-top: 1px solid mix(#fff, $base-color, 40%);
    border-bottom: 1px solid mix(#fff, $base-color, 40%);
    text-align: center;
    font-size: 36px;
    color: #fff;
  }

  .detail {
    font-size: 16px;
    color: #fff;
    text-align: center;
    padding-top: 25px;

    p {
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
    margin: 60px auto 80px;
    user-select: none;
    cursor: pointer;
  }

  .picture {
    margin: auto;
    position: relative;
    left: 50%;
    transform: translateX(-50%);
  }
}

.products {
  $border-color: #eee;
  display: flex;
  flex-wrap: wrap;
  border-top: 1px solid $border-color;
  border-left: 1px solid $border-color;

  .product {
    box-sizing: border-box;
    width: calc(100% / 3);
    background-color: #fff;
    border-bottom: 1px solid $border-color;
    border-right: 1px solid $border-color;
    padding: 20px;
    position: relative;

    &:hover{
      background-color: rgba($base-color,.1);
      border: 1px solid mix(#fff,$base-color,.4);
    }
    .cover {
      width: 100%;
      max-height: 125px;
    }

    .discount {
      position: absolute;
      top: 20px;
      left: 20px;
      font-size: 16px;
      width: 100px;
      height: 100px;
      overflow: hidden;

      span {
        position: relative;
        top: 12px;
        left: 7px;
        z-index: 9;
        color: #fff;
      }

      &::after {
        content: '';
        display: block;
        width: 120px;
        height: 100%;
        background-color: rgba(#FF2E65, .8);
        position: absolute;
        transform: rotate(-39deg) translate(5%, -84%);;
      }
    }

    .name {
      font-size: 16px;
      color: #333;
      margin: 18px 0 12px;
    }

    .desc {
      font-size: 14px;
      color: #999;
      margin-bottom: 12px;
    }

    .lesson-count-and-tags {
      font-size: 14px;
      color: #666;
      margin-bottom: 35px;
    }

    .price {
      color: #f65314;

      .now {
        font-size: 18px;
      }

      .original {
        font-size: 12px;
        text-decoration: line-through;
        float: right;
      }
    }
  }
}
</style>