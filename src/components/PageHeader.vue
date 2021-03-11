<template>
  <header>
    <div class="container">
      <a class="logo" href="/"><img alt="" src="~@/assets/images/header_logo.png"></a>
      <div class="center">
        <ul>
          <li v-for="(item,index) in nav.list" :key="index"
              :class="{'active':nav.curIndex===index}"
              class="nav"
              @click="changeNav(index)">{{ item.name }}
          </li>
        </ul>
        <div class="search">
          <el-dropdown trigger="hover">
            <span class="el-dropdown-link">
              {{ searchType.curType }}&nbsp;<i class="el-icon-arrow-down el-icon--right"></i>
              </span>
            <el-dropdown-menu slot="dropdown">
              <el-dropdown-item v-for="type in searchType.list"
                                :key="type"
                                @click.native="changeSearchType(type)">{{ type }}
              </el-dropdown-item>
            </el-dropdown-menu>
          </el-dropdown>
          <input placeholder="请输入搜索内容" type="text">
          <span class="search-icon el-icon-search"></span>
        </div>
      </div>
      <div class="right-actions">
        <div class="learning-centre">学习中心</div>
        <el-badge :value="1" class="item">
          <span class="icon message el-icon-bell"></span>
        </el-badge>
        <el-badge :value="3" class="item">
          <span class="icon cart el-icon-shopping-cart-2"></span>
        </el-badge>
        <img alt="" class="header-avatar" src="~@/assets/images/header_avatar.png">
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: "PageHeader",
  components: {},
  data() {
    return {
      nav: {
        curIndex: 0,
        list: [{name: '首页', link: ''}, {name: '选课', link: ''}, {name: '公开课', link: ''},
          {name: '名师', link: ''}, {name: '金职位', link: ''}, {name: '专栏', link: ''}, {name: '下载APP', link: ''}]
      },
      searchType: {
        curType: '课程',
        list: ['课程', '问答', '咨询', '专栏']
      }
    }
  },
  methods: {
    changeNav(index) {
      this.nav.curIndex = index
    },
    changeSearchType(type) {

      this.searchType.curType = type
    }
  }
}
</script>

<style lang="scss" scoped>
@import "~@/assets/style/base";

header {
  width: 100%;
  height: $header-height;
  background-color: $base-color;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.3), 0 0 6px rgba(0, 0, 0, .3);

}

.container {
  width: 1920px;
  background-color: $base-color;
  height: 100%;
  margin: 0 auto;
  position: relative;
}

.logo {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  margin-left: 60px;
}

.center {
  width: 1250px;
  height: $header-height;
  margin: auto;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.nav {
  float: left;
  height: $header-height;
  line-height: $header-height;
  width: 74px;
  text-align: center;
  color: mix(#fff, $base-color, 75%);
  cursor: pointer;
  user-select: none;
  transition: all .3s;

  &:hover, &.active {
    background-color: mix(#000, $base-color, 10%);
    color: #fff;
  }
}

.search {
  $input-height: 40px;
  width: 464px;
  height: $input-height;
  background-color: #fff;
  border-radius: 20px;
  display: flex;

  .el-dropdown {
    margin-left: 20px;
    height: $input-height;
    line-height: $input-height;

    .el-dropdown-link {
      cursor: pointer;
      color: #666;
    }

    .el-icon-arrow-down {
      font-size: 14px;
    }
  }

  input {
    border: none;
    outline: none;
    padding-left: 15px;
    flex: 1;
  }

  .search-icon {
    width: 50px;
    height: $input-height;
    line-height: $input-height;
    text-align: center;
    font-size: 24px;
    color: #666;
  }
}

.right-actions {
  height: $header-height;
  display: flex;
  position: absolute;
  right: 0;
  top: 0;
  align-items: center;
  justify-content: space-around;
  width: 300px;
  box-sizing: border-box;
  cursor: pointer;
  padding-right: 50px;

  .icon {
    font-size: 28px;
    color: #fff;
    transition: font-size 0.2s;
    display: inline-block;
    width: 24px;
    height: 24px;

  }

  .icon {
    &:hover {
      font-size: 32px;
      animation: shake .3s ease;
    }
  }

  .message {
    transform-origin: top;
  }

  .cart {
    transform-origin: bottom;
  }

  @keyframes shake {
    0% {
      transform: rotate(6deg);
    }
    20% {
      transform: rotate(-6deg);
    }
    40% {
      transform: rotate(-4deg);
    }
    60% {
      transform: rotate(4deg);
    }
    80% {
      transform: rotate(-2deg);
    }
    100% {
      transform: rotate(2deg);
    }
  }

  .learning-centre {
    color: #fff;
    font-size: 14px;
    width: 60px;
    text-align: center;
    transition: font-size .05s;

    &:hover {
      font-size: 15px;
    }
  }

  .header-avatar {
    width: 40px;
    height: 40px;
    border-radius: 20px;
  }
}
</style>

<style>
.el-badge__content {
  border: none;
}
</style>