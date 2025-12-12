<script setup>
import { ref, onMounted, onUnmounted } from "vue";
import { Swiper, SwiperSlide } from "swiper/vue";
import { EffectFade, Autoplay } from "swiper/modules";
import "swiper/css";
import "swiper/css/effect-fade";

const { $gsap, $ScrollTrigger } = useNuxtApp();

const activeSwiper = ref("first");
const intervalId = ref(null);

const slides = {
  first: ["/img/adv-1-1.jpg", "/img/adv-1-2.jpg"],
  second: ["/img/adv-2-1.jpg", "/img/adv-2-2.jpg"],
  third: ["/img/adv-3-1.jpg", "/img/adv-3-2.jpg"],
  fourth: ["/img/adv-4-1.jpg", "/img/adv-4-2.jpg"],
  fifth: ["/img/adv-5-1.jpg", "/img/adv-5-2.jpg"],
  sixth: ["/img/adv-6-1.jpg", "/img/adv-6-2.jpg"],
};

const swiperKeys = Object.keys(slides);
let currentIndex = 0;

onMounted(() => {
  intervalId.value = setInterval(() => {
    currentIndex = (currentIndex + 1) % swiperKeys.length;
    activeSwiper.value = swiperKeys[currentIndex];
  }, 5000);

  $gsap.fromTo(
    ".adv-button",
    {
      y: 50,
      opacity: 0,
    },
    {
      y: 0,
      opacity: 1,
      duration: 0.2,
      ease: "power2.out",
      scrollTrigger: {
        trigger: ".advantages-block",
        start: "top 80%",
        toggleActions: "play none none reverse",
      },
    }
  );

  $gsap.to(".star-1", {
    scrollTrigger: {
      trigger: ".advantages-block",
      start: "top 80%",
      toggleActions: "play none none reverse",
    },
    rotation: 360,
    duration: 0.5,
    ease: "power2.out",
  });

  $gsap.to(".star-2", {
    scrollTrigger: {
      trigger: ".advantages-block",
      start: "top 70%",
      toggleActions: "play none none reverse",
    },
    rotation: -360,
    duration: 1,
    ease: "power2.out",
  });

  $gsap.to(".star-3", {
    scrollTrigger: {
      trigger: ".advantages-block",
      start: "top 60%",
      toggleActions: "play none none reverse",
    },
    rotation: 180,
    duration: 1.5,
    ease: "power2.out",
  });

  $gsap.to(".star-4", {
    scrollTrigger: {
      trigger: ".advantages-block",
      start: "top 50%",
      toggleActions: "play none none reverse",
    },
    rotation: -180,
    duration: 2,
    ease: "power2.out",
  });
});

onUnmounted(() => {
  if (intervalId.value) {
    clearInterval(intervalId.value);
  }
});
</script>

