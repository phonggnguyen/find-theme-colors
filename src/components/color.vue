<script lang="ts" setup>
import { ref } from 'vue'
import { useClipboard } from '@vueuse/core'

defineProps({
    color: String,
    keyc: String
})

const source = ref('')
const { text, copy, copied, isSupported } = useClipboard({ source })
    
</script>

<template>
    <div>
        <div ref="source" class="color" :style="{'background-color': color}" @click='copy()' />
        <p>
            {{ keyc }}
        </p>
        <p style="font-size: 12px">
            {{ color }}
        </p>

        <span v-if="copied">Copied!</span>
    </div>
</template>