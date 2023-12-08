 

<template>
  <div>
    <HelloWorld />
    <TopWeb />
    <RightWebs />
    <LeftWebs />
    <!-- <RightChiled/> -->


  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import TopWeb from './components/TopWeb.vue'
import LeftWebs from './components/LeftWebs.vue';
import RightWebs from './components/RightWebs.vue';


export default {
  name: 'App',
  components: {
    TopWeb,
    HelloWorld,
    LeftWebs,
    RightWebs,
    // RightChiled
  },

}
</script>

 
