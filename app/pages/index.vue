<script setup lang="ts">
import type { SplitterItem } from '@nuxt/ui'

const card = 'flex bg-elevated/50 border border-default rounded-xl items-center justify-center text-muted font-medium'

const items: SplitterItem[] = [
  { slot: 'left', minSize: 20, class: card },
  { slot: 'right', minSize: 70 }
]

const nested: SplitterItem[] = [
  { slot: 'top', minSize: 20, class: card },
  { slot: 'bottom', minSize: 20, class: card }
]
</script>

<template>
  <div class="flex w-full h-screen p-4">
    <USplitter
      id="splitter-nested-example"
      :items="items"
      class="w-full h-full"
    >
      <template #left>
        Aplicações
      </template>
      <template #right>
        <USplitter
          id="splitter-nested-example-inner"
          orientation="vertical"
          :items="nested"
          class="w-full h-full"
        >
          <template #top>
            Sistemas
          </template>
          <template #bottom>
            Módulos
          </template>
        </USplitter>
      </template>
    </USplitter>
  </div>
</template>
