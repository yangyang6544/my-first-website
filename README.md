# my-first-website
<template>
  <div class="w-full flex flex-col gap-4 py-2">
    <div class="flex flex-col gap-2 border p-4">
      <div class="flex gap-6">
        <div class="flex flex-col">
          <label class="text-sm font-bold">
            顏色
          </label>

          <input
            v-model="color1"
            type="color"
          >

          <input
            v-model="color2"
            type="color"
          >
        </div>

        <base-input
          v-model.number="quantity"
          type="range"
          :label="`最大數量: ${quantity}`"
          class="flex-1"
          :min="100"
          :step="1"
          :max="10000"
        />

        <base-input
          v-model.number="emitRate"
          type="range"
          :label="`發射頻率: ${emitRate}`"
          class="flex-1"
          :min="100"
          :step="1"
          :max="5000"
        />
      </div>

      <div
        class="w-full cursor-pointer select-none border rounded px-4 py-2 text-center"
        @click="refresh()"
      >
        重新產生
      </div>
    </div>

    <bg-firefly
      :key="key"
      v-slot="{ fps }"
      class="bg h-full w-full"
      :color="[color1, color2]"
      :capacity="quantity"
      :emit-rate="emitRate"
    >
      <div class="absolute left-0 top-0 p-4 text-white">
        {{ fps }}
      </div>
    </bg-firefly>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import BaseInput from '../../base-input.vue'
import BgFirefly from '../bg-firefly.vue'

const color1 = ref('#22f534')
const color2 = ref('#b3ff00')
const quantity = ref(5000)
const emitRate = ref(100)

const key = ref('')
function refresh() {
  key.value = Math.random().toFixed(5)
}
</script>

<style scoped lang="sass">
.bg
  background: linear-gradient(to top, #102b19, #191f1b)
</style>
}









        
