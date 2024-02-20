<template>
  <div class="cursor-pointer mt-4" ref="dropDown">
    <div class="border-blue-700 inline" @click="isDropDownVisible = true">
      <ul class="flex items-center justify-start">
        <li>
          <div class="w-[20px] theme-bg-hover hover-duration">
            {{mappedSelectedOption}}
          </div>
        </li>
        <li>
            <svg
              class="w-[25px] mt-1"
              focusable="false"
              aria-hidden="true"
              viewBox="0 0 24 24">
            <path fill="white" d="M7 10l5 5 5-5z"></path>
            </svg>
        </li>
      </ul>
    </div>


    <div
        class="absolute cursor-pointer rounded-full w-16 h-28 pt-3 theme-bg-lang-primary flex-row justify-start items-center"
        v-if="isDropDownVisible">
      <div
        class="option flex text-lg hover:rounded-xl theme-bg-hover theme-hover hover-duration justify-center"
      v-for="(option, index) in options"
      :key="index"
      @click="toggleOptionSelect(option)">
      {{option.name || option}}
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">
import {computed, defineProps, ref, onMounted, onBeforeUnmount} from "vue";
import DarkModeToggler from "@/components/DarkModeToggler.vue";

const dropDown = ref(null);
const props = defineProps({
  options:{
    type: Array,
    required: true
  }
})
const selectedOption = ref('EN')
const isDropDownVisible = ref(false);

const mappedSelectedOption = computed(()=>{
  return(selectedOption.value?.name || selectedOption.value)
})

const toggleOptionSelect = (option) => {
  selectedOption.value = option;
  closeDropDown(option)
}

const closeDropDown=(element)=>{
  if(!dropDown.value.contains(element.target)){
    isDropDownVisible.value = false;

  }
}
onMounted(()=>{

  window.addEventListener('click', closeDropDown)
})

onBeforeUnmount(()=>{
  window.removeEventListener('click', closeDropDown)

})
</script>

