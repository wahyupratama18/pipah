<template>
    <div class="min-h-screen bg-white bg-no-repeat bg-cover" :style="{'background-image': `url(${require('../assets/backgrounds/game.jpg')})`}">
        <div class="flex">
            <!-- Implementasi modal -->
            <button @click="showPauseModal" class="button h-12 w-12 rounded-full ml-6 mt-6">
                <i class="mdi mdi-stop mdi-36px" />
            </button>

            <div class="mx-auto flex items-center mt-6">
                <div class="button h-12 w-12 rounded-full">
                    <i class="mdi mdi-scoreboard mdi-36px" />
                </div>
                <h3 class="font-bold ml-2 text-xl text-yellow-500" v-text="scoring.score" />
                    
            </div>
        </div>

        <!-- Dumpster -->
        <div class="flex mt-64 ml-12">
            <img src="../assets/icons/anorganik.png" alt="Tempat Sampah" class="h-48" @drop="onDrop($event, transfer.anorganik)" @dragover.prevent @dragenter.prevent>
            <img src="../assets/icons/organik.png" alt="Tempat Sampah" class="h-48" @drop="onDrop($event, transfer.organik)" @dragover.prevent @dragenter.prevent>
        </div>

        <!-- Game -->
        <div>
            <img src="../assets/icons/apel.png" alt="Sampah" class="h-24 bottom-10 left-5 fixed" draggable @dragstart="dragging($event, transfer.organik)">
            <img src="../assets/icons/kertas.png" alt="Sampah" class="h-24 bottom-8 left-40 fixed" draggable @dragstart="dragging($event, transfer.anorganik)">
            <img src="../assets/icons/pisang.png" alt="Sampah" class="h-24 bottom-20 right-5 fixed" draggable @dragstart="dragging($event, transfer.organik)">
            <img src="../assets/icons/plastik.png" alt="Sampah" class="h-24 bottom-30 right-10 fixed" draggable @dragstart="dragging($event, transfer.anorganik)">
            <img src="../assets/icons/soda_merah.png" alt="Sampah" class="h-24 bottom-10 right-5 fixed" draggable @dragstart="dragging($event, transfer.anorganik)">
            <img src="../assets/icons/soda_hijau.png" alt="Sampah" class="h-24 bottom-30 left-40 fixed" draggable @dragstart="dragging($event, transfer.anorganik)">
        </div>

        <!-- Modals -->
        <Modal :show="pause.modal" :closeable="pause.closeable" @close="closeModal">
            <div class="bg-gradient-to-r from-yellow-300 to-yellow-400 p-8">
                <h2>Apakah yakin ingin mengakhiri permainan?</h2>

                <div class="flex my-6 justify-between">
                    <button class="invert-button px-6 py-2" @click="closeModal">Tidak</button>
                    <button class="button px-6 py-2" @click="showScoreModal">Ya</button>
                </div>
            </div>
        </Modal>
        <Modal :show="scored.modal" :closeable="scored.closeable" @close="closeModal">
            <div class="bg-gradient-to-r from-yellow-300 to-yellow-400 p-8">
                <h2>Yahh kurang beruntung. Coba lagi selanjutnya ya!</h2>

                <input type="text" class="input-style mt-4" placeholder="Nama Kamu" v-model="scoring.name">

                <div class="flex justify-end mt-4">
                    <button class="button" @click="setScore">Simpan</button>
                </div>
            </div>
        </Modal>
    </div>
</template>

<script>
import Modal from './Modal.vue'

export default {
    name: 'PlayGame',
    emits: ['moving'],
    components: {
        Modal
    },
    data(){
        return {
            scoring: {score: 0, name: ''},
            pause: {
                modal: false,
                closeable: true
            },
            playable: true,
            scored: {
                modal: false,
                closeable: false
            },
            transfer: {
                anorganik: 1,
                organik: 2
            },
            ifTrue: 5
        }
    },
    methods: {
        setScore(){
            const exist = localStorage.getItem('scores');
            let data = exist ? JSON.parse(exist) : []

            data = [...data, this.scoring]

            localStorage.setItem('scores', JSON.stringify(data))

            this.closeModal()
            this.$emit('moving', 3)
        },
        showPauseModal(){
            this.pause.modal = true
        },
        closeModal(){
            this.pause.modal = this.scored.modal = false
        },
        showScoredModal(){
            this.playable = false
            this.scored.modal = true
        },
        dragging(e, transfer) {
            if (this.playable) {
                e.dataTransfer.dropEffect = 'move'
                e.dataTransfer.effectAllowed = 'move'
                e.dataTransfer.setData('type', transfer)
            }
        },
        onDrop (e, accepted) {
            if (e.dataTransfer.getData('type') != accepted) {
                return this.showScoredModal()
            }

            this.scoring.score += this.ifTrue
        }
    }
}
</script>
