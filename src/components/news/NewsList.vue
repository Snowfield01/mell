<template>
  <div class="newscontainer">
    <ul class="mui-table-view">
      <li class="mui-table-view-cell mui-media" v-for="item in newslist" :key='item.id'>
        <a href="javascript:;">
          <img class="mui-media-object mui-pull-left" :src="item.img_url" />
          <div class="mui-media-body">
            <div class="bodyTitle">{{item.title}}</div> 
            <p class="mui-ellipsis">
                <span>{{item.add_time}}</span>
                <span>点击{{item.click}}次</span>
                
            </p>
          </div>
        </a>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
    data(){
        return {
            // meun1:'../../images/menu1.png',
            // meun2:'../../images/menu2.png',
            // meun3:'../../images/menu3.png',

            newslist:[],//用来存储数据库返回的数据
        }
    },
    created(){
        this.getnewsList()
    },
    methods:{
        getnewsList(){
            this.$http.get('http://yapi.shangyuninfo.com/mock/121/api/getnewslist')
            .then(
                result=>{
                    // console.log(result)
                    this.newslist = result.body.message;
                    // console.log(this.newslist)
                }
            )
            .catch()
        }
    }
};
</script>
<style>
.newscontainer {
  /* padding-top: 40px; */
}
.bodyTitle{
    font-size:14px;
}
.newscontainer .mui-ellipsis{
    display: flex;
}
.newscontainer .mui-media-body span:nth-of-type(1){
    font-size: 12px;
    color: #226aff;
   flex:8;
}
.newscontainer .mui-media-body span:nth-of-type(2){
    font-size: 12px;
    color: #226aff;
   flex:2;
}
</style>