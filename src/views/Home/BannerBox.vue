<template>
  <section class="container" ref="container">
    <div class="content">
      <div class="left-menu" @mouseleave="leftMenuMouseLeave">
        <div class="menu-items">
          <div v-for="(item,index) in menu.list"
               :key="index" :class="{active:menu.curIndex===index}"
               class="menu-item"
               @mouseenter="e=>menuItemMouseEnter(e,index)">
            <div class="menu-name"><span>{{ item.name }}</span><span class="right-arrow el-icon-arrow-right"></span>
            </div>
            <div class="submenu">
              <a v-for="(subItem,subIndex) in item.subMenu"
                       :key="subItem.name" class="sub-menu-item">
                {{ subItem.name }}
                <span v-if="subIndex!==item.subMenu.length-1">|</span></a>
            </div>
          </div>
        </div>

        <div :style="{left:(menu.curIndex!==null)?'250px':'-1000px'}" class="course-recommend">
          <template v-if="menu.curIndex!==null">
            <div class="title">课程推荐</div>
            <div class="courses">
              <div v-for="(item,index)  in menu.list[menu.curIndex].courseRecommend" :key="index" class="course">
                <img :src="item.img" alt="">
                <div class="course-name">{{ item.name }}</div>
                <div class="course-desc">{{ item.desc }}</div>
              </div>
            </div>
            <div class="title">了解更多</div>
            <div class="more">
              <div v-for="(item,index) in menu.list[menu.curIndex].learMore" :key="index" class="more-item">{{
                  item.name
                }}
              </div>
            </div>
          </template>
        </div>
      </div>
      <div class="right-banner">
        <el-carousel height="100%" trigger="click" @change="bannerChange">
          <el-carousel-item v-for="(item,index) in bannerImg.list" :key="index">
            <img alt="" :src="item.img" :ref="'banner_'+index">
          </el-carousel-item>
        </el-carousel>
      </div>
    </div>
  </section>
</template>

<script>
import ColorThief from 'colorthief'

export default {
  name: "BannerBox",
  components: {},
  data() {
    return {
      menu: {
        curIndex: null,
        list: [
          {
            name: '互联网',
            subMenu: [{name: '电商运营', link: ''}, {name: '抖音短视频', link: ''}, {name: 'UI设计', link: ''}],
            courseRecommend: [
              {name: 'PS零基础精品系列课1', desc: '0基础入门到精通', img: require('@/assets/images/course_recommend1.png')},
              {name: 'PS零基础精品系列课1', desc: '0基础入门到精通', img: require('@/assets/images/course_recommend1.png')},
              {name: 'PS零基础精品系列课1', desc: '0基础入门到精通', img: require('@/assets/images/course_recommend1.png')},
              {name: 'PS零基础精品系列课1', desc: '0基础入门到精通', img: require('@/assets/images/course_recommend1.png')}],
            learMore: [{name: '就业'}, {name: 'UI设计'}, {name: '考证'}, {name: '就业'}]
          }, {
            name: '兴趣艺术',
            subMenu: [{name: '摄影', link: ''}, {name: '乐器', link: ''}, {name: '美妆', link: ''}, {name: '育儿', link: ''}],
            courseRecommend: [
              {name: 'PS零基础精品系列课2', desc: '0基础入门到精通', img: require('@/assets/images/course_recommend2.png')},
              {name: 'PS零基础精品系列课2', desc: '0基础入门到精通', img: require('@/assets/images/course_recommend2.png')},
              {name: 'PS零基础精品系列课2', desc: '0基础入门到精通', img: require('@/assets/images/course_recommend2.png')},
              {name: 'PS零基础精品系列课2', desc: '0基础入门到精通', img: require('@/assets/images/course_recommend2.png')}],
            learMore: [{name: '就业'}, {name: 'UI设计'}, {name: '考证'}, {name: '就业'}]
          }, {
            name: '设计创作',
            subMenu: [{name: '品面设计', link: ''}, {name: '室内设计', link: ''}, {name: '电商设计', link: ''}],
            courseRecommend: [
              {name: 'PS零基础精品系列课3', desc: '0基础入门到精通', img: require('@/assets/images/course_recommend3.png')},
              {name: 'PS零基础精品系列课3', desc: '0基础入门到精通', img: require('@/assets/images/course_recommend3.png')},
              {name: 'PS零基础精品系列课3', desc: '0基础入门到精通', img: require('@/assets/images/course_recommend3.png')},
              {name: 'PS零基础精品系列课3', desc: '0基础入门到精通', img: require('@/assets/images/course_recommend3.png')}],
            learMore: [{name: '就业'}, {name: 'UI设计'}, {name: '考证'}, {name: '就业'}]
          }, {
            name: '实用外语',
            subMenu: [{name: '托福', link: ''}, {name: '雅思', link: ''}, {name: '日语', link: ''}, {name: '韩语', link: ''}],
            courseRecommend: [
              {name: 'PS零基础精品系列课4', desc: '0基础入门到精通', img: require('@/assets/images/course_recommend4.png')},
              {name: 'PS零基础精品系列课4', desc: '0基础入门到精通', img: require('@/assets/images/course_recommend4.png')},
              {name: 'PS零基础精品系列课4', desc: '0基础入门到精通', img: require('@/assets/images/course_recommend4.png')},
              {name: 'PS零基础精品系列课4', desc: '0基础入门到精通', img: require('@/assets/images/course_recommend4.png')}],
            learMore: [{name: '就业'}, {name: 'UI设计'}, {name: '考证'}, {name: '就业'}]
          }, {
            name: '学历考证',
            subMenu: [{name: '大专学历', link: ''}, {name: '本科学历', link: ''}, {name: 'ACAA', link: ''}],
            courseRecommend: [
              {name: 'PS零基础精品系列课5', desc: '0基础入门到精通', img: require('@/assets/images/course_recommend1.png')},
              {name: 'PS零基础精品系列课5', desc: '0基础入门到精通', img: require('@/assets/images/course_recommend1.png')},
              {name: 'PS零基础精品系列课5', desc: '0基础入门到精通', img: require('@/assets/images/course_recommend1.png')},
              {name: 'PS零基础精品系列课5', desc: '0基础入门到精通', img: require('@/assets/images/course_recommend1.png')}],
            learMore: [{name: '就业'}, {name: 'UI设计'}, {name: '考证'}, {name: '就业'}]
          }


        ]
      },
      bannerImg: {
        curIndex: 0,
        list: [
          {img: require('@/assets/images/u231.svg'), link: ''},
          {img: require('@/assets/images/u233.svg'), link: ''},
          {img: require('@/assets/images/u235.svg'), link: ''},
          {img: require('@/assets/images/u236.svg'), link: ''},
        ]
      }
    }
  },
  mounted() {

  },
  methods: {
    menuItemMouseEnter(e, index) {
      this.menu.curIndex = index
    },
    leftMenuMouseLeave() {
      this.menu.curIndex = null
    },
    bannerChange(index) {
      let curBannerImg = this.$refs['banner_' + index] && this.$refs['banner_' + index][0] || null;
      let colorThief = new ColorThief();
      let container = this.$refs.container
      let bgColor = getComputedStyle(document.getElementById('app')).backgroundColor
      let rgb = colorThief.getColor(curBannerImg)
      container.style.backgroundImage = `linear-gradient(to bottom, rgba(${rgb[0]}, ${rgb[1]}, ${rgb[2]}, 0.3), ${bgColor})`
    }
  }
}
</script>

