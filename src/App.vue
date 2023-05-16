<template>
  <header>
    <RouterLink to="/">
      <img alt="Burger Logo" class="logo" src="/img/logo.png" width="125" height="125" />
    </RouterLink>

    <div class="wrapper">
      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/pedidos">Pedidos</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>
</style>
