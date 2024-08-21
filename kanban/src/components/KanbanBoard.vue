<script setup lang="ts">
    import KanbanList from './KanbanList.vue'
    import Popup from './Popup.vue'
</script>

<script lang="ts">
export default {
    data() {
        return {
            lists: ["To do","Doing","Done"],
            items: [
                {name: "name", desc: "...", list:"To do"},
                {name: "other name", desc: "This one has a really long description. This means I can see what happens when it has to use multiple lines :).", list:"To do"}
            ],
            popupVisible: false,
            newList: ""
        };
    },
    methods: {
        addList() {
            const newList = this.newList
            this.newList = ""
            if (this.lists.includes(newList)) return // don't add lists with the same name as a previous list
            this.lists.push(newList)
        }
    }
    };
</script>

<template>
    <div class="kanban-board">
        <KanbanList v-for="list in lists" :items="items" :name="list" :key="list"></KanbanList>
        <button class="add-list" v-show="popupVisible==false" @click="popupVisible=true">+</button>
        <Popup :show="popupVisible" @close="popupVisible=false; newList=''">
            <div>
                <input v-model="newList" placeholder="name...">
                <button @click="addList()">Add</button>
            </div>
        </Popup>
    </div>
</template>

<style>
    .kanban-board {
        background-color: lightgray;
        
        display: flex;

        justify-content: space-around;
        flex-direction: row;
    }

    .add-list {
        font-weight: bold;
        font-size: x-large;
    }
</style>