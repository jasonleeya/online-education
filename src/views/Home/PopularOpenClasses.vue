<template>
  <section class="content">
    <section-title>热门公开课</section-title>
    <div class="courses">
      <div v-for="(item,index) in courses" :key="index" class="course">
        <div class="cover">
          <img class="cover-img" :src="item.cover" alt="">
          <div class="shadow"></div>
          <div class="live"><img src="~@/assets/images/live.gif" alt="">正在直播</div>
          <div class="title">{{ item.title }}</div>
          <div class="learn-now">立即学习</div>
        </div>
        <div class="bottom-info">
          <img class="teacher-avatar" :src="item.teacher.avatar" alt="">
          <span class="teacher-name">{{ item.teacher.name }}</span>
          <span class="viewer">
            <img class="people" src="~@/assets/images/mine.png" alt="">
            {{ item.viewers }}人正在观看
          </span>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import SectionTitle from "@/components/SectionTitle";

export default {
  name: "PopularOpenClasses",
  components: {SectionTitle},
  data() {
    return {
      courses: [
        {
          title: '淘宝开店实操',
          cover: require('@/assets/images/live_cover1.jpg'),
          teacher: {name: '诸葛老师', avatar: require('@/assets/images/teacher_avatar.png')},
          viewers: 250
        },
        {
          title: '抖音短视频',
          cover: require('@/assets/images/live_cover1.jpg'),
          teacher: {name: '彭彭老师', avatar: require('@/assets/images/teacher_avatar.png')},
          viewers: 250
        },
        {
          title: '淘宝开店实操',
          cover: require('@/assets/images/live_cover2.jpg'),
          teacher: {name: '诸葛老师', avatar: require('@/assets/images/teacher_avatar.png')},
          viewers: 250
        },
        {
          title: '淘宝开店实操',
          cover: require('@/assets/images/live_cover1.jpg'),
          teacher: {name: '诸葛老师', avatar: require('@/assets/images/teacher_avatar.png')},
          viewers: 250
        },
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
@import "~@/assets/style/base";

.courses {
  display: flex;
  justify-content: space-between;
}

.course {
  width: calc((100% - 120px) / 4);
  border-radius: 5px;
  overflow: hidden;
  box-shadow: 0 6px 10px 0 rgba(95, 99, 102, .1);
  transition: all .2s;
  position: relative;
  bottom: 0;

  &:hover {
    box-shadow: 0 6px 10px 0 rgba(95, 99, 102, 0.25);
    bottom: 2px;
  }

  .cover {
    width: 100%;
    height: 180px;
    position: relative;

    .shadow {
      width: 100%;
      height: 180px;
      position: absolute;
      top: 0;
      left: 0;
      background: rgba(0, 0, 0, .5);
    }

    .cover-img {
      width: 100%;
      height: 180px;
      position: absolute;
      top: 0;
      left: 0;
    }

    .live {
      width: 115px;
      height: 30px;
      background: rgba(0, 0, 0, .5);
      position: absolute;
      top: 0;
      left: 0;
      color: #fff;
      font-size: 12px;
      letter-spacing: 5px;
      border-bottom-right-radius: 5px;

      img {
        width: 26px;
        position: relative;
        top: 5px;
        margin: 0 5px;
      }
    }

    .title {
      font-size: 24px;
      color: #fff;
      position: absolute;
      top: 60px;
      width: 100%;
      text-align: center;
    }

    .learn-now {
      width: 90px;
      height: 30px;
      line-height: 30px;
      text-align: center;
      border-radius: 15px;
      position: absolute;
      bottom: 40px;
      left: 50%;
      transform: translateX(-50%);
      font-size: 14px;
      cursor: pointer;
      background-color: #fff;
      color: $base-color;
      transition: all .2s;
    }
  }

  &:hover .learn-now {
    background-color: $base-color;
    color: #fff;
  }

  .bottom-info {
    height: 65px;
    line-height: 65px;
    background-color: #fff;
    padding: 0 10px;
    cursor: default;

    .teacher-avatar {
      position: relative;
      width: 30px;
      height: 30px;
      border-radius: 15px;
      top: 8px;
      margin-right: 10px;
    }

    .teacher-name {
      font-size: 14px;
      color: #666;
    }

    .viewer {
      float: right;
      color: #999;
      font-size: 14px;

      .people {
        width: 18px;
        height: 18px;
        position: relative;
        top: 1px;
      }
    }
  }
}

</style>