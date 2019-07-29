<!--  -->
<template>
<div>
<div class='search'>
    <input v-model="keyworld" class="search-input" type="text" placeholder="输入城市名或拼音"/>
    <div class="search-content" v-show="keyworld" >
        <ul>
            <li class="search-item border-bottom" v-for="item of list" :key="item.id" @click="handleCityClick(item.name)">{{item.name}}</li>
            <li class="search-item border-bottom" v-show="hasNOdata">没有找到匹配数据</li>
        </ul>

    </div>    
</div> 
</div>
</template>

<script>
//这里可以导入其他文件（比如：组件，工具js，第三方插件js，json文件，图片文件等等）
//例如：import 《组件名称》 from '《组件路径》';
//import Swiper from "swiper";

export default {
name:'CitySearch',
props: {
    cities: Object
},
//import引入的组件需要注入到对象中才能使用
components: {},
data() {
//这里存放数据
return {
    keyworld: '',
    list: [],
    timer: null

};
},
//监听属性 类似于data概念
computed: {
    hasNOdata () {
        return !this.list.length
         
             
         
    }
},
//监控data中的数据变化
watch: {
    keyworld () {
        if(this.timer){
            clearTimeout(this.timer)
        }
        if(!this.keyworld){
            this.list=[]
            return
        }
        this.timer = setTimeout(() => {
            const result = []
            for (let i in this.cities) { 
                this.cities[i].forEach((value) => {
                    if (value.spell.indexOf(this.keyworld) > -1 || value.name.indexOf(this.keyworld) > -1){
                        result.push(value)
                    }    
                })
            }
            this.list = result


        },100)
    }
},
//方法集合 专门存放方法比如点击事件
methods: {
    handleCityClick (city) {
        this.$store.commit('changeCity',city)
        this.$router.push('/')
        
    }
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
<style lang="stylus" scoped>
.search
   height .72rem
   padding 0 .2rem
   background #00bcd4
   .search-input
      box-sizing: border-box
      width: 100%
      height: .62rem
      padding: 0 .1rem
      text-align: center
      border-radius: .06rem
      color: #666
.search-content
   position: absolute 
   z-index: 1
   over-flow: hidden
   top: 1.58rem
   left: 0
   right: 0
   bottom: 0
   background: #eeeeee
   .search-item
      line-height: .62rem
      padding-left: .2rem
      color: #666
      background: #ffffff
    
</style>