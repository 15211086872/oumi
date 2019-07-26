<!--  -->
<template>
<div>
    <home-header :city="city"></home-header>
    <home-swiper :list="swiperList"></home-swiper>
    <home-icons :list="iconsList"></home-icons>
    <home-recommend :list="recommendList"></home-recommend>
    <home-weekend :list="weekendList"></home-weekend>

</div>
</template>

<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcons  from './components/Icons'
import HomeRecommend from './components/Recommend'
import HomeWeekend from './components/Weekend'
import axios from 'axios'
//这里可以导入其他文件（比如：组件，工具js，第三方插件js，json文件，图片文件等等）
//例如：import 《组件名称》 from '《组件路径》';
//import Swiper from "swiper";

export default {
name:'Home',
//import引入的组件需要注入到对象中才能使用
components: {
    HomeHeader,
    HomeSwiper,
    HomeIcons,
    HomeRecommend,
    HomeWeekend
},
data() {
//这里存放数据
return {
    city: '',
    swiperList: [],
    iconsList: [],
    recommendList: [],
    weekendList: []

};
},
//监听属性 类似于data概念
computed: {},
//监控data中的数据变化
watch: {},
//方法集合 专门存放方法比如点击事件
methods: {
    getHomeInfo(){
        axios.get('/api/index.json')
           .then(this.getHomeInfoSucc)
    },
     getHomeInfoSucc(res){
         res = res.data
    if (res.ret && res.data){
        const data= res.data
        this.city=data.city
        this.swiperList=data.swiperList
        this.iconsList=data.iconsList
        this.recommendList=data.recommendList
        this.weekendList=data.weekendList
        
    }
    console.log(res)
        
    }

},
//生命周期 - 创建完成（可以访问当前this实例）
created() {


},
//生命周期 - 挂载完成（可以访问DOM元素）
mounted() {
    this.getHomeInfo()
    
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
<style  scoped>

</style>