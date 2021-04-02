<template>
  <v-app>
    <v-main>
      <v-container>
        <v-row>
          <v-col cols="2">1</v-col>
          <v-col cols="2">2</v-col>
          <v-col cols="2">3</v-col>
          <v-col cols="2">4</v-col>
          <v-col cols="2">5</v-col>
        </v-row>
      </v-container>

      <v-container fluid>
        <v-row justify="space-around">
          <v-col
              cols="auto"
              xs="12"
              lg="2"
              xl="2"
              v-for="i in 12"
          >
            <v-card
                class="mx-auto"
                max-width="344"
            >
              <v-img
                  src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg"
                  height="200px"
              ></v-img>

              <v-card-title>
                Протеины
              </v-card-title>

            </v-card>
          </v-col>
        </v-row>
      </v-container>

      <div class="text-center">
        <v-dialog
            v-model="dialog"
            width="500"
        >
          <template v-slot:activator="{ on, attrs }">
            <v-btn
                color="red lighten-2"
                dark
                v-bind="attrs"
                v-on="on"
            >
              Нажми на меня
            </v-btn>
          </template>

          <v-card>
            <v-card-title class="headline grey lighten-2">
             текст больше
            </v-card-title>

            <v-card-text>
              <v-text-field
                  v-model="firstname"
                  :rules="nameRules"
                  :counter="10"
                  label="First name"
                  required
              ></v-text-field>
            </v-card-text>

            <v-divider></v-divider>

            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn
                  color="primary"
                  text
                  @click="closeModal"
              >
                I accept
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-dialog>
      </div>

      <v-carousel :interval="500" :cycle="true" :continuous="true" v-model="model">
        <v-carousel-item
            v-for="(color, i) in colors"
            :key="color"
        >
          <v-sheet
              :color="color"
              height="100%"
              tile
          >
            <v-row
                class="fill-height"
                align="center"
                justify="center"
            >
              <div class="display-3">
                Slide {{ i + 1 }}
              </div>
            </v-row>
          </v-sheet>
        </v-carousel-item>
      </v-carousel>
    </v-main>
  </v-app>
</template>

<script>

export default {
  name: 'App',

  data: () => ({
    //
    messages: [
      {
        from:    'You',
        message: `12312312`,
        time:    '10:42am',
        color:   'deep-purple lighten-1',
      },
      {
        from:    'John Doe',
        message: 'Yeah, sure. Does 1:00pm work?',
        time:    '10:37am',
        color:   'green',
      },
      {
        from:    'You',
        message: 'Did you still want to grab lunch today?',
        time:    '9:47am',
        color:   'deep-purple lighten-1',
      },
    ],
    model: 0,
    firstname: '',
    colors: [
      'primary',
      'secondary',
      'yellow darken-2',
      'red',
      'orange',
    ],
    dialog: false,
    nameRules: [
      v => !!v || 'Имя обязательно',
      v => v.length <= 10 || 'Меньше 10 символов введи',
    ],
  }),
  methods: {
    logvmodel(){
      console.log(this.firstname)
    },
    closeModal(){
      this.dialog = false
      this.logvmodel()
    }
  }
};
</script>

<style>
.v-sheet.v-card:not(.v-sheet--outlined) {
  box-shadow: none !important;
}
</style>
