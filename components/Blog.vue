<template>
  <section class="w-full bg-white py-16 relative">
    <img
      src="../assets/images/money.png"
      alt=""
      class="hidden md:block absolute top-56 left-0"
    />
    <div class="max-w-6xl mx-auto px-4">
      <div class="text-center mb-12">
        <h2 class="text-4xl font-bold mb-2">Latest Blog</h2>
        <div class="relative inline-block">
          <span class="text-4xl font-bold">and Resources</span>
        </div>
      </div>
      <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-[51px]">
        <div
          v-for="(post, index) in blogPosts"
          :key="index"
          class="bg-white rounded-[12px] overflow-hidden border border-solid p-4 border-[#E8E8EA]"
        >
          <div>
            <img
              src="../assets/images/blog.png"
              alt="post.title"
              class="w-full h-[200px] object-cover"
            />
          </div>
          <div class="px-2 pt-6 flex flex-col justify-between items-start">
            <span
              class="bg-[#03D44A0D] text-[#03D44A] px-3 py-1 rounded-full text-sm"
            >
              {{ post.category }}
            </span>
            <h3 class="text-2xl font-medium mb-5 mt-4">
              {{ post.title }}
            </h3>
            <div class="flex items-center space-x-4 mb-6">
              <div class="flex items-center">
                <div class="w-8 h-8 rounded-full mr-2">
                  <img
                    src="../assets/images/Image.png"
                    alt=""
                    class="w-full h-full object-cover"
                  />
                </div>
                <span class="text-[#97989F] text-base font-normal">{{
                  post.author
                }}</span>
              </div>
              <span class="text-[#97989F] text-base font-normal">{{
                post.date
              }}</span>
            </div>
          </div>
        </div>
      </div>

      <!-- Carousel Indicators (Optional) -->
      <div class="flex justify-center space-x-2 mt-8">
        <button
          v-for="(_, index) in blogPosts"
          :key="index"
          @click="currentSlide.value = index"
          class="w-3 h-3 rounded-full transition-colors duration-300"
          :class="index === currentSlide.value ? 'bg-green-500' : 'bg-gray-300'"
        ></button>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue";

const currentSlide = ref(0);

const blogPosts = [
  {
    category: "Education",
    title: "Navigating International Payments for Education without Stress",
    author: "John Ebuka",
    date: "December 29, 2024",
    image: "/api/placeholder/800/400",
  },
  {
    category: "Education",
    title: "Step by Step on How to Pay Tuition from Nigeria to Ghana realtime",
    author: "John Ebuka",
    date: "December 30, 2024",
    image: "/api/placeholder/800/400",
  },
  {
    category: "Education",
    title: "Why Universities prefer Pay4Me app as their Africa Payment Partner",
    author: "John Ebuka",
    date: "December 30, 2024",
    image: "/api/placeholder/800/400",
  },
];

let interval = null;

const nextSlide = () => {
  currentSlide.value = (currentSlide.value + 1) % blogPosts.length;
};

onMounted(() => {
  interval = setInterval(() => {
    nextSlide();
  }, 5000);
});

onBeforeUnmount(() => {
  clearInterval(interval);
});
</script>

<style scoped>
/* Optional: Styling for the carousel */
@media (max-width: 640px) {
  /* Show 1 post on small screens */
  .grid {
    grid-template-columns: 1fr;
  }
}

@media (min-width: 641px) and (max-width: 1024px) {
  /* Show 2 posts on medium screens */
  .grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (min-width: 1025px) {
  /* Show 3 posts on large screens */
  .grid {
    grid-template-columns: repeat(3, 1fr);
  }
}
</style>
