<template>
  <div class="login-container">
    <form class="form" action>
      <div class="loginheader clearfix" :class="{active:shows<3}">
        <div class="SignFlow-tab" @click="active(1)" :class="{active:shows==1}">免密码登录</div>
        <div class="SignFlow-tab" @click="active(2)" :class="{active:shows==2}">密码登录</div>
      </div>
      <div class="loginPhoneNumber clearfix" :class="{active:shows==1}">
        <div class="phoneZone">
          <el-select
            id="number-zone"
            v-model="chinaNumber"
            placeholder="中国+86"
          >
            <el-option
              v-for="item in options"
              :key="item.value"
              :label="item.label"
              :value="item.value"
            ></el-option>
          </el-select>
        </div>
        <el-input class="phoneNumber" placeholder="手机号" v-model="phoneNumber" clearable></el-input>
      </div>
      <div class="loginVerificationCode clearfix" :class="{active:shows==1}">
        <div class="input-wrapper">
          <el-input maxlength="6" placeholder="输入6位短信验证码" v-model="verificationCode"></el-input>
        </div>

        <button @click="getVertifyCode">获取短信验证码</button>
      </div>

      <div class="loginUsername" :class="{active:shows==2}">
        <div class="input-wrapper">
          <el-input placeholder="手机号或邮箱" v-model="username"></el-input>
        </div>
      </div>
      <div class="loginPassword" :class="{active:shows==2}">
        <div class="input-wrapper">
          <el-input placeholder="密码" v-model="password"></el-input>
        </div>
      </div>
      <div class="loginOptions clearfix">
        <button class="overseaMobile" :class="{active:shows==2}" v-on:click.prevent="overSeaLogin()"> {{loginMessage}} </button>
        <button class="forgetPassword" :class="{active:shows==2}" @click.prevent="forgetPassword()">忘记密码?</button>

        <button class="voiceCode" :class="{active:shows==1}">接收语音验证码</button>
      </div>

      <button class="loginButton" :class="{active:shows<3}">注册/登录</button>
      
    </form>
    <div class="social-container-tip" :class="{active:shows<3}">
        <p>未注册手机验证后自动登录</p>
        <p>注册即代表同意<a href="javascript:void(0)">《XX协议》</a><a href="javascript:void(0)">《隐私保护指引》</a></p>
      </div>
    <div class="QRcode">
      <div class="imgContainer">
        <img src="./assets/icons/qr.png" :class="{active:shows<3}" @click="active(3)" alt />
        <img src="./assets/icons/phone.png" :class="{active:shows==3}" @click="active(2)" alt />
      </div>
    </div>
    <div class="QRloginContainer" :class="{active:shows==3}">
      <div class="saomadenglu">扫码登录</div>
      <div class="QRpicture">
        <img src="./assets/icons/qrpicture.png" alt />
      </div>
      <p>
        打开
        <span>知乎</span>App
      </p>
      <p>在｢我的｣页面右上角打开扫一扫</p>
    </div>
  </div>
</template>




<script>
export default {
  data() {
    return {
      shows: 1,
      phoneNumber: "",
      verificationCode: "",
      password: "",
      username: "",
      options: [
        {
          value: "86",
          label: "中国 +86"
        },
        {
          value: "852",
          label: "中国香港 +852"
        },
        {
          value: "853",
          label: "中国澳门 +853"
        },
        {
          value: "886",
          label: "中国台湾 +886"
        },
        {
          value: " 1",
          label: "美国 +1"
        },
        {
          value: "81",
          label: "日本 +81"
        }
      ],
      loginMessage:'海外手机登录',
      chinaNumber: "86",
      selfbutton: "select-button"
    };
  },
  methods: {
    active(num) {
      this.shows = num;
    },
    overSeaLogin() {
      console.log(1);
      console.log(this.loginMessage);
      
      if (this.loginMessage ==='海外手机登录') {
        this.loginMessage = '邮箱账号登录'

        return
      }
      if (this.loginMessage ==='邮箱账号登录') {
        this.loginMessage = "海外手机登录"
      }
      
    },
    forgetPassword(){

    },
    getVertifyCode(){
      
    }
  }
};
</script>
    






