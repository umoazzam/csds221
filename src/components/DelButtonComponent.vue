<template>
  <v-btn @click="deleteTask" variant="flat" color="error" icon>
    <v-icon>mdi-delete-forever</v-icon>
  </v-btn>
</template>

<script>
import toastr from "toastr";
import "toastr/build/toastr.css";

export default {
  props: {
    taskList: {
      type: Array,
      required: true,
    },
    title: {
      type: String,
      required: true,
    },
  },
  methods: {
    deleteTask() {
      const index = this.taskList.findIndex((task) => task.title === this.title);
      if (index !== -1) {
        this.taskList.splice(index, 1);
        toastr.success("Task was deleted successfully!");
      }
    },
  },
};
</script>
