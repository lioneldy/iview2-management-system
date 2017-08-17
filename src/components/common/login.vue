<style scoped>

.login {
  background-color: #666 !important; 
  background: url(../../assets/img/login/login1.jpg);
}

.login .logo {
  margin: 60px auto 20px auto;
  padding: 15px;
  text-align: center; }

.login .content {
  background: url(../../assets/img/bg-white-lock.png) repeat;
  width: 360px;
  margin: 0 auto;
  margin-bottom: 0px;
  padding: 30px;
  padding-top: 20px;
  padding-bottom: 15px;
  -webkit-border-radius: 7px;
  -moz-border-radius: 7px;
  -ms-border-radius: 7px;
  -o-border-radius: 7px;
  border-radius: 7px; }

/* footer copyright */
.login .copyright {
  text-align: center;
  margin: 0 auto;
  padding: 10px;
  color: #eee;
  font-size: 13px; }

@media (max-width: 480px) {
  /***
  Login page
  ***/
  .login .logo {
    margin-top: 10px; }
  .login .content {
    padding: 30px;
    width: 222px; }
  .login .content h3 {
    font-size: 22px; }
  .login .checkbox {
    font-size: 13px; } }


</style>

<template>
<div class="login">
    <div class="logo">
        <a href="/login">
            <img src="../../assets/img/logo2.png">
        </a>
    </div>
    <div class="content">
        <router-view></router-view>
    </div>
    <div class="copyright">
        <a href="http://www.cincc.cn" title="北京新方通信技术有限公司" target="_blank">北京新方通信技术有限公司</a>
        <br/>Copyright &copy; 2010-2016 CINCC ALL Rights Reserved
    </div>
</div>

</template>

<script>

export default {
    data() {
            return {
            }
        },
}

</script>
