<template>
  <div id="app">
    <tabs ref="tabs" @indexChanged="indexChangedHandler">
      <tab name="Корпоративные ценности" :selected="true">
        <h1>Корпоративные ценности</h1>
      </tab>
      <tab name="Корпоративные компетенции">
        <h1>Корпоративные компетенции</h1>
      </tab>
      <tab name="Профессиональные навыки">
        <h1>Профессиональные навыки</h1>
      </tab>
      <tab name="Предварительное решение об итоговой оценке">
        <h1>Предварительное решение об итоговой оценке</h1>
      </tab>
      <tab name="Завершение оценки">
        <h1>Завершение оценки</h1>
      </tab>
    </tabs>
    <button v-if="prevIsVisible" @click="prev()">Prev</button>
    <button @click="next()">Next</button>
  </div>
</template>

<script>
import Tabs from './components/Tabs.vue'
import Tab from "./components/Tab";

export default {
  name: 'App',
  components: {
    Tabs,
    Tab
  },
  data(){
    return {
      selectedIndex: 0,
    }
  },
  computed: {
    prevIsVisible(){
      return !!this.selectedIndex
    }
  },
  methods: {
    prev(){
      this.$refs.tabs.prev()
    },
    next(){
      this.$refs.tabs.next()
    },
    indexChangedHandler(index){
      this.selectedIndex = index
    }
  }
}
</script>

<style>
  ul{
    display: flex;
    justify-content: space-around;
  }
</style>
