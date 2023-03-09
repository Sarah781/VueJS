<template>
    <div class="box">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="Formulário para criação de uma nova tarefa">

                <input type="text" class="input" placeholder="Qual tarefa você deseja iniciar?" />
            </div>
            <div class="column">
                <div class="is-flex is-align-items-center is-justify-content-space-between">
                    <CronometroTempo />
                    <button class="button" @click="iniciarTarefa">
                        <span class="icon">
                            <i class="fas fa-play"></i>
                        </span>
                        <span>play</span>
                    </button>
                    <button class="button" @click="pararTarefa">
                        <span class="icon">
                            <i class="fas fa-stop"></i>
                        </span>
                        <span>stop</span>
                    </button>   
                </div>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import CronometroTempo from './Cronometro.vue'

export default defineComponent({
    name: 'FormulárioUsuario',
    components: {
        CronometroTempo
    },
    data () {
        return {
            tarefa: '',
            tempo: 0,
            cronometro: 0,
        }
    },
    methods: {
        iniciarTarefa() {
            //começar a contar o tempo
            this.cronometro = setInterval(() => {
                this.tempo+=1
            }, 1000)
        },
        pararTarefa() {
            //parar de contar o tempo
            clearInterval(this.cronometro)
        }
    },
})
</script>