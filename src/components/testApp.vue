<template>
    <!-- <p>{{ num }}</p>
    <button @click="num++">按钮</button> -->
    <p>{{ objRef.num }}</p>
    <button @click="objRef.num++" >按钮</button>
    <son :a="a" @fn="chanA"></son>

    <input type="checkbox" v-model="checkAll">全选/全不选
    <ul>
        <li v-for="(item ,index) in list" :key="index">
        <input type="checkbox" v-model="checkList[index]">{{ item }}
        </li>
    </ul>


    <child v-model:sum="sum">
    <template #link="scope">
        <a href="#">a标签{{ scope.title }}+{{scope.myNum}}</a>
            
    </template>
    <template v-slot:btn>
        <button>T</button>
        
    </template>
    
    </child>
    <myTable :arr="state.arr">
      <template #btn="scope">
        <button @click="hdClick(scope.index)">编辑</button>
        <button>删除</button>
      </template>
    </myTable>



</template>

<script lang='ts' setup>
import { computed, reactive, ref, toRefs, watch, watchEffect } from 'vue'
import son from "./sun.vue"
import child from './child.vue';
import myTable from './myTable.vue';
import{DataType} from "../../types/check"
    // let num =ref(20);
    //   watch(num,(newValue,oldValue)=>{
    //     console.log(newValue,oldValue)
    //   })
    let a=ref(10)
    let obj={
        num:30
    }
    let objRef=reactive(obj);
    // let {num}= toRefs(objRef)
    // watch(num,(newValue,oldValue)=>{
    //     console.log(newValue,oldValue)
    //   })
    //   watch(()=>objRef.num,(newValue,oldValue)=>{
    //     console.log(newValue,oldValue)
    //   })

        //立即监听
      watchEffect(() => {
        // 写在这里的数据变化都会触发
        console.log( objRef.num);
        
      });
      const chanA=()=>{
        a.value++
      }


      let data=reactive<DataType>({
        list:[10,20,30,40],
        checkList:[]
 
      })
      data.checkList=data.list.map(()=>false)
      let {list,checkList} =toRefs(data)
      let checkAll=computed({
        get(){
            return !data.checkList.includes(false)
        },
        set(newValue:boolean){
            data.checkList= data.checkList.map(()=>newValue)
        }
      })


      let sum=ref(20)



      let state=reactive({
        arr:[{name:"小明",age:"18"},{name:"小都",age:"28"},]
      })
      const hdClick=(index:  number)=>{
        console.log(state.arr[index])
      }


      console.log(globalVar,globalObj)
      fn("123")
</script>

<style lang="less" scope>
    
</style>            