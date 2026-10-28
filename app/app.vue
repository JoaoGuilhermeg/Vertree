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
  <div class="h-screen w-screen overflow-hidden">
    <UApp>
      <NuxtLayout>
        <NuxtPage />
      </NuxtLayout>
    </UApp>
  </div>
</template>
