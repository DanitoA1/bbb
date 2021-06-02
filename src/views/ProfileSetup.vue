<template>
  <v-container
    class="fill"
    fluid
    style="
    background: #F2F2FE;
    height: 100vh;
    "
  >
    <v-icon
      class="mt-8 ml-3 mainText"
      color="#0A0E46"
      size="35"
      @click="!formCount ? '' : prev()"
    >
      mdi-chevron-left
    </v-icon>
    <h2
      class="mainText mt-4 ml-4"
    >
      Complete your profile
    </h2>
    <p
      class="captionText mt-3 ml-4"
    >
      Update your personal details let’s get started
    </p>
    <div>
      <v-img
        src="@/assets/two-check-marks.svg"
        class="mx-auto mt-8"
        height="30"
        width="130"
        contain
      ></v-img>
    </div>
    <div v-if="!formCount">
      <v-text-field
        class="mx-4 mt-12"
        color="#6A4AEF"
        placeholder="Full Name"
        dense
        prepend-inner-icon="mdi-account"
      ></v-text-field>
      <v-text-field
        class="mx-4 mt-8"
        color="#6A4AEF"
        placeholder="Date of Birth"
        dense
        prepend-inner-icon="mdi-calendar-range"
        append-icon="mdi-menu-down"
      ></v-text-field>
      <v-text-field
        class="mx-4 mt-8"
        color="#6A4AEF"
        placeholder="Phone Number"
        dense
        prepend-inner-icon="mdi-phone"
      ></v-text-field>
      <v-text-field
        class="mx-4 mt-8"
        color="#6A4AEF"
        placeholder="Select Country"
        dense
        prepend-inner-icon="mdi-map-marker-outline"
      ></v-text-field>
      <v-btn
        class="text-capitalize font-weight-bold text-subtitle-1 mt-6"
        color="#0A0E46"
        dark
        large
        block
        @click="next()"
      >
        Next
      </v-btn>
      <p
        class="text-center captionText mt-6"
      >
        Skip
      </p>
    </div>
    <div v-else>
      <v-text-field
        class="mx-4 mt-12"
        color="#6A4AEF"
        placeholder="Enter Address"
        dense
        prepend-inner-icon="mdi-map-marker-outline"
      ></v-text-field>
      <v-text-field
        class="mx-4 mt-8"
        color="#6A4AEF"
        placeholder="City"
        dense
        prepend-inner-icon="mdi-home-city-outline"
      ></v-text-field>
      <v-text-field
        class="mx-4 mt-8"
        color="#6A4AEF"
        placeholder="State"
        dense
        prepend-inner-icon="mdi-home-city-outline"
      ></v-text-field>
      <v-text-field
        class="mx-4 mt-8"
        color="#6A4AEF"
        placeholder="Zip Code"
        dense
        prepend-inner-icon="mdi-text-short"
      ></v-text-field>
      <v-btn
        class="text-capitalize font-weight-bold text-subtitle-1 mt-6"
        color="#0A0E46"
        dark
        large
        block
        @click="next()"
      >
        Finish
      </v-btn>
      <p
        class="text-center captionText mt-6"
      >
        Skip
      </p>
    </div>
  </v-container>
</template>

<script>
export default {
  data () {
    return {
      show: false,
      show2: false,
      formCount: 0
    }
  },
  methods: {
    next () {
      this.formCount++
    },
    prev () {
      this.formCount--
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
    font: normal normal bold 25px/28px Montserrat;
    letter-spacing: 0px;
    color: #0A0E46;
    text-transform: capitalize;
    opacity: 1;
  }
  .captionText {
    text-align: left;
    font: normal normal normal 15px/28px Montserrat;
    letter-spacing: 0px;
    color: #0A0E46;
    opacity: 1;
  }
  .spanText {
    color: #6A4AEF;
  }
</style>
