<script >
import json from './data.json'
import Goal from './components/Goal.vue'
import Interval from './components/Interval.vue'
import Intervals from './components/Intervals.vue'
import { computed } from 'vue'
import { ref } from 'vue'
 const theme = ref('light')
 function onClick () {
   theme.value = theme.value === 'light' ? 'dark' : 'light'
 }
export default{
  components: {
    Interval,
    Goal
  },
  data:() =>({
     theme: 'light'
	}),
  provide() {
    return {
      json: json
    }
  }
}
</script>
<template>
  
  <v-app :theme="theme">
    <v-app-bar class="text-deep-purple" title="budgee">
      <v-spacer></v-spacer>
      <!-- <v-btn :icon="theme === 'light' ? 'mdi-weather-sunny' : 'mdi-weather-night'" @click="onClick" />  -->
      <v-btn icon="mdi-account-cog" />
    </v-app-bar>
    <v-main>
      <v-container>
          <Goal/>
          <Interval/> 
      </v-container>
    </v-main>
    <v-footer>
      <v-row>
        <v-col class="text-center align-self-end" cols="12">
          Made in NYC <v-icon icon="mdi-github" /> 
           <!-- {{ new Date().getFullYear() }} -->
           
        </v-col>
      </v-row>
    </v-footer>
  </v-app>
</template>
