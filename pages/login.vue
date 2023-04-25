<script lang="ts" setup>
const currentUser = useAuthUser()
const isAdmin = useAdmin()

async function onLoginSuccess() {
  const redirect = isAdmin.value ? '/admin' : '/user'

  await navigateTo(redirect)
}
</script>

<template>
  <div>
    <PageTitle title="Login page" />
    <FormLogin @success="onLoginSuccess" />
    <div class="flex gap-20 my-8 text-light-100">
      <div>
        <p  class="mb-3 font-bold">
          Try this user credentials:
        </p>
        <p class="mb-2">
          email: <code>user1@gmail.com</code>
          <br>
          password: <code>password</code>
        </p>
        <p>
          email: <code>user2@gmail.com</code>
          <br>
          password: <code>password</code>
        </p>
      </div>
      <div>
        <p class="mb-3 font-bold">
          Try this admin credentials:
        </p>
        <p class="mb-2">
          email: <code>admin1@gmail.com</code>
          <br>
          password: <code>password</code>
        </p>
        <p>
          email: <code>admin2@gmail.com</code>
          <br>
          password: <code>password</code>
        </p>
      </div>
    </div>
  </div>
</template>
