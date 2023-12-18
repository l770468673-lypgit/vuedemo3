<template>
    <div class="leftchile" > 

        <p>{{ chaundi }}</p>
        <p v-for="item in names" :key="item">{{item}}</p>
        <button @click="ChildCallParenrt">子传父</button>
        搜索 <input type="text" v-model="startsearch" >
    </div>
   
</template>

<script>
export default{
    methods:{
        ChildCallParenrt(){ 
            //$emit  子传父
            this.$emit("child2Parent",this.msg);
        },

    },
    watch:{ // 实时监听变化
        startsearch(newValus){
            this.$emit("child2ParentSearch",newValus);
        },
         
    },
    data(){
        return{
            msg:"传递的数据", 
            startsearch:""
        }
    },

    // 父传子 数据接收 返给 页面标签 
    props:["chaundi","names"]
}
</script>

<style scoped>
.leftchile{
    width: 80%;
    height: auto;
    text-align: center;

}
</style>