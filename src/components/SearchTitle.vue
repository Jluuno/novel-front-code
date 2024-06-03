<template>
  <div class="SearchContainer">
    <div class="search-box">
        <!-- 关闭 -->
        <div class="close"
          @click="closeSearchTitle(false)"
          >
            <svg 
            t="1717221705278"  viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="2294"><path d="M512 474.794667l261.8368-261.802667c24.7808-24.814933 61.986133 12.3904 37.205333 37.1712L549.1712 512l261.870933 261.8368c24.7808 24.7808-12.424533 61.986133-37.205333 37.205333L512 549.1712l-261.8368 261.870933c-24.7808 24.7808-61.986133-12.424533-37.205333-37.205333L474.8288 512 212.957867 250.1632c-24.7808-24.7808 12.424533-61.986133 37.205333-37.205333L512 474.8288z" fill="#999999" p-id="2295"></path></svg>
        </div>
       
        <!-- 搜索栏 -->
        <div class="search-main">
            <div class="search-input">
              <form class="padding-10">
                <div class="line-form">

                  
                    <div class="select-container">
                      <a href="#"
                      @mouseenter="changeSelectState(true)"
                      @mouseleave="changeSelectState(false)"
                      @click="changeClickSelectState(!isClickSelectState)"
                      :class="[isSelectState||isClickSelectState?'select-enter':'select-leave']"
                      
                      >
                        <span class="font-left">{{fontLeft}}</span>
                        <svg t="1717317782023" class="select" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="9247"><path d="M815.253186 634.31027H208.917468c-29.864551 0-47.783282 20.819859-32.851006 36.776061 22.35575 25.598187 289.771475 325.267627 303.167859 339.602612 16.468167 19.283967 52.305628 16.126858 67.237904 0 10.409929-11.092548 285.249128-321.939863 301.631968-339.602612 14.932276-17.577422-4.437019-35.24017-32.851007-36.776061zM208.917468 390.786186h606.335718c28.413987 0 47.783282-19.19864 32.851007-36.861389-16.38284-17.662749-291.222038-328.424737-303.167859-341.309157-13.396384-15.956203-49.233846-17.577422-67.152577 0-11.945821 16.126858-279.361545 315.71097-301.717295 341.309157-14.932276 16.04153 2.986455 36.861389 32.851006 36.861389z"  p-id="9248"></path></svg>
                      </a>

                      <!-- 选择搜索类型悬挂 -->
                      <ul
                      class="dropdown-menu"
                      :class="[isClickSelectState?'dropdown-menu-enter':'dropdown-menu-leave']"
                      >
                        <li
                        @mouseenter="changeDropdownMenu1(true)"
                        @mouseleave="changeDropdownMenu1(false)"
                        :class="{'li-enter':isDropdownMenu1}"
                        >
                          <a href="#"
                          @click="changeFontLeft('文章'),changeClickSelectState(!isClickSelectState)"
                          :class="{'DropDownMenuA-enter':isDropdownMenu1}"
                          >文章</a>
                        </li>
                        <li
                        @mouseenter="changeDropdownMenu2(true)"
                        @mouseleave="changeDropdownMenu2(false)"
                        :class="{'li-enter':isDropdownMenu2}"
                        >
                          <a href="#" 
                          @click="changeFontLeft('用户'),changeClickSelectState(!isClickSelectState)"
                          :class="{'DropDownMenuA-enter':isDropdownMenu2}"
                          >用户</a>
                        </li>
                      </ul>

                    </div>
                  


                  
                  <i class="line-inline"></i>
                  

                  <div class="input-container">
                    <input type="text" v-model="SearchContent" tabindex="1" placeholder
                          @mouseenter="changeLineState(true)"
                          @mouseleave="changeLineState(false)"
                          @focus="changeFormFocusState(true)"
                          @blur="changeFormFocusState(false)"
                          :class="[isFormFocusState ? 'line-form-input-enter' : 'line-form-input-leave']"
                          >
                          <i class="line-form-line"
                          :class="[isLineState || isFormFocusState ? 'line-form1-enter' : 'line-form1-leave']"
                          ></i>
                          <div
                          :class="[isFormFocusState || SearchContent ? 'scale-placeholder-enter' : 'scale-placeholder-leave']"
                          >

                  
                  
                          <span class="font-right">开启精彩搜索</span>
                
                
                        </div>
                  </div>


                  <svg t="1717316262714" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="2493"><path d="M854.87104 849.87904a30.01856 30.01856 0 0 1-42.43968 0l-140.12416-140.18048c-54.27712 46.8224-124.8256 75.33056-202.10688 75.33056-171.136 0-309.85216-138.71616-309.85216-309.85216 0-171.11552 138.71104-309.85216 309.85216-309.85216 171.15648 0 309.85216 138.73664 309.85216 309.85216 0 72.18688-24.9088 138.49088-66.304 191.14496l141.14816 141.15328a30.07488 30.07488 0 0 1-0.0256 42.40384zM470.1952 225.29536c-137.99424 0-249.87648 111.88736-249.87648 249.8816 0 138.01472 111.88736 249.8816 249.87648 249.8816 137.99936 0 249.87648-111.872 249.87648-249.8816 0.00512-137.99424-111.87712-249.8816-249.87648-249.8816z" p-id="2494" fill=var(--book-body-content)></path></svg>
                </div>

                
              </form>


              <div class="search-keywords">
                <div class="hot-search-title">
                  <span>热门搜索</span>
                </div>
                <!-- 标签 -->
                <div class="tag-container">
                        <a href="#"
                        class="tag"
                         v-for="(item, index) in hotSearchItems" :key="index"
                         >
                         <span>{{ item.tagName }}</span></a>
        

                      </div>
              </div>



              <div class="hot-book">
                <!-- 热门文章标题 -->
                <div class="hot-book-title">
                  <span>热门文章</span>
                </div>
                <!-- 热门文章轮播图 -->
                <!-- 轮播图盒子 超出要hidden-->
                <div class="swiper-container"
                @mouseenter="changeImageMouseState(true)"
                @mouseleave="changeImageMouseState(false)"
                >
                  <!-- 轮播图图片 -->
                  <div class="swiper-wrapper"
                  :class="[isImageMove?'swiper-wrapper-enter':'swiper-wrapper-leave']"
                  
                  >
                    <!-- 每一个图片项目 -->
                    <div class="swiper-slide"
                    v-for="(item,index) in hotSearchImageItems" :key="index"
                    >
                      <a href="#">
                        <div class="hover-zoom-img"
                          @mouseenter="mouseEnterImage(index,true)"
                          @mouseleave="mouseEnterImage(index,false)"
                        >
                          <!-- 图片 -->
                          <img :src='item.img' alt="" class="fit-cover"
                          :class="[isImageMove?'ban-img-prevent-enter':'ban-img-prevent-leave',itemImageStates[index]?.isMouseEnterImage?'fit-cover-enter':'fit-cover-leave']">
                          <!-- 书名 -->
                          <div class="img-title1"
                          :class="[itemImageStates[index]?.isMouseEnterImage?'img-title1-enter':'img-title1-leave']"
                          ><span>{{item.title}}</span></div>
                          <!-- 悬浮书名+日期 -->
                          <div class="img-title2"
                          :class="[itemImageStates[index]?.isMouseEnterImage?'img-title2-enter':'img-title2-leave']"
                          >
                            <!-- 隐藏的书名 -->
                            <div class="hidden-title"><span>{{item.title}}</span></div>
                            <!-- 隐藏的日期 -->
                            <div class="hidden-time">
                              <div class="hidden-time-div">{{item.time}}</div>
                              <div class="hidden-time-svg">
                                
                                  <!-- svg -->
                                  <svg t="1716998291127" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="9060"><path d="M512 619.789474c-59.284211 0-107.789474-48.505263-107.789474-107.789474s48.505263-107.789474 107.789474-107.789474 107.789474 48.505263 107.789474 107.789474-48.505263 107.789474-107.789474 107.789474z m0-80.842106c16.168421 0 26.947368-10.778947 26.947368-26.947368s-10.778947-26.947368-26.947368-26.947368-26.947368 10.778947-26.947368 26.947368 10.778947 26.947368 26.947368 26.947368z" fill="#fff" p-id="9061"></path><path d="M509.305263 781.473684C231.747368 781.473684 80.842105 512 80.842105 512S234.442105 242.526316 512 242.526316c280.252632 0 431.157895 269.473684 431.157895 269.473684s-153.6 266.778947-433.852632 269.473684c2.694737 0 0 0 0 0z m2.694737-80.842105c167.073684 0 282.947368-123.957895 334.147368-188.631579-48.505263-64.673684-164.378947-188.631579-334.147368-188.631579-167.073684 0-282.947368 123.957895-334.147368 188.631579 48.505263 64.673684 164.378947 188.631579 334.147368 188.631579z" fill="#fff" p-id="9062"></path></svg>
                                  {{item.viewsCount}}
                          
                              </div>
                            </div>
                          </div>
                        </div>
                      </a>
                    </div>


                   

                   
                  
                   
                  </div>


                  <!-- 上一张图片按钮 -->
                  <div class="swiper-button-prev"
                  :class="[isImageMove?'swiper-button-prev-visible':'swiper-button-prev-hidden',isImageMouseState?'swiper-button-prev-mouseenter':'swiper-button-prev-mouseleave']"
                  @click="moveImage(false)"
                  >
                  <svg t="1717418562207" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="5154"><path d="M729.6 931.2l-416-425.6 416-416c9.6-9.6 9.6-25.6 0-35.2-9.6-9.6-25.6-9.6-35.2 0l-432 435.2c-9.6 9.6-9.6 25.6 0 35.2l432 441.6c9.6 9.6 25.6 9.6 35.2 0C739.2 956.8 739.2 940.8 729.6 931.2z" p-id="5155" fill="#fff"></path></svg>
                  </div>


                  <!-- 下一张图片按钮 -->
                  <div class="swiper-button-next"
                  @click="moveImage(true)"
                  :class="[isImageMove?'swiper-button-next-hidden':'swiper-button-next-visible',isImageMouseState?'swiper-button-next-mouseenter':'swiper-button-next-mouseleave']"
                  >
                  <svg t="1717418491679" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="4184"><path d="M761.6 489.6l-432-435.2c-9.6-9.6-25.6-9.6-35.2 0-9.6 9.6-9.6 25.6 0 35.2l416 416-416 425.6c-9.6 9.6-9.6 25.6 0 35.2s25.6 9.6 35.2 0l432-441.6C771.2 515.2 771.2 499.2 761.6 489.6z" p-id="4185" fill="#fff"></path></svg>
                  </div>

                </div>
              </div>
            </div>
        </div>
    </div>
  </div>
