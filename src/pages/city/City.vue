<!--  -->
<template>
<div >
    <city-header></city-header>
    <city-search></city-search>
    <city-list :cities="cities"
     :hot="hotCities"
     :letter= "letter"
    ></city-list>
     <city-alphabet :cities="cities" @change="handleLetterchange"></city-alphabet>
 
 
</div>
</template>

<script>
import axios from 'axios'
import CityHeader from './components/Header'
import CitySearch from './components/Search'
import CityList from './components/List'
import CityAlphabet from './components/Alphabet'

//这里可以导入其他文件（比如：组件，工具js，第三方插件js，json文件，图片文件等等）
//例如：import 《组件名称》 from '《组件路径》';
//import Swiper from "swiper";

export default {
name:'City',
//import引入的组件需要注入到对象中才能使用
components: {
    CityHeader,
    CitySearch,
    CityList,
    CityAlphabet
   
},
data() {
//这里存放数据
return {
    cities: {},
    hotCities:[],
    letter: ''

};
},
//监听属性 类似于data概念
computed: {},
//监控data中的数据变化
watch: {},
//方法集合 专门存放方法比如点击事件
methods: {
    getCityInfo(){
        axios.get('/api/city.json')
        .then(this.handleGetCityInfoSucc)

    },
    handleGetCityInfoSucc(res){
        res=res.data
        if(res.ret && res.data) {
        const data= res.data
        this.cities=data.cities
        this.hotCities=data.hotCities
        }

    },
    handleLetterchange(letter){
        this.letter= letter
        

    }

},
//生命周期 - 创建完成（可以访问当前this实例）
created() {

},
//生命周期 - 挂载完成（可以访问DOM元素）
mounted() {
    this.getCityInfo()
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

</style>