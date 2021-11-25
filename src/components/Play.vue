<template>
    <div class="min-h-screen bg-white bg-no-repeat bg-cover" :style="{'background-image': `url(${require('../assets/game.jpg')})`}">
        <div class="flex">
            <!-- Implementasi modal -->
            <button @click="showPause" class="button h-12 w-12 rounded-full ml-6 mt-6">
                <i class="mdi mdi-stop mdi-36px" />
            </button>
        </div>

        <div class="flex mt-64 ml-12">
            <img src="../assets/anorganik.png" alt="Tempat Sampah" class="h-48">
            <img src="../assets/organik.png" alt="Tempat Sampah" class="h-48">
        </div>

        <!-- Modals -->
        <modal :show="pause" :closeable="true" @close="closePause">test</modal>
    </div>
</template>

<script>
import Modal from './Modal.vue'

export default {
    name: 'Play',
    emits: ['moving'],
    components: {
        Modal
    },
    data(){
        return {
            scoring: {score: 0, name: ''},
            pause: false,
            playable: true
        }
    },
    methods: {
        setScore(){
            const exist = localStorage.getItem('scores');
            let data = exist ? JSON.parse(exist) : []

            data = [...data, this.scoring]

            localStorage.setItem('scores', JSON.stringify(data))

            this.$emit('moving', 3)
        },
        showPause(){
            this.pause = true
            console.log(this.pause)
        },
        closePause(){
            console.log('close')
            this.pause = false
        }
    }
}
</script>
