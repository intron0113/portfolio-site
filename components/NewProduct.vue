<template>
  <v-container>
    <v-row>
      <v-col
        v-for="product in products"
        :key="product.id"
        cols="12"
        sm="6"
        md="4"
        lg="4"
        style="cursor: pointer"
        @click="selectedProduct = product"
      >
        <v-card class="mx-auto my-4" max-width="300">
          <v-row>
            <v-col cols="12">
              <v-img class="" :src="product.image" max-height="150">
                <v-card-title></v-card-title>
              </v-img>
            </v-col>
            <v-col cols="12">
              <v-card-text class="my-0 pa-2 text--primary">
                <div class="text-h6 my-2">
                  {{ product.product }}
                </div>
                <v-divider></v-divider>
                <div class="my-2">
                  {{ product.category }}
                </div>
                <div class="my-2">
                  {{ product.use }}
                </div>
              </v-card-text>
              <v-divider class="my-2"></v-divider>
            </v-col>
          </v-row>
        </v-card>
      </v-col>
    </v-row>
    <!-- モーダルウィンド -->
    <div v-if="overlay" @click="selectedProduct = null">
      <v-overlay :value="overlay">
        <v-container>
          <v-row>
            <v-col cols="12">
              <v-card
                class="always-show-scrollbar"
                :height="bkPoint.cardHeight"
                :width="bkPoint.cardWidth"
              >
                <v-row align-content="center">
                  <v-col cols="12" sm="6">
                    <v-card-title class="text-h4">
                      {{ selectedProduct.product }}
                    </v-card-title>
                    <v-card-text class="v-text">
                      <!-- {{ selectedProduct.category }} -->
                      {{ selectedProduct.text }}
                    </v-card-text>
                    <v-card-subtitle class="text-h6">
                      使用言語など
                    </v-card-subtitle>
                    <v-card-text class="v-text">
                      {{ selectedProduct.useTec }}
                    </v-card-text>
                    <v-card-subtitle class="text-h6">
                      開発期間
                    </v-card-subtitle>
                    <v-card-text class="v-text">
                      {{ selectedProduct.development }}
                    </v-card-text>
                    <v-divider class="grey lighten-2 my-2"></v-divider>
                    <v-card-subtitle class="text-h6"> </v-card-subtitle>
                    <v-row>
                      <v-col cols="12">
                        <a
                          :href="selectedProduct.github"
                          style="color: inherit"
                        >
                          <v-icon>mdi-github</v-icon>
                          github
                        </a>
                      </v-col>
                      <v-col cols="12">
                        <a :href="selectedProduct.link" style="color: inherit">
                          <v-icon>mdi-link-box-variant-outline</v-icon>
                          siteLink
                        </a>
                      </v-col>
                      <v-col v-if="selectedProduct.frame !== ''" cols="12">
                        <a :href="selectedProduct.frame" style="color: inherit">
                          <v-icon>mdi-application-parentheses-outline</v-icon>
                          ワイヤーフレーム・画面遷移図
                        </a>
                      </v-col>
                      <v-col v-if="selectedProduct.db !== ''" cols="12">
                        <a :href="selectedProduct.db" style="color: inherit">
                          <v-icon>mdi-database</v-icon>
                          DB
                        </a>
                      </v-col>
                      <v-col v-if="selectedProduct.er !== ''" cols="12">
                        <a :href="selectedProduct.er" style="color: inherit">
                          <v-icon>mdi-source-branch</v-icon>
                          ER
                        </a>
                      </v-col>
                    </v-row>
                    <!-- <v-divider class="grey lighten-2 my-2"></v-divider> -->
                  </v-col>
                  <v-col cols="12" sm="6">
                    <v-img
                      v-for="(item, i) in selectedProduct.items"
                      :key="i"
                      class="mt-4 mx-4 image-d"
                      :src="item.src"
                    />
                  </v-col>
                  <v-col cols="12">
                    <v-card-actions class="justify-center">
                      <v-btn
                        color="success"
                        class="ma-5"
                        @click="selectedProduct = null"
                      >
                        close</v-btn
                      >
                    </v-card-actions>
                  </v-col>
                </v-row>
              </v-card>
            </v-col>
          </v-row>
        </v-container>
      </v-overlay>
    </div>
  </v-container>
</template>

