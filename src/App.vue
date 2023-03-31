
<template>
  <div class="bg-white text-black p-16">
    <RadioAccordion :options="options"></RadioAccordion>
  </div>
</template>

<script setup>
  import RadioAccordion from "./components/RadioAccordion.vue";
  import { ref, watch} from 'vue'

  const options = ref([
    { id: '1', title: "I'm looking to sell a property I own", subtitle: 'Awesome, we can get your listing published right now', details: ['Create a listing now', 'Explore active listings in your area'] },
    { id: '2', title: "I'm looking for a good deal to buy", subtitle: "Great! We're so glad you're here. Start browsing and happy hunting", details: ['Create a listing now', 'Explore active listings in your area'] },
    { id: '3', title: "I'm just exploring", subtitle: "No problem, we'd love to help you learn about Aloha My Home", details: ['Create a listing now', 'Explore active listings in your area'] },
  ])

  const active = ref(null)

  watch(active, (newValue, oldValue) => {
    if (newValue !== oldValue) {
      emit('update:modelValue', newValue)
    }
  })

  const onChange = (event, option) => {
    active.value = event.target.checked ? option.id : null
  }

</script>


<style>
  @import 'tailwindcss/utilities.css';
</style>
