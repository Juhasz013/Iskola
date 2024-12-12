<script setup>
import { RouterLink, RouterView } from "vue-router";
</script>
<script>
export default {
  data() {
    return {
      url:'http://localhost:8000/api'
    }
  },
}
</script>

<template>
  <div>
    <h1>Iskola</h1>
    <header>
      <div class="m-3">
        <nav>
          <RouterLink to="/">Home</RouterLink> |
          <RouterLink to="/kartyak">Kártyak</RouterLink>
        </nav>
      </div>
    </header>
    <RouterView :url="url" />
  </div>
</template>

<style scoped></style>
