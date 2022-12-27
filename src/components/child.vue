<template>
     <slot name="btn"></slot>
  <p>child {{ sum }}</p>
  <button @click="hdClick">按钮</button>
 
  <slot name="link" title="test" :myNum="num"></slot>

</template>

<script lang="ts" setup>
import { ref } from "vue";
const props =  defineProps({
    sum: {
    type: Number,
    default: 1
  }
})
const emit = defineEmits<{
  (event: "update:sum",n:number): void;
}>();
let n=props.sum
const hdClick = () => {
    emit('update:sum',n++)
};


let num=ref(30)
</script>

<style lang="less" scope></style>
