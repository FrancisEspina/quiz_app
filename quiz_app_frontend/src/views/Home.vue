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

        <v-btn @click="dialogBox = true" class="mx-3"> Subjects </v-btn>
      </div>
    </div>
    <v-dialog v-model="dialogBox" width="500px">
      <v-card>
        <div class="pa-6">
          <h3>Subjects</h3>
          <br />
          <v-row class="d-flex">
            <v-col cols="8">
              <v-text-field
                v-model="addSubject"
                density="default"
                label="Subject Name"
              ></v-text-field>
            </v-col>
            <v-col>
              <v-btn
                class="mt-3"
                append-icon="mdi mdi-check"
                color="green"
                variant="outlined"
                >ADD</v-btn
              >
            </v-col>
            <!-- remvoe -->
            <v-col cols="8">
              <v-select v-model="addSubject" variant="outlined"></v-select>
            </v-col>
            <v-col>
              <v-btn
                class="mt-3"
                append-icon="mdi mdi-close"
                color="red"
                variant="outlined"
                >Remove</v-btn
              >
            </v-col>
          </v-row>
        </div>
      </v-card>
    </v-dialog>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      addSubject: "",
      dialogBox: false,
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
