<template>
  <div class="userWrap">
    <header>
      <div class="headerTop">
        <a class="goback" href="#" @click="$router.push('/main')"></a>
        <div @click="toggleISregisiteWrap(true)"><a href="#">注册</a></div>
      </div>
      <div class="mylogo">
        <img src="./logo.png" alt="">
      </div>
      <div class="Mlogin">
        <ul>
          <li class="leftL" @click="toggleTabShow(true)" >
            <a href="#">普通登录</a>
            <i class="iTRS" style="display: block" v-if="isTabShow"></i>
          </li>
          <li class="rightL" @click="toggleTabShow(false)">
            <a href="#">手机动态密码登录</a>
            <i class="iTRS" style="display: block" v-if="!isTabShow"></i>
          </li>
        </ul>
      </div>
    </header>
    <div class="Ubody">
      <div class="iformWrap">
        <div class="iformContent">
          <form method="post" v-if="isTabShow==true" class="loginFrom">
            <div class="loginI">
              <ul>
                <li>
                  <span class="micon"></span>
                  <input type="text" id="username" class="loginIp" placeholder="手机号/邮箱/用户名">
                </li>
                <li>
                  <span class="miconL"></span>
                  <input type="password" id="password" class="loginIp" placeholder="密码">
                </li>
                <div style="position: relative;top: 10px;left: 261px;">
                  <a href="#">忘记密码？</a>
                </div>
              </ul>
            </div>
          </form>

          <form method="post" v-if="isTabShow==false" class="iphoneloginFrom">
            <div class="loginII">
              <ul>
                <li>
                  <span class="mNumIco"></span>
                  <input type="text" name="mNumIco" id="mNumIco" class="mNumT" placeholder="手机号/邮箱/用户名">
                </li>
                <li>
                  <span class="mpasswordIco"></span>
                  <input type="text" name="varify" id="varify" class="dttext" placeholder="请输入图片内容">
                  <span class="yZTP">
                    <img src="./seccode.png" alt="">
                  </span>
                </li>
                <li>
                  <span class="mpasswordIcoC"></span>
                  <input type="text" name="code" id="code" class="code" placeholder="动态密码">
                  <a href="#" class="acpswd">获取动态密码</a>
                </li>
                  <div style="position: relative;top: 10px;left: 261px;">
                    <a href="#">忘记密码？</a>
                  </div>
                </ul>
            </div>
          </form>
        </div>
      </div>
      <div class="loginButton">
        <div>
          <a href="#">登陆</a>
        </div>

      </div>
      <div class="HZWeb">
        <div class="Webtitle">
          <b>合作网站登录</b>
        </div>
        <ul>
          <li class="QQ">
            <a href="#">
              <img src="./QQ.png" alt="">
            </a>
          </li>
          <li class="ZFB">
            <a href="#">
              <img src="./ZFB.png" alt="">
            </a>
          </li>
        </ul>
      </div>

    </div>
    <div class="regisiteWrap" v-show="ISregisiteWrap">
      <regisite/>
    </div>
  </div>

</template>
<script>
  import PubSub from 'pubsub-js'
  import regisite from '../../components/regisite/regisite.vue'
    export default{
      components:{
        regisite
      },
      data(){
          return{
            isTabShow:true,
            ISregisiteWrap:false
          }
      },
      methods:{
          //实现点击跳转
        toggleTabShow(a,isb){

            this.isTabShow =a
        },
        //显示遮罩层
        toggleISregisiteWrap(){
          this.ISregisiteWrap = !this.ISregisiteWrap
        }
      }
    }
</script>