<script>
export default {
  data: () => ({
    selectedProduct: null,
    products: [
      {
        id: '1',
        image: require('@/assets/compa.jpg'),
        product: 'Co-mpa',
        category: 'web app',
        use: 'Nuxt.js firebase',
        text: '医療職に従事している際に、アウトプットの場がもっと身近にあればという悩みを抱えていました。解決策として、記事投稿サイトをきっかけにアウトプット学習を行えないかと考え記事投稿アプリを開発しました。ログイン機能、マークダウン記法による記事作成、タグ検索、全文検索機能を実装。本格的にアプリ開発を始めて行い、DB設計、ワイヤーフレーム作成も行いました。開発を通してCRUD、ユーザー登録などの基礎的な考え方を学ぶことができ、アプリケーション開発の流れを学ぶ事ができました。今後もアップデートを行い、医療従事者のチーム医療の一端になれればと考えています。',
        useTec:
          'Nuxt.js,vuetify,firebase/Authentication,firebase/Database,firebase/Storage,firebase/Hosting,algolia(検索用)',
        development: '3ヶ月',
        link: 'https://compa-med.web.app/',
        github: 'https://github.com/intron0113/compa-web',
        // frame: 'https://overflow.io/s/98APJPR4?node=62ca7c5c',
        // db: 'https://docs.google.com/spreadsheets/d/1l1vmaS1n-Wi9eQiGgZyTJePAXTVOeSBd_XsbWaIajqM/edit#gid=0',
        // er: 'https://drive.google.com/file/d/1GuVbAFcmBnXY_tYudYg_ICtA5gQQ6Lt8/view?usp=sharing',
        frame: '',
        db: '',
        er: '',
        items: [
          {
            src: require('@/assets/compa.jpg'),
          },
          {
            src: require('@/assets/compa-login.jpg'),
          },
          {
            src: require('@/assets/compa-post.jpg'),
          },
          {
            src: require('@/assets/compa-mypage.jpg'),
          },
        ],
      },
      {
        id: '2',
        image: require('@/assets/portfolio.jpg'),
        product: 'Portfolio Site',
        category: 'LP',
        use: 'Nuxt.js firebase',
        text: 'このWebページです。Nuxt.jsを使用しSPAとして、1枚のランディングページに仕上げました。vuetifyの機能を使用しシンプルに見やすくを意識しました。contactformはnetlifyを使用し実装しています。',
        useTec: 'Nuxt.js,vuetify',
        development: '20時間',
        link: 'https://sy-portfoliosite.netlify.app/',
        github: 'https://github.com/intron0113/portfolio-site',
        frame: '',
        db: '',
        er: '',
        items: [
          {
            src: require('@/assets/portfolio.jpg'),
          },
          {
            src: require('@/assets/portfolio-works.jpg'),
          },
          {
            src: require('@/assets/portfolio-skill.jpg'),
          },
        ],
      },
      {
        id: '3',
        image: require('@/assets/dinoscore.jpg'),
        product: 'Dino-score',
        category: 'web app',
        use: 'vue.js vuetify',
        text: 'ログイン機能を持たせていない簡単なwebアプリです。甥からのスコア表が欲しいと依頼があり作成しました。点数を加点していくとランダムで画像が切り替わります。',
        useTec: 'Vue.js,vuetify',
        development: '10時間',
        link: 'https://so-aki-dinoscore.netlify.app/',
        github: 'https://github.com/intron0113/Score-bord-For-children-Vuetify',
        frame: '',
        db: '',
        er: '',
        items: [
          {
            src: require('@/assets/dinoscore.jpg'),
          },
          {
            src: require('@/assets/dinoscore-2.jpg'),
          },
          {
            src: require('@/assets/dinoscore-1.jpg'),
          },
        ],
      },
      {
        id: '4',
        image: require('@/assets/umean.jpg'),
        product: 'umean-foods',
        category: 'LP',
        use: 'vue.js vuetify',
        text: 'サイトリをニューアルしたいと知人の梅干屋から依頼があり、開発しました。依頼者から要望を聞き実際の機能を省略し見た目や操作性重視で開発しました。自社HPとECサイトを兼ねていたのでECのバックエンド部分は実装しませんでしたが、商品ページから買い物カゴに追加する機能をvuexを利用して実装しました。結果サイトリニューアルには至りませんでしたが、依頼を受け納品チェックを受けるという流れは体験できました。',
        useTec: 'Vue.js,vuetify',
        development: '40時間',
        link: 'https://umean-foods-testsite.netlify.app/',
        github: 'https://github.com/intron0113/Fictitious-store-Vuex.Vuerouter',
        frame: '',
        db: '',
        er: '',
        items: [
          {
            src: require('@/assets/umean.jpg'),
          },
          {
            src: require('@/assets/umean-detail.jpg'),
          },
          {
            src: require('@/assets/umean-cart.jpg'),
          },
        ],
      },
    ],
  }),
  computed: {
    overlay() {
      return !!this.selectedProduct
    },
    bkPoint() {
      // $vuetify.breakpointでブレークポイントを取得
      const bkPt = this.$vuetify.breakpoint
      const point = {
        name: bkPt.name,
        cardHeight: 200,
        titleLength: 10,
        textLength: 15,
      }
      switch (bkPt.name) {
        case 'xl':
          point.cardHeight = 800
          point.cardWidth = 1080
          break
        case 'lg':
          point.cardHeight = 800
          point.cardWidth = 1080
          break
        case 'md':
          point.cardHeight = 800
          point.cardWidth = 860
          break
        case 'sm':
          point.cardHeight = 800
          point.cardWidth = 500
          break
        case 'xs':
          point.cardHeight = 600
          point.cardWidth = 300
          break
        default:
          break
      }
      return point
    },
  },
}
</script>
<style lang="scss">
.always-show-scrollbar {
  overflow-y: scroll !important;
}
.image-d {
  max-width: 100%;
  max-height: 400px;
  text-align: center;
}
.v-text {
  letter-spacing: 0.2em;
  line-height: 2rem;
}
</style>
