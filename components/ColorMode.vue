<template>
  <button @click="toggleDarkMode">
    Icon:
    <Icon :name="isDark ? 'heroicons:moon' : 'heroicons:sun'" />

  </button>
</template>

<script setup lang="ts">

const isDark = ref(false)

const toggleDarkMode = () => {
  isDark.value = !isDark.value
}

watch(isDark, (newValue) => {
  document.body.classList.toggle('dark-mode', newValue)
  localStorage.setItem('darkMode', newValue.toString())
})

onMounted(() => {
  isDark.value = localStorage.getItem('darkMode') === 'true'
})
</script>

<style scoped>
:global(body.dark-mode) {
  background-color: #333;
  color: #fff;
}
</style>