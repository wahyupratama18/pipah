<template>
    <div class="min-h-screen bg-white bg-no-repeat bg-cover" :style="{'background-image': `url(${require('../assets/game.jpg')})`}">
        <div class="text-green-500" v-text="'Test Play'" />
    </div>
</template>

<script>

export default {
    name: 'Play',
    emits: ['moving']
}
</script>
