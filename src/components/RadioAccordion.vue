<template>
  <div>
    <p class="text-left ml-8 text-slate-400 font-bold">What are you looking to do?</p>
    <div id="accordion-flush" :data-accordion="accordionData" :data-active-classes="activeClasses" :data-inactive-classes="inactiveClasses">
      <RadioItem v-for="item in options" :key="item.id" :item="item"/>
    </div>
  </div>
</template>

<script setup>
  import RadioItem from './RadioItem.vue'
  import { defineProps, ref } from 'vue'

  const props = defineProps(['options'])
  const accordionData = 'collapse'
  const activeClasses = 'bg-white dark:bg-gray-900 text-gray-900 dark:text-white'
  const inactiveClasses = 'text-gray-500 dark:text-gray-400'

</script>
<style>
  @import 'tailwindcss/utilities.css';
</style>
