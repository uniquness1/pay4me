<template>
  <div class="w-full max-w-6xl mx-auto px-4 py-8">
    <div
      class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 divide-y sm:divide-y-0 sm:divide-x divide-gray-200"
    >
      <div class="flex flex-col items-center justify-center p-6 rounded-lg">
        <h2
          class="text-3xl sm:text-4xl lg:text-6xl font-bold text-[#18063C] mb-2"
        >
          <span ref="activeUsers">0</span>k+
        </h2>
        <p class="text-gray-500 text-lg">Active users</p>
      </div>
      <div class="flex flex-col items-center justify-center p-6 rounded-lg">
        <h2
          class="text-3xl sm:text-4xl lg:text-6xl font-bold text-[#18063C] mb-2"
        >
          <span ref="passiveUsers">0</span>k
        </h2>
        <p class="text-gray-500 text-lg">Passive users</p>
      </div>
      <div class="flex flex-col items-center justify-center p-6 rounded-lg">
        <h2
          class="text-3xl sm:text-4xl lg:text-6xl font-bold text-[#18063C] mb-2"
        >
          <span ref="increase">0</span>%
        </h2>
        <p class="text-gray-500 text-lg">Increase in users</p>
      </div>
      <div class="flex flex-col items-center justify-center p-6 rounded-lg">
        <h2
          class="text-3xl sm:text-4xl lg:text-6xl font-bold text-[#18063C] mb-2"
        >
          ><span ref="testimonials">0</span>k
        </h2>
        <p class="text-gray-500 text-lg">Good Testimonials</p>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";

const activeUsers = ref(null);
const passiveUsers = ref(null);
const increase = ref(null);
const testimonials = ref(null);

const easeOutQuad = (t) => t * (2 - t);

const animateNumber = (element, target, duration = 2000) => {
  const startTime = performance.now();

  const updateNumber = (currentTime) => {
    const elapsed = currentTime - startTime;
    const progress = Math.min(elapsed / duration, 1);

    const value = Math.floor(easeOutQuad(progress) * target);
    element.textContent = value;

    if (progress < 1) {
      requestAnimationFrame(updateNumber);
    }
  };

  requestAnimationFrame(updateNumber);
};

const startAnimations = () => {
  setTimeout(() => animateNumber(activeUsers.value, 115), 100);
  setTimeout(() => animateNumber(passiveUsers.value, 88), 300);
  setTimeout(() => animateNumber(increase.value, 30), 500);
  setTimeout(() => animateNumber(testimonials.value, 10), 700);
};

onMounted(() => {
  const observer = new IntersectionObserver(
    (entries) => {
      if (entries[0].isIntersecting) {
        startAnimations();
        observer.disconnect();
      }
    },
    { threshold: 0.2 }
  );
  if (activeUsers.value) {
    observer.observe(activeUsers.value.parentElement.parentElement);
  }
});
</script>
