<template>
  <NuxtLayout>
    <NuxtPage />
  </NuxtLayout>

  <select v-model="$colorMode.preference" class="hidden">
    <option value="system" selected>white</option>
    <option value="dark">Dark</option>
  </select>
</template>