<style lang="stylus" rel="stylesheet.stylus">
.userWrap
  position absolute
  top 0
  right 0
  height 100%
  width 100%
  z-index 105
  background white
  header
    display block
    width 100%
    height 177px
    position relative
    top 0
    left 0
    background url("./bg.png") no-repeat
    .headerTop
      position relative
      box-sizing border-box
      height 50px
      width 100%
      padding 0 16px
      //background red
      .goback
        background url("./goback.png") no-repeat
        background-size 12px 15px
        display inline-block
        width 22px
        height 20px
        position relative
        top 20px
        left -6px

      div
        a
          color white
          font-size 18px
          position relative
          left 307px
          top -2px

    .mylogo
      box-sizing border-box
      width 100%
      height 83.88px
      padding 1em 0 2em 0
      img
        width 20%
        display: block
        margin auto

    .Mlogin
      width 100%
      height 44px
      ul
        background rgba(255,255,255,0.4)
        width 100%
        height 44px
        .iTRS
          display block
          width 0
          height 0
          border-left 10px solid transparent
          border-right 10px solid transparent
          border-bottom 10px solid #fff
          position absolute
          bottom 0px
          left 0
          right 0
          margin auto
        .leftL
          position relative
          width 50%
          height 44px
          line-height 44px
          text-align center
          a
            font-size 15px
            color white
        .rightL
          position relative
          width 50%
          height 44px
          line-height 44px
          text-align center
          /*background red*/
          top -44px
          left 187px
          a
            font-size 15px
            color white
            right -194px
            top -44px


  .Ubody
    position relative
    width 100%
    height 70%
    top 0
    left 0
    .iformContent
      box-sizing border-box
      width 92%
      height 92px
      padding 0 .5em 0 .5em
      margin 0 auto
      .loginFrom
        display block
        box-sizing border-box
        width 100%
        height 100%
        .loginI
          height 100%
          width 100%
          ul
            height 100%
            width 100%
            &>li
              width 100%
              height 50%
              border-bottom #e2e2e2 solid 1px
              padding 12px 0 12px 30px
              position relative
              input::-webkit-input-placeholder
                color #999
              &>input
                width 100%
                display block
                height 21px
                font-size 15px
                font-family  "Microsoft Yahei",tahoma,arial
                outline none
                color: #666
                position relative
                top -15px
                left 35px

              .micon
                float left
                width 17px
                height 21px
                display inline-block
                position relative
                top 10px
                background url("./ico3.png") no-repeat
                background-size contain
              .miconL
                float left
                width 17px
                height 21px
                display inline-block
                position relative
                top 10px
                background url("./ico4.png") no-repeat
                background-size contain
      .iphoneloginFrom
        display block
        box-sizing border-box
        width 100%
        height 150%
        .loginII
          height 100%
          width 100%
          ul
            height 100%
            width 100%
            &>li
              box-sizing border-box
              border-bottom #e2e2e2 solid 1px
              padding 12px 0 12px 30px
              position relative
              width 100%
              height 46px
              .mNumT
                position relative
                left 56px
                bottom 22px
                width 100%
                height 21px
                display block
                font-size 15px
                border none
                padding 0
                color #666
                font-family "Microsoft Yahei" tahoma arial
                outline none
              .mNumIco
                display inline-block
                width 25px
                height 20px
                background url("./ico1.png") no-repeat
                background-size contain

              .mpasswordIco
                display inline-block
                width 25px
                height 20px
                background url("./ico1.png") no-repeat
                background-size contain
              .dttext
                position relative
                left 56px
                bottom 22px
                width 100%
                height 21px
                display block
                font-size 15px
                border none
                padding 0
                color #666
                font-family "Microsoft Yahei" tahoma arial
                outline none
              .yZTP
                display inline-block
                width 85px
                height 40px
                img
                  position relative
                  left 216px
                  bottom 48px
              .mpasswordIcoC
                display inline-block
                width 25px
                height 20px
                background url("./ico4.png") no-repeat
                background-size contain
              .code
                display inline-block
                position relative
                left 29px
              .acpswd
                display inline-block
                box-sizing border-box
                position relative
                top -30px
                left 205px
                color #ff4259
                border 1px solid #eb4c33
                border-radius 3px
                width 100px
                height 30px
                text-align center
                padding 0.3em 0
                font-size 12pxa



    .loginButton
      width 100%
      height 44px
      position relative
      top 110px
      div
        width 90%
        height 100%
        background #2ec975
        margin 0 auto
        border-radius 5px
      a
        display inline-block
        font-size 15px
        color white
        line-height 44px
        height 44px
        position relative
        left 100px


    .HZWeb
      position relative
      width 100%
      height 120px
      top 190px
      .Webtitle
        width 100%
        height 20px
        color #d7d7d7
        text-align center
      ul
        &>li
          margin-top 20px
          text-align center
          width 124px
          height 57px
          float left
          &>a
            display inline-block
            width 97px
            height 57px
            img
              width 57px
              height 57px


  .regisiteWrap
    position absolute
    top 0
    right 0
    height 100%
    width 100%
    z-index 106
</style>
