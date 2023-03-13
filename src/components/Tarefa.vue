<template>
    <div class="box has-text-weight-bold">
        <div class="columns">
            <div class="column is-7">
                Descrição da Tarefa
            </div>
            <div class="column">
                <CronometroTempo :tempo="15" />
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import CronometroTempo from './Cronometro.vue'

export default defineComponent({
    name: 'TarefaemExecução',
    components: {
        CronometroTempo: () => import('./Cronometro.vue')
    }
})
</script>
