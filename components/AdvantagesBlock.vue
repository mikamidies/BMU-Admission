<script setup>
import { ref } from "vue";
import { Swiper, SwiperSlide } from "swiper/vue";
import { EffectFade, Autoplay } from "swiper/modules";
import "swiper/css";
import "swiper/css/effect-fade";

const activeSwiper = ref("first");

const slides = {
  first: ["/img/adv-1-1.jpg", "/img/adv-1-2.jpg"],
  second: ["/img/adv-2-1.jpg", "/img/adv-2-2.jpg"],
  third: ["/img/adv-3-1.jpg", "/img/adv-3-2.jpg"],
  fourth: ["/img/adv-4-1.jpg", "/img/adv-4-2.jpg"],
  fifth: ["/img/adv-5-1.jpg", "/img/adv-5-2.jpg"],
  sixth: ["/img/adv-6-1.jpg", "/img/adv-6-2.jpg"],
};
</script>

<template>
  <div class="advantages-block">
    <div class="container">
      <h4 class="adv-title">Why choose BMU?</h4>
      <div class="adv-grid">
        <div class="adv-left">
          <div class="adv-row">
            <div
              class="adv-button first-button"
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
  display: none;
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
.adv-button:hover {
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
.adv-button:hover .button-name {
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
.adv-button:hover .button-desc {
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
.adv-button:hover .button-arrow {
  background: #ffffff;
}
.button-arrow span {
  color: #ffffff;
  transition: 0.5s;
}
.adv-button:hover .button-arrow span {
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

/* Responsive styles */
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
  .adv-button:hover {
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
}
</style>