<style lang="scss" scoped>
@import "~@/assets/style/base";

$menu-width: 250px;
$menu-item-height: 86px;
$course-recommend-width: 740px;
.container {
  width: 100%;
  padding-top: 60px;
  --bg-color: $bg-color;
}

.content {
  width: $content-width;
  margin: 0 auto;
  overflow: hidden;
  box-shadow: 0 5px 20px 0 rgb(0 0 0 / 30%);
  background-color: #fff;
  display: flex;
}

.left-menu {
  width: $menu-width;
  position: relative;
}

.menu-items {
  position: relative;
  z-index: 99;
}

.menu-item {
  height: $menu-item-height;
  background-color: $dark;
  border-bottom: 1px solid mix(#fff, $dark, 15%);
  padding: 20px 20px 0 20px;
  box-sizing: border-box;
  transition: background-color .3s;

  &.active {
    background-color: mix(#fff, $dark, 15%);
  }

  &.active .sub-menu-item {
    color: #fff;
  }
}

.menu-name {
  color: #fff;
  display: flex;
  justify-content: space-between;
}

.submenu {
  margin-top: 15px;
}

.sub-menu-item {
  color: #666;
  font-size: 14px;
  cursor: pointer;
  transition: color .3s;
}

.el-link.is-underline:hover:after {
  border-color: #fff;
}

.course-recommend {
  width: $course-recommend-width;
  height: $menu-item-height*5;
  background-color: #fff;
  position: absolute;
  left: $menu-width;
  top: 0;
  transition: left 0.2s ease;
  z-index: 9;

  .title {
    font-size: 16px;
    color: #333;
    padding: 30px;
  }
}

.courses {
  display: flex;
  padding: 30px;
  justify-content: space-between;
  background-color: mix(#fff, $base-color, 85%);

  img {
    width: 150px;
    height: 90px;
  }

  .course-name {
    font-size: 14px;
    color: #333;
    margin-top: 24px;
  }

  .course-desc {
    font-size: 12px;
    color: #999;
    margin-top: 10px;
  }
}

.more {
  width: 100%;
  display: flex;

  .more-item {
    width: 70px;
    height: 25px;
    line-height: 25px;
    text-align: center;
    background-color: mix(#fff, $base-color, 20%);
    margin-left: 30px;
    font-size: 14px;
    color: #fff;
  }
}

.right-banner {
  height: $menu-item-height*5;
  flex: 1;
}

.el-carousel {
  height: $menu-item-height*5;
  width: 100%;

  img {
    width: 100%;
    height: 100%;
  }
}
</style>