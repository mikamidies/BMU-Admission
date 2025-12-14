<script setup>
import { ref, onMounted, onUnmounted } from "vue";
import { Swiper, SwiperSlide } from "swiper/vue";
import { EffectFade, Autoplay } from "swiper/modules";
import "swiper/css";
import "swiper/css/effect-fade";

const { $gsap, $ScrollTrigger } = useNuxtApp();

const persons = [
  {
    name: "Yuri Loktionov, Ph.D., CFA",
    title: "MIT, USA",
    imgSrc: "/img/team/team-1.png",
  },
  {
    name: "Lionel Henderson, DBA",
    title: "Athabasca University, Canada",
    imgSrc: "/img/team/team-2.png",
  },
  {
    name: "Montu Saxena, Ph.D.",
    title: "University of Cambridge, U.K.",
    imgSrc: "/img/team/team-3.png",
  },
  {
    name: "Simon Pawley",
    title: "University College London, U.K.",
    imgSrc: "/img/team/team-4.png",
  },
  {
    name: "Christian Capone, PMP",
    title: "PM Institute, USA",
    imgSrc: "/img/team/team-5.png",
  },
  {
    name: "Estela Eaton",
    title: "University of Warwick, U.K.",
    imgSrc: "/img/team/team-6.png",
  },
  {
    name: "Joel Bryant, J.D.",
    title: "Purdue Global Law School, USA",
    imgSrc: "/img/team/team-7.png",
  },
  {
    name: "Kenneth Myers",
    title: "University of Texas, USA",
    imgSrc: "/img/team/team-8.png",
  },
  {
    name: "John Jinkner, DBA.",
    title: "Jacksonville University, USA",
    imgSrc: "/img/team/team-9.png",
  },
  {
    name: "David Collett",
    title: "Sheffield Hallam University, UK.",
    imgSrc: "/img/team/team-10.png",
  },
  {
    name: "Mike Jackson",
    title: "University of Sunderland, U.K.",
    imgSrc: "/img/team/team-11.png",
  },
  {},
  {},
  {},
];

onMounted(() => {
  $gsap.fromTo(
    ".section-title",
    { opacity: 0, y: 50 },
    {
      opacity: 1,
      y: 0,
      duration: 1,
      ease: "power2.out",
      scrollTrigger: {
        trigger: ".section-title",
        start: "top 80%",
        end: "bottom 20%",
        toggleActions: "play none none reverse",
      },
    }
  );

  $gsap.fromTo(
    ".faculty-card",
    { opacity: 0, y: 50, scale: 0.9 },
    {
      opacity: 1,
      y: 0,
      scale: 1,
      duration: 0.8,
      stagger: 0.1,
      ease: "back.out(1.7)",
      scrollTrigger: {
        trigger: ".faculty-block",
        start: "top 80%",
        end: "bottom 20%",
        toggleActions: "play none none reverse",
      },
    }
  );
});

onUnmounted(() => {
  $ScrollTrigger.getAll().forEach((trigger) => trigger.kill());
});
</script>

<template>
  <section class="faculty-block">
    <div class="container">
      <h4 class="section-title">Featured Faculty</h4>
      <Swiper
        :slides-per-view="1"
        :space-between="16"
        :loop="false"
        :autoplay="{ delay: 3000, disableOnInteraction: false }"
        :modules="[Autoplay]"
        :breakpoints="{
          640: {
            slidesPerView: 2,
            spaceBetween: 20,
          },
          768: {
            slidesPerView: 3,
            spaceBetween: 24,
          },
          1024: {
            slidesPerView: 4,
            spaceBetween: 32,
          },
        }"
        class="faculty-swiper"
      >
        <SwiperSlide
          class="faculty-slide"
          v-for="item in persons"
          :key="item.name"
        >
          <div class="faculty-card">
            <div class="card-img">
              <img :src="item.imgSrc" alt="" class="faculty-img" />
            </div>
            <div class="card-content">
              <h5 class="faculty-name">{{ item.name }}</h5>
              <p class="faculty-title">{{ item.title }}</p>
            </div>
          </div>
        </SwiperSlide>
      </Swiper>
    </div>
  </section>
</template>

<style scoped>
.faculty-block {
  padding: 80px 0;
  overflow: hidden;
}
.swiper {
  padding: 32px;
  overflow: visible;
}
.faculty-slide {
  height: 100%;
  padding: 0px;
}
.faculty-card {
  position: relative;
  height: 100%;
}
.faculty-card::after {
  content: "";
  position: absolute;
  top: 0px;
  left: 0px;
  width: 100%;
  height: 100%;
  background: #192b69;
  z-index: 1;
  border-radius: 20px;
  transition: 0.3s;
  opacity: 0;
}
.faculty-card::before {
  content: "";
  position: absolute;
  bottom: 0px;
  right: 0px;
  width: 100%;
  height: 100%;
  background: #e5e5e5;
  z-index: 2;
  border-radius: 20px;
  transition: 0.3s;
}
.card-img {
  position: relative;
  z-index: 2;
  width: 100%;
  height: 480px;
  overflow: hidden;
  border-radius: 20px;
  z-index: 3;
}
.faculty-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.3s ease;
}
.card-content {
  position: absolute;
  z-index: 3;
  bottom: 20px;
  left: 20px;
  right: 20px;
  top: auto;
  transition: 0.3s;
  opacity: 0;
  background: white;
  border-radius: 12px;
  padding: 16px;
}
.faculty-name {
  font-size: 20px;
  font-weight: 700;
  color: #000000;
  margin-bottom: 8px;
  white-space: nowrap;
}
.faculty-title {
  font-size: 16px;
  font-weight: 400;
  color: #555555;
  white-space: nowrap;
}
.swiper-slide:nth-child(12),
.swiper-slide:nth-child(13),
.swiper-slide:nth-child(14) {
  opacity: 0;
}
:deep(.swiper-slide-active) .faculty-card::after {
  transform: translate(-20px, -20px);
  opacity: 1;
  background: var(--blue);
}
:deep(.swiper-slide-active) .faculty-card::before {
  background: #6096ba;
}
:deep(.swiper-slide-active) .faculty-img {
  transform: scale(1.15);
}
:deep(.swiper-slide-active) .card-content {
  opacity: 1;
}

@media (max-width: 768px) {
  .faculty-block {
    padding: 60px 0;
  }
  .swiper {
    padding: 20px;
  }
  .card-img {
    height: 320px;
  }
  .card-content {
    padding: 12px;
    bottom: 16px;
    left: 16px;
    right: 16px;
  }
  .faculty-name {
    font-size: 16px;
    white-space: normal;
    margin-bottom: 4px;
  }
  .faculty-title {
    font-size: 14px;
    white-space: normal;
  }
}

@media (min-width: 769px) and (max-width: 1023px) {
  .card-img {
    height: 400px;
  }
  .faculty-name {
    font-size: 18px;
  }
  .faculty-title {
    font-size: 15px;
  }
}
</style>
