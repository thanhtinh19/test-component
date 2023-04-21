<template>
  <div id="app">
    <ComponentVueParent/>
    <!-- <ComponentComputedVue/> -->
    <ComponentWatchVue/>
  </div>
</template>

<script>
 import ComponentWatchVue from './components/ComponentWatch.vue'
// import ComponentComputedVue from './components/ComponentComputed.vue'

import ComponentVueParent from './components/ComponentParent.vue'

export default {
  name: 'App',
  components: {
    ComponentVueParent,
    // ComponentComputedVue,
    ComponentWatchVue
  }
}
</script>

<style>
  #app{
    margin: 0 auto;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
</style>
