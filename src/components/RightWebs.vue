<template>
    <div class="nrightweb1">
      <keep-alive>
      <components :is="changeDate"></components>
    </keep-alive>
        <button @click="changeWeb">改变组件</button> 

    </div>
</template>

<script>

import RightChiled from './RightChiled.vue';
import RightChiled2 from './RightChiled2.vue';
// const RightChiled2 =defineAsyncComponent(()=>
//     import('./RightChiled2.vue') 
// );
 
export default {
    name: 'RightWebs',
    components: {
        RightChiled,
        RightChiled2

    },
    data() {
        return {
            changeDate: "RightChiled",
        }
    },
    methods: {
        changeWeb() {
            this.changeDate = this.changeDate == "RightChiled" ? "RightChiled2" : "RightChiled"
        },
    }

}
</script>

<style scoped>
.nrightweb1 {
    text-align: center;
    float: right;
    width: 30%;
    height: 600px;
    border: 2px solid red;
    border-block-color: red;
    text-align: center;
    box-sizing: border-box;
}
</style>