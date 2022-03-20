<script setup lang="ts">
import { ref } from "@nuxtjs/composition-api";

const todos = ref<string[]>([]);

let taskName = ref<string>("");

const addItem = () => {
  todos.value.push(taskName.value);
  taskName.value = "";
};
</script>

<template>
  <v-app>
    <v-card
      width="600px"
      class="mx-auto mt-10 blue white--text"
      tile
      elevation="0"
    >
      <p class="text-h3 text-center ma-0">TODO LIST</p>
    </v-card>

    <v-card width="600px" class="mx-auto mt-10" tile>
      <v-text-field
        @keydown.enter="addTodo"
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

    <v-card class="mx-auto mt-10" width="600px" tile>
      <v-list dense flat class="mb-0">
        <v-subheader class="mb-3 d-flex justify-space-between ">
          <span class="text-h6 blue--text"> 1 Items Left </span>
          <div class="">
            <v-btn-toggle tile color="blue align-self-center" group>
              <v-btn  value="left"> All </v-btn>
              <v-btn  value="center"> Active </v-btn>
              <v-btn  value="right"> Completed </v-btn>
            </v-btn-toggle>
          </div>
        </v-subheader>
        <v-divider />
        <v-list-item-group>
          <v-list-item class="pt-3 pb-3">
            <v-list-item-action>
              <v-checkbox></v-checkbox>
            </v-list-item-action>
            <v-list-item-content>
              <v-list-item-title class="text-h5">vue.js</v-list-item-title>
            </v-list-item-content>
            <v-list-icon>
              <v-btn icon class="mr-5">
                <v-icon class="mx-auto">mdi-pencil</v-icon>
              </v-btn>
              <v-btn icon>
                <v-icon class="mx-auto">mdi-delete</v-icon>
              </v-btn>
            </v-list-icon>
          </v-list-item>
          <v-divider />
        </v-list-item-group>
      </v-list>
    </v-card>
  </v-app>
</template>

<style scoped>
p {
  line-height: 50px;
}
.v-input {
  flex: initial;
  font-size: 20px;
}
.theme--light.v-divider {
  border-color: rgb(201, 192, 192);
}
::v-deep .v-ripple__container {
  display: none !important;
}

::v-deep .v-text-field > .v-input__control > .v-input__slot:before {
  border: none;
}

::v-deep .v-list {
  padding-bottom: 0;
}
</style>
