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
    <button :disabled="clicldiscble" :class="lclass" style="display: block" @click="addNum()">
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
    <div v-if="flag" v-big="n" v-fbind="n">你可以看见我if</div>
    <div v-else>你可以看见我</div>
    <div v-show="flag">你可以看见我show</div>
    <div>
      ----------------列表渲染---------getclickHndler
      事件传递参数------------------------
    </div>
    <div>
      <p v-for="item in names" :key="item.id" @click="getclickHndler(item)">
        {{ item }}
      </p>
    </div>
    <div>-------------------------------------------------</div>
    <p> <input type="text" placeholder="请输入查询数据" v-model="keyWord"></p>
    <div v-for="item of fileloadjso" :key="item.id">
      <p>{{ item.alarmContent }}</p>

    </div>
    <div>-----------------事件修饰符号--------------------------------</div>
    <div>
      1.prevent:阻止默认事件(常用) 2. stop:阻止事件冒泡(常用) 3.
      once:事件只触发一次(常用) 4.captrue:使用事件的捕捉模式(不常用)
      5.self:只有event.target是当前操作的元素时才触发事件(不常用)
      6.passive:事件的默行为立即执行，无需等待事件回调执行完毕(不常用)
      v-once v-click
      v-pre ： 让程序跳过代码所在节点的编译过程， 不让程序调用 ，不会解析
      v-big  /
      Vue.directive（方法，指令） 设置为 全局自定义函数
    </div>
    <div>-----------------监测数组变化--------------------------------</div>
    <div>
      监测数组变化，如 push()、pop()、shift()、unshift()、splice()、sort() 和
    </div>
    <div>
      -----------------计算属性-
      将判断放在函数中、复杂逻辑还是放在计算属性中，不在函数中，
      会节约加载次数-------------------------------
    </div>
    <div>
      <P>"names len >0" {{ lenthIsNotNull }} </P>
      <P>"names len 0" {{ lenthIsNotNulls() }} </P>
    </div>
    <div>-----------------响应式数据侦听--用 watch ------------------------------</div>
    <p>{{ msg }}</p>
    <button @click="changedate()">数据侦听</button>
    <div>-----------------表单输入绑定- -----v-model -----</div>
    v-model.lazy 懒惰、、.number数字、、trim 去空格 , 在表单中 用户输入的同时，获取输入的数据
    <form>
      <input type="text" v-model="changemsg">
      <P> {{ changemsg }} </P>
    </form>
    <input type="checkbox" id="checkbox" v-model.number="checked">
    <button>{{ checked }}</button>
    <div>-----------------模板引用 获取 dom 通过$refs 获取 -----</div>
    在Vue中很少会用到直接操作DOM， 很消耗资源。但不可避免有时候需要用到，这时我们可以通过ref和$refs这两个来实现
    <div>---------组件组成 --单文件组件SFC.---</div>
    <div>---------注册方式为 全局注册和局部注册.---</div>
    <div>---------传递数据方式 props. 父传子数据只读，不可修改---</div>
    <div>---组件事件------传递数据方式 子传父 通过 this.$emit("方法名","数据") 传递， 父布局通过 @方法名=“自定义方法” 接收---</div>
    <div>1 插槽slot， 2 具名插槽， 3 插槽传递数据 4 具名插槽传递数据 v-slot:default==>简写#default</div>
    <div>--------- is的用法--传递一个组件.-components =-是 承载组建的标签--</div>

    <div>--------- keep-alive 组件保持存活---</div>
    <div>--------- 异步组件 ---</div>
    <div>--provide(){},传递数据，从一级页面传递到三级甚至四级页面， 三级四级页面通过 inject 接受数据</div>
    <button @click="numnames.c++"> names 内容变化</button>
    <button> names </button>



  </div>
</template> 
<script >


export default {

// 自定义方法 v-xxx 指令
  deactivated: {
    big(element,bind) { 
      console.log(bind.value); 
    },
 
    
  } ,
    //计算属性
  computed: {
    // 计算属性下面是需要一个方法
    lenthIsNotNull() {
      return this.names.length > 0 ? 'YES' : 'NO'
    },
    lenthIsNotNull3: {
      get() {
        return this.names.length > 0 ? 'YES' : 'NO'
      },
    },
    //用计算属性实现数据搜索
    fileloadjso() {
      return this.loadjson.filter((p) => {
        console.log("用计算属性实现数据搜索  p==" + p.alarmContent);
        console.log("用计算属性实现数据搜索  this.keyWord==" + this.keyWord);
        return p.alarmContent.includes(this.keyWord);
      })
    }
  },

  methods: {
    changedate() {
      this.msg = "changeNAME"
    },
    addNum() {
      // Your method logic goes here
      this.numcount++
    },
    getclickHndler(names) {
      console.log(names);
    },
    lenthIsNotNulls() {
      return this.names.length > 0 ? 'NO' : 'YES'
    },
  },

  // 监视
  watch: {//减写
    msg(newValu, oldValu) {
      console.log(newValu, oldValu);
    },
    numnames: {    //    不减写
      immediate: true,// 初始化先调用一次 
      deep: true, // 穿透  深度检测， 可以检测到 numnames  下的所有的数据发生变化
      handler() {
        console.log(this.numnames.c);

      }

    },

    //#region 
    //  通过watch 实现输入框搜索数据  数据过滤
    // keyWord: {
    //   immediate: true,
    //   handler(newValu) {
    //     console.log("newValu==" + newValu);
    //     // filter  过滤方法 
    //     this.fileloadjso = this.loadjson.filter((d) => {
    //       console.log("d==" +d.alarmContent.indexOf(newValu));
    //       return d.alarmContent.indexOf(newValu) !== -1
    //     })
    //   }
    // },
    //#endregion
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
      n:"test big",
      names: ["赵", "赵1", "赵2", "赵3"],
      numnames: { a: 1, b: 2, c: 3 },
      numcount: 10,
      keyWord: "",
      // fileloadjso: [],
      loadjson: [{
        "alarmContent": "救命",
      }, {
        "alarmContent": "着火",
      }, {
        "alarmContent": "110",
      }, {
        "alarmContent": "210",
      }, {
        "alarmContent": "310",
      }, {
        "alarmContent": "410",
      }
      ],
      changemsg: "",
      checked: true,
    };
  },
};
</script>
<!-- //scoped  让当前样式 只在当前组件中生效 -->
<style scoped >
.namclass {
  color: red;
  font-size: 30px;
}
</style>
