<script setup>
import { ref, onMounted, onUnmounted } from "vue";
import { Swiper, SwiperSlide } from "swiper/vue";
import { EffectFade, Autoplay } from "swiper/modules";
import "swiper/css";
import "swiper/css/effect-fade";

const { $gsap, $ScrollTrigger } = useNuxtApp();

onMounted(() => {
  $gsap.fromTo(
    ".dir-title",
    { opacity: 0, y: 50 },
    {
      opacity: 1,
      y: 0,
      duration: 1,
      ease: "power2.out",
      scrollTrigger: {
        trigger: ".dir-title",
        start: "top 80%",
        end: "bottom 20%",
        toggleActions: "play none none reverse",
      },
    }
  );

  $gsap.fromTo(
    ".dir-item.big__item",
    { opacity: 0, x: -100 },
    {
      opacity: 1,
      x: 0,
      duration: 1.2,
      ease: "power2.out",
      scrollTrigger: {
        trigger: ".dir-item.big__item",
        start: "top 80%",
        end: "bottom 20%",
        toggleActions: "play none none reverse",
      },
    }
  );

  $gsap.fromTo(
    ".right-side",
    { opacity: 0, x: 100 },
    {
      opacity: 1,
      x: 0,
      duration: 1.2,
      ease: "power2.out",
      scrollTrigger: {
        trigger: ".directions-block",
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
  <div class="directions-block">
    <div class="container">
      <h4 class="dir-title">Programs</h4>
      <div class="dir-grid">
        <div class="dir-item big__item">
          <h5 class="dir-name">Foundation Faculty</h5>
          <p class="dir-text">
            Our foundation faculty consists of highly qualified professionals
            dedicated to providing a strong academic base for our students.
          </p>
          <div class="item-list">
            <div class="list-item">
              <p class="list-name">Academic English Skills</p>
              <p class="list-desc">
                Development of academic reading, writing, listening and
                speaking; vocabulary building; debating and analytical thinking.
              </p>
            </div>
            <div class="list-item">
              <p class="list-name">Business & Management Foundations</p>
              <p class="list-desc">
                Introduction to business processes, corporate governance,
                problem-solving and decision-making through theory and case
                studies.
              </p>
            </div>
            <div class="list-item">
              <p class="list-name">Mathematics & Applied Statistics</p>
              <p class="list-desc">
                Microsoft Office, basic programming (HTML/CSS), web design
                concepts and cybersecurity essentials.
              </p>
            </div>
            <div class="list-item">
              <p class="list-name">Global & Social Studies</p>
              <p class="list-desc">
                Key issues in global development, sustainability, economic
                change and social transformation in Central Asia and beyond.
              </p>
            </div>
          </div>
        </div>
        <div class="right-side">
          <Swiper
            :modules="[Autoplay]"
            :autoplay="{ delay: 5000 }"
            :speed="1000"
            :loop="true"
            :direction="'vertical'"
            :space-between="24"
          >
            <SwiperSlide>
              <div class="right-item">
                <h4 class="right-name">BSc in Accounting and Finance</h4>

                <div class="right-content">
                  <div class="flexer">
                    <p class="right-txt">
                      BSc (Hons) in Accounting and Finance at BMU, validated by
                      QMU: ACCA-aligned, preparing graduates for global careers
                      in accounting and finance
                    </p>
                    <p class="bachelors">
                      <img src="/img/star.svg" alt="" />
                      Bachelor’s Degree
                    </p>
                  </div>
                  <div class="right-icon">
                    <img src="/img/dir-1.webp" alt="" />
                  </div>
                </div>
              </div>
              <div class="right-item">
                <h4 class="right-name">
                  BSc in Management Information Systems
                </h4>
                <div class="right-content">
                  <div class="flexer">
                    <p class="right-txt">
                      BSc (Hons) in Management Information Systems at BMU,
                      validated by QMU: blending business and IT skills for
                      dynamic careers
                    </p>
                    <p class="bachelors">
                      <img src="/img/star.svg" alt="" />
                      Bachelor’s Degree
                    </p>
                  </div>
                  <div class="right-icon">
                    <img src="/img/dir-2.webp" alt="" />
                  </div>
                </div>
              </div>
            </SwiperSlide>
            <SwiperSlide>
              <div class="right-item">
                <h4 class="right-name">BSc in Banking and Finance</h4>

                <div class="right-content">
                  <div class="flexer">
                    <p class="right-txt">
                      BSc (Hons) in Banking and Finance at BMU, validated by
                      QMU: CFA-aligned, preparing graduates for global careers
                      in banking and finance
                    </p>
                    <p class="bachelors">
                      <img src="/img/star.svg" alt="" />
                      Bachelor’s Degree
                    </p>
                  </div>
                  <div class="right-icon">
                    <img src="/img/dir-3.webp" alt="" />
                  </div>
                </div>
              </div>
              <div class="right-item">
                <h4 class="right-name">BBA with Project Management</h4>

                <div class="right-content">
                  <div class="flexer">
                    <p class="right-txt">
                      BBA with PM: international degree combining business
                      fundamentals and project management skills for careers
                      across private and public sectors
                    </p>
                    <p class="bachelors">
                      <img src="/img/star.svg" alt="" />
                      Bachelor’s Degree
                    </p>
                  </div>
                  <div class="right-icon">
                    <img src="/img/dir-4.webp" alt="" />
                  </div>
                </div>
              </div>
            </SwiperSlide>
            <SwiperSlide>
              <div class="right-item">
                <h4 class="right-name">
                  BBA with Digital Marketing and e-Business
                </h4>
                <div class="right-content">
                  <div class="flexer">
                    <p class="right-txt">
                      BBA Digital Marketing & E-Business: international degree
                      combining business fundamentals with digital and
                      e-business skills for careers
                    </p>
                    <p class="bachelors">
                      <img src="/img/star.svg" alt="" />
                      Bachelor’s Degree
                    </p>
                  </div>
                  <div class="right-icon">
                    <img src="/img/dir-5.webp" alt="" />
                  </div>
                </div>
              </div>
              <div class="right-item">
                <h4 class="right-name">
                  BBA with Logistics and Supply Chain Management
                </h4>
                <div class="right-content">
                  <div class="flexer">
                    <p class="right-txt">
                      BBA Logistics & Supply Chain: international degree merging
                      business fundamentals with logistics and supply chain
                      expertise for careers
                    </p>
                    <p class="bachelors">
                      <img src="/img/star.svg" alt="" />
                      Bachelor’s Degree
                    </p>
                  </div>
                  <div class="right-icon">
                    <img src="/img/dir-6.webp" alt="" />
                  </div>
                </div>
              </div>
            </SwiperSlide>
            <SwiperSlide>
              <div class="right-item">
                <h4 class="right-name">
                  BBA with Economics and Sustainable Development
                </h4>
                <div class="right-content">
                  <div class="flexer">
                    <p class="right-txt">
                      BBA Economics & Sustainable Development: international
                      degree combining business fundamentals with economics and
                      sustainability expertise for dynamic careers
                    </p>
                    <p class="bachelors">
                      <img src="/img/star.svg" alt="" />
                      Bachelor’s Degree
                    </p>
                  </div>
                  <div class="right-icon">
                    <img src="/img/dir-7.webp" alt="" />
                  </div>
                </div>
              </div>
              <div class="right-item">
                <h4 class="right-name">
                  BBA with Communication and Public Relations
                </h4>
                <div class="right-content">
                  <div class="flexer">
                    <p class="right-txt">
                      BBA Communication & Public Relations: international degree
                      combining business fundamentals with communication and PR
                      expertise for dynamic careers
                    </p>
                    <p class="bachelors">
                      <img src="/img/star.svg" alt="" />
                      Bachelor’s Degree
                    </p>
                  </div>
                  <div class="right-icon">
                    <img src="/img/dir-8.webp" alt="" />
                  </div>
                </div>
              </div>
            </SwiperSlide>
          </Swiper>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.directions-block {
  padding: 60px 0;
  background-color: #f9f9f9;
}
.dir-title {
  font-size: 36px;
  font-weight: 700;
  margin-bottom: 40px;
  color: var(--blue);
}
.dir-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 30px;
}
.dir-item.big__item {
  background-color: var(--blue);
  padding: 32px;
  border-radius: 16px;
  -webkit-box-shadow: 0px 0px 54px -25px var(--blue);
  -moz-box-shadow: 0px 0px 54px -25px var(--blue);
  box-shadow: 0px 0px 54px -25px var(--blue);
}
.dir-item {
  background-color: #e0e0e0;
  border-radius: 16px;
}
.dir-name {
  font-size: 24px;
  font-weight: 600;
  color: #fff;
  margin-bottom: 24px;
}
.dir-text {
  font-size: 16px;
  line-height: 24px;
  color: #e0e0e0;
  margin-bottom: 32px;
}
.item-list {
  background: white;
  padding: 24px;
  border-radius: 12px;
}
.list-item {
  margin-bottom: 20px;
}
.list-item:last-child {
  margin-bottom: 0;
}
.list-name {
  font-size: 20px;
  font-weight: 600;
  color: var(--blue);
  margin-bottom: 8px;
}
.list-desc {
  font-size: 14px;
  line-height: 20px;
  color: #555;
  max-width: 90%;
  position: relative;
  padding-left: 48px;
}
.list-desc::after {
  content: "";
  position: absolute;
  top: 10px;
  left: 0;
  width: 32px;
  height: 4px;
  background-color: var(--blue);
}
.right-side {
  min-width: 0;
}
.swiper {
  height: 572px;
  border-radius: 16px;
}
.swiper-slide {
  display: flex;
  flex-direction: column;
  gap: 24px;
}
.right-item {
  height: 100%;
  background: white;
  border-radius: 16px;
  align-items: center;
  padding: 24px;
}
.right-content {
  display: grid;
  grid-template-columns: 1fr 300px;
  gap: 24px;
  height: calc(100% - 48px);
}
.right-name {
  font-size: 24px;
  font-weight: 600;
  color: var(--blue);
  margin-bottom: 24px;
}
.right-txt {
  font-size: 16px;
  line-height: 24px;
  color: #555;
}
.right-icon {
  width: 100%;
  height: 178px;
  border-radius: 12px;
  overflow: hidden;
}
.right-icon img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
.flexer {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
.bachelors {
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 16px;
  font-weight: 500;
  color: var(--blue);
  margin-top: 16px;
}
@media (max-width: 768px) {
  .directions-block {
    padding: 40px 0;
  }
  .dir-title {
    font-size: 28px;
    margin-bottom: 30px;
  }
  .dir-grid {
    grid-template-columns: 1fr;
    gap: 20px;
  }
  .dir-item.big__item {
    padding: 24px;
  }
  .dir-name {
    font-size: 20px;
    margin-bottom: 20px;
  }
  .dir-text {
    font-size: 14px;
    line-height: 20px;
    margin-bottom: 24px;
  }
  .item-list {
    padding: 20px;
  }
  .list-name {
    font-size: 18px;
  }
  .list-desc {
    font-size: 13px;
    line-height: 18px;
    padding-left: 40px;
  }
  .list-desc::after {
    width: 28px;
    height: 3px;
  }
  .right-side {
    order: -1; /* Переместить наверх на мобильных */
  }
  .swiper {
    height: 400px;
  }
  .right-item {
    padding: 20px;
  }
  .right-content {
    grid-template-columns: 1fr;
    gap: 16px;
    height: auto;
  }
  .right-name {
    font-size: 20px;
    margin-bottom: 16px;
  }
  .right-txt {
    font-size: 14px;
    line-height: 20px;
  }
  .right-icon {
    height: 150px;
  }
}
</style>
