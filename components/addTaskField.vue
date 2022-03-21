<script setup lang="ts">
import { Ref, ref } from "@nuxtjs/composition-api";

let newTaskName = ref<string>("");

const emit = defineEmits<{
  (event: 'add-todo', addTaskName:Ref<string>): void;
}>();


</script>

<template>
  <v-app>
    <v-card width="600px" class="mx-auto mt-10" tile>
      <v-text-field
        v-model="newTaskName"
        @keydown.enter="emit('add-todo',newTaskName)"
        autofocus
        autocomplete="off"
        clearable
        color="primary"
        hide-details="auto"
        maxlength="20"
        placeholder="What needs to be done?"
        solo
        flat
        height="70px"
      ></v-text-field>
    </v-card>
  </v-app>
</template>
