<template>
  <v-container
    class="d-flex align-center justify-center"
    style="min-height: 80vh"
  >
    <div class="text-center">
      <v-icon size="100">mdi mdi-cat</v-icon>
      <h1 style="font-size: 90px">ChudyQUIZ</h1>

      <div class="mx-auto">
        <v-btn
          v-for="button in buttons"
          :key="button"
          :to="button.path"
          class="mx-3"
        >
          {{ button.name }}
        </v-btn>
      </div>
    </div>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      is_Ready: true,
      buttons: [
        {
          name: "Add Questions",
          path: "questions",
        },
        {
          name: "Take Test",
          path: "test",
        },
      ],
    };
  },
};
</script>
