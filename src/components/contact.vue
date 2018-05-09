<template>
  <div>
      <div class="headerl headers">
          <div class="inner">
              <div class="letterl">
                  <router-link to="/listen">
                    <i style="color:black;margin-top:0.08rem" class="fa fa-chevron-left" aria-hidden="true"></i>
                  </router-link>
                  <div class="searchl">
                      专辑详情
                  </div>
                  <i style="float:right;opacity:0" class="fa fa-search btn" aria-hidden="true"></i>
              </div>
          </div>
      </div> 
      <div class="head" v-for="item,index in listen" v-if="index==id">
          <div class="inner">
              <div class="head_top">
                  <div class="head_top_left">
                      <img :src="item.url">
                  </div>
                  <div class="head_top_right">
                      <h1>{{item.name}}</h1>
                      <h2>主播：<span>{{item.host}}</span></h2>
                      <h2>播放：{{item.times}}</h2>
                      <h2>分类：<span>{{item.classify}}</span></h2>
                  </div>
              </div>
              <div class="head_mid">
                  <button type="submit" style="margin-left:0.1rem;margin-right:0.4rem">已订阅</button>
                  <button type="submit" style="background:#5dcaad">继续播放</button>
              </div>
          </div>
      </div>
      <div class="con_tab">
          <ul>
              <li>详情</li>
              <li class="per">节目</li>
              <li>相似</li>
          </ul>
      </div>
      <div class="con_cont" v-for="item,index in listen" v-if="index==id">
          <ul>
              <li v-for="i in item.cont">
                  <img :src="i.img" alt="">
                  <h1>{{i.main}}</h1>
                  <span>{{i.update_time}}</span>
              </li>
          </ul>
      </div>
  </div>
</template> 
<script>
import Axios from "axios"
export default {
  data(){
      return{
          id:'',
          listen:'',
          index:''
      }
  },
  methods:{
      cartView() {
        Axios({
            url:"../../static/listen.json",
            method:"get",
            params:{}
        }).then(res=>{
            this.listen=res.data
            this.id=this.$route.query.id
        })
      }
  },
  computed:{
  },
  mounted(){
        document.body.style.background="#f3f4f5"
        this.cartView()
  }
}
</script>
<style>
body{
    padding-bottom: 0
}
.head{
    height: 4.3rem;
    background: white;
}
.head_top{
    padding-top: 0.5rem;
    overflow: hidden;
}
.head_top_left{
    float: left;
    width: 2rem;
    height: 2.1rem;
    background: red;
}
.head_top_left img{
    width: 100%;
    height: 100%;
}
.head_top_right{
    float: left;
    margin-left: 0.2rem
}
.head_top_right h1{
    width: 3.8rem;
    font-weight: normal;
    font-size: 0.36rem;
    color: #333333
}
.head_top_right h2{
    font-weight: normal;
    font-size: 0.3rem;
    color: #999999
}
.head_top_right span{
    color: #4b90e2
}
.head_mid button{
    width: 40%;
    height: 0.8rem;
    background: #cccccc;
    color: white;
    font-size: 0.3rem;
    border:none;
    border-radius: 10px
}
.con_tab{
    margin-top:0.3rem;
    height: 1.2rem;
    background: white;
}
.con_tab ul{
    width: 100%;
    overflow: hidden;
}
.con_tab li{
    float: left;
    width: 33%;
    height: 1.2rem;
    font-size: 0.3rem;
    text-align: center;
    line-height: 1.2rem;
    border-bottom: 2px solid transparent;
    color: #6e6e6e;
}
.con_tab .per{
    border-bottom: 2px solid #fa593b;
    color: #fa593b;
}
.con_cont{
    border-top: 1px solid #e8e8e8;
}
.con_cont li{
    height: 1.5rem;
    background: white;
}
.con_cont li img{
    float: left;
    width: 1rem;
    height: 1rem;
    border-radius: 50%;
    margin-top: 0.25rem;
    margin-left: 0.3rem;
}
.con_cont li h1{
    font-weight: normal;
    font-size: 0.32rem;
    color: #343434;
    width: 55%;
    float: left;
    height: 1rem;
    margin-left: 0.4rem;
    margin-top: 0.25rem;
}
.con_cont li span{
    display: block;
    width: 0.8rem;
    float: right;
    font-size: 0.24rem;
    color: #999999;
    margin-right: 0.2rem;
    margin-top: 0.25rem;
}
</style>
