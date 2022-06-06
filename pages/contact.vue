<template>
  <v-container fluid>
    <section class="contact-container">
      <v-row class="text-center">
        <v-col v-if="!finished" cols="12">
          <!-- <template v-if="!finished"> -->
          <!-- <v-card
            class="always-show-scrollbar"
            :height="bkPoint.cardHeight"
            :width="bkPoint.cardWidth"
          > -->
          <v-card class="always-show-scrollbar" :width="bkPoint.cardWidth">
            <v-container>
              <v-row>
                <v-col cols="12">
                  <h2>お問合せ</h2>
                </v-col>
                <v-col cols="12">
                  <v-form
                    v-model="contactFormValidation.valid"
                    name="contact"
                    method="POST"
                    data-netlify="true"
                    lazy-validation
                    @submit.prevent
                  >
                    <v-text-field
                      v-model="form.name"
                      color="teal"
                      :rules="contactFormValidation.nameRules"
                      label="名前"
                      required
                    ></v-text-field>
                    <!-- <p>
                      <label>
                        お名前:
                        <input v-model="form.name" type="text" name="name" />
                      </label>
                    </p> -->
                    <v-text-field
                      v-model="form.email"
                      color="teal"
                      :rules="contactFormValidation.emailRules"
                      label="メールアドレス"
                      required
                    ></v-text-field>
                    <!-- <p>
                      <label>
                        メールアドレス:
                        <input v-model="form.email" type="email" name="email" />
                      </label>
                    </p> -->
                    <v-textarea
                      v-model="form.content"
                      filled
                      auto-grow
                      color="teal"
                      :rules="contactFormValidation.contentsRules"
                      label="内容"
                      required
                      rows="12"
                      row-height="30"
                    ></v-textarea>
                    <!-- <p>
                      <label>
                        お問い合わせ内容:
                        <textarea
                          id="form-content"
                          v-model="form.content"
                          name="content"
                        />
                      </label>
                    </p> -->
                    <!-- <p>
                      <button @click="handleSubmit" v-text="'送信'" />
                    </p> -->
                    <v-btn
                      :loading="form.loading"
                      :disabled="!contactFormValidation.valid"
                      block
                      large
                      color="info"
                      class="mt-4 font-weight-bold"
                      @click="handleSubmit"
                      >送信
                    </v-btn>
                  </v-form>
                </v-col>
              </v-row>
            </v-container>
          </v-card>
          <!-- </template> -->
        </v-col>
        <v-col v-else cols="12">
          <div class="section-title-block">
            <div class="font-weight-bold text-center my-16">
              お問い合わせ頂きありがとうございました。
            </div>

            <v-row justify="center" class="my-6">
              <v-col cols="3">
                <v-btn
                  href=""
                  block
                  x-large
                  color="success"
                  nuxt-link
                  to="/"
                  dark
                  >TOPへ</v-btn
                >
              </v-col>
            </v-row>
          </div>
        </v-col>
      </v-row>
    </section>
  </v-container>
</template>
<script>
import axios from 'axios'
export default {
  layout: 'plain',
  data() {
    return {
      form: {
        name: '',
        email: '',
        content: '',
        loading: false,
      },
      contactFormValidation: {
        valid: false,
        nameRules: [(v) => !!v || '名前は必須項目です'],
        emailRules: [(v) => !!v || 'メールアドレスは必須項目です'],
        contentsRules: [(v) => !!v || '内容は必須項目です'],
      },
      finished: false,
    }
  },
  computed: {
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
          point.cardHeight = 800
          point.cardWidth = 300
          break
        default:
          break
      }
      return point
    },
  },
  methods: {
    encode(data) {
      return Object.keys(data)
        .map(
          (key) => `${encodeURIComponent(key)}=${encodeURIComponent(data[key])}`
        )
        .join('&')
    },
    handleSubmit() {
      const axiosConfig = {
        header: { 'Content-Type': 'application/x-www-form-urlencoded' },
      }
      axios
        .post(
          '/',
          this.encode({
            'form-name': 'contact',
            ...this.form,
          }),
          axiosConfig
        )
        .then(() => {
          this.finished = true
        })
    },
  },
}
</script>
<style>
.contact-container {
  padding: 64px;
  text-align: center;
}
</style>
