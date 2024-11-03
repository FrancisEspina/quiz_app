<template>
  <v-container>
    <div class="text-center mt-5">
      <v-icon size="40">mdi mdi-cat</v-icon>
      <h1 style="font-size: 24px">ChudyQUIZ</h1>
      <br />
    </div>
    <v-row>
      <v-col cols="12" lg="6">
        <v-btn
          variant="outlined"
          prepend-icon="mdi mdi-arrow-left"
          color="white"
          :to="'/'"
          >Home</v-btn
        >
        <div>
          <v-card variant="outlined" class="my-5">
            <div class="pa-10">
              <h2><b>Create Question</b></h2>
              <br />
              <v-row>
                <v-col>
                  Question Type
                  <v-radio-group inline v-model="questionType">
                    <v-radio label="Multiple Choice" value="mcq"></v-radio>
                    <v-radio label="Identification" value="identify"></v-radio>
                  </v-radio-group>
                </v-col>
                <v-col>
                  Difficulty
                  <v-radio-group v-model="difficulty">
                    <v-radio label="Easy" value="1"></v-radio>
                    <v-radio label="Average" value="2"></v-radio>
                    <v-radio label="Difficult" value="3"></v-radio>
                  </v-radio-group>
                </v-col>
              </v-row>
              <br />

              <v-textarea
                variant="outlined"
                rounded="xl"
                v-model="question"
                label="Question"
              ></v-textarea>

              <!-- Choices/Answer -->
              <div v-if="questionType == 'mcq'">
                <v-row no-gutters="">
                  <v-col
                    v-for="(label, index) in labels.slice(0, max)"
                    :key="index"
                    cols="12"
                    sm="6"
                  >
                    <v-text-field
                      width="350px"
                      density="default"
                      :label="label"
                      v-model="choice[label]"
                    ></v-text-field>
                  </v-col>
                </v-row>

                <br />
                <v-row>
                  <v-col>
                    <v-select
                      width="200px"
                      label="Correct Answer"
                      :items="labels.slice(0, max)"
                      variant="outlined"
                      v-model="correctAnswer"
                    ></v-select>
                  </v-col>
                  <v-col>
                    <br />
                    Add Choices
                    <v-btn-group>
                      <v-btn
                        class="mx-2"
                        @click="maxFunction(true)"
                        rounded="lg"
                        color="white"
                        icon="mdi mdi-plus"
                        variant="flat"
                      ></v-btn>
                      <v-btn
                        @click="maxFunction(false)"
                        rounded="lg"
                        color="white"
                        icon="mdi mdi-minus"
                        variant="flat"
                      ></v-btn>
                    </v-btn-group>
                  </v-col>
                </v-row>
              </div>
              <div v-else>
                <v-text-field label="Answer" density="default"></v-text-field>
              </div>
            </div>
          </v-card>
        </div>
      </v-col>
      <v-col>
        <v-card variant="outlined" class="ma-5" v-for="item in 5" :key="item">
          <div class="pa-5">
            <div class="float-start">
              <div class="d-flex align-center">
                <div class="me-2">
                  <h3>
                    <b> Question #{{ item }}</b>
                  </h3>
                </div>
                <v-chip> Easy </v-chip>
              </div>
            </div>
            <br />
            <div class="float-end">
              <v-icon color="">mdi mdi-close</v-icon>
            </div>

            <div class="mt-8">lorem sdadasasdsadasddadasdadasdasdasdasddas</div>
            <br />
          </div>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>
<script>
export default {
  data() {
    return {
      // default
      max: 4,
      correctAnswer: null,
      questionType: "mcq",
      difficulty: "1",
      question: "",
      subjects: ["SOCSCI", "RFBT", "MATH", "SCIENCE"],
      labels: ["A", "B", "C", "D", "E", "F"], // Define your labels here
      choice: {
        A: null,
        B: null,
        C: null,
        D: null,
        E: null,
        F: null,
      },
    };
  },

  mounted() {},
  methods: {
    maxFunction(add) {
      if (add) {
        this.max < 6 ? this.max++ : alert("Maximum number of choices reached!");
      } else {
        this.max > 4 ? this.max-- : alert("Minimum number of choices reached!");
      }
    },
  },
};
</script>
