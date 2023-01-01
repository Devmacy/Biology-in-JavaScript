<template xmlns="http://www.w3.org/1999/html">
  <div style="display: flex;align-items: center">
    <div>
      设置初代基因频率
      <br>
      A1A1:<input type="number" v-model="A1A1"/> <br>
      A1A2:<input type="number" v-model="A1A2"/> <br>
      A2A2:<input type="number" v-model="A2A2"/> <br>
    </div>

    <div>
      <div>
        A1的概率 {{ A1 }}
      </div>

      <div>
        A2的概率 {{ A2 }}
      </div>
    </div>
  </div>

  <div class="current-card">
    第{{ generation }}代
    <div>
      A1A1:{{ A1A1 }}
    </div>
    <div>
      A1A2:{{ A1A2 }}
    </div>
    <div>
      A2A2:{{ A2A2 }}
    </div>
  </div>

  <button @click="generateNext" style="background: #646cff;color: #f9f9f9">产生下一代</button>
</template>

<script setup>
import {computed, ref} from "vue";

// 定义代数
let generation = ref(0);

// 定义基因类型频率
let A1A1 = ref(0.15);
let A2A2 = ref(0.35);
let A1A2 = computed(() => (1 - A1A1.value - A2A2.value));

// 定义等位基因
let A1 = computed(() => (A1A1.value + (A1A2.value / 2)))
let A2 = computed(() => 1 - A1.value)

//产生下一代
const generateNext = () => {
  ++generation.value;
  let left = A1.value;
  let right = A2.value;
  A1A1.value = roundNumber(left * left, 3);
  A2A2.value = roundNumber(right * right, 3);
  A1A2.value = roundNumber(2 * left * right, 3);
}

const roundNumber = (num, decimals = 1) => {
  const shifter = Math.pow(10, decimals)
  return Math.round(num * shifter) / shifter
}
</script>

<style scoped lang="css">
.current-card {
  margin: 5px;
  padding: 10px 5px;
  border: 1px dotted #646cff;
  border-radius: 20px;
}
</style>
