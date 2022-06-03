<template>
  <div>
    <section id="top">
      <div class="topimage">
        <div class="topimage-back"></div>
        <div class="container">
          <div class="topimage-text">
            <v-row align="center" justify="center">
              <v-col class="text-center" cols="12">
                <h1>Shota's portfolio site</h1>
                <p></p>
              </v-col>
            </v-row>
          </div>
        </div>
      </div>
    </section>
    <section id="about">
      <v-col cols="12">
        <div class="inner">
          <div class="section-title-block">
            <h2 class="headline font-weight-bold text-center my-16">ABOUT</h2>
          </div>
          <v-row justify="center">
            <v-col cols="12" sm="12" md="7" lg="9">
              <Profile />
            </v-col>
          </v-row>
        </div>
      </v-col>
    </section>
    <section id="works">
      <v-col cols="12">
        <h2 class="headline font-weight-bold text-center my-16">WORKS</h2>
        <ProductList />
      </v-col>
    </section>
    <section id="contact">
      <v-col cols="12">
        <div class="inner">
          <div class="section-title-block">
            <h2 class="headline font-weight-bold text-center my-16">CONTACT</h2>
            <p class="section-desc text-center">
              お問合わせは下記からご連絡をください。
            </p>
          </div>
          <div class="contact-wrapper">
            <div class="contact-list">
              <v-row class="text-center">
                <v-col>
                  <v-btn href="" x-large color="success" dark
                    >Extra large Button</v-btn
                  >
                </v-col>
              </v-row>
            </div>
          </div>
        </div>
      </v-col>
    </section>

    <section>
      <TopImage />
      <div class="discription">
        <h2>Whtat's Co-mpa?</h2>
        <p class="discription__comment">
          Co-mpaはco-medical posting aplication の略になります。
          <br />
          当サイトは日々自己研鑽されている医療従事者の方にむけて<br />
          アウトプットの場を提供する事を目的に開発しました。<br />
          自己研鑽の一端に有効活用してください。<br />
        </p>
      </div>
      <div class="features">
        <h2>Co-mpaでできること</h2>
        <div class="features__list">
          <div class="contents">
            <p class="contents__title">アウトプット機能</p>
            <div class="contents__discription">
              <p>マークダウン形式で記事を書き投稿できます。</p>
            </div>
          </div>
          <div class="contents">
            <p class="contents__title">検索機能</p>
            <div class="contents__discription">
              <p>他のユーザーの記事を検索し閲覧できます。</p>
            </div>
          </div>
          <div class="contents">
            <p class="contents__title">編集機能</p>
            <div class="contents__discription">
              <p>記事編集で文字の付け足しや、削除ができます。</p>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<scripti>
// import Kodawari from '../components/organisms/Kodawari.vue';
export default {
  middleware: "loggedInIsRedirects",
};
</scripti>

<style lang="scss" scoped>
.discription {
  width: 100%;
  height: 250px;
  color: #232323;
  font-size: 1rem;
  line-height: 35px;
  letter-spacing: 0.1rem;
  text-align: center;
  padding: 20px;
}
.discription__comment {
  font-size: 1rem;
}
.features {
  width: 100%;
  height: 360px;
  // margin: 50px 0 0 0;
  padding: 48px 0 0 0;
  text-align: center;
  background-color: #f0e8df;
}
.features__list {
  display: flex;
  margin-top: 50px;
}
.contents {
  width: 30%;
  margin: 0 30px;
}
.contents__title {
  border: solid 3px orange;
  padding: 0.5em;
  border-radius: 0.5em;
}
@media (max-width: 576px) {
  .features {
    width: 100%;
    height: 550px;
  }
  .features__list {
    flex-direction: column;
    width: 100%;
  }
  .contents {
    width: 80%;
    margin: 0 auto;
  }
  .contents__discription {
    font-size: 0.8rem;
    margin-bottom: 30px;
  }
  .discription__comment {
    font-size: 0.8rem;
    padding: 10px;
    line-height: 20px;
  }
}
/* @media (min-width: px) {
  .home {
  background: url("~@/assets/mv.png");
  background-blend-mode: lighten;
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
  width: 100%;
  height: 55vh;
  }
} */
.v-toolbar__content {
  justify-content: space-between;
}

.topimage {
  width: 100%;
  height: 400px;
  background: url('~assets/topimage.jpg');
  background-position: center center;
  background-repeat: no-repeat;
  background-size: cover;
  padding: 10rem 0rem 20rem 0rem;
  color: #fff;
  position: relative;
}

.topimage-back {
  width: 100%;
  position: absolute;
  height: 100%;
  top: 0;
  left: 0;
  background-color: rgba(0, 0, 0, 0.5);
}
.topimage-text {
  position: absolute;
  /* top: 50px; */
  /* right: 50px; */
}
</style>
