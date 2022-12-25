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
          }">
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
            <el-timeline-item timestamp="1999/01/01" placement="top" color='black'>
              <el-card>
                <h4>漆黑使の降臨</h4>
                <p>🤫一位天选少年 登录地球online 1999/01/01 00:11</p>
              </el-card>
            </el-timeline-item>
            <el-timeline-item timestamp="2000/02/02" placement="top" color='#0bbd87'>
              <el-card>
                <h4>花の咲く</h4>
                <p>😶世界に一つだけの花 悄悄开放 2000/02/02 ??:??</p>
              </el-card>
            </el-timeline-item>
            <el-timeline-item timestamp="2021/10/17" placement="top" color='#0bbd87'>
              <el-card>
                <h4>认识邱诗盈</h4>
                <p>一起玩 《火化吧》 2021/10/17 14:00</p>
              </el-card>
            </el-timeline-item>
            <el-timeline-item timestamp="2021/12/15" placement="top" color='#0bbd87'>
              <el-card>
                <h4>单独吃饭（date）</h4>
                <p>一起吃饭喝酒 一起回家 2021/12/15 18:10</p>
              </el-card>
            </el-timeline-item>
            <el-timeline-item timestamp="2021/12/19" placement="top" color='#0bbd87'>
              <el-card>
                <h4>充电宝贝</h4>
                <p>没有充电 没有送送 精神内耗啦 2021/12/19 ～20:00</p>
              </el-card>
            </el-timeline-item>
            <el-timeline-item timestamp="2021/12/28" placement="top" color='#0bbd87'>
              <el-card>
                <h4>牵牵贴贴抱抱蹭蹭</h4>
                <p>好好送化妆的小花花回家啦 牵手手贴贴抱抱 蹭蹭味道 2021/12/28 ～22:00</p>
              </el-card>
            </el-timeline-item>
            <el-timeline-item timestamp="2021/12/29" placement="top" color='#0bbd87'>
              <el-card>
                <h4>北外滩</h4>
                <p>要幸福要健康要快乐 大跨步的走 被吸引啦 2021/12/29 ～24:00</p>
              </el-card>
            </el-timeline-item>
            <el-timeline-item timestamp="2021/12/31" placement="top" color='pink'>
              <el-card>
                <h4>跨年夜</h4>
                <p>下班一起吃晚饭 随意表白-其1 2021/12/31 22:00</p>
              </el-card>
            </el-timeline-item>
            <el-timeline-item timestamp="2022/01/02" placement="top" color='#0bbd87'>
              <el-card>
                <h4>🍞唱歌之夜</h4>
                <p>唱歌时突然出现 翘着腿腿 没赶上末班车 2022/01/02 19:00</p>
              </el-card>
            </el-timeline-item>
            <el-timeline-item timestamp="2022/01/03" placement="top" color='pink'>
              <el-card>
                <h4>❤️和小花花在一起啦</h4>
                <p>挂着腿腿的 🌼の恋 开始于 2022/01/03 ～02:00</p>
              </el-card>
            </el-timeline-item>
            <el-timeline-item timestamp="2022/01/04" placement="top" color='#0bbd87'>
              <el-card>
                <h4>🚇冬日早起计划</h4>
                <p>早起一起上班 世纪大道见 开始期待早上了 2022/01/04 07:25</p>
              </el-card>
            </el-timeline-item>
            <el-timeline-item timestamp="2022/01/08" placement="top" color='#0bbd87'>
              <el-card>
                <h4>百丘</h4>
                <p>穿着绿色连衣裙一起回家 在百丘说说了好多 2022/01/08 ～18:00</p>
              </el-card>
            </el-timeline-item>
            <el-timeline-item timestamp="2022/01/09" placement="top" color='pink'>
              <el-card>
                <h4>😘亲亲</h4>
                <p>第一次在外滩 吃着棒棒糖亲亲啦 2022/01/09 17:20</p>
              </el-card>
            </el-timeline-item>
            <el-timeline-item timestamp="2022/01/16" placement="top" color='pink'>
              <el-card>
                <h4>哭哭</h4>
                <p>吃饭喝酒哭哭 回家亲亲了好久 2022/01/16 19:00</p>
              </el-card>
            </el-timeline-item>
            <el-timeline-item timestamp="2022/01/17" placement="top" color='pink'>
              <el-card>
                <h4>🍭上班</h4>
                <p>做完核酸去上班 尝了好久棒棒糖味的kiss 2022/01/17 08:00</p>
              </el-card>
            </el-timeline-item>
            <el-timeline-item timestamp="2022/01/19" placement="top" color='#0bbd87'>
              <el-card>
                <h4>凌晨的会面</h4>
                <p>偷偷跑出来接打本结束的宝宝 一起吃夜宵回家 2022/01/19 00:50</p>
              </el-card>
            </el-timeline-item>
            <el-timeline-item timestamp="2022/01/19" placement="top" color='pink'>
              <el-card>
                <h4>👫第一次date</h4>
                <p>在一起之后 终于单独date 2022/01/19 19:00</p>
              </el-card>
            </el-timeline-item>
            <el-timeline-item timestamp="2022/01/21" placement="top" color='pink'>
              <el-card>
                <h4>接下班</h4>
                <p>戴着猫耳被接下班啦 逛了逛湖 去看了《爱情神话》 2022/01/21 18:00</p>
              </el-card>
            </el-timeline-item>
            <el-timeline-item timestamp="2022/02/03" placement="top" color='pink'>
              <el-card>
                <h4>🎂生日快乐</h4>
                <p>去上海中心吃饭 一起看到下雪了❄️ 在车上乱摸 2022/02/03 12:00</p>
              </el-card>
            </el-timeline-item>
            <el-timeline-item timestamp="2022/02/08" placement="top" color='pink'>
              <el-card>
                <h4>带回家</h4>
                <p>趁爸妈不在带回家 一起躺躺乱摸 2022/02/08 18:00</p>
              </el-card>
            </el-timeline-item>
            <el-timeline-item timestamp="2022/02/19" placement="top" color='pink'>
              <el-card>
                <h4>一起睡觉</h4>
                <p>去南京路开房间 贴了ns一起玩 乱摸 2022/02/19 10:00</p>
              </el-card>
            </el-timeline-item>
            <el-timeline-item timestamp="2022/02/21" placement="top" color='pink'>
              <el-card>
                <h4>🏰迪士尼</h4>
                <p>一起去迪士尼啦 拍了好多照片 2022/02/21 07:30</p>
              </el-card>
            </el-timeline-item>
            <el-timeline-item timestamp="2022/07/01" placement="top" color='pink'>
              <el-card>
                <h4>奉贤旅游</h4>
                <p>一离职就一起开车去旅游 2022/07/01～04</p>
              </el-card>
            </el-timeline-item>
            </el-timeline-item>
            <el-timeline-item timestamp="2022/07/13" placement="top" color='pink'>
              <el-card>
                <h4>临港旅游</h4>
                <p>临港 海洋馆 迪士尼 温泉 好快呀 2022/07/13～16</p>
              </el-card>
            </el-timeline-item>
            <el-timeline-item timestamp="2022/08/03" placement="top" color='pink'>
              <el-card>
                <h4>第一次话剧</h4>
                <p>一起看《你好，我找Smith》 2022/08/03 19:30</p>
              </el-card>
            </el-timeline-item>
            <el-timeline-item timestamp="2022/08/07" placement="top" color='pink'>
              <el-card>
                <h4>出上海旅游啦</h4>
                <p>安吉&桐庐 不舍得回家呢 2022/08/07～11</p>
              </el-card>
            </el-timeline-item>
            <el-timeline-item timestamp="2022/08/12" placement="top" color='pink'>
              <el-card>
                <h4>🎁收礼物</h4>
                <p>收到了好多礼物 惊喜制造大师！BLUE来了 真的做做啦❤️ 2022/08/12</p>
              </el-card>
            </el-timeline-item>
            <el-timeline-item timestamp="2022/08/25" placement="top" color='pink'>
              <el-card>
                <h4>愚园路逛吃</h4>
                <p>在愚园路吃早饭 买午饭 吃甜品 戴着沙利叶去打《曦和失焰》 2022/08/25 09:00</p>
              </el-card>
            </el-timeline-item>
            <el-timeline-item timestamp="2022/09/05" placement="top" color='pink'>
              <el-card>
                <h4>Last贴贴</h4>
                <p>真的在酒店贴了一天 吃到了不错的餐厅太好了 送回家还是哭哭了 2022/09/05 09:00</p>
              </el-card>
            </el-timeline-item>
            <el-timeline-item timestamp="2022/09/05" placement="top" color='grey'>
              <el-card>
                <h4>✈️和小花花的暂时分别</h4>
                <p>去🇨🇭瑞士读书 在机场送送 2022/09/05 16:10</p>
                <el-image 
                  style="width: 30px; height: 30px"
                  src="./static/attach.png" 
                  :preview-src-list="srcList">
                </el-image>
              </el-card>
            </el-timeline-item>
            <el-timeline-item timestamp="2023/01/03" placement="top" color='pink'>
              <el-card>
                <h4>和小花花在一起一周年啦</h4>
                <p>怎么才第一年！还会有很多很多年！✍️甜甜契约 有效期至 2222/13/14 05:21</p>
              </el-card>
            </el-timeline-item>
            <el-timeline-item timestamp="♾️" placement="top" color='pink'>
              <el-card>
                <h4>To be continued..</h4>
                <p>つつく..</p>
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
      srcList:['./static/2422.png', './static/2428.png', './static/2423.png','./static/2424.png','./static/2426.png','./static/2427.png',],
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
          showClose: true,
          message: '认证成功！欢迎小宝宝！',
          type: 'success'
        });
      }else {
        this.$message({
          showClose: true,
          message: '写错啦！再想想看👀',
          type: 'error'
        })
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
