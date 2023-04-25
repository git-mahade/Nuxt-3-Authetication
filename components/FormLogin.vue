<script lang="ts" setup>
const emit = defineEmits(['success'])

const { login } = useAuth()

const form = reactive({
  data: {
    email: 'admin@gmail.com',
    password: 'password',
    rememberMe: false,
  },
  error: '',
  pending: false,
})

async function onLoginClick() {
  try {
    form.error = ''
    form.pending = true

    await login(form.data.email, form.data.password, form.data.rememberMe)

    emit('success')
  }
  catch (error: any) {
    console.error(error)

    if (error.data.message)
      form.error = error.data.message
  }
  finally {
    form.pending = false
  }
}
</script>

<template>
  <p v-if="form.error" mb-3 text-red-500>
    {{ form.error }}
  </p>
  <form class="mb-3 flex flex-col gap-3" @submit.prevent="onLoginClick">
    <input class="p-3" v-model="form.data.email" type="email" placeholder="Email" required>
    <input class="p-3" v-model="form.data.password" type="password" placeholder="Password" required>
    <button
      type="submit" :disabled="form.pending" class="p-3 rounded bg-light-100" hover="bg-light-700"
      transition-colors
    >
      Log In
    </button>
  </form>
</template>
