<template>
  <div>
      <div class="headerl headers">
          <div class="inner">
              <div class="letterl">
                  <router-link to="/login">
                    <i style="color:black;margin-top:0.08rem" class="fa fa-chevron-left" aria-hidden="true"></i>
                  </router-link>
                  <div class="searchl">
                      登录
                  </div>
                  <div class="reg">注册</div>
              </div>
          </div>
      </div>
      <div class="log">
          <ul style="width:85%;margin:0 auto">
              <li class="use">账号密码登录</li>
              <li>快捷免密登录</li>
          </ul>
      </div>
      <div class="log_cont">
          <input type="text" placeholder="请输入账号" ref="username">
          <input type="password" placeholder="请输入密码" ref="password">
          <button @click="login">登录</button>
      </div>
  </div>
</template>
<script>
import Axios from "axios"
import Nav from "./nav"
import "../css/headerl.css"
import "../css/mine.css"
import "../css/find.css"
export default {
  data(){
    return{
      
    }
  },
  components:{Nav},
  methods:{
        login(){
            Axios({
            url:"/api/Handler/AdminRegHandler?action=login",
            method:"POST",
            data:{
                userName:this.$refs.username.value,
                password:this.$refs.password.value
            } 
        }).then(res=>{
            console.log(res)
            if(res.data.success){
            this.$router.push("mine")
            }
        })
      }
  }
}
</script>
<style>
.reg{
    float: right;
    font-size: 0.36rem;
    color: #f86442;
    margin-top: 0.35rem
}
body{
    background: white;
}
.log{
    height: 1rem;
    width: 100%;
    /* background: red; */
    border-bottom: 1px solid #e5e5e5
}
.log li{
    float: left;
    width: 50%;
    text-align: center;
    color: #9b9b9b;
    font-size: 0.36rem;
    line-height: 0.97rem;
    border-bottom: 3px solid transparent;
}
.log .use{
    color: #f86442;
    border-bottom: 3px solid #f86442;
}
.log_cont{
    width: 85%;
    margin: 0 auto
}
.log_cont input{
    width: 100%;
    height: 1rem;
    border: 1px solid #dfdfdf;
    padding-left: 5px;
    color: #c8c8c8;
    font-size: 0.3rem
}
.log_cont button{
    width: 100%;
    height: 1rem;
    color: white;
    background: #fbad9b;
    font-size: 0.34rem;
    border: none; 
}
</style>
