<template>
    <box>
        <div class="columns mr-4 ml-4">
            <div class="column is-7">
                {{ tarefa.description || 'Tarefa sem descrição' }}
            </div>
            <div class="column">
                <cronometro :timeInSeconds="tarefa.timeInSeconds"/>
            </div>
        </div>
    </box>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue'

import Cronometro from './Cronometro.vue'
import Box from './Box.vue'
import ITarefa from '@/interfaces/ITarefa'

export default defineComponent({
    name: "Tarefa",
    components: {
        Cronometro,
        Box
    },
    props: {
        tarefa: {
            type: Object as PropType<ITarefa>,
            required: true
        }
    }
})
</script>
