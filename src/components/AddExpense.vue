<script setup>
 defineProps({
   amnt: {
     type: String,
     required: true
   },
   note: {
     type: String,
     required: true
   }   
 })
</script>

<template>
    <v-timeline-item icon="mdi-currency-usd" dot-color="deep-purple" dot-size="x-small" fill-dot>
        <v-form v-model="valid">
            <v-row>
                <div class="d-flex justify-space-between flex-grow-1">
                <v-col cols="8">
                    <v-text-field
                        :v-model="amnt"
                        prepend-inner-icon="mdi-currency-usd"
                        counter="10"
                        label="Amount"
                        variant="underlined"
                        required
                    ></v-text-field>
                </v-col>
                <v-col cols="11">
                    <v-autocomplete
                        :v-model="note"
                        @keydown.enter="addexpense"
                        prepend-inner-icon="mdi-notebook-edit-outline"
                        clearable
                        label="Note"
                        variant="underlined"
                        required
                    ></v-autocomplete>
                </v-col>
            </div>
            </v-row>    
        </v-form>
    </v-timeline-item>
</template>