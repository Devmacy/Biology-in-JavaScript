<template>
  <div>
    输入循环次数：<input type="number" v-model="loopTimes"/>
    <br>
    <button style="background: #646cff;color: #f9f9f9" @click="setRandomNumber(loopTimes)">生成</button>
    <br>
    总和：{{ sumRandomNum }}
    <br>
    平均数：{{ sumRandomNum / randomNumList.length || '0' }}
    <br>
<!--    {{ randomNumList }}-->
  </div>
</template>

<script setup>
import {ref, watch} from "vue";

// 定义循环次数
let loopTimes = ref(10)

// 随机数数组
let randomNumList = ref([])
// 定义总和
let sumRandomNum = ref(0)

watch(loopTimes, (cur, prev) => {
  randomNumList.value = []
  sumRandomNum.value = 0
})

/**
 * 循环生成随机数
 * @param loopTimes 次数
 */
const setRandomNumber = (loopTimes = 0) => {
  const times = Math.round(loopTimes)
  for (let i = 0; i < times; i++) {
    const num = Math.random()
    sumRandomNum.value = sumRandomNum.value + num
    randomNumList.value.push(num)
  }
}

</script>

<style scoped>

</style>
