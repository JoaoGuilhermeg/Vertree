<script setup lang="ts">
import { ref } from 'vue'
import type { NavigationMenuItem, SidebarProps } from '@nuxt/ui'

defineProps<Pick<SidebarProps, 'variant' | 'collapsible' | 'side'>>()

const open = ref(true)

const items: NavigationMenuItem[] = [
  {
    label: 'Visão Geral',
    icon: 'i-lucide-eye',
    to: '/'
  },
  {
    label: 'Sistemas',
    icon: 'i-lucide-square-stack',
    badge: '4'
  },
  {
    label: 'Configurações',
    icon: 'i-lucide-settings'
  }
]
</script>

<template>
  <aside
    class="shrink-0 h-screen sticky top-0 flex flex-col border-r border-default bg-default transition-all duration-200 z-30"
    :class="open ? 'w-64' : 'w-16'"
  >
    <!-- Sidebar -->
    <div class="h-14 shrink-0 flex items-center justify-between px-4 border-b border-default">
      <div
        v-if="open"
        class="flex items-center gap-2"
      >
        <UIcon
          name="i-lucide-box"
          class="size-6 text-primary"
        />
        <span class="font-bold tracking-wide text-xl">Vertree</span>
      </div>

      <UButton
        icon="i-lucide-panel-left"
        color="neutral"
        variant="ghost"
        aria-label="Alternar Sidebar"
        @click="open = !open"
      />
    </div>

    <!-- Lista -->
    <div class="flex-1 p-3 overflow-y-auto">
      <UNavigationMenu
        :items="items"
        orientation="vertical"
        :collapsed="!open"
        
        
      />
    </div>
  </aside>
</template>
