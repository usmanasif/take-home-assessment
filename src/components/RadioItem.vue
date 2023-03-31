<template>
  <div class="w-full">
    <div id="accordion-flush" data-accordion="collapse" :data-active-classes="{'bg-white': isChecked, 'dark:bg-gray-900': isChecked, 'text-gray-900': isChecked, 'dark:text-white': isChecked}" :data-inactive-classes="{'text-gray-500': !isChecked, 'dark:text-gray-400': !isChecked}">
      <h2 :id="'accordion-flush-heading-'+item.id">
        <div class="flex items-center border-solid border-1 outline-1 shadow-md p-4 m-6 rounded-md"
          :class="isChecked ? 'bg-[#FDF8ED]' : 'bg-white'"
        >
          <input
            type="checkbox"
            :id="item.id"
            v-model="isChecked"
            class="mr-2 mb-9 w-4 h-4 self-start mt-1"
          >
          <div class="flex flex-col mb-3 w-full">
            <label class="font-bold self-start">{{ item.title }}</label>
            <label class="self-start">{{ item.subtitle }}</label>
            <div
              :id="'accordion-flush-body-'+item.id"
              class="text-left"
              :class="isChecked ? '' : 'hidden'"
              :aria-labelledby="'accordion-flush-heading-'+item.id"
            >
              <hr class="mx-0.5 my-4">
              <div v-for="detail in item.details" class="flex justify-between">
                <p class="mb-2 inline-block align-middle py-1">{{ detail }}</p>
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" id="arrow-right"><path fill="none" d="M0 0h24v24H0V0z"></path><path d="M10 17l5-5-5-5v10z"></path></svg>
              </div>
            </div>
          </div>
        </div>
      </h2>
    </div>
  </div>
</template>

<script>
import { defineComponent, ref } from 'vue';

export default defineComponent({
  props: {
    item: {
      type: Object,
      required: true,
    },
  },
  setup(props) {
    const isChecked = ref(false);

    return {
      isChecked,
    };
  },
});
</script>

<style>
  @import 'tailwindcss/utilities.css';
</style>
