<template>
  <div id="sign">

    <h1 class="header">{{header}}</h1>

    <div class="pure-u-1-3 detail">
      <h2>Network</h2>
      {{ssid}}
    </div>

    <div class="pure-u-1-3">
      <vue-qr v-bind:text="qr_code_value" v-bind:size="350"></vue-qr>
    </div>

    <div class="pure-u-1-3 detail">
      <h2>Password</h2>
      {{password}}
    </div>

    <h1 class="footer">{{footer}}</h1>

    <img src="../assets/wifi.png" class="wifi-icon">

    <h2>Scan with your camera app to connect</h2>
  </div>
</template>

<script lang="ts">
import Vue from "vue";

import VueQr from 'vue-qr'

export default Vue.extend({
  components: {
    VueQr,
  },
  props: {
    ssid: String,
    password: String,
    security: String,

    header: String,
    footer: String,
  },
  computed: {
    qr_code_value (): string {
      return(`WIFI:S:${this.ssid};T:${this.security};P:${this.password};;`)
    }
  },
})
</script>

<style>

#sign {
  margin: 0 auto;
  padding: 2em;
  border: 5px solid #6193FE;
  border-radius: 30px;
  height: 650px;
  width: 1200px;
}

.wifi-icon {
  width: 80px;
  height: 80px;
}

.header {
  margin-top: 40px;
}

.detail {
  margin-top: 100px;
}

</style>

