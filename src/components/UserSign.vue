<template>
  <div class="sign">
    <div class="sign-container">
      <div class="sign-box">
        <!-- 关闭 -->
        <div class="close"
        @click="closeSign(false)"
        @mouseenter="changeCloseState(true)"
        @mouseleave="changeCloseState(false)"
        >
          <svg 
          :class="[isCloseState?'svg-close-enter':'svg-close-leave']"
          t="1717221705278"  viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="2294"><path d="M512 474.794667l261.8368-261.802667c24.7808-24.814933 61.986133 12.3904 37.205333 37.1712L549.1712 512l261.870933 261.8368c24.7808 24.7808-12.424533 61.986133-37.205333 37.205333L512 549.1712l-261.8368 261.870933c-24.7808 24.7808-61.986133-12.424533-37.205333-37.205333L474.8288 512 212.957867 250.1632c-24.7808-24.7808 12.424533-61.986133 37.205333-37.205333L512 474.8288z" fill="#999999" p-id="2295"></path></svg>
        </div>
        <!-- 盒子 -->
        <div class="tab-content">
          <!-- 登录 -->
            <div class="tab-sign-in" :style="{display:isSignIn?'block':'none'}" style="transition: all .3s">
            <!-- 头 -->
            <div class="sign-heading">
              <div class="title">
                <span>登录</span>
              </div>
              <a href="#"
              @mouseenter="changeJumpState(true)"
              @mouseleave="changeJumpState(false)"
              @click="showSignUp"
              :class="[isJumpState?'jump-enter':'jump-leave']"
              >
                没有帐号？立即注册
                <svg t="1717224689664" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="3262"><path d="M307.6 104.6c-14.2 14.2-14.2 37.2 0 51.4L655 503.4c2.8 2.9 2.8 7.5 0 10.3L307.6 861.2c-14.2 14.2-14.2 37.2 0 51.4 14.2 14.2 37.2 14.2 51.4 0l347.4-347.4c15.6-15.6 23.4-36 23.4-56.5s-7.8-41-23.4-56.5L359 104.6c-14.2-14.2-37.2-14.2-51.4 0z" p-id="3263"></path></svg>
              </a>
            </div>


            <!-- 登陆体 -->
            <div class="sign-in">
              <form>
                <div class="line-form">
                  <input type="text" v-model="username" tabindex="1" placeholder
                  @mouseenter="changeLine1State(true)"
                  @mouseleave="changeLine1State(false)"
                  @focus="changeForm1FocusState(true)"
                  @blur="changeForm1FocusState(false)"
                  :class="[isForm1FocusState?'line-form-input-enter':'line-form-input-leave']"
                  >
                  <i class="line-form-line"
                  :class="[isLine1State||isForm1FocusState?'line-form1-enter':'line-form1-leave']"
                  ></i>
                  <div
                  :class="[isForm1FocusState||username?'scale-placeholder-enter':'scale-placeholder-leave']"
                  ><span>用户名或邮箱</span></div>
                </div>

                <div class="line-form">
                  <input type="password" v-model="password"  tabindex="2" placeholder
                  @mouseenter="changeLine2State(true)"
                  @mouseleave="changeLine2State(false)"
                  @focus="changeForm2FocusState(true)"
                  @blur="changeForm2FocusState(false)"
                  class="password"
                  :class="[isForm2FocusState?'line-form-input-enter':'line-form-input-leave']"
                  >
                  <i  class="line-form-line"
                  :class="[isLine2State||isForm2FocusState?'line-form2-enter':'line-form2-leave']"
                  ></i>
                  <div
                  :class="[isForm2FocusState||password?'scale-placeholder-enter':'scale-placeholder-leave']"
                  ><span>登录密码</span>
                </div>
                <svg 
                @click="changePasswordState(true)"
                :class="[isPasswordState?'svg-show-password-change':'svg-show-password-default']"
                t="1717230430362"  viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="3113"><path d="M512 801.03c-104.03 0-214.16-48.72-318.47-140.91-78.12-69.04-125.05-137.1-127-139.96a14.42 14.42 0 0 1 0-16.31c1.95-2.86 48.88-70.92 127-139.96 104.3-92.2 214.44-140.92 318.47-140.92s214.16 48.72 318.47 140.91c78.13 69.04 125.04 137.1 127 139.96a14.42 14.42 0 0 1 0 16.31c-1.96 2.86-48.87 70.92-127 139.96C726.16 752.31 616.02 801.03 512 801.03zM96.28 512C129.65 556.98 300.43 772.13 512 772.13S894.34 556.98 927.72 512C894.34 467.02 723.56 251.87 512 251.87S129.65 467.02 96.28 512zM512 656.52c-79.68 0-144.52-64.83-144.52-144.52S432.32 367.48 512 367.48 656.51 432.31 656.51 512 591.68 656.52 512 656.52z m0-260.13c-63.75 0-115.61 51.86-115.61 115.61S448.25 627.61 512 627.61 627.61 575.75 627.61 512 575.75 396.39 512 396.39z" fill=var(--main-font-color) p-id="3114"></path></svg>
                <svg
                class="svg-hidden-password"
                @click="changePasswordState(false)"
                :class="[isPasswordState?'svg-show-password-default':'svg-show-password-change']"
                t="1717231009541"  viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="4091"><path d="M802.219871 221.61333c-10.022261-10.022261-26.278503-10.022261-36.275181 0L221.830271 765.726725c-10.022261 10.022261-10.022261 26.252921 0 36.275182 10.022261 10.022261 26.252921 10.022261 36.275182 0l544.113395-544.113395c9.998725-10.021238 9.998725-26.27748 0.001023-36.275182z" fill="" p-id="4092"></path><path d="M802.363134 221.99707c-10.022261-10.022261-26.278503-10.022261-36.275182 0L221.973534 766.111488c-10.022261 10.022261-10.022261 26.252921 0 36.275182 10.022261 10.022261 26.252921 10.022261 36.275181 0l544.113395-544.113395c10.024308-9.998725 10.024308-26.253944 0.001024-36.276205zM551.908942 370.744859c-12.660344-3.548826-25.942859-5.610788-39.751353-5.610788-80.990592 0-146.661268 65.670675-146.661268 146.661268 0 13.787004 2.037403 27.093055 5.609765 39.751352l180.802856-180.801832zM473.076502 653.014664c12.467963 3.452635 25.53456 5.442966 39.105647 5.442966 80.990592 0 146.661268-65.670675 146.661267-146.661268 0-13.571087-1.990331-26.637684-5.442966-39.105646L473.076502 653.014664z" fill="" p-id="4093"></path><path d="M233.914494 688.714747l34.500768-34.500768c-54.498218-36.084846-101.370759-84.252893-136.25629-142.0349C212.671681 378.75223 356.984461 296.394501 512.01228 296.394501c34.742269 0 68.882833 4.339842 101.969392 12.275581l39.032992-39.032992c-45.194318-13.690814-92.594885-21.171182-141.003408-21.171182-176.824241 0-341.011674 96.55201-428.501284 251.965615l-6.616698 11.772115 6.616698 11.773138c37.644365 66.819848 89.5045 122.68418 150.404522 164.737971zM940.490028 500.4305C902.918317 433.657724 851.105255 377.841487 790.30347 335.787696l-34.477232 34.477232c54.402027 36.059264 101.202936 84.180238 136.040372 141.915174-80.488149 133.451408-224.799906 215.784578-379.852284 215.784578-34.646078 0-68.691475-4.339842-101.682867-12.202926l-39.056527 39.056527c45.122687 13.641695 92.428086 21.098527 140.739394 21.098527 176.847777 0 341.036233-96.55201 428.476725-251.989151l6.615675-11.747555-6.616698-11.749602z" fill=var(--main-font-color) p-id="4094"></path></svg>
                </div>
                

                <div class="line-form3">
                  <span class="check-box">
                    <input type="checkbox" id="remember" checked="checked" tabindex="4" name="remember" value="forever">
                    <label for="remember" class="remember-password">记住登录</label>
                  </span>
                  <span class="find-password">
                    <a href="#"
                    @mouseenter="changeFindPasswordState(true)"
                    @mouseleave="changeFindPasswordState(false)"
                    :class="[isFindPasswordState?'find-password-a-enter':'find-password-a-leave']"
                    >找回密码</a>
                  </span>
                </div>

                <!-- 登录按钮 -->
                <div class="but-sign-in">
                  <button>
                    <a href="#">
                      <svg t="1717235396456" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="5095"><path d="M853.333333 128h-256V42.666667h341.333334v938.666666h-341.333334v-85.333333h256z" fill="#fff" p-id="5096"></path><path d="M652.16 469.333333L512 319.445333 571.306667 256 810.666667 512l-239.36 256L512 704.554667 652.16 554.666667H85.333333v-85.333334z" fill="#fff" p-id="5097"></path></svg>
                    </a>
                    <span class="login">登录</span>
                  </button>
                </div>
              </form>
            </div>
          </div>

          

            <!-- 注册 -->
          <div class="tab-sign-up sign-up-newHeight" :style="{display:isSignUp?'block':'none'}" style="transition: all .3s;">
            <!-- 头 -->
            <div class="sign-heading">
              <div class="title">
                <span>注册</span>
              </div>
              <a href="#"
              @mouseenter="changeJumpState(true)"
              @mouseleave="changeJumpState(false)"
              @click="showSignIn"
              :class="[isJumpState?'jump-enter':'jump-leave']"
              >
              已有帐号，立即登录
                <svg t="1717224689664" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="3262"><path d="M307.6 104.6c-14.2 14.2-14.2 37.2 0 51.4L655 503.4c2.8 2.9 2.8 7.5 0 10.3L307.6 861.2c-14.2 14.2-14.2 37.2 0 51.4 14.2 14.2 37.2 14.2 51.4 0l347.4-347.4c15.6-15.6 23.4-36 23.4-56.5s-7.8-41-23.4-56.5L359 104.6c-14.2-14.2-37.2-14.2-51.4 0z" p-id="3263"></path></svg>
              </a>
            </div>
            <!-- 注册体 -->
            <div class="sign-up">
              <form>

                <div class="line-form">
                  <input type="text" v-model="SignUpUsername" tabindex="1" placeholder
                  @mouseenter="changeLine1State(true)"
                  @mouseleave="changeLine1State(false)"
                  @focus="changeForm1FocusState(true)"
                  @blur="changeForm1FocusState(false)"
                  :class="[isForm1FocusState?'line-form-input-enter':'line-form-input-leave']"
                  >
                  <i class="line-form-line"
                  :class="[isLine1State||isForm1FocusState?'line-form1-enter':'line-form1-leave']"
                  ></i>
                  <div
                  :class="[isForm1FocusState||SignUpUsername?'scale-placeholder-enter':'scale-placeholder-leave']"
                  ><span>设置用户名</span></div>
                </div>


                <!-- 2 -->
                <div class="line-form">
                  <input type="text" v-model="email" tabindex="2" placeholder
                  @mouseenter="changeLine2State(true)"
                  @mouseleave="changeLine2State(false)"
                  @focus="changeForm2FocusState(true)"
                  @blur="changeForm2FocusState(false)"
                  :class="[isForm2FocusState?'line-form-input-enter':'line-form-input-leave']"
                  >
                  <i class="line-form-line"
                  :class="[isLine2State||isForm2FocusState?'line-form2-enter':'line-form2-leave']"
                  ></i>
                  <div
                  :class="[isForm2FocusState||email?'scale-placeholder-enter':'scale-placeholder-leave']"
                  ><span>邮箱</span></div>
                </div>


                <!-- 3 -->
                <div class="line-form">
                  <input type="password" v-model="SignUpPassword"  tabindex="3" placeholder
                  @mouseenter="changeLine3State(true)"
                  @mouseleave="changeLine3State(false)"
                  @focus="changeForm3FocusState(true)"
                  @blur="changeForm3FocusState(false)"
                  class="password2"
                  :class="[isForm3FocusState?'line-form-input-enter':'line-form-input-leave']"
                  >
                  <i  class="line-form-line"
                  :class="[isLine3State||isForm3FocusState?'line-form2-enter':'line-form2-leave']"
                  ></i>
                  <div
                  :class="[isForm3FocusState||SignUpPassword?'scale-placeholder-enter':'scale-placeholder-leave']"
                  ><span>登录密码</span>
                </div>
                <svg 
                @click="changePasswordState2(true)"
                :class="[isPasswordState2?'svg-show-password-change':'svg-show-password-default']"
                t="1717230430362"  viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="3113"><path d="M512 801.03c-104.03 0-214.16-48.72-318.47-140.91-78.12-69.04-125.05-137.1-127-139.96a14.42 14.42 0 0 1 0-16.31c1.95-2.86 48.88-70.92 127-139.96 104.3-92.2 214.44-140.92 318.47-140.92s214.16 48.72 318.47 140.91c78.13 69.04 125.04 137.1 127 139.96a14.42 14.42 0 0 1 0 16.31c-1.96 2.86-48.87 70.92-127 139.96C726.16 752.31 616.02 801.03 512 801.03zM96.28 512C129.65 556.98 300.43 772.13 512 772.13S894.34 556.98 927.72 512C894.34 467.02 723.56 251.87 512 251.87S129.65 467.02 96.28 512zM512 656.52c-79.68 0-144.52-64.83-144.52-144.52S432.32 367.48 512 367.48 656.51 432.31 656.51 512 591.68 656.52 512 656.52z m0-260.13c-63.75 0-115.61 51.86-115.61 115.61S448.25 627.61 512 627.61 627.61 575.75 627.61 512 575.75 396.39 512 396.39z" fill=var(--main-font-color) p-id="3114"></path></svg>
                <svg
                class="svg-hidden-password"
                @click="changePasswordState2(false)"
                :class="[isPasswordState2?'svg-show-password-default':'svg-show-password-change']"
                t="1717231009541"  viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="4091"><path d="M802.219871 221.61333c-10.022261-10.022261-26.278503-10.022261-36.275181 0L221.830271 765.726725c-10.022261 10.022261-10.022261 26.252921 0 36.275182 10.022261 10.022261 26.252921 10.022261 36.275182 0l544.113395-544.113395c9.998725-10.021238 9.998725-26.27748 0.001023-36.275182z" fill="" p-id="4092"></path><path d="M802.363134 221.99707c-10.022261-10.022261-26.278503-10.022261-36.275182 0L221.973534 766.111488c-10.022261 10.022261-10.022261 26.252921 0 36.275182 10.022261 10.022261 26.252921 10.022261 36.275181 0l544.113395-544.113395c10.024308-9.998725 10.024308-26.253944 0.001024-36.276205zM551.908942 370.744859c-12.660344-3.548826-25.942859-5.610788-39.751353-5.610788-80.990592 0-146.661268 65.670675-146.661268 146.661268 0 13.787004 2.037403 27.093055 5.609765 39.751352l180.802856-180.801832zM473.076502 653.014664c12.467963 3.452635 25.53456 5.442966 39.105647 5.442966 80.990592 0 146.661268-65.670675 146.661267-146.661268 0-13.571087-1.990331-26.637684-5.442966-39.105646L473.076502 653.014664z" fill="" p-id="4093"></path><path d="M233.914494 688.714747l34.500768-34.500768c-54.498218-36.084846-101.370759-84.252893-136.25629-142.0349C212.671681 378.75223 356.984461 296.394501 512.01228 296.394501c34.742269 0 68.882833 4.339842 101.969392 12.275581l39.032992-39.032992c-45.194318-13.690814-92.594885-21.171182-141.003408-21.171182-176.824241 0-341.011674 96.55201-428.501284 251.965615l-6.616698 11.772115 6.616698 11.773138c37.644365 66.819848 89.5045 122.68418 150.404522 164.737971zM940.490028 500.4305C902.918317 433.657724 851.105255 377.841487 790.30347 335.787696l-34.477232 34.477232c54.402027 36.059264 101.202936 84.180238 136.040372 141.915174-80.488149 133.451408-224.799906 215.784578-379.852284 215.784578-34.646078 0-68.691475-4.339842-101.682867-12.202926l-39.056527 39.056527c45.122687 13.641695 92.428086 21.098527 140.739394 21.098527 176.847777 0 341.036233-96.55201 428.476725-251.989151l6.615675-11.747555-6.616698-11.749602z" fill=var(--main-font-color) p-id="4094"></path></svg>
                </div>


                <!-- 4 -->
                <div class="line-form">
                  <input type="text" v-model="inviteCode"  tabindex="4" placeholder
                  @mouseenter="changeLine4State(true)"
                  @mouseleave="changeLine4State(false)"
                  @focus="changeForm4FocusState(true)"
                  @blur="changeForm4FocusState(false)"
                  class="password"
                  :class="[isForm4FocusState?'line-form-input-enter':'line-form-input-leave']"
                  >
                  <i  class="line-form-line"
                  :class="[isLine4State||isForm4FocusState?'line-form2-enter':'line-form2-leave']"
                  ></i>
                  <div
                  :class="[isForm4FocusState||inviteCode?'scale-placeholder-enter':'scale-placeholder-leave']"
                  ><span>邀请码(选填)</span>
                </div>
                <svg t="1717251147392" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="6087"><path d="M514.048 54.272q95.232 0 178.688 36.352t145.92 98.304 98.304 145.408 35.84 178.688-35.84 178.176-98.304 145.408-145.92 98.304-178.688 35.84-178.176-35.84-145.408-98.304-98.304-145.408-35.84-178.176 35.84-178.688 98.304-145.408 145.408-98.304 178.176-36.352zM515.072 826.368q26.624 0 44.544-17.92t17.92-43.52q0-26.624-17.92-44.544t-44.544-17.92-44.544 17.92-17.92 44.544q0 25.6 17.92 43.52t44.544 17.92zM567.296 574.464q-1.024-16.384 20.48-34.816t48.128-40.96 49.152-50.688 24.576-65.024q2.048-39.936-8.192-74.752t-33.792-59.904-60.928-39.936-87.552-14.848q-62.464 0-103.936 22.016t-67.072 53.248-35.84 64.512-9.216 55.808q1.024 26.624 16.896 38.912t34.304 12.8 33.792-10.24 15.36-31.232q0-12.288 7.68-30.208t20.992-34.304 32.256-27.648 42.496-11.264q46.08 0 73.728 23.04t25.6 57.856q0 17.408-10.24 32.256t-26.112 28.672-33.792 27.648-33.792 28.672-26.624 32.256-11.776 37.888l1.024 38.912q0 15.36 14.336 29.184t37.888 14.848q23.552-1.024 37.376-15.36t12.8-32.768l0-24.576z" p-id="6088" fill="#999"></path></svg>
                </div>


                <!-- 注册按钮 -->
                <!-- 登录按钮 -->
                <div class="but-sign-up">
                  <button>
                    <a href="#">
                      <svg t="1717251289028" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="7984"><path d="M632.555 583.662a334.724 334.724 0 0 1 34.43 15.764c13.844 7.312 19.14 24.463 11.828 38.308-7.312 13.845-24.463 19.14-38.308 11.829-39.825-21.033-84.256-32.18-130.354-32.18-134.46 0-249.156 95.628-274.315 225.944-2.968 15.373-17.837 25.43-33.21 22.462-15.374-2.968-25.43-17.837-22.462-33.21 22.237-115.181 102.51-207.796 207.629-248.892-76.518-42.868-128.233-124.698-128.233-218.602 0-138.316 112.198-250.435 250.592-250.435 138.392 0 250.59 112.12 250.59 250.435 0 93.886-51.695 175.702-128.187 218.577z m71.487-218.577c0-106.992-86.804-193.735-193.89-193.735-107.088 0-193.892 86.742-193.892 193.735 0 106.992 86.804 193.734 193.892 193.734 107.086 0 193.89-86.743 193.89-193.734z m12.694 346.77V626.83a28.26 28.26 0 0 1 3.87-14.324 28.468 28.468 0 0 1 10.175-10.174 28.26 28.26 0 0 1 14.324-3.87 28.26 28.26 0 0 1 14.324 3.87 28.468 28.468 0 0 1 10.174 10.174 28.26 28.26 0 0 1 3.87 14.324v85.025h84.179c15.656 0 28.348 12.692 28.348 28.349 0 15.656-12.692 28.348-28.348 28.348h-84.18v84.08a28.26 28.26 0 0 1-3.87 14.324 28.468 28.468 0 0 1-10.173 10.174 28.26 28.26 0 0 1-14.324 3.87 28.26 28.26 0 0 1-14.324-3.87 28.468 28.468 0 0 1-10.175-10.174 28.26 28.26 0 0 1-3.87-14.324v-84.08h-85.124c-15.656 0-28.348-12.692-28.348-28.348 0-15.657 12.692-28.349 28.348-28.349h85.124z" fill="#fff" p-id="7985"></path></svg>
                    </a>
                    <span class="register">注册</span>
                  </button>
                </div>

              </form>

            </div>
          </div>


        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props:['isSignIn','isSignUp'],
  data(){
    return{
      username:'',
      password:'',
      email:'',
      SignUpUsername:'',
      SignUpPassword:'',
      inviteCode:'',
      isLine1State:false,
      isLine2State:false,
      isLine3State:false,
      isLine4State:false,
      isForm1FocusState:false,
      isForm2FocusState:false,
      isForm3FocusState:false,
      isForm4FocusState:false,
      isPasswordState:false,
      isPasswordState2:false,
      isJumpState:false,
      isFindPasswordState:false,
      isCloseState:false,
      
    }
  },
  methods:{
    closeSign(state){
      this.$emit('update:isSignIn',state)
      this.$emit('update:isSignUp',state)
    },
    changeLine1State(state){
      this.isLine1State=state
    },
    changeForm1FocusState(state){
      this.isForm1FocusState=state
    },
    changeLine2State(state){
      this.isLine2State=state
    },
    changeForm2FocusState(state){
      this.isForm2FocusState=state
    },
    changeLine3State(state){
      this.isLine3State=state
    },
    changeForm3FocusState(state){
      this.isForm3FocusState=state
    },
    changeLine4State(state){
      this.isLine4State=state
    },
    changeForm4FocusState(state){
      this.isForm4FocusState=state
    },
    changePasswordState(state){
      this.isPasswordState=state
      const type=document.querySelector('.password')
      if(this.isPasswordState){
        type.type='text'
      }else{
        type.type='password'
      }
    },
     changePasswordState2(state){
      this.isPasswordState2=state
      const type=document.querySelector('.password2')
      if(this.isPasswordState2){
        type.type='text'
      }else{
        type.type='password'
      }
    },
    changeJumpState(state){
      this.isJumpState=state
    },
    changeFindPasswordState(state){
      this.isFindPasswordState=state
    },
    changeCloseState(state){
      this.isCloseState=state
    },
    showSignUp(){
      this.$emit('update:isSignIn',false)
      this.$emit('update:isSignUp',true)
    },
    showSignIn(){
      this.$emit('update:isSignIn',true)
      this.$emit('update:isSignUp',false)
    }
  }
}
</script>

<style>
@import url(../css/UserSign.css);
</style>