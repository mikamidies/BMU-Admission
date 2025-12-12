<script setup>
const { $gsap, $ScrollTrigger } = useNuxtApp();

onMounted(() => {
  $gsap.to(".porogram-img_1", {
    scrollTrigger: {
      trigger: ".program-section",
      start: "top bottom",
      end: "bottom top",
      scrub: 1,
    },
    y: -100,
    scale: 1.1,
    ease: "none",
  });

  $gsap.to(".porogram-img_2", {
    scrollTrigger: {
      trigger: ".program-section",
      start: "top bottom",
      end: "bottom top",
      scrub: 1,
    },
    y: -10,
    scale: 0.95,
    ease: "none",
  });

  $gsap.fromTo(
    ".logo",
    {
      y: 100,
      opacity: 0,
    },
    {
      scrollTrigger: {
        trigger: ".program-section",
        start: "top 80%",
        end: "top 50%",
        scrub: false,
        toggleActions: "restart none restart none",
      },
      y: 0,
      opacity: 1,
      duration: 1.5,
      ease: "bounce.out",
    }
  );

  const tl = $gsap.timeline({
    scrollTrigger: {
      trigger: ".program-right",
      start: "top 90%",
      toggleActions: "restart none restart none",
    },
  });

  tl.fromTo(
    ".program-item",
    {
      x: -50,
      opacity: 0,
      scale: 0.8,
    },
    {
      x: 0,
      opacity: 1,
      scale: 1,
      duration: 0.8,
      stagger: 0.2,
      ease: "back.out(1.7)",
    }
  );

  $gsap.fromTo(
    ".program-paragraph",
    {
      y: 50,
      opacity: 0,
    },
    {
      scrollTrigger: {
        trigger: ".program-right",
        start: "top 90%",
        toggleActions: "restart none restart none",
      },
      y: 0,
      opacity: 1,
      duration: 1,
      ease: "power2.out",
    }
  );

  $gsap.fromTo(
    ".program-desc",
    {
      y: 30,
      opacity: 0,
    },
    {
      scrollTrigger: {
        trigger: ".program-right",
        start: "top 80%",
        toggleActions: "restart none restart none",
      },
      y: 0,
      opacity: 1,
      duration: 1,
      delay: 0.3,
      ease: "power2.out",
    }
  );
});
</script>

<template>
  <section class="program-section">
    <div class="container">
      <div class="program-left">
        <img src="/img/photo-2.jpg" alt="" class="porogram-img_1" />
        <img src="/img/photo-1.jpg" alt="" class="porogram-img_2" />

        <div class="logo">
          <img src="/img/qm.png" alt="" />
        </div>
      </div>
      <div class="program-right">
        <h4 class="program-title">
          <Icon name="lucide:graduation-cap" size="20" />
          About the Program
        </h4>
        <h3 class="program-paragraph">
          An introduction to our <span> Foundation Program </span>
        </h3>

        <p class="program-desc">
          The BMU Foundation is a one-year English-medium programme developed
          with the University of Reading to build strong academic skills and
          provide a recognised pathway into bachelor’s studies at BMU and other
          international universities.
        </p>
        <div class="program-items">
          <div class="program-item item-1">
            <div class="program-logo">
              <Icon name="lucide:building-2" size="32" />
            </div>
            <p>Recognised with University of Reading</p>
          </div>
          <div class="program-item item-2">
            <div class="program-logo">
              <Icon name="lucide:speech" size="32" />
            </div>
            <p>Fully taught in English</p>
          </div>
          <div class="program-item item-3">
            <div class="program-logo">
              <Icon name="lucide:earth" size="32" />
            </div>
            <p>International progression options</p>
          </div>
          <div class="program-item item-4">
            <div class="program-logo">
              <Icon name="lucide:graduation-cap" size="32" />
            </div>
            <p>Direct pathway to BMU Bachelor’s</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.program-section {
  padding: 120px 0 160px 0;
}
.container {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 80px;
}
.program-left {
  position: relative;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
}
.porogram-img_1 {
  width: 100%;
  border-radius: 16px;
  height: 480px;
  object-fit: cover;
}
.porogram-img_2 {
  width: 100%;
  border-radius: 16px;
  height: 480px;
  object-fit: cover;
  transform: translate(-80px, 80px);
  border: 4px solid #ffffff;
}
.logo {
  position: absolute;
  bottom: -40px;
  right: 0;
  background: rgba(255, 255, 255, 0.6);
  border-radius: 24px;
  box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
  backdrop-filter: blur(5px);
  -webkit-backdrop-filter: blur(5px);
  border: 1px solid rgba(255, 255, 255, 0.3);
  padding: 24px;
}
.logo img {
  width: 280px;
  height: auto;
  object-fit: contain;
}
.program-title {
  display: flex;
  align-items: center;
  gap: 8px;
  font-size: 16px;
  font-weight: 600;
  color: var(--blue);
  margin-bottom: 16px;
}
.program-paragraph {
  font-size: 48px;
  line-height: 56px;
  font-weight: 700;
  margin-bottom: 24px;
}
.program-paragraph span {
  color: var(--blue);
}
.program-desc {
  font-size: 18px;
  line-height: 28px;
  color: #555555;
  margin-bottom: 40px;
}
.program-items {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 32px 40px;
}
.program-item {
  display: grid;
  align-items: center;
  grid-template-columns: 64px auto;
  gap: 16px;
}
.program-item p {
  font-size: 16px;
  line-height: 24px;
  font-weight: 500;
  color: #333333;
  max-width: 80%;
}
.program-logo {
  background: var(--blue);
  width: 64px;
  height: 64px;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 12px;
  color: #ffffff;
}

