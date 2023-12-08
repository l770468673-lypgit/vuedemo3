<template>
    <div class="leftweb">
        <!-- @child2Parent 自定义方法 -->
        <p> 父布局接收----{{ receiveChildDate }}</p>
        <!-- // chaundi="lclass" :names="names" 父对子布局传递数据 -->
        <!-- @child2Parent="c2pdate" @child2ParentSearch="toParentSearch"  父监听子传递的方法 -->
        <LeftChildVue :chaundi="lclass" :names="names" @child2Parent="c2pdate" @child2ParentSearch="toParentSearch" />
        <!-- <LeftChildVue chaundi="父布局传递的页面数据" /> -->
    </div>
</template>
<style scoped>
.leftweb {
    text-align: center;
    float: left;
    width: 70%;
    height: 500px;
    border: 2px solid red;
    box-sizing: border-box;
}
</style>
<script>
import LeftChildVue from './LeftChild.vue'

export default {
    name: 'LeftWebs',
    components: {
        LeftChildVue
    },
    data() {
        return {
            lclass: "这是通过v-bind父布局传递的数据",
            names: ["赵", "赵1", "赵2", "赵3"],
            receiveChildDate: ""
        }
    },
    methods: {
        // 子传父
        c2pdate(msg) {
            this.receiveChildDate = msg;
            console.log(msg);
        },
        // 子传父
        toParentSearch(msga){
            this.receiveChildDate = msga;
 
        }
    }

}

</script>