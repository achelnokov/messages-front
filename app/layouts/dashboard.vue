<template>
  <aside class="sidebar">
    <div class="sidebar-logo">
      <div class="">
        <img class="w-17 h-17" src="../assets/images/MTC_Logo_CMYK.svg" alt="logo">
      </div>
      <div class="ml-3 font-bold text-2xl">
        <h2>Messages</h2>
      </div>
    </div>

    <div class="sidebar-nav">
      <div class="nav-section-title">Меню</div>
      <NuxtLink to="/" class="nav-item">
          <Icon name="solar:home-2-bold-duotone" />
          <span class="nav-text">Главная страница</span>
      </NuxtLink>

      <div class="nav-section-title">Сторонние системы</div>
      <NuxtLink to="/messages" class="nav-item">
        <Icon name="solar:letter-line-duotone" />
        <span class="nav-text">Сообщения</span>
      </NuxtLink>
      <NuxtLink to="/systems" class="nav-item">
        <Icon name="solar:bill-list-line-duotone" />
        <span class="nav-text">Список сторонних систем</span>
      </NuxtLink>

    </div>
  </aside>
  <header class="header justify-end">
    <button class="header-btn" @click="changeTheme">
      <Icon :name="$colorMode.preference == 'white' ? 'solar:moon-bold' : 'solar:sun-bold'" />
    </button>

      <button class="header-btn" @click="changeTheme">
      <Icon name="solar:logout-2-bold-duotone" />
    </button>
  </header>
  <main class="main">
    <div class="p-5">
      <slot />
    </div>
  </main>
</template>

<script setup>


function changeTheme() {
  const colorMode = useColorMode()
  colorMode.preference = (colorMode.preference == 'white') ? 'dark' : 'white'
}
</script>