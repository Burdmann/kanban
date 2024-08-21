<script setup lang="ts">
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
import KanbanBoard from './components/KanbanBoard.vue'
import KanbanList from './components/KanbanList.vue'
import KanbanItem from './components/KanbanItem.vue'
</script>

<template>
  <header>
    <div class="wrapper">
    </div>
  </header>

  <main>
    <KanbanBoard/>
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>

<style>
  button {
    background-color: #fff9f3;
    border: 1px solid #381010;
  }
</style>