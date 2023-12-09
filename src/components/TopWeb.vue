<template>
    <div class="n2">头部页面

        <MParent />
   
    </div>
</template>

<script>

import MParent from './MParent.vue';
 

export default {

    components: {
        MParent,
 
    },
    // provide:{
    //     message: "爷爷的数据"
    // },
    data(){
        return{
            message: "爷爷的数据"
        }
        
    },
    provide(){
       return{
        message:this.message
       }
    }
}
</script>

<style scoped>
.n2 {
    width: 100%;
    height: 100px;
    border: 2px solid red;
    border-block-color: red;
    text-align: center;
    box-sizing: border-box;
}
</style>