<script setup lang="ts">
import qrcode from 'qrcode-generator'
import { computed } from 'vue'

const props = defineProps<{ url: string; size?: number }>()

const svg = computed(() => {
  const qr = qrcode(0, 'M')
  qr.addData(props.url)
  qr.make()
  return qr.createSvgTag({ cellSize: 4, margin: 0 })
})
</script>

<template>
  <div
    class="inline-block bg-white p-3 rounded-lg"
    :style="{ width: `${props.size ?? 180}px`, height: `${props.size ?? 180}px` }"
    v-html="svg"
  />
</template>
