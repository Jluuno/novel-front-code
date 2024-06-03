<template>
  <div class="sidebar">
    <!-- 最新小说 -->
    <div class="theme-box theme-box1"
        @mouseenter="changeBoxBodyTitleState(true)"
        @mouseleave="changeBoxBodyTitleState(false)"
    >
      <!-- 侧栏盒子 -->
      <div class="box-body">
        <ul class="list-inline">
          <li>
            <a href="#" 
            :class="[
              { 'mouse-enter': isBoxBodyTitleState },
              isBoxBodyTitleState ? 'a-enter' : 'a-leave'
              ]"
            >
            最新小说</a>
          </li>
        </ul>
      </div>
      <!-- 侧栏列表 -->
      <div class="tab-content">
        <div class="tab-pane"
        v-for="(item,index) in newBookItems" :key="index"
        @mouseenter="changeTabPaneState(index,true)"
        @mouseleave="changeTabPaneState(index,false)"
        >
          <!-- 列表小盒子 flex -->
          <div class="posts-mini">
            <!-- 图片 -->
            <div class="tab-image-container">
              <div class="tab-image">
                <a href="#">
                  <img :src=item.imgSrc alt=""
                  :class="[itemStates[index]?.isTabPaneState?'img-enter':'img-leave']"
                  >
                </a>
              </div>
            </div>
            <!-- 其他信息 -->
            <div class="tab-other">
              <!-- 标题 -->
              <h2 class="item-heading"
                @mouseenter="changeHeadingTitleState(index,true)"
                @mouseleave="changeHeadingTitleState(index,false)"
              >
                <span class="heading-number"
                :class="`bg-color-${index+1}`"
                >{{ index+1 }}</span>
                <a href="#"
                :class="[itemStates[index]?.isHeadingTitleState?'item-heading-title-enter':'item-heading-title-leave']"
                >{{ item.title }}</a>
              </h2>
              <!-- 作者，评论等元素 -->
              <div class="item-meta">
                <!-- 左边 -->
                <div class="userAndTime">
                  <a href="#" class="avatar-mini">
                    <!-- 头像 -->
                      <img :src=item.avatar alt=""
                      @mouseenter="changeAvatarState(index,true)"
                      @mouseleave="changeAvatarState(index,false)"
                      :class="[itemStates[index]?.isAvatarState?'avatar-img-enter':'avatar-img-leave']"
                      >
                  </a>
                    <!-- 时间 -->
                  <span class="meta-time">{{item.time}}</span>
                </div>
                <!-- 右边 -->
                <div class="meta-right">
                  <a href="">
                    <!-- svg -->
                    <svg t="1717045165693" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="2548"><path d="M853.333333 768c35.413333 0 64-20.650667 64-55.978667V170.581333A63.978667 63.978667 0 0 0 853.333333 106.666667H170.666667C135.253333 106.666667 106.666667 135.253333 106.666667 170.581333v541.44C106.666667 747.285333 135.338667 768 170.666667 768h201.173333l110.016 117.44a42.752 42.752 0 0 0 60.586667 0.042667L651.904 768H853.333333z m-219.029333-42.666667h-6.250667l-115.797333 129.962667c-0.106667 0.106667-116.010667-129.962667-116.010667-129.962667H170.666667c-11.776 0-21.333333-1.621333-21.333334-13.312V170.581333A21.205333 21.205333 0 0 1 170.666667 149.333333h682.666666c11.776 0 21.333333 9.536 21.333334 21.248v541.44c0 11.754667-9.472 13.312-21.333334 13.312H634.304zM341.333333 490.666667a42.666667 42.666667 0 1 0 0-85.333334 42.666667 42.666667 0 0 0 0 85.333334z m170.666667 0a42.666667 42.666667 0 1 0 0-85.333334 42.666667 42.666667 0 0 0 0 85.333334z m170.666667 0a42.666667 42.666667 0 1 0 0-85.333334 42.666667 42.666667 0 0 0 0 85.333334z" fill="#999999" p-id="2549"></path></svg>
                    <span>{{item.commentsCount}}</span>
                  </a>
                  <a href="">
                    <!-- svg -->
                    <svg t="1716998291127" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="9060"><path d="M512 619.789474c-59.284211 0-107.789474-48.505263-107.789474-107.789474s48.505263-107.789474 107.789474-107.789474 107.789474 48.505263 107.789474 107.789474-48.505263 107.789474-107.789474 107.789474z m0-80.842106c16.168421 0 26.947368-10.778947 26.947368-26.947368s-10.778947-26.947368-26.947368-26.947368-26.947368 10.778947-26.947368 26.947368 10.778947 26.947368 26.947368 26.947368z" fill="#999999" p-id="9061"></path><path d="M509.305263 781.473684C231.747368 781.473684 80.842105 512 80.842105 512S234.442105 242.526316 512 242.526316c280.252632 0 431.157895 269.473684 431.157895 269.473684s-153.6 266.778947-433.852632 269.473684c2.694737 0 0 0 0 0z m2.694737-80.842105c167.073684 0 282.947368-123.957895 334.147368-188.631579-48.505263-64.673684-164.378947-188.631579-334.147368-188.631579-167.073684 0-282.947368 123.957895-334.147368 188.631579 48.505263 64.673684 164.378947 188.631579 334.147368 188.631579z" fill="#999999" p-id="9062"></path></svg>
                    <span>{{item.viewsCount}}</span>
                  </a>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>

      
    </div>



    <!-- 热门小说 -->
    <div class="theme-box"
    @mouseenter="changeHotNovelState(true)"
    @mouseleave="changeHotNovelState(false)"
    >
      <!-- 主题title -->
      <div class="box-body theme-title">
        <ul class="hot-novel-ul">
          <li>
            <a href="#"
            :class="[isHotNovelState?'hot-a-enter':'hot-a-leave']"
            >热门小说</a>
          </li>
        </ul>
      </div>
      <!-- 热门小说列表 -->
      <div class="box-body hot-novel-lists">
        <div class="hot-novel-li-container"
        v-for="(item,index) in hotBookItems" :key="index"
        @mouseenter="changeHotBookItemState(index,true)"
        @mouseleave="changeHotBookItemState(index,false)"
        >
          <div class="hot-novel-li">
            <h2 class="hot-novel-h2">
              <span class="heading-number"
              :class="`bg-color-${index+1}`"
              >{{index+1}}</span>
              <a href="#"
              :class="[hotBookItemState[index]?.isHotBookItemState?'hot-novel-a-enter':'hot-novel-a-leave']"
              >{{item.title}}</a>
            </h2>
          </div>
        </div>

      </div>
    </div>






    <!-- 小说标签 -->
    <div class="theme-box"
    @mouseenter="changeTagState(true)"
    @mouseleave="changeTagState(false)"
    >
      <!-- 主题title -->
      <div class="box-body theme-title">
        <ul class="hot-novel-ul">
          <li>
            <a href="#"
            :class="[isTagState?'hot-a-enter':'hot-a-leave']"
          
            >小说标签</a>
          </li>
        </ul>
      </div>

      <!-- 标签 -->
      <div class="box-body tag-container">
        <a href="#"
        class="tag"
         @mouseenter="changeTagState(index,true)"
         @mouseleave="changeTagState(index,false)"
         v-for="(item,index) in tagsItems" :key="index"
         :class="`tag${index + 1}`"
         >
         <span>{{item.tagName}}</span></a>
        

      </div>

      
    </div>
  </div>
