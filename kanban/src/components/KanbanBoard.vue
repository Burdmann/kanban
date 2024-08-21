<script setup lang="ts">
    import KanbanList from './KanbanList.vue'
    import Popup from './Popup.vue'
</script>

<script lang="ts">
export default {
    data() {
        return {
            lists: ["Test","Test2"],
            items: [
                {name: "name", desc: "...", list:"Test"},
                {name: "other name", desc: "...", list:"Test2"}
            ],
            popupVisible: false,
            newList: ""
        };
    },
    methods: {
        addList() {
            this.lists.push(this.newList)
            this.newList = ""
        }
    }
    };
</script>

<template>
    <div class="board">
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
    .board {
        background-color: red;
        
        display: flex;

        justify-content: space-around;
        flex-direction: row;
    }

    .add-list {
        font-weight: bold;
        font-size: x-large;
    }
</style>