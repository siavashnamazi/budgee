<script>
import Expenses from '../components/Expenses.vue'

export default {
  components: {
    Expenses
  },
  inject: ['json'],
  created() {
    //console.log(this.json) // injected value
  },
  computed: {
    expenseSum () {
      return this.json.intervals[0].expenses.map(item => item.expense_amnt).reduce((prev, next) => prev + next);
    },
    expenseBal () {
      return this.json.intervals[0].interval_budget - this.expenseSum;
    }
  }
}
</script>

<template>
    <v-row v-for="interval in json.intervals" :key="interval.interval_id" >
        <v-col class="text-center" cols="12">
            <p><v-chip variant="outlined" color="deep-purple">{{expenseSum}} 💸</v-chip> <v-icon size="x-small" color="deep-purple" icon="mdi-sword-cross"/> <v-chip variant="outlined" color="green">{{expenseBal}} 🤑</v-chip></p>     
        </v-col>
    </v-row>
    <v-row class="justify-center"> 
        <v-col class="d-flex justify-center">   
            <v-timeline density="compact" truncate-line="both">
                <Expenses />
            </v-timeline>
        </v-col>
    </v-row>
</template>



