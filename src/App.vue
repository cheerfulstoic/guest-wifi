<template>
  <div id="app">
    <div id="intro">
      <h1>Guest Wi-Fi Sign Generator</h1>

      <p>Use the below form to create a sign that you can print out and display in our home or office to share your wi-fi password with guests.  Modern phone cameras apps can be used to scan the QR code to sign in without typing!</p>
    </div>

    <form class="pure-form pure-form-stacked">
      <fieldset>
        <legend><em>Options (this form won't appear in the final print)</em></legend>

        <div class="pure-g">
          <div class="pure-u-1 pure-u-md-1-3">
            <label for="multi-ssid">Network Name</label>
            <input type="text" v-model="ssid" id="multi-ssid" class="pure-u-23-24">
          </div>
          <div class="pure-u-1 pure-u-md-1-3">
            <label for="multi-password">Password</label>
            <input type="text" v-model="password" id="multi-password" class="pure-u-23-24">
          </div>
          <div class="pure-u-1 pure-u-md-1-3">
            <label for="multi-security">Security Type</label>
            <select v-model="security" id="multi-security" class="pure-u-23-24">
              <option disabled value="">Choose One</option>
              <option>WPA</option>
              <option>WEP</option>
            </select>
          </div>
          <div class="pure-u-1 pure-u-md-1-3">
            <label for="multi-header">Header</label>
            <input type="text" v-model="header" id="multi-header" class="pure-u-23-24">
          </div>
          <div class="pure-u-1 pure-u-md-1-3">
            <label for="multi-footer">Footer</label>
            <input type="text" v-model="footer" id="multi-footer" class="pure-u-23-24">
          </div>
          <div class="pure-u-1 pure-u-md-1-3">
            <button v-on:click="print" class="pure-button pure-u-23-24">Print</button>
          </div>
        </div>
      </fieldset>
    </form>
    <Sign
      v-bind:ssid="ssid"
      v-bind:password="password"
      v-bind:security="security"
      v-bind:header="header"
      v-bind:footer="footer"
      />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';

import Sign from './components/Sign.vue'

@Component({
  components: {
    Sign,
  },
  data (): object {
    return({
      ssid: '',
      password: '',
      security: '',

      header: 'Welcome to Our Home!',
      footer: '',
    })
  },
  methods: {
    print (): void { window.print() },
  },
})
export default class App extends Vue {}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

@media print {
  @page {size: landscape}

  #intro, form {
    display: none;
  }
}

</style>
