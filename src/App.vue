<template>
  <div id="app">
    <!-- <router-view/> -->

    <el-menu :default-active="activeIndex" class="el-menu-demo" mode="horizontal" @select="handleSelect" style="margin-bottom:10px">
      <el-menu-item index="1" style="font-size:16px;width: 140px;">My Bio</el-menu-item>
      <el-menu-item index="2" style="font-size:16px;width: 140px;">Only For 🌼盈🤫</el-menu-item>
      <!-- <el-submenu index="2">
        <template slot="title">我的工作台</template>
        <el-menu-item index="2-1">选项1</el-menu-item>
        <el-menu-item index="2-2">选项2</el-menu-item>
        <el-menu-item index="2-3">选项3</el-menu-item>
        <el-submenu index="2-4">
          <template slot="title">选项4</template>
          <el-menu-item index="2-4-1">选项1</el-menu-item>
          <el-menu-item index="2-4-2">选项2</el-menu-item>
          <el-menu-item index="2-4-3">选项3</el-menu-item>
        </el-submenu>
      </el-submenu> -->
      <!-- <el-menu-item index="3" disabled>消息中心</el-menu-item>
      <el-menu-item index="4"><a href=" " target="_blank">订单管理</a></el-menu-item> -->
    </el-menu>

    <el-row v-if="activeIndex==1">
      <h1>I CAN DO ALL THINGS!</h1>
      <el-row style="margin-top:40px">
        <el-col :offset="4" :span="16">
          <el-image
          :src="require('@/assets/IMG_4672.jpg')"
          :fit="contain"></el-image>
        </el-col>
      </el-row>
    </el-row>
    <el-row v-if="activeIndex==2" style="margin-top:40px">
      <el-col :offset="4" :span="16">
        <template>
          <el-carousel trigger="click" :interval="4000" type="card" height="250px" width="800px">
            <el-carousel-item v-for="item in 6" :key="item">
              <h3 class="medium">{{ item }}</h3>
            </el-carousel-item>
          </el-carousel>
        </template>
      </el-col>
    </el-row>
  </div>
</template>

<script>
export default {
  name: 'App',
  data () {
    return {
      activeIndex: '1',
    }
  },
  methods: {
    handleSelect(key, keyPath) {
      this.activeIndex = key;
      console.log(key, keyPath);
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.el-carousel__item h3 {
    color: #475669;
    font-size: 14px;
    opacity: 0.75;
    line-height: 200px;
    margin: 0;
  }
  
.el-carousel__item:nth-child(2n) {
  background-color: #99a9bf;
}

.el-carousel__item:nth-child(2n+1) {
  background-color: #d3dce6;
}
</style>
