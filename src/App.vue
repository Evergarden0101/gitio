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
          :fit='imgFit'></el-image>
        </el-col>
      </el-row>
    </el-row>

    <template>
      <el-dialog title="角色认证" :visible.sync="dialogFormVisible">
        <el-form :model="form" label-width="100px" :label-position="labelPosition">
          <el-form-item label="你怎么喊我" style="margin-left:20px">
            <el-input v-model="form.name" autocomplete="off" style="width:500px;margin-bottom: 10px;" clearable></el-input>
          </el-form-item>
          <el-form-item label="初见" style="margin-left:20px">
            <el-date-picker
              v-model="form.first"
              type="date"
              placeholder="选择日期"
              value-format="yyyy-MM-dd"
              style="width:500px;margin-bottom: 10px;">
            </el-date-picker>
          </el-form-item>
          <el-form-item label="贴贴" style="margin-left:20px">
            <el-date-picker
              v-model="form.date"
              type="date"
              placeholder="选择日期"
              value-format="yyyy-MM-dd"
              style="width:500px;margin-bottom: 10px;">
            </el-date-picker>
          </el-form-item>
        </el-form>
        <div slot="footer" class="dialog-footer">
          <!-- <el-button @click="dialogFormVisible = false">取 消</el-button> -->
          <el-button type="primary" @click="submitForm">确 定</el-button>
        </div>
      </el-dialog>
    </template>

    <el-row v-if="activeIndex==2">
      <el-row style="margin-top:40px">
        <el-col :span="7" :offset="4">
          <aplayer autoplay :music="{
            title: 'Gotta Have You',
            artist: 'The Weepies',
            src: './static/Gotta Have You.mp3',
            pic: '',
            lrc: ''
          }"
          mode = 'single'>
          </aplayer>
        </el-col>
        <el-col :span="6" :offset="1" style="font-size:60px">
          <el-rate
            v-model="rate"
            :colors="colors"
            show-text
            :texts = "texts">
          </el-rate>
        </el-col>
      </el-row>
      <el-row style="margin-top:30px">
        <el-col :span="18" :offset="3" >
          <el-divider><i class="el-icon-service" style="font-size:30px"></i></el-divider>
        </el-col>
      </el-row>
      <el-row style="margin-top:30px">
        <el-col :span="16" :offset="4">
          <template>
            <el-carousel trigger="click" :interval="4000" type="card" height="250px" width="800px">
              <el-carousel-item v-for="item in 6" :key="item">
                <h3 class="medium">{{ item }}</h3>
              </el-carousel-item>
            </el-carousel>
          </template>
        </el-col>
      </el-row>

      <el-row style="margin-top:50px">
        <el-col :span="12" :offset="6">
          <el-timeline>
            <el-timeline-item timestamp="2021/10/17" placement="top" color='#0bbd87'>
              <el-card>
                <h4>认识邱诗盈</h4>
                <p>一起玩 《火花吧》 2021/10/17 14:00</p>
              </el-card>
            </el-timeline-item>
            <el-timeline-item timestamp="2022/01/03" placement="top" color='#0bbd87'>
              <el-card>
                <h4>和小花花在一起啦</h4>
                <p>🌼の恋 开始于 2022/01/03 ～02:00</p>
              </el-card>
            </el-timeline-item>
            <el-timeline-item timestamp="2022/09/05" placement="top" color='#0bbd87'>
              <el-card>
                <h4>和小花花暂时分别啦</h4>
                <p>✈️瑞士读书 在机场分开 2022/09/05 16:10</p>
              </el-card>
            </el-timeline-item>
            <el-timeline-item timestamp="2023/01/03" placement="top" color='#0bbd87'>
              <el-card>
                <h4>和小花花在一起一周年啦，怎么才第一年！还会有很多很多年！</h4>
                <p>甜甜契约✍️ 有效期至 2222/13/14 05:21</p>
              </el-card>
            </el-timeline-item>
          </el-timeline>
        </el-col>
      </el-row>

    </el-row>
  </div>
</template>

<script>
import aplayer from 'vue-aplayer'
export default {
  name: 'App',
  components: {
    aplayer
  },
  data () {
    return {
      activeIndex: '2',
      dialogFormVisible: false,
      labelPosition: 'left',
      imgFit:'contain',
      rate: null,
      iconClasses: ['icon-rate-face-1', 'icon-rate-face-2', 'icon-rate-face-3'],
      colors: ['#99A9BF', '#F7BA2A', '#FF9900'],
      texts: ['辣鸡', '不行', '一般', '不错', '亲亲'],
      form:{
        name: '',
        first: '',
        date: '',
      },
      formLabelWidth: '200px',
    }
  },
  methods: {
    handleSelect(key, keyPath) {
      console.log(key, keyPath);
      if (key == '2') {
        this.dialogFormVisible = true;
      }else {
        this.dialogFormVisible = false;
        this.activeIndex = key;
      }
    },
    submitForm(){
      if(this.form.name == '江2' && this.form.first == '2021-10-17' && this.form.date == '2022-01-03') {
        this.dialogFormVisible = false;
        this.activeIndex = '2';
        this.$message({
          message: '认证成功！欢迎小宝宝！',
          type: 'success'
        });
      }else {
        this.$message.error('写错啦！再想想看👀');
      }
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
