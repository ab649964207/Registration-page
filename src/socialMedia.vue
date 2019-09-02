<template>
  <div class="card-login">
    <span>社交账户登录</span>
    <div class="login-social-button weixinIcon">
      <img src="./assets/icons/weixin.png" alt="">
      微信
    </div>
    <div class="login-social-button">
        <img src="./assets/icons/qq.png" alt="">
        QQ
    </div>
    <div class="login-social-button">
        <img src="./assets/icons/weibo.png" alt="">
        微博
    </div>
  </div>
</template> 
<style>
.card-login {
    background-color: #fff;
    display: flex;
    height: 60px;
    line-height: 60px;
    width: 450px;
    border-radius: 5px;
    padding: 0 30px;
    color: #8590a6;
    margin: 20px auto;
    box-shadow: 0 1px 3px 0 rgba(0,0,0,.1);
}
.login-social-button {
   justify-content: center;
   display: flex;
   line-height: 60px;
   -moz-user-focus: pointer;
}
.login-social-button img {
  width: 30px;
  height: 30px;
  margin: 15px 8px 15px 20px;
  
}
.weixinIcon{
  margin-left: 25px;
}
</style>