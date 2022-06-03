<template>
  <div>
    <v-container fluid>
      <v-card width="100vw">
        <!-- <v-card-title class="pa-5 justify-center display-1 font-italic">
          自己紹介
        </v-card-title> -->

        <v-row justify="center" align-content="center">
          <v-col cols="12" sm="5" md="5" align="center">
            <v-row
              justify="space-around"
              align-content="center"
              style="height: 100%"
            >
              <v-col cols="12">
                <v-avatar class="icon-user" style="width: 120px; height: 120px">
                  <img
                    src="~/assets/topimage1.jpg"
                    alt="PROFILE"
                    style="object-fit: cover"
                    class="image"
                  />
                </v-avatar>
              </v-col>
              <v-col cols="3">
                <a href="https://github.com/intron0113">
                  <v-icon x-large>mdi-github</v-icon>
                </a>
              </v-col>
              <v-col cols="3">
                <a href="https://twitter.com/yopiken13">
                  <v-icon x-large>mdi-twitter</v-icon>
                </a>
              </v-col>

              <!-- <IconUser
                :image="/assets/topimage1.jpg"
                style="width: 72px; height: 72px"
              /> -->
            </v-row>
          </v-col>
          <v-col cols="12" sm="6" md="6">
            <v-list>
              <v-list-item v-for="profile in profiles" :key="profile.content">
                <v-list-item-content>
                  <v-list-item-title
                    ><v-icon>mdi-check</v-icon>
                    {{ profile.content }}</v-list-item-title
                  >
                </v-list-item-content>
              </v-list-item>
            </v-list>
          </v-col>
        </v-row>
      </v-card>
    </v-container>
  </div>
</template>
<script>
export default {
  data: () => ({
    profiles: [
      { content: '名前:吉澤翔太' },
      { content: '生年月日:1990年1月13日' },
      { content: '出身地:神奈川県横浜市' },
      { content: '出身大学:帝京短期大学' },
      { content: '資格:臨床検査技師' },
    ],
  }),
  methods: {
    moreAbout() {
      this.$router.push('/about')
    },
  },
}
</script>
<style lang="scss" scoped>
.icon-user {
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 50%;
  width: 100px;
  min-width: 100px;
  height: 100px;
  overflow: hidden;

  > .image {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
}
</style>
