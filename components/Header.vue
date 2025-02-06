<script setup>
import { ref } from "vue";
import { Menu, X } from "lucide-vue-next";

const isMenuOpen = ref(false);

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value;
};
</script>

<template>
  <header
    class="max-w-7xl mx-auto py-4 px-4 flex justify-between items-center relative"
  >
    <div class="w-[150px] lg:w-[190px] h-[48px]">
      <img
        class="w-full h-full object-contain"
        src="../assets/images/pay4me.png"
        alt="Pay4Me Logo"
      />
    </div>
    <nav class="hidden lg:flex items-center gap-12">
      <ul class="flex items-center gap-8">
        <li
          v-for="item in ['About', 'Blog', 'Support']"
          :key="item"
          class="text-base text-[#404040] font-normal cursor-pointer hover:text-[#03D44A] transition-colors"
        >
          {{ item }}
        </li>
      </ul>
      <button
        class="px-6 py-3 bg-[#03D44A] text-white text-base font-semibold rounded-full cursor-pointer hover:bg-[#02B83E] transition-colors"
      >
        Get Mobile App
      </button>
    </nav>
    <div class="lg:hidden">
      <button @click="toggleMenu" class="text-[#404040] focus:outline-none">
        <Menu v-if="!isMenuOpen" :size="24" />
        <X v-else :size="24" />
      </button>
    </div>
    <Transition
      enter-active-class="transition duration-300 ease-out"
      enter-from-class="opacity-0 scale-95"
      enter-to-class="opacity-100 scale-100"
      leave-active-class="transition duration-200 ease-in"
      leave-from-class="opacity-100 scale-100"
      leave-to-class="opacity-0 scale-95"
    >
      <nav
        v-if="isMenuOpen"
        class="lg:hidden absolute top-full left-0 w-full bg-white shadow-lg z-50"
      >
        <div class="flex flex-col p-4">
          <ul class="space-y-4">
            <li
              v-for="item in ['About', 'Blog', 'Support']"
              :key="item"
              class="text-base text-[#404040] font-normal cursor-pointer hover:text-[#03D44A] transition-colors"
            >
              {{ item }}
            </li>
          </ul>
          <button
            class="mt-4 w-full px-6 py-3 bg-[#03D44A] text-white text-base font-semibold rounded-full cursor-pointer hover:bg-[#02B83E] transition-colors"
          >
            Get Mobile App
          </button>
        </div>
      </nav>
    </Transition>
  </header>
</template>
