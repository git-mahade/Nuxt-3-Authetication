<script lang="ts" setup>
definePageMeta({
  middleware: ['admin-only'],
})

const currentUser = useAuthUser()
</script>

<template>
  <div>
    <PageTitle title="Admin page" />
    <PageDescription description="This page should only be visible if user has admin role" />
    <PageUser :user="currentUser" />
  </div>
</template>
