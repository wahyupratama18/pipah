<template>
  <div>
    <Home v-if="menus == 1" @moving="moved" />
    <Play v-if="menus == 2" @moving="moved" />
    <Highscore v-if="menus == 3" @moving="moved" />
  </div>
</template>

<script>
import Highscore from './components/Highscore.vue'
import Home from './components/Home.vue'
import Play from './components/Play.vue'

export default {
  name: 'Game',
  components: {
    Highscore,
    Home,
    Play
  },
  data(){
    return {
      menus: 1
    }
  },
  methods: {
    moved(menus){
      this.menus = menus
    }
  }
}
</script>