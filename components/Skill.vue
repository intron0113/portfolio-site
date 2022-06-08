<template>
  <!-- <v-container> -->
  <v-row>
    <v-col cols="12" sm="6">
      <v-card>
        <v-card-title>フロントエンド</v-card-title>
        <v-list dense>
          <v-list-item v-for="(item, index) in front" :key="index">
            <v-list-item-action>
              <v-icon>{{ item.icon }}</v-icon>
              <!-- <img :src="item.icon"></img> -->
            </v-list-item-action>
            <v-list-item-content>
              <v-list-item-title>
                {{ item.text }}
              </v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-card>
    </v-col>
    <v-col cols="12" sm="6">
      <v-card>
        <v-card-title>バックエンド・その他</v-card-title>
        <v-list dense>
          <v-list-item v-for="(item, index) in back" :key="index">
            <v-list-item-action>
              <v-icon>{{ item.icon }}</v-icon>
              <!-- <img :src="item.icon"></img> -->
            </v-list-item-action>
            <v-list-item-content>
              <v-list-item-title>
                {{ item.text }}
              </v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-card>
    </v-col>
  </v-row>
  <!-- </v-container> -->
</template>
<script>
export default {
  data() {
    return {
      front: [
        { icon: 'mdi-language-html5', text: 'HTML' },
        { icon: 'mdi-language-css3', text: 'CSS' },
        { icon: 'mdi-sass', text: 'Sass' },
        { icon: 'mdi-language-javascript', text: 'JavaScript' },
        { icon: 'mdi-vuejs', text: 'Vue.js' },
        { icon: 'mdi-nuxt', text: 'Nuxt.js' },
      ],
      back: [
        { icon: 'mdi-nodejs', text: 'Node.js' },
        // { icon: 'mdi-docker', text: 'Docker' },
        { icon: 'mdi-github', text: 'git/github' },
        { icon: 'mdi-firebase', text: 'firebase' },
        { icon: 'mdi-slack', text: 'slack' },
        // { icon: 'mdi-language-ruby-on-rails', text: 'Ruby on Rails' },
      ],
    }
  },
}
</script>
<style lang="scss" scoped></style>
