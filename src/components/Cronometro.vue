<template>
    <section>
        <strong>
            {{ tempoFormatado }}
        </strong>
    </section>
</template>

<script lang="ts">

 import { defineComponent } from 'vue'

export default defineComponent({
    name: 'CronometroTempo',
    props: {
        tempo: {
            type: Number,
            default: 0
        }
    },
    computed: {
        tempoFormatado() : string {
            return new Date(this.tempo * 1000).toISOString().substr(11, 8)
        }
    }
})
</script>