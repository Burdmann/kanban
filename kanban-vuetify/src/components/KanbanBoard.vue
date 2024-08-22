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
    };
</script>

<template>
    <v-container class="fill-height">
      <v-responsive
        class="align-center fill-height mx-auto"
        max-width="1800"
        min-height="1000"
      >
  
        <v-row>
            <KanbanList v-for="name in lists" :name="name" :items="items"/>
        </v-row>
      </v-responsive>
    </v-container>
  </template>
