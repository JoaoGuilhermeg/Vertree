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
const applications = ref<Application[]>([
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
    const checkName = app.name.toLowerCase().includes(term)
    const checkDescription = app.description.toLowerCase().includes(term)
    const checkText = checkName || checkDescription
    
    //verifica categoria
    const checkCateg =
    categSelect.value === 'TODOS' || app.categ === categSelect.value

    //apos checagem
    return checkText && checkCateg

  })
})

//seleção(padrao primeiro item)
const selectAplicationId = ref<number | null> (null)
const selectSystemId = ref<number | null>(null)

function selecionarAplicacao(id: number) {
  selectAplicationId.value = id
  selectSystemId.value = null // zera o sistema ao trocar de aplicação
}
const abas = [{
  label:'Atualizações disponíveis',
  icon:'i-lucide-arrow-down',
  slot:'atualizacao'
},
{
  label:''
}
]
</script>

<template>
  <div class="w-full h-full overflow-hidden p-14">
    <USplitter
      id="splitter-nested-example"
      :items="items"
      class="w-full h-full"
    >
      <!-- Painel Esquerdo: lista -->
      <template #left>
        <div class="flex flex-col h-full w-full p-3 gap-3">
    
    <!-- topo: Título + botao de adicionar -->
    <div class="flex items-center justify-between shrink-0">
      <span class="font-bold text-sm">Aplicações</span>
      <!-- Coloque aqui um UButton para adicionar -->
    </div>yyyyh

    <!-- filtros de busca e Select de categoria -->
    <div class="shrink-0 space-y-2">
      
    </div>

    <!-- lista com scroll de cards -->
    <div class="flex-1 min-h-0 overflow-y-auto space-y-2 pr-2">

    </div>

  </div>
</template>

      <!-- painel direito superior e inferior -->
      <template #right>
        <USplitter
          id="main-splitter"
          orientation="vertical"
          :items="nested"
          class="w-full h-full"
        >
          <template #top>
            <div class="shrink-0 p-1">
              <h1>Sistemas</h1>
                <p class="text-sm text-muted">
                  Selecione uma aplicação para listar os sistemas vinculados.
                </p>
            </div>
          </template>

          <template #bottom>
             <div class="shrink-0 p-1">
              <h2>Módulos</h2>
                <p class="text-sm text-muted">
                  Módulos correspondentes ao sistema.
                </p>
            </div>
          </template>
        </USplitter>
      </template>
    </USplitter>
  </div>
</template>