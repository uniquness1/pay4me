<template>
  <section
    class="bg-[#EBFFF2] py-12 sm:py-16 lg:py-[106px] flex flex-col items-center px-4"
  >
    <h2
      class="text-2xl sm:text-3xl lg:text-4xl font-bold text-center mb-8 lg:mb-[72.4px]"
    >
      What Our Happy <br />
      <span class="relative inline-block">
        Users Say
        <span
          class="absolute inset-x-0 bottom-0 h-2 bg-yellow-300 -z-10"
        ></span>
      </span>
    </h2>

    <div class="relative w-full max-w-5xl overflow-hidden">
      <div
        class="flex transition-transform duration-500 ease-in-out"
        :style="{ transform: `translateX(-${currentSlide * 100}%)` }"
      >
        <div
          v-if="isMobile"
          v-for="(testimonial, index) in testimonials"
          :key="`mobile-${index}`"
          class="w-full flex-shrink-0 px-4"
        >
          <div
            class="bg-white text-center rounded-[10.8px] px-4 sm:px-6 pt-[30px] sm:pt-[50px] pb-6 sm:pb-9"
          >
            <img
              :src="testimonial.image"
              alt="User"
              class="w-12 h-12 sm:w-16 sm:h-16 rounded-full mx-auto mb-3"
            />
            <p
              class="text-sm sm:text-base font-normal text-[#12141D] text-center"
            >
              {{ testimonial.text }}
            </p>
            <h4 class="mt-3 font-bold">{{ testimonial.name }}</h4>
            <span class="text-xs text-gray-500">{{ testimonial.role }}</span>
          </div>
        </div>
        <div
          v-else
          v-for="(group, index) in slideGroups"
          :key="`desktop-${index}`"
          class="flex gap-4 lg:gap-[66px] w-full flex-shrink-0"
        >
          <div
            v-for="(testimonial, i) in group"
            :key="i"
            class="bg-white text-center rounded-[10.8px] px-4 sm:px-6 pt-[30px] sm:pt-[50px] pb-6 sm:pb-9 w-1/3"
          >
            <img
              :src="testimonial.image"
              alt="User"
              class="w-12 h-12 sm:w-16 sm:h-16 rounded-full mx-auto mb-3"
            />
            <p
              class="text-sm sm:text-base font-normal text-[#12141D] text-center"
            >
              {{ testimonial.text }}
            </p>
            <h4 class="mt-3 font-bold">{{ testimonial.name }}</h4>
            <span class="text-xs text-gray-500">{{ testimonial.role }}</span>
          </div>
        </div>
      </div>
    </div>

    <div class="flex space-x-2 mt-6 sm:mt-8">
      <button
        v-for="index in isMobile ? testimonials.length : slideGroups.length"
        :key="index"
        @click="currentSlide = index - 1"
        class="w-2 h-2 sm:w-3 sm:h-3 rounded-full transition-colors duration-300"
        :class="index - 1 === currentSlide ? 'bg-black' : 'bg-gray-300'"
      ></button>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      currentSlide: 0,
      testimonials: [
        {
          name: "Jenny Wilson",
          role: "Immigrant",
          text: "“I just simply love tools that make my life easier! I have everything that I need in one place, and that allows my tuition payments to be more organized.”",
          image: "https://randomuser.me/api/portraits/women/1.jpg",
        },
        {
          name: "Jesse Yusuf",
          role: "Student",
          text: "The way this app is designed and scoped is absolutely awesome! It surpasses all competition in its efforts to satisfy every need and desire!",
          image: "https://randomuser.me/api/portraits/men/1.jpg",
        },
        {
          name: "Emma Kristin",
          role: "Student",
          text: "“Very easy to use and set up is simple. I can easily provide live support to my website visitors in real-time. It also provides many integrations.”",
          image: "https://randomuser.me/api/portraits/women/2.jpg",
        },
        {
          name: "Michael Lee",
          role: "Entrepreneur",
          text: "The way this app is designed and scoped is absolutely awesome! It surpasses all competition in its efforts to satisfy every need and desire!",
          image: "https://randomuser.me/api/portraits/men/2.jpg",
        },
        {
          name: "Sophia Gomez",
          role: "Freelancer",
          text: "“Very easy to use and set up is simple. I can easily provide live support to my website visitors in real-time. It also provides many integrations.”!",
          image: "https://randomuser.me/api/portraits/women/3.jpg",
        },
        {
          name: "John Doe",
          role: "Developer",
          text: "The way this app is designed and scoped is absolutely awesome! It surpasses all competition in its efforts to satisfy every need and desire!",
          image: "https://randomuser.me/api/portraits/men/3.jpg",
        },
        {
          name: "Michael Lee",
          role: "Entrepreneur",
          text: "The way this app is designed and scoped is absolutely awesome! It surpasses all competition in its efforts to satisfy every need and desire!",
          image: "https://randomuser.me/api/portraits/men/2.jpg",
        },
        {
          name: "Sophia Gomez",
          role: "Freelancer",
          text: "“Very easy to use and set up is simple. I can easily provide live support to my website visitors in real-time. It also provides many integrations.”!",
          image: "https://randomuser.me/api/portraits/women/3.jpg",
        },
        {
          name: "John Doe",
          role: "Developer",
          text: "The way this app is designed and scoped is absolutely awesome! It surpasses all competition in its efforts to satisfy every need and desire!",
          image: "https://randomuser.me/api/portraits/men/3.jpg",
        },
      ],
      interval: null,
      windowWidth: window.innerWidth,
    };
  },
  computed: {
    isMobile() {
      return this.windowWidth < 768;
    },
    slideGroups() {
      return this.testimonials.reduce((result, item, index) => {
        const chunkIndex = Math.floor(index / 3);
        if (!result[chunkIndex]) result[chunkIndex] = [];
        result[chunkIndex].push(item);
        return result;
      }, []);
    },
  },
  methods: {
    handleResize() {
      this.windowWidth = window.innerWidth;
      this.currentSlide = 0;
    },
    startAutoplay() {
      this.interval = setInterval(() => {
        const maxSlides = this.isMobile
          ? this.testimonials.length
          : this.slideGroups.length;
        this.currentSlide = (this.currentSlide + 1) % maxSlides;
      }, 6000);
    },
  },
  mounted() {
    window.addEventListener("resize", this.handleResize);
    this.startAutoplay();
  },
  beforeDestroy() {
    window.removeEventListener("resize", this.handleResize);
    clearInterval(this.interval);
  },
  watch: {
    isMobile() {
      clearInterval(this.interval);
      this.startAutoplay();
    },
  },
};
</script>
