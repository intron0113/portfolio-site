<template>
  <v-app light>
    <v-app-bar
      color="primary"
      :clipped-left="$vuetify.breakpoint.lgAndUp"
      clipped-right
      app
    >
      <div class="con">
        <v-row justify="center" align="center">
          <v-col cols="10" class="d-block d-sm-none">
            <v-toolbar-title
              style="width: 100%"
              class="ml-0 pl-4"
              @click="$router.push('/')"
            >
              <span class="white--text" style="cursor: pointer">{{
                title
              }}</span>
              <v-spacer />
            </v-toolbar-title>
          </v-col>

          <v-col cols="12" class="d-none d-sm-block">
            <v-tabs centered class="tab">
              <v-tab
                class="tab"
                v-for="(item, index) in headerMenuitems"
                :key="index"
                @click="headerMenuItemsClick(item.href)"
              >
                {{ item.text }}
              </v-tab>
            </v-tabs>
          </v-col>
          <v-col cols="2" class="d-block d-sm-none">
            <v-app-bar-nav-icon @click="drawer = true"></v-app-bar-nav-icon>
          </v-col>
        </v-row>
      </div>
    </v-app-bar>

    <v-navigation-drawer v-model="drawer" fixed temporary>
      <v-list nav dense>
        <v-list-item
          v-for="(item, index) in headerMenuitems"
          :key="index"
          @click="headerMenuItemsClick(item.href)"
        >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title class="white--text">
              {{ item.text }}
            </v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-main>
      <nuxt />
    </v-main>
    <v-footer color="primary">
      <v-containeer style="width: 100%">
        <v-row justify="center">
          <v-col cols="12">
            <div class="white--text" style="text-align: center">
              &copy; {{ new Date().getFullYear() }} {{ author }}
            </div>
          </v-col>
        </v-row>
      </v-containeer>
    </v-footer>
    <!-- </v-sheet> -->
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      search: false,
      drawer: null,
      title: "Shota's portfolio",
      headerMenuitems: [
        { icon: '', text: 'Top', href: '#top' },
        { icon: '', text: 'about', href: '#about' },
        { icon: '', text: 'works', href: '#works' },
        { icon: '', text: 'skill', href: '#skill' },
        { icon: '', text: 'contact', href: '#contact' },
      ],
      author: "Shota's portfolio",
      justify: 'space-between',
    }
  },
  methods: {
    githublLink() {
      const url = 'https://www.yahoo.co.jp/'
      window.location.href = url
    },
    twitterlLink() {
      const url = 'https://www.yahoo.co.jp/'
      window.location.href = url
    },
    toggleDrawer() {
      this.drawer = !this.drawer
    },
    avatarMenuItemClick(href) {
      switch (href) {
        case '/logout':
          window.alert('TODO implement logout')
          break
        default:
          this.$router.push(href)
          break
      }
    },
    headerMenuItemsClick(href) {
      switch (href) {
        default:
          this.$router.push(href)
          break
      }
    },
    changeSerach() {
      this.search = !this.search
    },
    setCanMessageSubmit() {
      this.canMessageSubmit = true
    },
    say() {
      if (!this.canMessageSubmit) {
        return
      }
      // -- submit message -- //
      this.$router.push('/serch')
      this.message = ''
      this.canMessageSubmit = false
    },
  },
}
</script>
<style>
.tab {
  font-size: 12px;
  background-color: #202f55;
  border-color: #202f55;
}
.v-slide-group__content {
  background-color: #202f55;
  border-color: #202f55;
}
.v-tab--active {
  color: white !important;
}
.serachMobile {
  position: fixed;
  z-index: 10;
  width: 90vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.theme--dark.v-tabs > .v-tabs-bar {
  background-color: #202f55;
}
</style>
