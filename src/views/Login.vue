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
      Login
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
        :type="show2 ? 'text' : 'password'"
        :append-icon="show2 ?'mdi-eye-outline':'mdi-eye-off-outline'"
        @click:append="show2=!show2"
      ></v-text-field>
    </div>
    <div>
      <v-row
        justify="space-between"
      >
        <v-col cols="8">
          <p
            class="ml-8 captionText mt-8"
          >
            Remember me next time
          </p>
        </v-col>
        <v-col
          cols="3"
        >
          <v-switch
            class="mt-7 mr-3"
            inset
            dark
            dense
            color="white"
          ></v-switch>
        </v-col>
      </v-row>
    </div>
    <div class="mx-8">
      <v-btn
        class="text-capitalize mt-6"
        large
        block
        to="dashboard"
      >
        Sign In
      </v-btn>
      <div class="text-center">
        <v-bottom-sheet
          v-model="sheet"
          inset
        >
          <template v-slot:activator="{ on, attrs }">
            <p
              class="text-center captionText mt-6"
              v-bind="attrs"
              v-on="on"
            >
              Forgot Password
            </p>
          </template>
          <v-sheet
            v-if="!passRecoveryPage"
            class="text-center rounded-t-xl"
            height="60vh"
            color="#F2F2FE"
          >
            <h2 class="mainText2 pt-10 ml-8">
              Forgot Password
            </h2>
            <p class="captionText2 pt-5 ml-8">
              Enter email for the verification process. We will send a 6 digit code to your email.
            </p>
            <div class="mx-8">
              <v-text-field
                class="mt-12"
                placeholder="Email"
                dense
                prepend-inner-icon="mdi-account"
              ></v-text-field>
              <v-btn
                class="text-capitalize font-weight-bold text-subtitle-1 mt-6"
                color="#0A0E46"
                dark
                large
                block
                @click="next()"
              >
                Continue
              </v-btn>
            </div>
          </v-sheet>
          <v-sheet
            v-else-if="passRecoveryPage === 1"
            class="text-center rounded-t-xl"
            height="60vh"
            color="#F2F2FE"
          >
            <h2 class="mainText2 pt-10 ml-8">
              Enter the 6 Digit Code
            </h2>
            <p class="captionText2 pt-5 ml-8">
              Enter the 6 digit code that you received on your email
            </p>
            <div class="mt-10">
              <PincodeInput
                class="test"
                v-model="code"
                :length='6'
              />
            </div>
            <v-row class="mt-3">
              <v-col>
                <v-icon
                  color="#6A4AEF"
                  size="22"
                >
                  mdi-clock-time-three-outline
                </v-icon>
                <span class="spanText2 mx-2">
                  01:53
                </span>
                <span class="spanText2">
                  Resend Code
                </span>
              </v-col>
            </v-row>
            <div class="mx-8">
              <v-btn
                class="text-capitalize font-weight-bold text-subtitle-1 mt-8"
                color="#0A0E46"
                dark
                large
                block
                @click="next()"
              >
                Continue
              </v-btn>
            </div>
          </v-sheet>
          <v-sheet
            v-if="passRecoveryPage === 2"
            class="text-center rounded-t-xl"
            height="60vh"
            color="#F2F2FE"
          >
            <h2 class="mainText2 pt-10 ml-8">
              Reset Password
            </h2>
            <p class="captionText2 pt-5 ml-8">
              Set a new password to access your account
            </p>
            <div class="mx-8">
               <v-text-field
                class="mt-8"
                placeholder="Password"
                dense
                prepend-inner-icon="mdi-lock"
                :type="show2 ? 'text' : 'password'"
                :append-icon="show2 ?'mdi-eye-outline':'mdi-eye-off-outline'"
                @click:append="show2=!show2"
              ></v-text-field>
               <v-text-field
                class="mt-8"
                placeholder="Confirm Password"
                dense
                prepend-inner-icon="mdi-lock"
                :type="show2 ? 'text' : 'password'"
                :append-icon="show2 ?'mdi-eye-outline':'mdi-eye-off-outline'"
                @click:append="show2=!show2"
              ></v-text-field>
              <v-btn
                class="text-capitalize font-weight-bold text-subtitle-1 mt-6"
                color="#0A0E46"
                dark
                large
                block
                @click="sheet=!sheet"
              >
                Reset Password
              </v-btn>
            </div>
          </v-sheet>
        </v-bottom-sheet>
      </div>
      <p
        class="text-center captionText mt-14"
      >
        Don’t have an account? <router-link to="/"><span class="spanText font-weight-bold">Create one</span></router-link>
      </p>
    </div>
  </v-container>
</template>

<script>
import PincodeInput from 'vue-pincode-input'

export default {
  data () {
    return {
      show: false,
      show2: false,
      sheet: false,
      passRecoveryPage: 0
    }
  },
  components: {
    PincodeInput
  },
  watch: {
    sheet () {
      this.passRecoveryPage = 0
    }
  },
  methods: {
    next () {
      this.passRecoveryPage++
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
  .mainText2 {
    text-align: left;
    font: normal normal 600 18px/28px Montserrat;
    letter-spacing: 0px;
    color: #000000;
    text-transform: capitalize;
    opacity: 1;
  }
  .captionText {
    text-align: left;
    font: normal normal normal 14px Montserrat;
    letter-spacing: 0px;
    color: #F9F7FD;
    opacity: 1;
  }
  .captionText2 {
    text-align: left;
    font: normal normal normal 15px/28px Montserrat;
    letter-spacing: 0px;
    color: #000000;
  }
  .spanText {
    color: #6A4AEF;
  }
  .spanText2 {
    text-align: left;
    font: normal normal medium 15px/36px Poppins;
    letter-spacing: 0px;
    color: #5D43DC;
    opacity: 1;
  }
  a, a:hover, a:focus, a:active {
    text-decoration: none;
    color: inherit;
  }
</style>
