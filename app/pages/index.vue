<script setup lang="ts">
import type { SplitterItem } from '@nuxt/ui'

//Scroll
const scrollablePanel = 'flex flex-col h-full w-full bg-elevated/50 border border-default rounded-xl p-4 overflow-y-auto'

// Estilo para painéis de conteúdo simples/centralizado
const centeredCard = 'flex items-center justify-center h-full w-full bg-elevated/50 border border-default rounded-xl text-muted font-medium'

const items: SplitterItem[] = [
  { slot: 'left', minSize: 15, defaultSize: 25, class: scrollablePanel },
  { slot: 'right', minSize: 30, defaultSize: 75 }
]

const nested: SplitterItem[] = [
  { slot: 'top', minSize: 15, defaultSize: 50, class: scrollablePanel },
  { slot: 'bottom', minSize: 15, defaultSize: 50, class: scrollablePanel }
]

interface Application {
  id: number
  name: string
  categ:string
  description:string
}

 //lista original
const applications = ref<Aplicacoes[]>([
  {
    id: 1,
    name:'MV Soul',
    categ:'Web',
    description:'MV Sistemas'
  },
  {
    id: 2,
    name:'Senior',
    categ:'Desktop',
    description:'Senior'
  },
  {
    id: 3,
    name:'Sisac',
    categ:'Desktop',
    description:'Engplus'
  },
  {
    id: 4,
    name:'Conformidades',
    categ:'Web',
    description:'TI'
  }
])

//campo de busca
const searchText =ref('')

//categoria do filtro(default "TODOS")
const categSelect = ref ('TODOS')


//filtro
const aplicattionsFilter = computed(() => {
  return applications.value.filter((app) =>{

    const term = searchText.value.toLowerCase()
    const checkName = app.nome.toLowCase().includes(term)
    const checkDescription = app.description.toLowerCase().includes(term)
    const checkText = checkName || checkDescription
    
    //verifica categoria
    const checkCateg =
    categSelect.value === 'TODOS' || app.categ === categSelect.value

    //apos checagem
    return checkText && checkCateg

  })
})

</script>

<template>
  <div class="w-full h-screen p-4">
    <USplitter
      id="splitter-nested-example"
      :items="items"
      class="w-full h-full"
    >
      <!-- Painel Esquerdo: Lista de Aplicações -->
      <template #left>
        
      </template>

      <!-- Painel Direito: Splitter -->
      <template #right>
        <USplitter
          id="splitter-nested-example-inner"
          orientation="vertical"
          :items="nested"
          class="w-full h-full"
        >
          <template #top>
            <h2 class="text-xs font-semibold text-muted uppercase tracking-wider mb-2">
              Sistemas
            </h2>
            <p class="text-sm text-muted">
              Selecione uma aplicação para listar os sistemas vinculados.
            </p>
          </template>

          <template #bottom>
            <h2 class="text-xs font-semibold text-muted uppercase tracking-wider mb-2">
              Módulos
            </h2>
            <p class="text-sm text-muted">
              Módulos correspondentes ao sistema selecionado.
            </p>
          </template>
        </USplitter>
      </template>
    </USplitter>
  </div>
</template>