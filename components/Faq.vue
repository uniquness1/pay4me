<template>
  <section class="w-full bg-white pt-[54px] pb-[103px] relative">
    <img
      src="../assets/images/dots.png"
      alt=""
      class="hidden md:block absolute bottom-14 right-0"
    />
    <div class="max-w-6xl mx-auto px-4">
      <h2 class="pb-3 border-b-2 w-full text-4xl font-light">FAQ</h2>
      <div v-for="(item, index) in items" :key="index" class="py-2">
        <div
          @click="toggle(index)"
          class="flex justify-between items-center cursor-pointer border-b border-b-[#ccc] py-2"
        >
          <span class="text-xl font-normal text-[#181A1D]">{{
            item.question
          }}</span>
          <ChevronDownIcon
            :class="{
              'rotate-180': isOpen(index),
              'transition-transform': true,
              transform: true,
            }"
            class="w-6 h-6 text-gray-500"
          />
        </div>

        <!-- Accordion Content -->
        <div v-show="isOpen(index)" class="pl-8 pt-2">
          <p class="text-gray-600">{{ item.answer }}</p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from "vue";
import { ChevronDownIcon } from "lucide-vue-next";
const items = ref([
  {
    question: "What is the Pay4Me App?",
    answer:
      "Vue.js is a progressive JavaScript framework for building user interfaces. It is designed to be incrementally adoptable, which makes it easy to integrate with other libraries or existing projects.",
  },
  {
    question: "How does the Pay4Me App work?",
    answer:
      "An accordion is a UI element that displays content in a collapsible container. It helps organize large amounts of content into sections that can be expanded or collapsed by the user.",
  },
  {
    question: "What is the payment processing timeline on the Pay4Me App?",
    answer:
      "Tailwind CSS is a utility-first CSS framework that allows developers to build custom designs without writing custom CSS. It provides utility classes that can be applied directly to HTML elements.",
  },
  {
    question: "How do I get started using the Pay4Me App?",
    answer:
      "Vue.js uses a reactive data binding system that allows your application’s state to automatically update the DOM when the data changes. This is done using Vue’s `reactive()` and `ref()` APIs.",
  },
]);

const openItems = ref([]);
function toggle(index) {
  const isOpen = openItems.value.includes(index);
  if (isOpen) {
    openItems.value = openItems.value.filter((item) => item !== index);
  } else {
    openItems.value.push(index);
  }
}
function isOpen(index) {
  return openItems.value.includes(index);
}
</script>
