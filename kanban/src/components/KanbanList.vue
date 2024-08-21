<script setup lang="ts">
    import KanbanItem from './KanbanItem.vue'
    const props = defineProps<{
        name: string
        items: {
            name: string;
            desc: string;
            list: string;
        }[]
    }>()
</script>

<script lang="ts">
export default {
    methods: {
        onDrop(evt, list) {
            const itemID = evt.dataTransfer.getData('itemID')
            const item = this.items.find((item) => item.name == itemID)
            item.list = list
        },
    },
    computed: {
    getList() {
      return this.items.filter((item) => item.list === this.name)
    },
  },
}
</script>

<template>
    <div class="kanban-list" @drop="onDrop($event, name)" @dragover.prevent @dragenter.prevent>
        <h2 style="font-weight: bold; text-align: center;">{{name}}</h2>
        <!-- <div v-for="item in items" class="kanban-item" :key="item">{{ item }}</div> -->
        <KanbanItem v-for="item in getList" :name="item.name" :desc="item.desc" :key="item.name"></KanbanItem>
    </div>
</template>

<style>
    .kanban-list {
        background-color: blue;
        
        display: flex;
        width: auto;
        justify-content: space-around;
        flex-direction: column;
        margin: 20px;
    }

</style>