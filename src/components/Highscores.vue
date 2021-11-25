<template>
    <div class="min-h-screen bg-white bg-no-repeat bg-cover" :style="{'background-image': `url(${require('../assets/backgrounds/home.png')})`}">
        <div class="flex ml-6">
            <button @click="home" class="button h-12 w-12 rounded-full mx-4 mt-6">
                <i class="mdi mdi-chevron-left mdi-36px" />
            </button>
        </div>
        <div class="flex justify-center font-bold mt-6">
            <h2 class="text-green-500 text-4xl text-center w-72" v-text="'Skor Terbaik'" />
        </div>

        <div class="flex font-bold mt-6 md:justify-center ml-6 md:ml-0">
            <ol class="text-left list-decimal" v-if="scores.length > 0">
                <li class="text-lg text-green-500" v-for="(score, i) in scores" :key="i" v-text="`(${score.score}) - ${score.name}`" />
            </ol>
            <h4 v-else v-text="'Data skor tidak tersedia, yuk main'" class="text-lg text-green-500" />
        </div>
    </div>
</template>

<script>

export default {
    name: 'Highscores',
    emits: ['moving'],
    data(){
        return {
            scores: [
                {name: 'Testing', score: 100},
                {name: 'Testing', score: 150},
                {name: 'Testing', score: 75}, 
            ]
        }
    },
    methods: {
        home(){
            this.$emit('moving', 1)
        },
    },
    mounted() {
        if (localStorage.getItem('scores')) {
            this.scores = JSON.parse(localStorage.getItem('scores'))
            .sort((a,b) => b.score - a.score).slice(0, 5)
        }
    }
}
</script>
