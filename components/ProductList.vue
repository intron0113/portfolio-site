<template>
  <v-container>
    <v-row>
      <v-col
        cols="12"
        sm="6"
        md="4"
        lg="4"
        v-for="product in products"
        :key="product.id"
      >
        <v-card class="mx-auto" @click="openData(product, index)">
          <v-img
            class="white--text align-end"
            src="https://dummyimage.com/250x150/000/fff"
          >
            <v-card-title></v-card-title>
          </v-img>
          <v-card-subtitle class="pb-0"></v-card-subtitle>

          <v-card-text class="text--primary">
            <div>{{ product.category }}</div>
            <div>{{ product.use }}</div>
            <div>{{ product.info }}</div>
          </v-card-text>

          <v-card-actions>
            <v-btn clor="orange" text> link </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'ProductList',
  data: () => ({
    sortYear: '全て',
    products: [
      {
        id: 1,
        name: 'compa',
        image: '../assets/works/dummyimage.png',
        year: '2022',
        category: 'Web app',
        use: 'Nuxt.js firebase',
        // use: 'Nuxt.js firebase',
      },
      {
        id: 2,
        name: 'work2',
        image: '../assets/works/dummyimage.png',
        year: '2019',
        category: 'LP',
        use: 'Vue.js',
        info: '',
      },
      {
        id: 3,
        name: 'work3',
        image: '../assets/works/dummyimage.png',
        year: '2018',
        category: 'LP',
        use: 'デザイン',
      },
      {
        id: 4,
        name: 'work4',
        image: '../assets/works/dummyimage.png',
        year: '2019',
        category: 'LP',
        use: 'Vue.js',
        info: '',
      },
    ],
  }),
  methods: {
    openData(product) {
      this.$router.push(`/works/${product.name}`)
    },
  },
  computed: {},
}
</script>
