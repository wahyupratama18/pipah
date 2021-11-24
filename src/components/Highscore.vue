<template>
    <div class="min-h-screen bg-white bg-no-repeat bg-cover" :style="{'background-image': `url(${require('../assets/home.png')})`}">
        <h2 v-text="'Highscore'" />
    </div>
</template>

<script>

export default {
    name: 'Highscore',
    emits: ['moving']
}
</script>
