<template>
  <div id="app">
    <transition name="fade">
      <div v-if="isSignIn||isSignUp" class="overlay"></div>
    </transition>
    
    
    <BookHeader 
      :currentActiveIndex="currentActiveIndex" 
      :isNight="isNight" 
      :isVisible="isVisible" 
      :menuItems="menuItems" 
      @update:menuItems="updateMenuItems"
      @update:currentActiveIndex="updateCurrentActiveIndex"
      @update:isNight="updateIsNight"
      @update:isVisible="updateIsVisible"
      @update:isSignIn="updateIsSignIn"
      @update:isSignUp="updateIsSignUp"
      @update:isSearchTitle="updateIsSearchTitle"
    />
    <div class="main" :class="{ 'disabled': isSignIn||isSignUp }">
      <BookBody 
      :currentActiveIndex="currentActiveIndex" 
      :isNight="isNight" 
      :isVisible="isVisible" 
      :menuItems="menuItems" 
      :bookItems="bookItems"
      @update:menuItems="updateMenuItems"
      @update:currentActiveIndex="updateCurrentActiveIndex"
      @update:isNight="updateIsNight"
      @update:isVisible="updateIsVisible"
    />
      <SideBar
      :newBookItems="newBookItems"
      :hotBookItems="hotBookItems"
      :tagsItems="tagsItems"
      />
    </div>

    <transition name="slide-fade">
    <UserSign v-if="isSignIn||isSignUp"
    :isSignIn="isSignIn"
    :isSignUp="isSignUp"
    @update:isSignIn="updateIsSignIn"
    @update:isSignUp="updateIsSignUp"
    />
    </transition>


    <transition name="move">
    <SearchTitle v-if="isSearchTitle"
    :isSearchTitle="isSearchTitle"
    :hotSearchItems="hotSearchItems"
    :hotSearchImageItems="hotSearchImageItems"
    @update:isSearchTitle="updateIsSearchTitle"
    />
  </transition>
  </div>
</template>

<script>
import BookHeader from './components/BookHeader.vue'
import BookBody from './components/BookBody.vue';
import SideBar from './components/SideBar.vue';
import UserSign from './components/UserSign.vue'
import SearchTitle from './components/SearchTitle.vue';


