<template>
  <v-app>
    <v-main background-colorr:secondary class="py-8 px-6">
      <div class="con">
        <v-row justify="center">
          <v-col cols="12">
            <!-- <v-card class="mx-auto" max-width="344"> -->
            <v-card class="px-5">
              <v-row>
                <v-col cols="12" sm="6">
                  <v-card-title> Co-mpa </v-card-title>

                  <v-card-subtitle> Webアプリケーション </v-card-subtitle>

                  <v-card-actions>
                    <v-btn color="orange lighten-2" text> Explore </v-btn>

                    <v-spacer></v-spacer>

                  </v-card-actions>

                  <v-expand-transition>
                    <div>
                      <v-divider></v-divider>

                      <v-card-text>
                        I'm a thing. But, like most politicians, he promised
                        more than he could deliver. You won't have time for
                        sleeping, soldier, not with all the bed making you'll be
                        doing. Then we'll go with that data file! Hey, you add a
                        one and two zeros to that or we walk! You're going to do
                        his laundry? I've got to find a way to escape.
                      </v-card-text>
                    </div>
                  </v-expand-transition>
                </v-col>
                <v-col cols="12" sm="6">
                  <!-- <v-img
                    src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg"
                    height="200px"
                  ></v-img> -->
                  <img src="@/assets/topimage1.jpg" height="200px"></img>
                </v-col>
              </v-row>
            </v-card>
          </v-col>
        </v-row>
      </div>
    </v-main>
  </v-app>
</template>
<script>
export default {
  data: () => ({
    show: false,
  }),
}
</script>
<style>
.con {
  width: 96%;
  max-width: 980px;
  padding: 30px 0;
  margin: 0 auto;
  /* min-height: calc(100vh - 61px); */
  display: flex;
  justify-content: center;
  align-items: flex-start;
}
</style>
