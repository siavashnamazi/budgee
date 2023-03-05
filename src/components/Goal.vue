<script>

export default {
  inject: ['json'],
  created() {
    //console.log(this.json) // injected value
  }
}
</script>

<template>
  <v-row v-for="goal in json.goals" justify="center" class="b">
    <v-col class="text-center text-truncate" >
      <!-- Current Goal 🤑: <br/> -->
      <v-avatar class="" size="40" rounded="0">
        <v-img :src="goal.thumb"></v-img>
      </v-avatar>{{ goal.goal_name }} - 
      <span class="text-deep-purple">${{ goal.goal_budget }}</span>/<span class="text-success">${{ goal.amnt_run }}</span> <v-icon size="x-small" color="grey" icon="mdi-pencil" />
    </v-col>
  </v-row>
</template>
