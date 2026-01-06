<script setup lang="ts">
import { ref } from 'vue'
import { Input } from 'vexip-ui'

const value = ref('')
</script>

<template>
  <div class="view-container">
    <Input v-model:value="value" placeholder="请输入文本" style="max-width: 300px;;"></Input>
    <p>Input Value: {{ value }}</p>
  </div>
</template>
<style scoped>
p {
  margin: 0%;
  padding-top: 2%;
}

.view-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 10px;
  ;
}
</style>