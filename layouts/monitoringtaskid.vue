<template>
  <div>
    <header class="shadow-sm bg-white">
      <nav class="container mx-auto p-4 flex justify-between">
        <NuxtLink to="/monitoring-taskid" class="btn font-bold"
          >Monitoring Task Id</NuxtLink
        >
      </nav>
    </header>
    <div class="container mx-auto p-4 bg-red-700">
      <slot />
    </div>
  </div>
</template>
<style scoped>
.router-link-exact-active {
  color: rgb(238, 197, 232);
  text-decoration: none;
}
</style>
