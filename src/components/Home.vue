<template>
    <div class="min-h-screen bg-white bg-no-repeat bg-cover" :style="{'background-image': `url(${require('../assets/home.png')})`}">
        <div class="grid grid-cols-1">
            <!-- Buttons -->
            <div class="flex justify-end mt-6 mr-6">
                <button class="button h-12 w-12 rounded-full mx-4">
                    <i class="mdi mdi-music mdi-36px" />
                </button>
                <button @click="viewScore" class="button h-12 w-12 rounded-full mx-4">
                    <i class="mdi mdi-scoreboard mdi-36px" />
                </button>
            </div>

            <div class="flex justify-center font-bold mt-6">
                <div class="text-green-500 text-3xl text-center w-72">
                    <h1 v-text="'PIPAH'" />
                    <hr>
                    <h3 v-text="'Pilah Sampah'" />
                </div>

            </div>

            <div class="flex justify-center mt-16">
                <button @click="play" class="button font-bold px-6" v-text="'M U L A I'"/>
            </div>
        </div>
    </div>
</template>

<script>

export default {
    name: 'Home',
    emits: ['moving'],
    methods: {
        play(){
            this.$emit('moving', 2)
        },
        viewScore(){
            this.$emit('moving', 3)
        }
    }
}
</script>
