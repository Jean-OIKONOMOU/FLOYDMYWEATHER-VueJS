<template>
  <div id="app">
    <axios/>
  </div>
</template>

<script>
//import todo from './components/todolist.vue'
import {TweenMax, CSSPlugin, ScrollToPlugin, Draggable, Elastic} from "gsap/all";
import axios from './components/axiostest.vue'

export default {
  name: 'app',
  components: {
  axios,
},
data() {
  return {
    //titlee: "ceci est un test"
  }
}
}
</script>
