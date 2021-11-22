<template>
  <div>
    <Home v-if="menus == 1" />
    <Play v-if="menus == 2" />
    <Highscore v-if="menus == 3" />
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
  }
}
</script>