<style>
.QRloginContainer {
  text-align: center;
  display: none;
  padding: 40px 0;
}
.QRloginContainer.active {
  display: block;
}
.saomadenglu {
  font-size: 32px;
  margin-bottom: 40px;
}
.QRpicture {
  margin-bottom: 20px;
}
.QRloginContainer > p > span {
  color: tomato;
  font-size: 1.5em;
  padding: 5px;
}


/* 协议通知 */
.social-container-tip{
  font-size: 14px;
  display: none;
  color: grey;
  background-color: #f6f6f6;
  padding: 20px 10px;
  border-radius: 0 0 5px 5px;
}
.social-container-tip.active{
  display: block;
}




.loginheader {
  display: none;
  padding-bottom: 10px;
}
.loginheader.active {
  display: block;
}
.form {
  padding: 0 30px 20px 30px;
}
.login-container {
  width: 400px;
  background-color: #fff;
  margin: 100px auto;
  width: 450px;
  border-radius: 5px;
  position: relative;
}

/* 免密码登录+密码登录公用头部样式 */

.SignFlow-tab {
  display: inline-block;
  font-size: 20px;
  line-height: 45px;
  padding: 10px 15px;
  cursor: pointer;
}
.SignFlow-tab.active {
  font-weight: 600;
  color: #1a1a1a;
}
.SignFlow-tab.active::after {
  content: "";
  height: 3px;
  width: 100%;
  display: block;
  border-bottom: 3px solid tomato;
}

.QRcode img {
  width: 60px;
  height: 60px;
  position: absolute;
  display: none;
  right: 0;
  top: 0;
  mask-image: url("./assets/icons/mask.png");
}
.QRcode img.active {
  display: block;
}

/* 免密码登录样式 */

.loginPhoneNumber,
.loginVerificationCode {
  border-bottom: 1px solid #ebebeb;
  border-radius: 0;
  margin: 0;
  padding: 0;
  display: none;
  position: relative;
}
.loginPhoneNumber.active,
.loginVerificationCode.active {
  display: block;
}

.phoneZone {
  width: 135px;
  margin-left: 15px;
  display: inline-block;
}
.phoneZone input {
  padding: 0px 5px;
}
.loginPhoneNumber input,
.loginVerificationCode input {
  border: none;
  margin: 5px 0;
}
.loginPhoneNumber .phoneNumber {
  width: 230px;
}

.loginVerificationCode button {
  position: absolute;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
  background-color: transparent;
  border: none;
  color: rgb(230, 136, 120);
}

/* 密码登录样式 */
.loginUsername,
.loginPassword {
  height: 49px;
  border-bottom: 1px solid #ebebeb;
  display: none;
}
.loginUsername.active,
.loginPassword.active {
  display: block;
}

.loginUsername input,
.loginPassword input {
  border: none;
  margin: 0;
  margin: 5px 0;
}
/* 通用样式 */

.login-options {
  height: 60px;
  line-height: 60px;
  display: block;
}
.loginButton {
  width: 100%;
  background-color: tomato;
  border: none;
  color: white;
  border-radius: 5px;
  padding: 10px 0;
  margin: 20px 0 0  0;
  display: none;
}
.loginButton.active {
  display: block;
}
.loginOptions {
  margin: 10px 0;
}
.loginOptions button {
  background-color: transparent;
  border: none;
  color: #8590a6;
  display: none;
}
.voiceCode.active {
  float: right;
  display: inline-block;
}
.forgetPassword.active {
  float: right;
  display: inline-block;
}
.overseaMobile.active {
  display: inline-block;
  color: rgb(230, 136, 120);
}
</style>