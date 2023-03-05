<script>
import AddExpense from './AddExpense.vue'
export default {
  components: {
    AddExpense
  },
  inject: ['json'],
  beforeCreate() {
    console.log(this.json) // injected value
  },
  computed: {
    timeline () {
      return this.json.intervals[0].expenses.slice().reverse()
    }
  },
  methods: {
    addexpense () {
      this.json.intervals[0].expenses.push({
        expense_id: this.json.intervals[0].expenses.length + 1,
        expense_amnt: parseInt(this.expense_amnt),
        expense_note: this.expense_note,
      })
      this.expense_amnt = null,
      this.expense_note = null
      console.log(this.json) 
    }
  }
}
</script>
<template>
  <v-slide-x-transition group>
    <v-timeline-item v-for="expense in timeline" :key="expense.expense_id" icon="mdi-currency-usd" dot-color="deep-purple" size="x-small" fill-dot>
        <div class="">
            <div class="">
            ${{ expense.expense_amnt }} @{{ expense.expense_note }} <v-icon size="x-small" color="grey-lighten-1" icon="mdi-pencil" />
            </div>
        </div>
    </v-timeline-item>
  </v-slide-x-transition>
    <!-- <AddExpense amnt="expense_amnt" note="expense_note"  /> -->
    <v-timeline-item icon="mdi-currency-usd" dot-color="deep-purple" dot-size="x-small" fill-dot>
        <v-form>
            <v-row>
              <div class="d-flex justify-space-between flex-grow-1">
                  <v-col cols="8">
                      <v-text-field
                          v-model="expense_amnt"
                          type="number"
                          prepend-inner-icon="mdi-currency-usd"
                          label="Amnt"
                          variant="underlined"
                          color="deep-purple"
                          required
                      ></v-text-field>
                  </v-col>
                  <v-col cols="11">
                      <v-text-field
                          v-model="expense_note"
                          @keydown.enter="addexpense"
                          prepend-inner-icon="mdi-notebook-edit-outline"
                          label="Note"
                          variant="underlined"
                          color="deep-purple"
                          required
                      ></v-text-field>
                  </v-col>
              </div>
            </v-row>    
        </v-form>
    </v-timeline-item>
</template>