export default {
  components: {
    BookHeader,
    BookBody,
    SideBar,
    UserSign,
    SearchTitle
  },
  data() {
    
    return {
      currentActiveIndex: 0,
      isNight: false,
      isVisible: false,
      isSignIn: false, // 控制登录状态
      isSignUp:false,//控制注册状态
      isSearchTitle:false,//控制搜索栏
      menuItems: [
        { id:1,label: '玄幻·魔幻', isHovered: false },
        { id:2,label: '都市·职场', isHovered: false },
        { id:3,label: '武侠·仙侠', isHovered: false },
        { id:4,label: '科幻·灵异', isHovered: false },
        { id:5,label: '网游·竞技', isHovered: false },
        { id:6,label: '军事·历史', isHovered: false },
        { id:7,label: '女生·言情', isHovered: false },
        { id:8,label: '二次元', isHovered: false }
      ],
      bookItems:[
        {
        id:1,
        title:'《我能进入蜀山游戏》（校对版全本）作者：问心万古',
        imgSrc:require('./assets/我能进入蜀山游戏.jpg'),
        txt:'【TXT信息】：4.78 MB|226.54万字|14.16万总推荐|2.9评分',
        content:'有人看到清风观的道长召出一柄飞剑飞向了云端！ 有人在清风观的山道上看到了灯笼自己漂浮行走！ 清风观有一扇门打开，对面竟然...',
        money:'60',
        tag1:'# 轻松',
        tag2:'# 随身流',
        uname:'江湖小号',
        avatar:require('./assets/user-avatar.jpg'),
        time:'5小时前',
        commentsCount:'42',
        viewsCount:'11',
        likesCount:'8'
      },
      {
        id:2,
        title:'《吞天造化经》（校对版全本）作者：鬼疯子',
        imgSrc:require('./assets/吞天造化经.jpg'),
        txt:'【TXT信息】：11.31 MB | 521.9万字 | 613.6万累计人气值 | 2.6 评分',
        content:'洛毅为国而战重伤，却反被青梅竹马背叛，人仙血脉被抽离，其背后的真凶竟是自己的父皇和皇兄！ 成为废人后，被卖入帝国做赘...',
        money:'60',
        tag1:'# 修仙',
        tag2:'# 晋升流',
        uname:'我是你们的霸霸',
        avatar:require('./assets/user-avatar2.jpg'),
        time:'10小时前',
        commentsCount:'13',
        viewsCount:'15',
        likesCount:'4'
      },
      {
        id:3,
        title:'《吞天造化经》（校对版全本）作者：鬼疯子',
        imgSrc:require('./assets/吞天造化经.jpg'),
        txt:'【TXT信息】：11.31 MB | 521.9万字 | 613.6万累计人气值 | 2.6 评分',
        content:'洛毅为国而战重伤，却反被青梅竹马背叛，人仙血脉被抽离，其背后的真凶竟是自己的父皇和皇兄！ 成为废人后，被卖入帝国做赘...',
        money:'60',
        tag1:'# 修仙',
        tag2:'# 晋升流',
        uname:'我是你们的霸霸',
        avatar:require('./assets/user-avatar2.jpg'),
        time:'10小时前',
        commentsCount:'13',
        viewsCount:'15',
        likesCount:'4'
      }
      ],
      newBookItems:[
        {
          title:'《武侠：开局获得一甲子内力！》（校对版全本）作者：三十二变',
          imgSrc:require('./assets/武侠：开局获得一甲子内力！.jpg'),
          avatar:require('./assets/001.jpg'),
          uname:'小小龙',
          time:'5分钟前',
          commentsCount:'33',
          viewsCount:'55',
        },
        {
          title:'《武侠：开局获得一甲子内力！》（校对版全本）作者：三十二变',
          imgSrc:require('./assets/武侠：开局获得一甲子内力！.jpg'),
          avatar:require('./assets/001.jpg'),
          uname:'小小龙',
          time:'5分钟前',
          commentsCount:'33',
          viewsCount:'55',
        },
        {
          title:'《武侠：开局获得一甲子内力！》（校对版全本）作者：三十二变',
          imgSrc:require('./assets/武侠：开局获得一甲子内力！.jpg'),
          avatar:require('./assets/001.jpg'),
          uname:'小小龙',
          time:'5分钟前',
          commentsCount:'33',
          viewsCount:'55',
        },
        {
          title:'《武侠：开局获得一甲子内力！》（校对版全本）作者：三十二变',
          imgSrc:require('./assets/武侠：开局获得一甲子内力！.jpg'),
          avatar:require('./assets/001.jpg'),
          uname:'小小龙',
          time:'5分钟前',
          commentsCount:'33',
          viewsCount:'55',
        },
        {
          title:'《武侠：开局获得一甲子内力！》（校对版全本）作者：三十二变',
          imgSrc:require('./assets/武侠：开局获得一甲子内力！.jpg'),
          avatar:require('./assets/001.jpg'),
          uname:'小小龙',
          time:'5分钟前',
          commentsCount:'33',
          viewsCount:'55',
        },
        {
          title:'《武侠：开局获得一甲子内力！》（校对版全本）作者：三十二变',
          imgSrc:require('./assets/武侠：开局获得一甲子内力！.jpg'),
          avatar:require('./assets/001.jpg'),
          uname:'小小龙',
          time:'5分钟前',
          commentsCount:'33',
          viewsCount:'55',
        },
      ],
      hotBookItems:[
        {title:'《最后的黑暗之王》（校对版全本）作者：山川不念'},
        {title:'《一花一酒一仙人，亦眠亦醉亦长生》（校对版全本）作者：少吃亿点'},
        {title:'《我能采集万物》（校对版全本）作者：存叶'},
        {title:'《穿越：逆天改命只为长生不死》（校对版全本）作者：屌丝哥'},
        {title:'《古仙复苏，一万狐狸拜我为师》（校对版全本）作者：葡萄果醋'},
        {title:'《九转修罗诀》（校对版全本）作者：李中有梦'},
        {title:'《九转修罗诀》（校对版全本）作者：李中有梦'},
        {title:'《九转修罗诀》（校对版全本）作者：李中有梦'},
      ],
      tagsItems:[
        {tagName:'轻松'},
        {tagName:'穿越'},
        {tagName:'热血'},
        {tagName:'系统流'},
        {tagName:'重生'},
        {tagName:'腹黑'},
        {tagName:'赚钱'},
        {tagName:'无限流'},
        {tagName:'甜文'},
        {tagName:'爽文'},
        {tagName:'学生'},
        {tagName:'种田文'},
        {tagName:'位面'},
        {tagName:'明星'},
        {tagName:'宅男'},
        {tagName:'淡定'},
        {tagName:'技术流'},
        {tagName:'坚毅'},
        {tagName:'穿越时空'},
        {tagName:'机智'},
      ],
      hotSearchItems:[
        {tagName:'校对'},
        {tagName:'唐家三少'},
        {tagName:'赘婿'},
        {tagName:'封侯'},
        {tagName:'镇妖博物馆'},
        {tagName:'武侠世界'},
        {tagName:'天启'},
        {tagName:'都市灵剑仙'},
        {tagName:'宿主请留步'},
        {tagName:'乐园'},
        {tagName:'时停499年'},
        {tagName:'火影之救世主'},
        {tagName:'绝对交易'},
        {tagName:'文艺世界'},
        {tagName:'最强弃少'},
        {tagName:'极道骑士'},
        {tagName:'帝临鸿蒙'},
        {tagName:'不灭'},
        {tagName:'我要做球王'},
        {tagName:'灵魂拼图'},
      ],
      hotSearchImageItems:[
        {
          img:require('./assets/1.jpg'),
          title:'《道诡异仙》（精校版全本）作者：狐尾的笔',
          time:'1年前',
          viewsCount:1111111111
        },
        {
          img:require('./assets/2.jpg'),
          title:'《这游戏也太真实了》（校对版全本）作者：晨星LL',
          time:'2年前',
          viewsCount:21
        },
        {
          img:require('./assets/3.jpg'),
          title:'《深空彼岸》（校对版全本）作者：辰东',
          time:'1个月前',
          viewsCount:100
        },
        {
          img:require('./assets/4.jpg'),
          title:'《神秘复苏》（精校版全本）作者：佛前献花',
          time:'2个月前',
          viewsCount:113
        },
        {
          img:require('./assets/5.jpg'),
          title:'《遮天》（精校版全本）作者：辰东',
          time:'3个月前',
          viewsCount:222
        },
        {
          img:require('./assets/6.jpg'),
          title:'《秦吏》（精校版全本）作者：七月新番',
          time:'7个月前',
          viewsCount:111
        },
        
      ]
    }
  },
  methods: {
    updateMenuItems({ index, isHovered }) {
    this.menuItems[index].isHovered = isHovered;
    },
    updateCurrentActiveIndex(newIndex) {
      this.currentActiveIndex = newIndex;
    },
    updateIsNight(state){
      this.isNight=state
    },
    updateIsVisible(state){
      this.isVisible=state
    },
    updateIsSignIn(state){
      this.isSignIn=state
    },
    updateIsSignUp(state){
      this.isSignUp=state
    },
    updateIsSearchTitle(state){
      this.isSearchTitle=state
    }    
  }
}
</script>

<style>
.main{
  display: flex;
  justify-content: space-between;
  width: 78vw;
  margin: 0 auto;
  padding-top: 7vw;
}

.main.disabled {
  opacity: 0.8; /* 变暗 */
  pointer-events: none; /* 禁用点击事件 */
}


  /* 添加动画效果 */
.fade-enter-active, .fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active in <2.1.8 */ {
  opacity: 0;
}

/* 滑动淡入淡出动画效果 */
.slide-fade-enter-active {
  transition: all 0.5s ease;
}
.slide-fade-leave-active {
  transition: all 0.5s ease;
}
.slide-fade-enter, .slide-fade-leave-to {
  transform: translateY(-20px);
  opacity: 0;
}

.overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  z-index: 9999;
  pointer-events: all; /* 允许点击遮罩层关闭 */
}


/* 移动 */
.move-enter-active, .move-leave-active {
  transition: all .5s ease;
}
.move-enter, .move-leave-to {
  transform: translateY(-566px);
  opacity: 1;
}
.move-enter-to, .move-leave {
  transform: translateY(0);
  opacity: 1;
}

</style>

