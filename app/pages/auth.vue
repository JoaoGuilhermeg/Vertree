<script setup lang="ts">
import * as z from 'zod'
import type { FormSubmitEvent, AuthFormField } from '@nuxt/ui'

const toast = useToast()

const fields: AuthFormField[] = [{
  name: 'email',
  type: 'email',
  label: 'Email',
  placeholder: 'Insira seu e-mail',
  required: true
}, {
  name: 'password',
  label: 'Senha',
  type: 'password',
  placeholder: 'Insira sua senha',
  required: true
}, {
  name: 'remember',
  label: 'Lembrar de mim',
  type: 'checkbox'
}]
const schema = z.object({
  email: z.email('O email é inválido').nonempty('O email é obrigatório'),
  password: z.string('A senha é obrigatória').min(8, 'A senha deve ter pelo menos 8 caracteres')
})

type Schema = z.output<typeof schema>

function onSubmit(payload: FormSubmitEvent<Schema>) {
  console.log('Submitted', payload)
}
</script>

<template>
  <div class="flex flex-col items-center justify-center w-full min-h-screen p-4 bg-slate-50 dark:bg-slate-900">
    <UPageCard class="w-full max-w-md">
      <UAuthForm
        :schema="schema"
        title="Login"
        description="Insira suas credenciais para acessar sua conta."
        icon="i-lucide-user"
        :fields="fields"
        :submit-button-text="'Entrar'"
        @submit="onSubmit"
      />
    </UPageCard>
  </div>
</template>
