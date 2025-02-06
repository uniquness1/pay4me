<template>
  <section>
    <section class="py-12 md:py-[108px] bg-white w-full">
      <div
        class="max-w-6xl mx-auto px-4 flex flex-col gap-5 items-center justify-center"
      >
        <h2
          class="text-3xl md:text-[38.88px] font-bold text-[#12141D] leading-tight md:leading-[47.52px] text-center"
        >
          Trusted by Partners
        </h2>
        <p
          class="max-w-[355px] mx-auto text-center text-base md:text-[19.44px] font-normal text-[#12141D]"
        >
          Partners in growth, leaders in innovation. Driving success, we achieve
          more.
        </p>
      </div>

      <div
        class="max-w-6xl mx-auto w-full flex flex-wrap justify-center mt-8 md:mt-[57.28px] px-4"
      >
        <div
          v-for="partner in partners.slice(0, 5)"
          :key="partner.id"
          class="flex justify-center"
        >
          <img
            class="max-w-[200px] h-auto object-contain"
            :src="partner.src"
            :alt="partner.alt"
          />
        </div>
        <div class="hidden md:flex w-full justify-center"></div>
        <div class="mb-[246.6px] flex flex-wrap justify-center">
          <div
            v-for="partner in partners.slice(5)"
            :key="partner.id"
            class="flex items-center justify-center"
          >
            <img
              class="max-w-[200px] h-auto object-contain"
              :src="partner.src"
              :alt="partner.alt"
            />
          </div>
        </div>
      </div>
    </section>

    <div class="relative w-full bg-[#EBFFF2]">
      <div
        class="bg-[#03D44A] w-full max-w-7xl mx-auto py-[64.04px] absolute top-[-200px] left-1/2 transform -translate-x-1/2 md:rounded-[10.8px] overflow-hidden"
      >
        <h2
          class="text-3xl md:text-[38.88px] track-[-1.08px] font-bold text-white leading-tight md:leading-[47.52px] text-center"
        >
          Scan QR Code to Download
        </h2>
        <p
          class="max-w-[400px] mx-auto text-center text-base md:text-[19.44px] leading-[30.24px] my-4 font-normal text-white"
        >
          Our custom QR code will take you to your app store to download our
          awesome native apps
        </p>
        <div
          class="max-w-max mx-auto mt-4 bg-white p-3 pl-4 md:pl-10 flex gap-14 items-center justify-between"
        >
          <div>
            <h2 class="text-[#000000] text-base sm:text-xl font-normal">
              View on mobile.
            </h2>
            <h2 class="text-[#000000] text-3xl sm:text-4xl font-medium">
              Scan the <br />
              QR code
            </h2>
          </div>
          <img
            src="../assets/images/qr code.png"
            alt=""
            class="w-[151px] h-[151px]"
          />
        </div>

        <img
          src="../assets/images/phone.png"
          alt=""
          class="hidden md:block absolute bottom-0 right-0 w-[365px] h-[365px] object-contain"
        />
      </div>

      <footer class="pb-[104px] pt-[150px] w-full px-4">
        <div
          class="max-w-7xl mx-auto w-full grid grid-cols-1 sm:grid-cols-2 md:grid-cols-4 lg:grid-cols-[1fr_1fr_1fr_1fr_1.5fr] gap-8 md:gap-16 pt-[120px] md:pt-[160px]"
        >
          <div>
            <div class="flex justify-center md:justify-start">
              <img
                src="../assets/images/pay4me.png"
                alt="Pay4Me Logo"
                class="w-[190px] h-[47.29px]"
              />
            </div>
            <p
              class="mt-8 md:mt-[280px] text-lg font-light pb-2 border-b text-center md:text-start"
            >
              support@pay4me.app
            </p>
          </div>

          <div class="text-center md:text-left">
            <ul class="space-y-5">
              <li class="text-base font-medium md:font-normal text-black mb-6">
                Company
              </li>
              <li class="text-sm font-normal text-black">Home</li>
              <li class="text-sm font-normal text-black">About us</li>
              <li class="text-sm font-normal text-black">Blog</li>
              <li class="text-sm font-normal text-black">Careers</li>
            </ul>
          </div>

          <div class="text-center md:text-left">
            <p
              class="md:hidden my-8 md:mt-[180px] text-lg font-light pb-2 border-b"
            >
              (123) 456-7890
            </p>
            <ul class="space-y-5">
              <li class="text-base font-medium md:font-normal text-black mb-6">
                Support
              </li>
              <li class="text-sm font-normal text-black">FAQ'S</li>
              <li class="text-sm font-normal text-black">Live Support</li>
              <li class="text-sm font-normal text-black">Contact us</li>
            </ul>
            <p
              class="hidden md:block mt-8 md:mt-[215px] text-lg font-light pb-2 border-b"
            >
              (123) 456-7890
            </p>
          </div>

          <div class="text-center md:text-left">
            <ul class="space-y-5">
              <li class="text-base font-medium md:font-normal text-black mb-6">
                Legals
              </li>
              <li class="text-sm font-normal text-black">Terms of Service</li>
              <li class="text-sm font-normal text-black">Privacy Policy</li>
              <li class="text-sm font-normal text-black">KYC/AML Policy</li>
            </ul>
          </div>

          <div class="text-center md:text-left">
            <h2 class="text-base font-medium md:font-normal text-black mb-6">
              Head Office
            </h2>
            <p class="text-sm font-normal text-black">
              USA - 500 S 8th St, Boise, ID 83702
            </p>
            <p class="text-sm font-normal text-black">
              Nigeria - 5th Floor, Brassars' Place, 69 Admiralty Way,<br
                class="md:hidden"
              />
              Lekki Phase 1, Lagos.
            </p>

            <div class="mt-8 md:mt-[61px]">
              <h2 class="text-base font-normal text-black mb-6">Newsletter</h2>
              <div
                class="border-b-black border-b flex items-center justify-between pb-2"
              >
                <input
                  type="email"
                  name=""
                  id=""
                  placeholder="Enter your Email address"
                  class="w-full md:w-auto"
                />
                <Mail class="w-5 h-5 text-black" />
              </div>
            </div>

            <div class="mt-8 md:mt-[70px]">
              <p class="text-xs font-normal text-black">
                © 2024 Pay4Me. All rights reserved.
              </p>
              <div
                class="flex items-center justify-center md:justify-start gap-4 mt-[17px]"
              >
                <a href="#" aria-label="Facebook">
                  <Facebook
                    class="w-5 h-5 text-black hover:text-blue-600 transition"
                  />
                </a>
                <a href="#" aria-label="Twitter">
                  <Twitter
                    class="w-5 h-5 text-black hover:text-blue-400 transition"
                  />
                </a>
                <a href="#" aria-label="Instagram">
                  <Instagram
                    class="w-5 h-5 text-black hover:text-pink-500 transition"
                  />
                </a>
              </div>
            </div>
          </div>
        </div>
      </footer>
    </div>
  </section>
</template>

<script setup>
import img1 from "../assets/images/1 1.png";
import img2 from "../assets/images/2 1.png";
import img3 from "../assets/images/3 1.png";
import img4 from "../assets/images/4 1.png";
import img5 from "../assets/images/5 1.png";
import img6 from "../assets/images/6 1.png";
import img7 from "../assets/images/7 1.png";
import img8 from "../assets/images/8 1.png";
import { Mail, Facebook, Twitter, Instagram } from "lucide-vue-next";

const partners = [
  { id: 1, src: img1, alt: "Partner 1" },
  { id: 2, src: img2, alt: "Partner 2" },
  { id: 3, src: img3, alt: "Partner 3" },
  { id: 4, src: img4, alt: "Partner 4" },
  { id: 5, src: img5, alt: "Partner 5" },
  { id: 6, src: img6, alt: "Partner 6" },
  { id: 7, src: img7, alt: "Partner 7" },
  { id: 8, src: img8, alt: "Partner 8" },
];
</script>
