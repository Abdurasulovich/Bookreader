<template>
  <header class="w-full min-h-dvh fixed z-10 top-0 px-[125px]">
<div class="border-b box-border mt-2 pb-[9px]  w-[] flex justify-between overflow-hidden items-end theme-bg-primary" >
    <div class="flex  flex-row items-center">
      <div class="h-11 w-16  mb-3">
      <img  src="@/components/icons/MainLogo.png"/>
      </div>
      <span class="italic font-sans mt-5 ml-5 text-white">
        <strong>Reading starts with book reader</strong>
      </span>
    <a class="text-white mt-5 font-light underline ml-10" href="/"><strong>How to buy?</strong></a>
    </div>


    <div class="flex items-center justify-start gap-x-3">

      <div :class="isVisible ? 'border-1' : 'border-0'" ref="dropDown" class="mt-4 theme-border rounded-[8px] theme-search-line-border-color w-[270px] h-[40px] flex justify-between">
        <div class="flex items-center">
          <input v-if="isVisible" aria-invalid="false" name="search" type="text"
                 class="text-inherit rounded-[8px] text-white px-3 outline-none shadow-none transition duration-200 w-[230px] bg-bgColorPrimaryDark">
          <!--search button-->
          <div v-if="isVisible" class="ml-2 bg-bgColorPrimary h-[15px] w-[1.50px] "></div>
        </div>
          <button @click="searchLineVisibility" class="mr-2">
            <svg
                width="16"
                height="17"
                viewBox="0 0 16 17"
                fill="none"
                xmlns="http://www.w3.org/2000/svg">
              <path class="fill-white" d="M7.29264 1.78784C3.98683 1.78784 1.29395 4.48072 1.29395 7.78655C1.29395 11.0924 3.98683 13.7905 7.29264 13.7905C8.70466 13.7905 10.0033 13.2956 11.0296 12.474L13.5283 14.9714C13.6544 15.0923 13.8228 15.159 13.9975 15.1572C14.1722 15.1554 14.3392 15.0853 14.4628 14.9619C14.5864 14.8385 14.6567 14.6716 14.6588 14.4969C14.6608 14.3223 14.5943 14.1537 14.4736 14.0275L11.9749 11.5288C12.7972 10.5009 13.2926 9.20019 13.2926 7.78655C13.2926 4.48072 10.5985 1.78784 7.29264 1.78784ZM7.29264 3.1212C9.87787 3.1212 11.958 5.20133 11.958 7.78655C11.958 10.3718 9.87787 12.4571 7.29264 12.4571C4.70742 12.4571 2.62728 10.3718 2.62728 7.78655C2.62728 5.20133 4.70742 3.1212 7.29264 3.1212Z" fill="#989898">
              </path>
            </svg>
          </button>
      </div>

      <drop-down-component :options="options"/>

      <dark-mode-toggler/>

      <ol class="mt-5 ml-5 flex gap-x-4 items-center justify-start">
        <li class="">
          <a href="tel:+998913774506" class="text-white font-medium">+998 91 377 45 06</a>
        </li>
        <li class="ms-1">
          <ul class="flex align-items-end p-0 m-0">
            <li>
              <a href="https://www.facebook.com/djalekeev-javlonbek"
                 class="text-white text-decoration-none d-flex align-items-end"
                 target="_blank">
                <svg
                    width="24"
                    height="24"
                    viewBox="0 0 24 24"
                    xmlns="http://www.w3.org/2000/svg">
                  <path
                      d="M15.1743 5.32083H17V2.14083C16.685 2.0975 15.6018 2 14.3402 2C11.7079 2 9.90476 3.65583 9.90476 6.69917V9.5H7V13.055H9.90476V22H13.4661V13.0558H16.2534L16.6959 9.50083H13.4653V7.05167C13.4661 6.02417 13.7428 5.32083 15.1743 5.32083Z"
                      fill="white">
                  </path>
                </svg>
              </a>
            </li>
            <li
                class="mx-2">
              <a
                  href="https://www.instagram.com/dav1d.john?igsh=MXUyc25hbDVpeWM2cg=="
                  class="text-decoration-none d-flex align-items-end"
                  target="_blank">
                <svg
                    width="24"
                    height="24"
                    viewBox="0 0 24 24"
                    fill="none"
                    xmlns="http://www.w3.org/2000/svg">
                  <path
                      d="M12 9.3C11.2839 9.3 10.5972 9.58446 10.0908 10.0908C9.58446 10.5972 9.3 11.2839 9.3 12C9.3 12.7161 9.58446 13.4028 10.0908 13.9092C10.5972 14.4155 11.2839 14.7 12 14.7C12.7161 14.7 13.4028 14.4155 13.9092 13.9092C14.4155 13.4028 14.7 12.7161 14.7 12C14.7 11.2839 14.4155 10.5972 13.9092 10.0908C13.4028 9.58446 12.7161 9.3 12 9.3ZM12 7.5C13.1935 7.5 14.3381 7.97411 15.182 8.81802C16.0259 9.66193 16.5 10.8065 16.5 12C16.5 13.1935 16.0259 14.3381 15.182 15.182C14.3381 16.0259 13.1935 16.5 12 16.5C10.8065 16.5 9.66193 16.0259 8.81802 15.182C7.97411 14.3381 7.5 13.1935 7.5 12C7.5 10.8065 7.97411 9.66193 8.81802 8.81802C9.66193 7.97411 10.8065 7.5 12 7.5ZM17.85 7.275C17.85 7.57337 17.7315 7.85952 17.5205 8.0705C17.3095 8.28147 17.0234 8.4 16.725 8.4C16.4266 8.4 16.1405 8.28147 15.9295 8.0705C15.7185 7.85952 15.6 7.57337 15.6 7.275C15.6 6.97663 15.7185 6.69048 15.9295 6.4795C16.1405 6.26853 16.4266 6.15 16.725 6.15C17.0234 6.15 17.3095 6.26853 17.5205 6.4795C17.7315 6.69048 17.85 6.97663 17.85 7.275ZM12 4.8C9.7734 4.8 9.4098 4.8063 8.3739 4.8522C7.6683 4.8855 7.1949 4.98 6.7557 5.151C6.3651 5.3022 6.0834 5.4831 5.7837 5.7837C5.50201 6.05586 5.28542 6.38813 5.1501 6.7557C4.9791 7.1967 4.8846 7.6692 4.8522 8.3739C4.8054 9.3675 4.8 9.7149 4.8 12C4.8 14.2266 4.8063 14.5902 4.8522 15.6261C4.8855 16.3308 4.98 16.8051 5.1501 17.2434C5.3031 17.6349 5.4831 17.9166 5.7819 18.2154C6.0852 18.5178 6.3669 18.6987 6.7539 18.8481C7.1985 19.02 7.6719 19.1154 8.3739 19.1478C9.3675 19.1946 9.7149 19.2 12 19.2C14.2266 19.2 14.5902 19.1937 15.6261 19.1478C16.3299 19.1145 16.8042 19.02 17.2434 18.8499C17.6331 18.6978 17.9166 18.5169 18.2154 18.2181C18.5187 17.9148 18.6996 17.6331 18.849 17.2461C19.02 16.8024 19.1154 16.3281 19.1478 15.6261C19.1946 14.6325 19.2 14.2851 19.2 12C19.2 9.7734 19.1937 9.4098 19.1478 8.3739C19.1145 7.6701 19.02 7.1949 18.849 6.7557C18.7134 6.3885 18.4972 6.05636 18.2163 5.7837C17.9443 5.50186 17.612 5.28525 17.2443 5.1501C16.8033 4.9791 16.3299 4.8846 15.6261 4.8522C14.6325 4.8054 14.2851 4.8 12 4.8ZM12 3C14.4453 3 14.7504 3.009 15.7098 3.054C16.6683 3.099 17.3208 3.2493 17.895 3.4725C18.489 3.7011 18.9894 4.0107 19.4898 4.5102C19.9474 4.96011 20.3016 5.50433 20.5275 6.105C20.7498 6.6783 20.901 7.3317 20.946 8.2902C20.9883 9.2496 21 9.5547 21 12C21 14.4453 20.991 14.7504 20.946 15.7098C20.901 16.6683 20.7498 17.3208 20.5275 17.895C20.3022 18.496 19.948 19.0404 19.4898 19.4898C19.0398 19.9473 18.4956 20.3014 17.895 20.5275C17.3217 20.7498 16.6683 20.901 15.7098 20.946C14.7504 20.9883 14.4453 21 12 21C9.5547 21 9.2496 20.991 8.2902 20.946C7.3317 20.901 6.6792 20.7498 6.105 20.5275C5.50409 20.302 4.95977 19.9478 4.5102 19.4898C4.05247 19.04 3.69834 18.4957 3.4725 17.895C3.2493 17.3217 3.099 16.6683 3.054 15.7098C3.0117 14.7504 3 14.4453 3 12C3 9.5547 3.009 9.2496 3.054 8.2902C3.099 7.3308 3.2493 6.6792 3.4725 6.105C3.69771 5.50396 4.05192 4.95959 4.5102 4.5102C4.9599 4.05231 5.50419 3.69816 6.105 3.4725C6.6792 3.2493 7.3308 3.099 8.2902 3.054C9.2496 3.0117 9.5547 3 12 3Z"
                      fill="white">
                  </path>
                </svg>
              </a>
            </li>
            <li>
              <a
                  href="https://t.me/javlonbek_abdurasulovich"
                  class="text-decoration-none d-flex align-items-end"
                  target="_blank">
                <svg
                    width="24"
                    height="24"
                    viewBox="0 0 24 24"
                    fill="none"
                    xmlns="http://www.w3.org/2000/svg">
                  <path
                      d="M9.84784 14.5451L9.517 19.0122C9.99034 19.0122 10.1953 18.817 10.4412 18.5826L12.6604 16.5467L17.2588 19.7794C18.1022 20.2306 18.6964 19.993 18.9239 19.0346L21.9423 5.45712L21.9431 5.45632C22.2106 4.25952 21.4923 3.79153 20.6706 4.08512L2.9285 10.6059C1.71764 11.0571 1.73598 11.7051 2.72267 11.9987L7.25861 13.3531L17.7947 7.02431C18.2905 6.70911 18.7414 6.88351 18.3705 7.19871L9.84784 14.5451Z"
                      fill="white">
                  </path>
                </svg>
              </a>
            </li>
          </ul>
        </li>
      </ol>
    </div>
</div>
  </header>
</template>
<script setup lang="ts">
import DropDownComponent from "@/components/dropDownComponent.vue";
import {onBeforeUnmount, onMounted, ref} from "vue";
import DarkModeToggler from "@/components/DarkModeToggler.vue";

const isVisible = ref(false);
const options = ref([
  {
    name: 'UZ',
    value: 'UZ',
  },
  {
    name: 'RU',
    value: 'RU',
  },
  {
    name: 'EN',
    value: 'EN',
  }
]);
const dropDown = ref(null);
const closeDropDown=(element)=>{
  if(!dropDown.value.contains(element.target)){
    isVisible.value = false;
  }
}
onMounted(()=>{

  window.addEventListener('click', closeDropDown)
})

onBeforeUnmount(()=>{
  window.removeEventListener('click', closeDropDown)

})

const searchLineVisibility=()=>{
  isVisible.value = !isVisible.value
}
</script>