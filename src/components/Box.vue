<template>
    <div class="box has-text-weight-bold" :style="style">
        <slot></slot>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
    name: 'Box',
    data () {
        return {
            style: {
                backgroundColor: '#FAF0CA',
                'margin-inline': '1rem',
                color: '#000'
            }
        }
    }
})
</script>
