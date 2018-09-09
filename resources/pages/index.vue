<template>
<v-layout >
  <v-layout fill-height column justify-center align-center class="blur" v-if="show">

    <p>Log in</p>
    <v-text-field label="Email" prepend-icon="email" required></v-text-field>
    <v-text-field label="Password" prepend-icon="lock" required></v-text-field>
    <v-layout>

      <v-btn @click="changeForm()">
        Create an account
      </v-btn>
      <v-btn color="primary" @click="login()">
        Login
      </v-btn>

    </v-layout>
  </v-layout>

  <!-- <Login v-if="!ShowLogForm" />
<Reg v-if="ShowLogForm" /> -->

  <v-layout align-center justify-center v-if="!show">
    <v-stepper value="1" v-model="e1" alt-labels class="stepper">
      <v-stepper-header>

        <v-stepper-step :complete="e1 > 1" step="1">Account setup</v-stepper-step>
        <v-divider></v-divider>
        <v-stepper-step :complete="e1 > 2" step="2">Profile details</v-stepper-step>

      </v-stepper-header>

      <v-stepper-items>
        <v-stepper-content step="1">

          <v-layout align-center justify-start fill-height column>

            <v-text-field label="Email" prepend-icon="email" required></v-text-field>
            <v-text-field :counter="10" label="Password" prepend-icon="lock" required></v-text-field>
            <v-text-field :counter="10" label="Confirm Password" prepend-icon="lock" required></v-text-field>

          </v-layout>

          <v-btn color="primary" @click="e1 = 2">
            Continue
          </v-btn>

          <v-btn flat @click="changeForm()">Cancel</v-btn>
        </v-stepper-content>

        <v-stepper-content step="2">
          <v-layout align-center justify-start fill-height column>

            <v-text-field label="First Name" prepend-icon="person" required></v-text-field>
            <v-text-field label="Second Name" prepend-icon="person_outline" required></v-text-field>

            <v-menu ref="menu" :close-on-content-click="false" v-model="menu" :nudge-top="110" :return-value.sync="date">

              <v-text-field slot="activator" v-model="date" label="Birthd ate" prepend-icon="event" readonly></v-text-field>
              <v-date-picker v-model="date" @input="$refs.menu.save(date)"></v-date-picker>

            </v-menu>

            <v-text-field label="Phone" prepend-icon="phone"></v-text-field>
          </v-layout>

          <v-btn color="primary" @click="e1 = 1">
            Complete
          </v-btn>

          <v-btn flat @click="changeForm()">Cancel</v-btn>

        </v-stepper-content>
      </v-stepper-items>
    </v-stepper>
  </v-layout>
</v-layout>
</template>

<script>
import Logo from '~/components/Logo.vue'
import Reg from '~/components/Reg.vue'
// import Login from '~/components/Login.vue'
import VuetifyLogo from '~/components/VuetifyLogo.vue'

export default {
  data() {
    return {
      show: true,
      e1: 0,
    }
  },
  components: {
    Logo,
    VuetifyLogo
  },
  methods: {
    changeForm() {
      this.show = !this.show 
    },
    login() {
      return null;
    }
  }
}
</script>

<style lang="less">
@media screen and(max-width: 812px) {
  .stepper {
    min-width: 100%;
    width: 80%;
  }
}

.blur {
  top: 50px; // filter: blur(5px);
  p {
    font-size: 25px;
  }
}

.hiden {
  display: none;
}

.stepper {
  width: 50%;
}
</style>

