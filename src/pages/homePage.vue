<template>
   <div class="f_container" :style="{'-webkit-overflow-scrolling': scrollMode}">
      <div class="header">
        <div class="user" @click="handleClick"><img src="@/assets/icons/user_icon.png"/></div>
        <div class="search">服务搜索</div>
        <div class="scan_code"><img src="@/assets/icons/scan_icon.png"/></div>
      </div>
    <div class="f_center">

    <div class="banner">
      <swiper height="210px" :loop="loop" :auto="auto">
        <swiper-item class="swiper-demo-img" ><img src="@/assets/banner1.jpg"></swiper-item>
        <swiper-item class="swiper-demo-img" ><img src="@/assets/banner1.jpg"></swiper-item>
        <swiper-item class="swiper-demo-img" ><img src="@/assets/banner1.jpg"></swiper-item>
      </swiper>
    </div>
    <div class="localInfo">
        <div class="local">成华</div>
        <div class="weather">天气</div>
        <div class="today">今日限行</div>
    </div>
    <div class="cells">
        <div class="cell-item" v-for=" (item,index) in navArr " :key="index">
            <img src="@/assets/logo.png"/>
           <div is-link> {{item.name}}</div>
        </div>
    </div>
    <div class="information">
      <p class="information_title"><span>精选消息</span><span>换一换</span></p>
    </div>
    <div class="img_info">
       <div class="img_info_item">
         <img src="@/assets/banner1.jpg">
         <div>省公安厅指挥中心（办公室）副主任张伟一莅临视察工作…</div>
       </div>
    </div>
    </div>
     <popup v-model="popupVisible" width="70%" position="left" >
        <div>
         nihao
        </div>
      </popup>
   </div>
</template>
<script>

import { Swiper, SwiperItem, Popup } from 'vux'

export default {
  components: {Swiper, SwiperItem, Popup},
  beforeRouteEnter (to, from, next) {
    next()
  },
  mounted () {

  },
  data () {
    return {
      loop: true,
      auto: true,
      popupVisible: false,
      scrollMode: 'touch', // 移动端弹性滚动效果，touch为弹性滚动，auto是非弹性滚动
      navArr: [{
        name: '进度查询'
      }, {
        name: '预约查询'
      }, {
        name: '诉求查询'
      }, {
        name: '办事指南'
      }, {
        name: '预约排号'
      }, {
        name: '车辆违章查询'
      }, {
        name: '社保查询'
      }, {
        name: '全部'
      }]
    }
  },
  methods: {
    handleClick: function () {
      this.popupVisible = true
    }
  }
}
</script>
<style scoped>
.f_container{
  width: 100%;
  height: 100%;
  overflow: hidden;
  -webkit-overflow-scrolling: touch
}
.header{
   display: flex;
   position: fixed;
   top: 0;
   left: 0;
   width: 100%;
   height: 55px;
   z-index: 100;
   align-items: center;
   color: #FFF;
   text-align: center;
   background: rgba(0,0,0,0.2)
}
.header .user{
  flex: 1 0 10%;
}
.header .search{
  flex: 0 0 70%;
}
.header .scan_code{
  flex: 1 0 10%;
}
.f_center{
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  overflow: auto;
  -webkit-overflow-scrolling:touch;
}

.localInfo{
  display: flex;
  height: 52px;
  box-sizing: border-box;
  flex-direction:row;
   align-items: center;
}
.weather,.local,.today{
  flex: 1;
  text-align: left;
  font-size: 15px;
  padding: 0 18px
}
.today{
  color: #999999;
}
.banner{
  width: 100%;
  height:210px;
  position: relative
}
.banner img{
  width: 100%;
  position: absolute;
  left: 0;
  left: 0;
  height: 100%;
}
.cells{
 display: flex;
 flex-direction:row;
 flex-wrap: wrap ;
 align-items:  center ;
}
.cell-item{
 flex: 0 0 25%;
 padding:18px 0;
 box-sizing: border-box;
 text-align:center;
 font-size: 14px;
}
.cell-item img{
 width: 32px;
 height: 32px
}
.information_title{
  display: flex;
  margin-top: 30px;
  flex-direction: row;
  justify-content: space-between;
}
.information_title span{
  font-size: 15px;
  padding: 0 10px;
}
.information_title span:first-of-type{
  color: #999999
}
.information_title span:last-of-type{
  color:#0088EB
}
.img_info{
  padding: 0 10px;
  font-size: 18px;
  font-family: PingFangSC-Regular;
  font-size: 18px;
  color: #222222;
  letter-spacing: 0.22px;
  text-align: justify;
  margin-bottom: 20px
}
.img_info_item img{
  width: 100%;
  height: 158px;
}

.popup_win{
   width: 60%;
   left: 30%;
   height: 100%;
}
</style>