</template>

<script>
export default {
  props:['newBookItems','hotBookItems','tagsItems'],
  data(){
    return{
      isBoxBodyTitleState:false,
      isHotNovelState:false,
      isTagState:false,
      itemStates: {},
      hotBookItemState:{},
    }
  },
  methods:{
    ensureItemState(index) {
      if (!this.itemStates[index]) {
        this.$set(this.itemStates, index, {
          isTabPaneState:false,
          isHeadingTitleState:false,
          isAvatarState:false,
          });
      }
    },
    ensureHotBookItemState(index) {
      if (!this.hotBookItemState[index]) {
        this.$set(this.hotBookItemState, index, {
          isHotBookItemState:false,
          });
      }
    },
    changeBoxBodyTitleState(state){
      this.isBoxBodyTitleState=state
    },
    changeTabPaneState(index,state){
      this.ensureItemState(index)
      this.$set(this.itemStates[index], 'isTabPaneState', state);
    },
    changeHeadingTitleState(index,state){
      this.ensureItemState(index)
      this.$set(this.itemStates[index], 'isHeadingTitleState', state);
    },
    changeAvatarState(index,state){
      this.ensureItemState(index)
      this.$set(this.itemStates[index], 'isAvatarState', state);
    },
    changeHotNovelState(state){
      this.isHotNovelState=state
    },
    changeHotBookItemState(index,state){
      this.ensureHotBookItemState(index)
      this.$set(this.hotBookItemState[index],'isHotBookItemState',state)
    },
    changeTagState(state){
      this.isTagState=state
    }
  }
}
</script>

<style>
@import '../css/SideBar.css'
</style>