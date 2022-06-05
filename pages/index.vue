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
        <NewProduct />
      </v-col>
    </section>
    <section id="skill">
      <div class="inner">
        <div class="section-title-block">
          <h2 class="headline font-weight-bold text-center my-16">SKILL</h2>
        </div>
        <v-row justify="center">
          <v-col cols="12" sm="12" md="7" lg="9">
            <Skill />
          </v-col>
        </v-row>
      </div>
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
  </div>
</template>

<script>
export default {
  // name: 'Home',
  // components: { ProductList },
}
</script>
<style>
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
