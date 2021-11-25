<template>
    <div class="min-h-screen bg-white bg-no-repeat bg-cover" :style="{'background-image': `url(${require('../assets/game.jpg')})`}">
        <div class="flex">
            <button @click="viewScore" class="button h-12 w-12 rounded-full ml-6 mt-6">
                <i class="mdi mdi-pause mdi-36px" />
            </button>
        </div>

        <div class="flex mt-64 ml-12">
            <img src="../assets/anorganik.png" alt="Tempat Sampah" class="h-48">
            <img src="../assets/organik.png" alt="Tempat Sampah" class="h-48">
        </div>
    </div>
</template>

<script>
export default {
    name: 'Play',
    emits: ['moving']
}
</script>
