<template>
    <p>{{ a }}</p>
    <button @click="hdClick">按</button>
</template>

<script lang='ts' setup>
import {defineProps ,defineEmits} from 'vue'

 defineProps({
    a: {
        type: Number,
        default:12
    }
})

 const emit = defineEmits<{
  (event: 'fn'): void
//   (event: 'update', id: number): void
}>()
 const hdClick=()=>{
    emit("fn")
 }
        
</script>

<style lang="less" scope>
    
</style>