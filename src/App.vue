<template>
  <v-app>
    <v-main>
      <div class="container">
        <div class="row">
          <div class="col col-2">1</div>
          <div class="col col-2">2</div>
          <div class="col col-2">3</div>
          <div class="col col-2">4</div>
          <div class="col col-2">5</div>
        </div>
      </div>

      <v-container>
        <v-row>
          <v-col cols="2">1</v-col>
          <v-col cols="2">2</v-col>
          <v-col cols="2">3</v-col>
          <v-col cols="2">4</v-col>
          <v-col cols="2">5</v-col>
        </v-row>
      </v-container>

      <v-container>
        <v-row justify="space-around">
          <v-card width="400" v-for="i in 5">
            <v-img
                height="200px"
                src="https://cdn.pixabay.com/photo/2020/07/12/07/47/bee-5396362_1280.jpg"
            >
              <v-app-bar
                  flat
                  color="rgba(0, 0, 0, 0)"
              >
                <v-app-bar-nav-icon color="white"></v-app-bar-nav-icon>

                <v-toolbar-title class="title white--text pl-0">
                  Messages
                </v-toolbar-title>

                <v-spacer></v-spacer>

                <v-btn
                    color="white"
                    icon
                >
                  <v-icon>mdi-dots-vertical</v-icon>
                </v-btn>
              </v-app-bar>

              <v-card-title class="white--text mt-8">
                <v-avatar size="56">
                  <img
                      alt="user"
                      src="https://cdn.pixabay.com/photo/2020/06/24/19/12/cabbage-5337431_1280.jpg"
                  >
                </v-avatar>
                <p class="ml-3">
                  John Doe
                </p>
              </v-card-title>
            </v-img>

            <v-card-text>
              <div class="font-weight-bold ml-8 mb-2">
                Today
              </div>

              <v-timeline
                  align-top
                  dense
              >
                <v-timeline-item
                    v-for="message in messages"
                    :key="message.time"
                    :color="message.color"
                    small
                >
                  <div>
                    <div class="font-weight-normal">
                      <strong>{{ message.from }}</strong> @{{ message.time }}
                    </div>
                    <div>{{ message.message }}</div>
                  </div>
                </v-timeline-item>
              </v-timeline>
            </v-card-text>
          </v-card>
        </v-row>
      </v-container>
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
        from: 'You',
        message: `12312312`,
        time: '10:42am',
        color: 'deep-purple lighten-1',
      },
      {
        from: 'John Doe',
        message: 'Yeah, sure. Does 1:00pm work?',
        time: '10:37am',
        color: 'green',
      },
      {
        from: 'You',
        message: 'Did you still want to grab lunch today?',
        time: '9:47am',
        color: 'deep-purple lighten-1',
      },
    ],
  }),
};
</script>