@media screen and (max-width: 1024px) {
  .container {
    grid-template-columns: 1fr;
    gap: 60px;
  }

  .program-section {
    padding: 60px 0 180px 0;
  }

  .program-left {
    order: 2;
  }

  .program-right {
    order: 1;
  }

  .program-paragraph {
    font-size: 40px;
    line-height: 48px;
  }

  .porogram-img_2 {
    transform: translate(-60px, 60px);
  }

  .logo {
    bottom: -30px;
  }

  .logo img {
    width: 220px;
  }
}

@media screen and (max-width: 768px) {
  .program-section {
    padding: 48px 0 140px 0;
  }

  .container {
    gap: 48px;
  }

  .program-paragraph {
    font-size: 32px;
    line-height: 40px;
    margin-bottom: 20px;
  }

  .program-desc {
    font-size: 16px;
    line-height: 26px;
    margin-bottom: 32px;
  }

  .program-items {
    grid-template-columns: 1fr;
    gap: 20px;
  }

  .program-item {
    grid-template-columns: 56px auto;
    gap: 12px;
  }

  .program-logo {
    width: 56px;
    height: 56px;
  }

  .program-item p {
    font-size: 15px;
    line-height: 22px;
    max-width: 100%;
  }

  .program-left {
    grid-template-columns: 1fr;
    gap: 20px;
  }

  .porogram-img_1 {
    height: 320px;
  }

  .porogram-img_2 {
    transform: translate(0, 0);
    height: 320px;
  }

  .logo {
    position: static;
    margin-top: 20px;
    padding: 20px;
  }

  .logo img {
    width: 180px;
  }
}

@media screen and (max-width: 480px) {
  .program-section {
    padding: 40px 0 100px 0;
  }

  .program-title {
    font-size: 14px;
    margin-bottom: 12px;
  }

  .program-paragraph {
    font-size: 26px;
    line-height: 34px;
  }

  .program-desc {
    font-size: 15px;
    line-height: 24px;
  }

  .program-items {
    gap: 16px;
  }

  .program-item {
    grid-template-columns: 48px auto;
    gap: 10px;
  }

  .program-logo {
    width: 48px;
    height: 48px;
  }

  .program-logo :deep(svg) {
    width: 24px;
    height: 24px;
  }

  .program-item p {
    font-size: 14px;
    line-height: 20px;
  }

  .porogram-img_1,
  .porogram-img_2 {
    height: 260px;
  }

  .logo {
    padding: 16px;
  }

  .logo img {
    width: 150px;
  }
}
</style>
