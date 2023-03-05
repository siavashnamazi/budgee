<script setup>
defineProps({
  msg: {
    type: String,
    required: true
  }
})
</script>

<template>
    <v-col class="text-center" cols="12">
       <h1>{{ msg }}</h1>     
    </v-col>
</template>
