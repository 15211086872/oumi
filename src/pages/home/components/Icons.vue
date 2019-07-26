<!-- .icons {
  width: 100%;
  overflow: hidden;
  height: 0;
  padding-bottom: 50%;

  .icon {
    position: relative;
    overflow: hidden;
    float: left;
    width: 25%;
    height: 0;
    padding-bottom: 25%;

    .icon-img {
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0.44rem;
      box-sizing: border-box;
      padding: 0.1rem;

      .icon-img-content {
        display: block;
        margin: 0 auto;
        height: 100%;
      }
    }

    .icon-img-text {
      position: absolute;
      left: 0;
      right: 0;
      bottom: 0;
      height: 0.44rem;
      line-height: 0.44rem;
      text-align: center;
      color: #333;
    }
  }
} -->
<template>
  <div>
    <!-- <div class="icons">
      <div class="icon">
        <div class="icon-img">
          <img
            class="icon-img-content"
            src="http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png"
          />
          <p class="icon-img-text">景点门票</p>
        </div>
      </div>
    </div> -->
    <div class="flex-box">
      <swiper :options="swiperOption" >
        <swiper-slide v-for="(page,index) of pages" :key="index">
          <ul>
            <li v-for="item of page" :key="item.id">
              <img :src="item.imgUrl" />
              <p>{{item.desc}}</p>
            </li>
          </ul>
        </swiper-slide>
      </swiper>
    </div>
  </div>
</template>

<script>
//这里可以导入其他文件（比如：组件，工具js，第三方插件js，json文件，图片文件等等）
//例如：import 《组件名称》 from '《组件路径》';
//import Swiper from "swiper";

export default {
  name: "HomeIcons",
  props:{
    list: Array
  },
  //import引入的组件需要注入到对象中才能使用
  components: {},
  data() {
    //这里存放数据
    return {
      swiperOption: {
        autoplay: false
      },
      
     
    };
  },
  //监听属性 类似于data概念
  computed: { 
    pages() {
     const pages = []
     this.list.forEach((item, index) => {
        const page = Math.floor(index / 8)
        console.log(pages)
        if (!pages[page]) {
         pages[page] = [];
        }
       pages[page].push(item)
      })
       return pages
     }
 
  },
  //监控data中的数据变化
  watch: {},
  //方法集合 专门存放方法比如点击事件
  methods: {},
  //生命周期 - 创建完成（可以访问当前this实例）
  created() {},
  //生命周期 - 挂载完成（可以访问DOM元素）
  mounted() {
    //this.getData();//加载完后执行getData这个函数


      
  },
  beforeCreate() {}, //生命周期 - 创建之前
  beforeMount() {}, //生命周期 - 挂载之前
  beforeUpdate() {}, //生命周期 - 更新之前
  updated() {}, //生命周期 - 更新之后
  beforeDestroy() {}, //生命周期 - 销毁之前
  destroyed() {}, //生命周期 - 销毁完成
  activated() {} //如果页面有keep-alive缓存功能，这个函数会触发
};
</script>  
<style  lang="stylus" scoped>


.flex-box {
  ul {
    text-align: center;
    display: flex;
    
    
    justify-content: space-around;
    flex-wrap: wrap;

    li {
      width: 25%;
     


      img {
        width: 60%;
        
      }

      span {
        display: block;
        
      }
    }
  }
}



</style>