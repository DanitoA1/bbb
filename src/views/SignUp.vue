<template>
  <v-container
    class="fill"
    fluid
    style="
    background: #0A0E46;
    height: 100vh;
    "
  >
    <p class="mainText pt-14 ml-8">
      Sign Up
    </p>
    <v-row
      class="mt-15 text-center"
      justify="center"
    >
      <v-col cols="auto">
        <v-btn
          class=""
          width="125"
        >
          <v-img
            src="@/assets/google-plus.svg"
            height="15"
            width="8"
            contain
          ></v-img>
        </v-btn>
      </v-col>
      <v-col cols="auto">
        <v-btn
          class=""
          color="#2169E1"
          width="125"
        >
          <v-img
            src="@/assets/facebook-f.svg"
            height="15"
            width="8"
            contain
          ></v-img>
        </v-btn>
      </v-col>
    </v-row>
    <div>
      <v-text-field
        class="mx-8 mt-12"
        dark
        placeholder="Email"
        dense
        prepend-inner-icon="mdi-email-outline"
      ></v-text-field>
      <v-text-field
        class="mx-8 mt-8"
        dark
        placeholder="Password"
        dense
        prepend-inner-icon="mdi-lock"
        :type="show ? 'text' : 'password'"
        :append-icon="show ?'mdi-eye-outline':'mdi-eye-off-outline'"
        @click:append="show=!show"
      ></v-text-field>
      <v-text-field
        class="mx-8 mt-8"
        dark
        placeholder="Confirm Password"
        dense
        prepend-inner-icon="mdi-lock"
        :type="show2 ? 'text' : 'password'"
        :append-icon="show2 ?'mdi-eye-outline':'mdi-eye-off-outline'"
        @click:append="show2=!show2"
      ></v-text-field>
    </div>
    <div class="mx-8">
      <v-btn
        class="text-capitalize mt-6"
        large
        block
      >
        Sign Up
      </v-btn>
      <p
        class="text-center captionText mt-6"
      >
        By signing up you agree to our
      </p>
      <p class="text-center captionText mt-n3">
        <span class="spanText">Terms of Service</span> and <span class="spanText">Privacy Policy</span>
      </p>
      <p
        class="text-center captionText mt-14"
      >
        Already have an account? <span class="spanText2 font-weight-bold">Login</span>
      </p>
    </div>
  </v-container>
</template>

<script>
export default {
  data () {
    return {
      show: false,
      show2: false
    }
  }
}
</script>

<style scoped>
  @import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;500;600;700&display=swap');

  .authBackground {
    background: #0A0E46;
    height: 100vh;
  }
  .mainText {
    text-align: left;
    font: normal normal bold 28px/34px Montserrat;
    letter-spacing: 0px;
    color: #F2F2FE;
    opacity: 1;
  }
  .captionText {
    text-align: left;
    font: normal normal normal 14px Montserrat;
    letter-spacing: 0px;
    color: #F9F7FD;
    opacity: 1;
  }
  .spanText {
    color: #6A4AEF;
    text-decoration: underline;
  }
  .spanText2 {
    color: #6A4AEF;
  }
</style>
