<template>
    <div class="tab-bar-item" @click="itemClick">
        <div v-if="!active"><slot name="item-icon" ></slot></div>
        <div v-else><slot name="item-active-icon" ></slot></div>
        <div :style="activeStyle"><slot name="item-text" ></slot></div>  
    </div>
</template>

<script>
export default {
    props: {
        path:String,
        activeColor:{
            type:String,
            default:'#F3D1AC'
        }
    },
    data() {
        return {
            tabBarMenu:[
                {itemClass:'glyphicon-home',
                itemTitle:'首页',},
                {itemClass:'glyphicon-th-list',
                itemTitle:'分类',}
            ],
            
            
        };
    },
    computed: {
        active(){
            return this.$route.path.indexOf(this.path) !== -1
        },
        activeStyle(){
            return this.active ? {color:this.activeColor} : {}
        }
    },
    created() {

    },
    mounted() {

    },
    watch: {

    },
    methods: {
        itemClick(){
            this.$router.push(this.path)
        }
    },
    components: {
        
    },
};
</script>

<style>
    .tab-bar-item{
      flex: 1;
      text-align: center;
      height:49px;
      font-weight: 300;
      cursor: pointer;
    }
    
    
</style>
