<template>
    <div class="min-h-screen bg-white bg-no-repeat bg-cover" :style="{'background-image': `url(${require('../assets/home.png')})`}">
        <div class="flex ml-6">
            <button @click="home" class="button h-12 w-12 rounded-full mx-4 mt-6">
                <i class="mdi mdi-chevron-left mdi-36px" />
            </button>
        </div>
        <div class="flex justify-center font-bold mt-6">
            <h2 class="text-green-500 text-4xl text-center w-72" v-text="'Skor Terbaik'" />
        </div>

        <div class="flex font-bold mt-6 md:justify-center ml-6 md:ml-0">
            <ol class="text-left list-decimal">
                <li class="text-lg text-green-500" v-for="(score, i) in scores" :key="i" v-text="`(${score.score}) - ${score.name}`" />
            </ol>
        </div>
    </div>
</template>

<script>

export default {
    name: 'Highscore',
    emits: ['moving'],
    data(){
        return {
            scores: [
                {name: 'Testing', score: 100}
            ]
        }
    },
    methods: {
        home(){
            this.$emit('moving', 1)
        },
    }
}
</script>
