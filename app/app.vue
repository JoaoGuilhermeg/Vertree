<script setup lang="ts">
useHead({
  meta: [
    { name: 'viewport', content: 'width=device-width, initial-scale=1' }
  ],
  link: [
    { rel: 'icon', href: '' }
  ],
  htmlAttrs: {
    lang: 'en'
  }
})

const title = 'Vertree - Versionamento de aplicações'
const description = 'Vertree é uma ferramenta de versionamento de aplicações que permite gerenciar e controlar as versões de seus projetos de forma eficiente e organizada.'

useSeoMeta({
  title,
  description,
  ogTitle: title,
  ogDescription: description,
  ogImage: 'https://vertree.vercel.app/og-image.png',
  twitterCard: 'summary_large_image'
})
</script>

<template>
  <UApp>
    <UMain class="flex min-h-screen w-full">
      <AppSidebar />
      <main class="flex-1 min-w-0 p-6 overflow-y-auto">
        <NuxtPage />
      </main>
    </UMain>

    <UFooter>
      <template #default>
        <p class="text-sm text-muted text-center">
          Vertree • © {{ new Date().getFullYear() }}
        </p>
      </template>
    </UFooter>
  </UApp>
</template>
