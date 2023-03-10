<template>
    <div class="is-flex is-align-items-center is-justify-content-space-between">
                    <CronometroTempo :tempo="tempo" />
                    <button class="button" @click="iniciarTarefa" :disabled="cronometroRodando">
                        <span class="icon">
                            <i class="fas fa-play"></i>
                        </span>
                        <span>play</span>
                    </button>
                    <button class="button" @click="pararTarefa" :disabled="!cronometroRodando">
                        <span class="icon">
                            <i class="fas fa-stop"></i>
                        </span>
                        <span>stop</span>
                    </button>   
                </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import Cronometro from './Cronometro.vue'

export default defineComponent({
    name: 'TemporizadorTarefa',
    emits: ['temporizadorFinalizado'],
    components: {
        CronometroTempo: Cronometro
    },
    data () {
        return {
            tarefa: '',
            tempo: 0,
            cronometro: 0,
            cronometroRodando: false
        }
    },
    methods: {
        iniciarTarefa() {
            //começar a contar o tempo
            this.cronometroRodando = true
            this.cronometro = setInterval(() => {
                this.tempo+=1
            }, 1000)
        },
        pararTarefa() {
            //parar de contar o tempo
            this.cronometroRodando = false
            clearInterval(this.cronometro)
            this.$emit('temporizadorFinalizado', this.tempo)
            this.tempo = 0
        }
    },
})
</script>