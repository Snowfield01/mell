<template>
  <div class="appContainer">
    <!-- 头部 -->
   
    <mt-header title="天亮商城">
      <span slot="left" >
        <mt-button icon="back" @click="goback" v-show="flag">返回</mt-button>
      </span>
     
    </mt-header>

    <!-- 内容部分 -->
    <transition mode="out-in">
      <router-view></router-view>
    </transition>
    <!-- 尾部 -->

    <nav class="mui-bar mui-bar-tab">
      <router-link class="mui-tab-item-wh" to="/home">
        <span class="mui-icon mui-icon-home"></span>
        <span class="mui-tab-label">首页</span>
      </router-link>
      <router-link class="mui-tab-item-wh" to="/member">
        <span class="mui-icon mui-icon-contact"></span>
        <span class="mui-tab-label">会员</span>
      </router-link>
      <router-link class="mui-tab-item-wh" to="/shopcar">
        <span class="mui-icon mui-icon-extra mui-icon-extra-cart">
          <span class="mui-badge" id="badge">{{$store.getters.getAllCount}}</span>
        </span>
        <span class="mui-tab-label">购物车</span>
      </router-link>
      <router-link class="mui-tab-item-wh" to="/search">
        <span class="mui-icon mui-icon-search"></span>
        <span class="mui-tab-label">搜索</span>
      </router-link>
    </nav>
  </div>
</template>
<script>
export default {
  //默认导出
  data(){
    return{
      flag:false
    }
  },
  created(){
    this.flag = this.$route.path =='/home'?false:true
  },
  methods:{
    goback(){
      // 只能返回上一级
      this.$router.go(-1)
    },
  },
   watch: {
    "$route.path":function(newVal){
        if(newVal =='/home'){
          this.flag = false
        }else{
          this.flag = true
        }
    }
  },
};
</script>
<style scoped>
.appContainer {
  overflow-x: hidden;
  padding-bottom: 50px;
  /* padding-top: 40px; */
}

.v-enter,
.v-leave-to {
  opacity: 0;
  transform: translateX(100%);
}
.v-leave-to {
  transform: translateX(-100%);
}
.v-enter-active,
.v-leave-active {
  transition: all 0.5s ease;
}

.mui-bar-tab .mui-tab-item-wh .mui-active {
  color: #007aff;
}
.mui-bar-tab .mui-tab-item-wh {
  display: table-cell;
  overflow: hidden;
  width: 1%;
  height: 50px;
  text-align: center;
  vertical-align: middle;
  white-space: nowrap;
  text-overflow: ellipsis;
  color: #929292;
}
.mui-bar-tab .mui-tab-item-wh .mui-icon {
  top: 3px;
  width: 24px;
  height: 24px;
  padding-top: 0;
  padding-bottom: 0;
}
.mui-bar-tab .mui-tab-item-wh .mui-icon ~ .mui-tab-label {
  font-size: 11px;
  display: block;
  overflow: hidden;
  text-overflow: ellipsis;
}
</style>