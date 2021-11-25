<template>
    <div class="min-h-screen bg-white bg-no-repeat bg-cover" :style="{'background-image': `url(${require('../assets/game.jpg')})`}">
        <div class="flex">
        </div>
        <div class="flex justify-center mt-16"  :style="{'position': 'absolute','z-index': '2','width': '100%','padding': '50px'}">
            <img src="../assets/Pause.png" alt="Pause" width ="400" height="400">
        </div>

            <div class="flex justify-center " :style="{'position': 'absolute','z-index': '3','width': '100%','margin-top': '250px'}">
                <button @click="play" class="button font-bold px-6 text-xl" v-text="'P L A Y '"/>
            </div>
            <div class="flex justify-center" :style="{'position': 'absolute','z-index': '3','width': '100%','margin-top': '340px'}">
                <button @click="play" class="button font-bold px-6 text-xl" v-text="'E X I T '"/>
            </div>
    </div>
</template>

<script>
export default {
    name: 'Pause',
    emits: ['moving']
}
</script>


