<template>
  <div>
    <v-container fluid>
      <div class="contact-wrapper">
        <div class="contact-list">
          <v-row class="text-center">
            <!-- <v-col cols="12">
              <v-btn href="" x-large color="success" dark>お問合せ</v-btn>
            </v-col> -->
            <v-col cols="12">
              <v-card>
                <v-container>
                  <v-row>
                    <v-col cols="12">
                      <h2>お問い合わせ</h2>
                    </v-col>
                    <v-col cols="12">
                      <v-form
                        ref="form"
                        v-model="contactFormValidation.valid"
                        lazy-validation
                      >
                        <v-text-field
                          v-model="contactForm.name"
                          :rules="contactFormValidation.nameRules"
                          label="名前"
                          required
                        ></v-text-field>
                        <v-text-field
                          v-model="contactForm.email"
                          :rules="contactFormValidation.emailRules"
                          label="メールアドレス"
                          required
                        ></v-text-field>
                        <v-textarea
                          v-model="contactForm.contents"
                          :rules="contactFormValidation.contentsRules"
                          label="内容"
                          required
                        ></v-textarea>
                        <v-btn
                          :loading="contactForm.loading"
                          :disabled="!contactFormValidation.valid"
                          block
                          large
                          color="info"
                          class="mt-4 font-weight-bold"
                          @click="sendMail()"
                          >送信
                        </v-btn>
                      </v-form>
                    </v-col>
                  </v-row>
                </v-container>
              </v-card>
            </v-col>
            <v-col cols="12">
              <v-snackbar
                v-model="snackBar.show"
                :color="snackBar.color"
                bottom
                right
                :timeout="6000"
                class="font-weight-bold"
              >
                {{ snackBar.message }}
              </v-snackbar>
            </v-col>
          </v-row>
        </div>
      </div>
    </v-container>
  </div>
</template>
<script>
// import { functions } from '@/plugins/firebase'
// export const functions = $firebase.functions()

export default {
  data: () => ({
    contactForm: {
      name: '',
      contents: '',
      email: '',
      loading: false,
    },
    contactFormValidation: {
      valid: false,
      nameRules: [(v) => !!v || '名前は必須項目です'],
      emailRules: [(v) => !!v || 'メールアドレスは必須項目です'],
      contentsRules: [(v) => !!v || '内容は必須項目です'],
    },
    snackBar: {
      show: false,
      color: '',
      message: '',
    },
  }),
  methods: {
    sendMail(functions) {
      if (this.$refs.form.validate()) {
        this.contactForm.loading = true
        const mailer = functions.httpsCallable('sendMail')

        mailer(this.contactForm)
          .then(() => {
            this.formReset()
            this.showSnackBar(
              'success',
              'お問い合わせありがとうございます。送信完了しました'
            )
          })
          .catch((err) => {
            this.showSnackBar(
              'error',
              '送信に失敗しました。twitterのDM機能をお試しください。'
            )
            console.log(err)
          })
          .finally(() => {
            this.contactForm.loading = false
          })
      }
    },
    showSnackBar(color, message) {
      this.snackBar.message = message
      this.snackBar.color = color
      this.snackBar.show = true
    },
    formReset() {
      this.$refs.form.reset()
    },
  },
}
</script>
<style lang="scss" scoped></style>
