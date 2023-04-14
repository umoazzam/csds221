<template>
  <v-dialog v-model="dialog" max-width="500px">
    <v-card>
      <v-card-actions>
        <v-btn color="primary" flat @click="closeDialog">Close</v-btn>
      </v-card-actions>
    </v-card>
  </v-dialog>
</template>

<script>
export default {
  data() {
    return {
      dialog: false,
    };
  },
  methods: {
    closeDialog() {
      this.$emit("exit-dialog");
    },
  },
};
</script>