</template>

<script>
export default {
  props:['hotSearchItems','hotSearchImageItems'],
  data(){
    return{
      SearchContent:'',
      isLineState:false,
      isFormFocusState:false,
      isSelectState:false,
      fontLeft:'文章',
      isClickSelectState:false,
      isDropdownMenu1:false,
      isDropdownMenu2:false,
      isImageMove:false,
      isImageMouseState:false,
      itemImageStates:{}
      
    }
  },
  methods:{
    ensureItemImageState(index) {
      if (!this.itemImageStates[index]) {
        this.$set(this.itemImageStates, index, {
          isMouseEnterImage:false,
          });
      }
    },
    closeSearchTitle(state){
      this.$emit('update:isSearchTitle',state)
    },
    changeFormFocusState(state){
      this.isFormFocusState=state
    },
    changeLineState(state){
      this.isLineState=state
    },
    changeSelectState(state){
      this.isSelectState=state
    },
    changeFontLeft(font){
      this.fontLeft=font
    },
    changeClickSelectState(state){
      this.isClickSelectState=state
    },
    changeDropdownMenu1(state){
      this.isDropdownMenu1=state
    }, 
    changeDropdownMenu2(state){
      this.isDropdownMenu2=state
    },
    moveImage(state){
      this.isImageMove=state
    },
    changeImageMouseState(state){
      this.isImageMouseState=state
    },
    mouseEnterImage(index,state){
      this.ensureItemImageState(index);
      this.$set(this.itemImageStates[index], 'isMouseEnterImage', state);
    }
  }
}
</script>

<style>
@import url(../css/SearchTitle.css);
</style>