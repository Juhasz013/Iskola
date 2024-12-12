<script setup>
import { RouterLink, RouterView } from "vue-router";
</script>

<template>
  <div>
    <h1>Iskola</h1>
    <header>
      <div class="m-3">
        <nav>
          <RouterLink to="/">Home</RouterLink> |
          <RouterLink to="/kartyak">Kartyak</RouterLink>
        </nav>
      </div>
    </header>
    <RouterView />
  </div>
</template>

<style scoped></style>
