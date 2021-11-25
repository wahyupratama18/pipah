<template>
  <div>
    <WelcomeHome v-if="menus == 1" @moving="moved" />
    <PlayGame v-if="menus == 2" @moving="moved" />
    <Highscores v-if="menus == 3" @moving="moved" />
  </div>
</template>

<script>
import Highscores from './components/Highscores.vue'
import WelcomeHome from './components/WelcomeHome.vue'
import PlayGame from './components/PlayGame.vue'

export default {
  name: 'BaseGames',
  components: {
    Highscores,
    WelcomeHome,
    PlayGame
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