<template>
  <div class="advantages-block">
    <img src="/img/star.svg" alt="" class="star-1" />
    <img src="/img/star.svg" alt="" class="star-2" />
    <img src="/img/star.svg" alt="" class="star-3" />
    <img src="/img/star.svg" alt="" class="star-4" />

    <div class="container">
      <h4 class="adv-title">Why choose BMU?</h4>
      <div class="adv-grid">
        <div class="adv-left">
          <div class="adv-row">
            <div
              class="adv-button first-button"
              :class="{ active: activeSwiper === 'first' }"
              @mouseenter="activeSwiper = 'first'"
            >
              <div class="button-top">
                <p class="button-name">Double Degree</p>
                <div class="button-arrow">
                  <Icon name="lucide:arrow-right" size="16" />
                </div>
              </div>
              <div class="button-bottom">
                <Icon name="lucide:graduation-cap" size="32" />
                <p class="button-desc">
                  Earn degrees from both BMU and the University of Reading
                </p>
              </div>
            </div>
            <div
              class="adv-button second-button"
              :class="{ active: activeSwiper === 'second' }"
              @mouseenter="activeSwiper = 'second'"
            >
              <div class="button-top">
                <p class="button-name">Modern Campus</p>
                <div class="button-arrow">
                  <Icon name="lucide:arrow-right" size="16" />
                </div>
              </div>
              <div class="button-bottom">
                <Icon name="lucide:building-2" size="32" />
                <p class="button-desc">
                  Our campus is equipped with modern facilities to support your
                  learning
                </p>
              </div>
            </div>
          </div>
          <div class="adv-row">
            <div
              class="adv-button third-button"
              :class="{ active: activeSwiper === 'third' }"
              @mouseenter="activeSwiper = 'third'"
            >
              <div class="button-top">
                <p class="button-name">International Faculty</p>
                <div class="button-arrow">
                  <Icon name="lucide:arrow-right" size="16" />
                </div>
              </div>
              <div class="button-bottom">
                <Icon name="lucide:user" size="32" />
                <p class="button-desc">
                  Learn from international faculty members who bring global
                  perspectives
                </p>
              </div>
            </div>
            <div
              class="adv-button fourth-button"
              :class="{ active: activeSwiper === 'fourth' }"
              @mouseenter="activeSwiper = 'fourth'"
            >
              <div class="button-top">
                <p class="button-name">Student Life</p>
                <div class="button-arrow">
                  <Icon name="lucide:arrow-right" size="16" />
                </div>
              </div>
              <div class="button-bottom">
                <Icon name="lucide:user-star" size="32" />
                <p class="button-desc">
                  Join a vibrant student community with diverse clubs, events,
                  and activities
                </p>
              </div>
            </div>
          </div>
          <div class="adv-row">
            <div
              class="adv-button fifth-button"
              :class="{ active: activeSwiper === 'fifth' }"
              @mouseenter="activeSwiper = 'fifth'"
            >
              <div class="button-top">
                <p class="button-name">Sports and Wellness</p>
                <div class="button-arrow">
                  <Icon name="lucide:arrow-right" size="16" />
                </div>
              </div>
              <div class="button-bottom">
                <Icon name="lucide:dumbbell" size="32" />
                <p class="button-desc">
                  Stay active and healthy with our state-of-the-art sports and
                  wellness facilities
                </p>
              </div>
            </div>
            <div
              class="adv-button sixth-button"
              :class="{ active: activeSwiper === 'sixth' }"
              @mouseenter="activeSwiper = 'sixth'"
            >
              <div class="button-top">
                <p class="button-name">Career Support</p>
                <div class="button-arrow">
                  <Icon name="lucide:arrow-right" size="16" />
                </div>
              </div>
              <div class="button-bottom">
                <Icon name="lucide:briefcase" size="32" />
                <p class="button-desc">
                  Receive personalized career support and guidance to help you
                  achieve goals
                </p>
              </div>
            </div>
          </div>
        </div>
        <div class="adv-right">
          <Swiper
            :key="activeSwiper"
            :slides-per-view="1"
            :loop="true"
            :autoplay="{ delay: 1500, disableOnInteraction: false }"
            :modules="[EffectFade, Autoplay]"
            effect="fade"
            class="mySwiper"
          >
            >
            <SwiperSlide v-for="src in slides[activeSwiper]" :key="src">
              <img :src="src" alt="" />
            </SwiperSlide>
          </Swiper>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.advantages-block {
  padding: 80px 0;
  background-color: #f9f9f9;
  transition: 0.3s;
  position: relative;
}
.adv-title {
  font-size: 36px;
  font-weight: 700;
  margin-bottom: 40px;
  color: var(--blue);
}
.adv-grid {
  display: grid;
  grid-template-columns: 6fr 4fr;
  gap: 24px;
  min-width: 0;
}
.adv-row {
  display: flex;
  gap: 4px;
  margin-bottom: 4px;
}
.adv-button {
  background-color: #ffffff;
  border-radius: 16px;
  padding: 24px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  cursor: pointer;
  transition: transform 0.2s;
  position: relative;
  overflow: hidden;
  width: calc(50% - 4px);
  transition: all 0.5s, background 0.2s;
}
.adv-button.active {
  width: calc(60% - 4px);
  background: var(--blue);
}
.button-top {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 16px;
}
.button-name {
  font-size: 22px;
  font-weight: 600;
  color: #333333;
  transition: color 0.2s;
}
.adv-button.active .button-name {
  color: #ffffff;
}
.button-desc {
  font-size: 16px;
  line-height: 24px;
  color: #ffffff;
  margin-top: 8px;
  width: 300px;
  text-align: right;
  opacity: 0;
  visibility: hidden;
  transition: opacity 0.1s, visibility 0.3s;
}
.adv-button.active .button-desc {
  opacity: 1;
  visibility: visible;
  transition-delay: 0.2s;
}
.button-bottom {
  display: flex;
  align-items: center;
  justify-content: flex-end;
  height: 64px;
}
.button-bottom span {
  position: absolute;
  bottom: -32px;
  left: 32px;
  width: 132px;
  height: 132px;
  color: white;
  opacity: 0.1;
}
.button-arrow {
  background: var(--blue);
  width: 32px;
  height: 32px;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 8px;
  transition: background 0.2s;
}
.adv-button.active .button-arrow {
  background: #ffffff;
}
.button-arrow span {
  color: #ffffff;
  transition: 0.5s;
}
.adv-button.active .button-arrow span {
  color: var(--blue);
  transform: rotate(-45deg);
}
.adv-right {
  min-width: 0;
  height: 490px;
}
.adv-right .swiper {
  border-radius: 16px;
  overflow: hidden;
  width: 100%;
  height: 100%;
}
.adv-right img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.star-1 {
  position: absolute;
  top: 30%;
  left: 5%;
  width: 32px;
  height: 32px;
  z-index: 0;
  transform: rotate(-10deg);
}
.star-2 {
  position: absolute;
  top: 12%;
  right: 30%;
  width: 32px;
  height: 32px;
  z-index: 0;
  transform: rotate(-10deg);
}
.star-3 {
  position: absolute;
  top: 90%;
  left: 15%;
  width: 40px;
  height: 40px;
  z-index: 0;
  transform: rotate(10deg);
}
.star-4 {
  position: absolute;
  bottom: 20%;
  right: 10%;
  width: 24px;
  height: 24px;
  z-index: 0;
  transform: rotate(10deg);
}

@media (max-width: 1024px) {
  .adv-title {
    font-size: 32px;
  }
  .adv-grid {
    grid-template-columns: 1fr 1fr;
    gap: 20px;
  }
  .adv-button {
    padding: 20px;
  }
  .button-name {
    font-size: 20px;
  }
  .adv-right {
    height: 400px;
  }
  .star-1,
  .star-2,
  .star-3,
  .star-4 {
    width: 24px;
    height: 24px;
  }
}

@media (max-width: 768px) {
  .advantages-block {
    padding: 60px 0;
  }
  .adv-title {
    font-size: 28px;
    margin-bottom: 30px;
  }
  .adv-grid {
    grid-template-columns: 1fr;
    gap: 16px;
  }
  .adv-row {
    flex-direction: column;
    gap: 8px;
    margin-bottom: 8px;
  }
  .adv-button {
    width: 100%;
    padding: 16px;
  }
  .adv-button.active {
    width: 100%;
  }
  .button-name {
    font-size: 18px;
  }
  .button-desc {
    width: 100%;
    text-align: left;
  }
  .adv-right {
    height: 300px;
  }
  .star-1,
  .star-2,
  .star-3,
  .star-4 {
    display: none;
  }
}
</style>
