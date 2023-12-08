<template>
    <div class="righttchile">
        <p>右侧侧子页面1AAAAA</p>
    </div>
</template>

<script>

/*
生命周期
 1 创建期
 2挂载期
 3更新期
 4销毁期


*/
export default {
    data() {
        return {

        }
    },

    beforeCreate() {
        console.log("页面1创建之前");
    },
    create() {
        console.log("页面1创建之后");
    },
    beforeMount() {
        console.log("页面1渲染之前");
    },
    mounted() {
        console.log("页面1渲染之后");
    },
    beforeUpdate() {
        console.log("页面1更新之前");
    }, updated() {
        console.log("页面1更新之后");
    },
    beforeDestroy() {
        console.log("页面1销毁之前");
    },
    destroyed() {
        console.log("页面1销毁之后");
    }





}
</script>

<style scoped>
.righttchile {
    width: 80%;
    height: 20px;
    margin: 0 auto;

}
</style>