<template>
    <table>
        <tr>
            <th>姓名</th>
            <th>年龄</th>
            <th>操作</th>
        </tr>
        <tr v-for="(item, index) in arr2" :key="index">
            <td>{{ item.name }}</td>
            <td>{{ item.age }}</td>

            <td >
                <slot name="btn" :index="index"></slot>
            </td>

        </tr>
    </table>
</template>

<script lang='ts' setup>
import { defineProps } from 'vue'
import {UserType} from "#/table"
let props=defineProps({
    arr: {
        type: Array,

        default: []
    }

})  

let arr2=props.arr as UserType[]
</script>

<style scope>
table {
    border-collapse: collapse;
}

table,
th,
td ,button{
    border: 1px solid #000;
}
button{padding: 5px;}
th,td{padding: 10px;}
</style>