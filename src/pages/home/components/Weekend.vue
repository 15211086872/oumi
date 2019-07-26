<!--  -->
<template>
<div>
   <div class='title'>周末去哪儿</div>
   <ul>
      <li class="item" v-for="item of list" :key="item.id">
          <div class="item-img-wrap">
              <img class="item-img" :src= 'item.imgUrl'/>
          </div>
          <div class="item-info">
              <P class="item-title">{{item.title}}</P>
              <p class="item-desc">{{item.desc}}</p>
              
          </div>


      </li>

    </ul>
 
</div>
</template>

<script>
//这里可以导入其他文件（比如：组件，工具js，第三方插件js，json文件，图片文件等等）
//例如：import 《组件名称》 from '《组件路径》';
//import Swiper from "swiper";

export default {
name:'HomeWeekend',
props: {
    list: Array
},
//import引入的组件需要注入到对象中才能使用
components: {},
data() {
//这里存放数据
return {
    

};
},
//监听属性 类似于data概念
computed: {},
//监控data中的数据变化
watch: {},
//方法集合 专门存放方法比如点击事件
methods: {

},
//生命周期 - 创建完成（可以访问当前this实例）
created() {

},
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
activated() {}, //如果页面有keep-alive缓存功能，这个函数会触发
}
</script>
<style  lang="stylus" scoped>
.title{
    color: #212121;
    
    line-height: 47px;
    background: #eee;
    text-indent: 20px;
}
.item-img-wrap{
        overflow: hidden
       
        height: 0
        padding-bottom: 34.5%

    
    .item-img{
        width : 100%
    }
}    
    .item-info{
        padding: .1rem;
    
        .item-title{
           line-light: .54rem;
           
           font-size: 16px;
           overflow: hidden;
           white-space: nowrap;
           text-overflow: ellipsis;
        }   
       
        .item-desc{
           line-height: .4rem;
           color: #ccc;
           overflow:hidden;
           white-space:nowrap;
           text-overflow:ellipsis;
       }
    }   
        
       





    

</style>