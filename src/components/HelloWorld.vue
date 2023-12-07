<template>
  <div>
    <!-- 内容绑定 -->
    <div>-----------------------内容绑定--------------------------</div>
    <h3>{{ msg }}</h3>

    <div>
      ----------------------- 事件处理 、属性绑定
      <!-- v-on:click="addNum()" -->
      --------------------------
    </div>
    <button
      :disabled="clicldiscble"
      :class="lclass"
      style="display: block"
      @click="addNum()"
    >
      数字增加
    </button>
    <p>{{ numcount }}</p>

    <button>
      <p v-html="html"></p>
    </button>

    <!-- 属性绑定  dynamic动态组件 / class控制style样式 / -->
    <!-- v-bind:id 可以简写  :id -->
    <p v-bind:id="appid" v-bind:appname="appname" :class="lclass">name/id</p>
    <!-- 条件渲染 -->
    <div>---------------------条件渲染----------------------------</div>

    <div v-if="flag">你可以看见我if</div>
    <div v-else>你可以看见我</div>
    <div v-show="flag">你可以看见我show</div>
    <div>----------------列表渲染---------getclickHndler 事件传递参数------------------------</div>
    <div>
      <p v-for="item in names" :key="item.id" @click="getclickHndler(item)">
        {{ item }}
      </p>
    </div>
    <div>-------------------------------------------------</div>
    <div v-for="item of loadjson" :key="item.id">
      <p>{{ item.alarmContent }}</p>
      <p>{{ item.alarmTime }}</p>
    </div>
    <div>-----------------事件修饰符号--------------------------------</div>
    <div> </div>
  </div>
</template>

<script>
 
export default {

  methods: {
    addNum() {
      // Your method logic goes here
      this.numcount++
    },
    getclickHndler(names){
      console.log(names);
    }
  },

  data() {
    return {
      msg: "首先根据正则获取组件中所有的{{}}，将{{}}里的值取出在data中取出对应的值，以文本节点的方式放上去。",
      html: "<a href='https://www.baidu.com'>百度一下你就知道</a>",
      appid: "ids",
      appname: "names",
      lclass: "namclass",
      clicldiscble: false,
      flag: true,
      names: ["赵", "赵1", "赵2", "赵3", "赵4", "赵5", "赵6", "赵7"],
      numcount:0,
      loadjson: [{
        "id": "172463497",
        "type": 1,
        "alarmContent": "救命",
        "alarmTime": "2023-11-15 11:42:00",
        "status": 1,
        "collectionId": "1721432012116430956",
        "alarmAddres": "sds/sdsd/sdsda",
      },{
        "id": "172463",
        "type": 1,
        "alarmContent": "着火",
        "alarmTime": "2023-11-15 11:42:00",
        "status": 1,
        "collectionId": "1721432012116430956",
        "alarmAddres": "sds/sdsd/sdsda",
      },{
        "id": "1724633826311786497",
        "type": 1,
        "alarmContent": "110",
        "alarmTime": "2023-11-15 11:42:00",
        "status": 1,
        "collectionId": "1721432012116430956",
        "alarmAddres": "sds/sdsd/sdsda",
      }]
    };
  },
};
</script>
<style >
.namclass {
  color: red;
  font-size: 30px;
}
</style>
