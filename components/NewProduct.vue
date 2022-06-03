<template>
  <!-- <v-app>
    <v-main> -->
  <v-container>
    <v-row>
      <v-col
        v-for="product in products"
        :key="product.id"
        cols="12"
        sm="6"
        md="4"
        lg="4"
        @click="selectedProduct = product"
        style="cursor: pointer"
      >
        <!-- <v-card justify="space-around"> -->
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
          <!-- <img class="image icon icon-user" src="@/assets/topimage1.jpg" /> -->
        </v-card>
      </v-col>
    </v-row>
    <div v-if="overlay" @click="selectedProduct = null">
      <v-overlay :value="overlay">
        <v-container>
          <v-row>
            <v-col>
              <v-card class="white" width="400">
                <v-card-text class="black--text">
                  <div v-text="selectedProduct.category"></div>
                  <div class="text-h6" v-text="selectedProduct.product"></div>
                  <div v-text="selectedProduct.use"></div>
                  <v-divider class="grey lighten-2 my-2"></v-divider>
                </v-card-text>
                <v-card-actions class="justify-center">
                  <v-btn
                    color="success"
                    class="ma-5"
                    @click="selectedProduct = null"
                  >
                    close</v-btn
                  >
                </v-card-actions>
              </v-card>
            </v-col>
          </v-row>
        </v-container>
      </v-overlay>
    </div>
  </v-container>
  <!-- </v-main>
  </v-app> -->
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
      },
      {
        id: '2',
        image: require('@/assets/portfolio.jpg'),
        product: 'Portfolio Site',
        category: 'LP',
        use: 'Nuxt.js firebase',
      },
      {
        id: '3',
        image: require('@/assets/dinoscore.jpg'),
        product: 'Dino-score',
        category: 'web app',
        use: 'vue.js vuetify',
      },
      {
        id: '4',
        image: require('@/assets/umean.jpg'),
        product: 'umean-foods',
        category: 'LP',
        use: 'vue.js vuetify',
      },
    ],
  }),
  computed: {
    overlay() {
      return !!this.selectedProduct
    },
  },
}
</script>
<style lang="scss">
.icon-user {
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 50%;
  width: 32px;
  min-width: 32px;
  height: 32px;
  overflow: hidden;
  margin-right: 10px;

  > .image {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
}
</style>
