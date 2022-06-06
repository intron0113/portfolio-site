<template>
  <v-app light class="over">
    <v-app-bar
      color="primary"
      :clipped-left="$vuetify.breakpoint.lgAndUp"
      clipped-right
      app
    >
      <!-- <v-app-bar color="primary"> -->
      <!-- <div> -->
      <!-- <v-app-bar id="app-bar" color="primary"> -->
      <!-- <v-app-bar color="primary"> -->
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
            <!-- <v-tabs centered class="tab">
              <v-tab
                v-for="(item, index) in headerMenuitems"
                :key="index"
                class="tab"
                @click="headerMenuItemsClick(item.href)"
              >
                {{ item.text }}
              </v-tab>
            </v-tabs> -->
            <!-- <v-toolbar-items justify="center"> -->
            <v-row justify="center">
              <!-- <v-col cols="3">
                <v-btn text>For Enterprise</v-btn>
              </v-col>
              <v-col cols="3">
                <v-btn text>For Enterprise</v-btn>
              </v-col>
              <v-col cols="3">
                <v-btn text>For Enterprise</v-btn>
              </v-col>
              <v-col cols="3">
                <v-btn text>For Enterprise</v-btn>
              </v-col> -->
              <v-col
                v-for="(item, index) in headerMenuitems"
                :key="index"
                cols="2"
                @click="headerMenuItemsClick(item.href)"
              >
                <v-btn text large>{{ item.text }}</v-btn>
              </v-col>
            </v-row>
            <!-- </v-toolbar-items> -->
          </v-col>
          <v-col cols="2" class="d-block d-sm-none">
            <v-app-bar-nav-icon @click="drawer = true"></v-app-bar-nav-icon>
          </v-col>
        </v-row>
      </div>
    </v-app-bar>
    <!-- </div> -->

    <v-navigation-drawer v-model="drawer" fixed temporary>
      <v-list nav dense>
        <v-list-item
          v-for="(item, index) in headerMenuitems"
          :key="index"
          class="color:white"
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
    <v-footer color="primary " class="height:60 width">
      <v-row justify="center">
        <v-col cols="12">
          <div class="white--text" style="text-align: center">
            &copy; {{ new Date().getFullYear() }} {{ author }}
          </div>
        </v-col>
      </v-row>
    </v-footer>
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
        { icon: '', text: 'Top', href: '/#top' },
        { icon: '', text: 'about', href: '/#about' },
        { icon: '', text: 'works', href: '/#works' },
        { icon: '', text: 'skill', href: '/#skill' },
        { icon: '', text: 'contact', href: '/contact' },
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
.over {
  overflow: hidden;
}
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

.theme--dark.v-tabs > .v-tabs-bar {
  background-color: #202f55;
}

.header {
  width: 97%; /* 幅いっぱいを指定 */
  height: 50px; /* 高さを50pxに指定 */
  background: #ccc; /* 背景色にグレーを指定 */
  padding: 20px 50px; /* ヘッダーに上下左右それぞれ余白を指定 */
  box-sizing: border-box; /* padding分を含んで幅を100%にするため */
  position: fixed; /* ウィンドウを基準に画面に固定 */
  top: 0; /* 上下の固定位置を上から0pxにする */
  left: 0; /* 左右の固定位置を左から0pxにする */
  display: flex; /* 中の要素を横並びにする */
  align-items: center; /* 中の要素を上下中央に並べる */
  z-index: 100;
}
</style>
