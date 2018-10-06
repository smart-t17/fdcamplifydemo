<template>
    <div id="app">
      <div v-if="!signedIn">
        <h1> FDC Authenticator Demo - Created by Maximiliano </h1>
         <FDC-Authenticator></FDC-Authenticator>
      </div>
      <div v-if="signedIn">
        <h1>Hello {{this.account.attributes.email}}</h1>
        <amplify-sign-out class="signout"></amplify-sign-out>
      </div>
    </div>
</template>

<script>
import { AmplifyEventBus } from 'aws-amplify-vue'
import { Auth } from 'aws-amplify'
import Authenticator from './components/amplify/Authenticator'

export default {
  name: 'app',
  components: {
    'FDC-Authenticator': Authenticator
  },

  async beforeCreate() {
    try {
      this.account = await Auth.currentAuthenticatedUser()
      this.signedIn = true
    } catch (err) {
      this.signedIn = false
    }
    AmplifyEventBus.$on('authState', async info => {
      if (info === 'signedIn') {
        this.signedIn = true
        this.account = await Auth.currentAuthenticatedUser()
      } else {
        this.signedIn = false
      }
    });
  },

  data () {
    return {
      signedIn: false,
      account : {}
    }
  }
}
</script>

<style>
body {
  margin: 0
}
.signout {
  background-color: #01a540;
  margin: 0;
  padding: 30px 0px 1px;
}
#app {
  font-family: Helvetica, Arial, sans-serif;
  text-align: center;
  color: #552222;
}

</style>