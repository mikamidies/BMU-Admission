<script setup>
import { ref, onMounted, onUnmounted } from "vue";

const words = ["manager", "leader", "director", "CEO", "expert"];
const currentWordIndex = ref(0);
const displayedText = ref("");
const isDeleting = ref(false);
let typingTimeout = null;

const typeWriter = () => {
  const currentWord = words[currentWordIndex.value];
  const speed = isDeleting.value ? 50 : 100;

  if (!isDeleting.value) {
    if (displayedText.value.length < currentWord.length) {
      displayedText.value = currentWord.substring(
        0,
        displayedText.value.length + 1
      );
      typingTimeout = setTimeout(typeWriter, speed);
    } else {
      typingTimeout = setTimeout(() => {
        isDeleting.value = true;
        typeWriter();
      }, 2000);
    }
  } else {
    if (displayedText.value.length > 0) {
      displayedText.value = currentWord.substring(
        0,
        displayedText.value.length - 1
      );
      typingTimeout = setTimeout(typeWriter, speed);
    } else {
      isDeleting.value = false;
      currentWordIndex.value = (currentWordIndex.value + 1) % words.length;
      typingTimeout = setTimeout(typeWriter, 500);
    }
  }
};

onMounted(() => {
  typeWriter();
});

onUnmounted(() => {
  if (typingTimeout) {
    clearTimeout(typingTimeout);
  }
});
</script>

<template>
  <section class="hero">
    <img src="/img/bacteria.svg" alt="" class="bacteria" />
    <div class="container">
      <div class="hero-left">
        <h1 class="hero-title">
          Apply to BMU. Become a professional
          <span class="typing-text">{{ displayedText }}</span>
        </h1>
        <p class="hero-subtitle">
          Short bachelor's and master's degree programs, practice-oriented
          courses and support for international students. Apply now and start
          building a profession tomorrow.
        </p>
        <div class="hero-infos">
          <p>Live & Online</p>
          <p class="dot">&#8226;</p>
          <p>Language: EN</p>
          <p class="dot">&#8226;</p>
          <p>Asia/Tashkent (UTC+5)</p>
          <p class="dot">&#8226;</p>
          <p>For local and foreign applicants</p>
        </div>
        <div class="hero-buttons">
          <button class="learn-button">
            <p>Learn More</p>
          </button>
          <button class="apply-button">
            <p>Apply Now!</p>
            <img class="gif" src="/img/animation.gif" alt="" />
          </button>
        </div>
      </div>
      <div class="hero-right">
        <div class="icon">
          <img src="/img/hero-1.webp" alt="BMU Campus" />
        </div>
        <div class="img">
          <img src="/img/campus.png" alt="BMU Students" />
        </div>

        <img src="/img/star.svg" alt="" class="star-1" />
        <img src="/img/star.svg" alt="" class="star-2" />
        <img src="/img/star.svg" alt="" class="star-3" />
        <img src="/img/star.svg" alt="" class="star-4" />
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero {
  padding: 80px 0;
  height: calc(100vh - 90px);
  background-color: #f9f9f9;
  overflow: hidden;
  position: relative;
}
.container {
  display: grid;
  grid-template-columns: 5fr 5fr;
  gap: 80px;
  height: 100%;
  position: relative;
  z-index: 1;
  padding: 32px 16px;
}
.hero-title {
  font-size: 56px;
  font-weight: 700;
  margin-bottom: 24px;
  line-height: 110%;
  color: black;
}
.hero-subtitle {
  font-size: 20px;
  line-height: 32px;
  margin-bottom: 32px;
}
.hero-infos {
  display: flex;
  gap: 16px;
  margin-bottom: 40px;
}
.hero-infos p {
  font-size: 16px;
  color: #666666;
  white-space: nowrap;
}
.hero-learn-button,
.hero-apply-button {
  padding: 16px 32px;
  font-size: 16px;
  border: none;
  cursor: pointer;
  margin-right: 16px;
}
.hero-learn-button {
  background-color: #007bff;
  color: #ffffff;
}
.apply-button {
  background-color: var(--red);
  color: #ffffff;
  border: none;
  border-radius: 16px;
  padding: 24px 56px;
  font-size: 18px;
  cursor: pointer;
  font-weight: 500;
  position: relative;
  overflow: hidden;
  transition: 0.3s all;
}
.learn-button {
  background-color: var(--blue);
  color: #ffffff;
  border: none;
  border-radius: 16px;
  padding: 24px 56px;
  font-size: 18px;
  cursor: pointer;
  font-weight: 500;
  position: relative;
  overflow: hidden;
  transition: 0.3s all;
}
.apply-button:hover,
.learn-button:hover {
  transform: scale(0.95);
}
.apply-button p,
.learn-button p {
  position: relative;
  z-index: 2;
  transform: translateY(2px);
}
.apply-button .gif {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0%;
  right: 0%;
  object-fit: cover;
  z-index: 1;
  opacity: 0.8;
  pointer-events: none;
  mix-blend-mode: luminosity;
}
.hero-buttons {
  display: flex;
  gap: 16px;
  align-items: center;
}
.hero-right {
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  justify-content: center;
}
.hero-right .icon {
  position: absolute;
  top: 0;
  left: 50%;
  /* transform: translateX(-20%); */
  background: rgba(255, 255, 255, 0.15);
  border-radius: 24px;
  box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
  backdrop-filter: blur(6.9px);
  -webkit-backdrop-filter: blur(6.9px);
  height: 300px;
  width: 300px;
  padding: 16px 16px 0 16px;
  z-index: 2;
  animation: jump 4s infinite;
}
@keyframes jump {
  0%,
  100% {
    transform: translateX(-30%) translateY(0);
  }
  50% {
    transform: translateX(-30%) translateY(-30px);
  }
}
.hero-right .icon img {
  width: 100%;
  height: 90%;
  object-fit: contain;
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
}
.hero-right .img {
  position: relative;
  z-index: 1;
  height: 400px;
  width: 90%;
  border-radius: 32px;
  overflow: hidden;
}
.hero-right .img img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
.bacteria {
  position: absolute;
  top: 100px;
  left: 0px;
  z-index: 0;
  width: 104%;
}
.star-1 {
  position: absolute;
  top: 50%;
  left: 0;
  width: 32px;
  height: 32px;
  z-index: 0;
  transform: translateY(-50%) rotate(-10deg);
  animation: jumpStar 3s infinite;
}
.star-2 {
  position: absolute;
  top: 80px;
  right: 0%;
  width: 24px;
  height: 24px;
  z-index: 0;
  transform: rotate(-10deg);
  animation: jumpStar 4s infinite;
}
.star-3 {
  position: absolute;
  top: 100px;
  right: -40px;
  width: 40px;
  height: 40px;
  z-index: 0;
  transform: rotate(10deg);
  animation: jumpStar 5s infinite;
}
.star-4 {
  position: absolute;
  bottom: 90px;
  right: -10px;
  width: 24px;
  height: 24px;
  z-index: 0;
  transform: rotate(10deg);
  animation: jumpStar 4s infinite;
}
@keyframes jumpStar {
  0%,
  100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-10px);
  }
}
.hero-title .typing-text {
  color: var(--blue);
  position: relative;
  display: inline-block;
  min-width: 220px;
  text-align: left;
}
.hero-title .typing-text::after {
  content: "|";
  animation: blink 0.7s infinite;
  margin-left: 2px;
}
@keyframes blink {
  0%,
  50% {
    opacity: 1;
  }
  51%,
  100% {
    opacity: 0;
  }
}

/* Responsive Styles */
@media screen and (max-width: 1024px) {
  .container {
    grid-template-columns: 1fr;
    gap: 48px;
    padding: 24px 16px;
  }

  .hero {
    height: auto;
    min-height: calc(100vh - 90px);
    padding: 48px 0;
  }

  .hero-title {
    font-size: 42px;
  }

  .hero-title .typing-text {
    min-width: 180px;
  }

  .hero-right {
    align-items: center;
    margin-top: 32px;
  }

  .hero-right .icon {
    left: 40%;
    height: 240px;
    width: 240px;
  }

  .hero-right .img {
    height: 350px;
    width: 100%;
  }

  .bacteria {
    width: 150%;
    top: auto;
    bottom: 0;
    left: -20%;
  }
  .star-1 {
    left: -4px;
    top: -10px;
    z-index: 2;
  }
  .star-4 {
    bottom: 0px;
    right: -20px;
    z-index: 2;
  }
  .star-3 {
    right: 0;
    top: 10px;
    z-index: 2;
  }
  .star-2 {
    top: 0px;
    right: 40px;
    z-index: 2;
  }
}

@media screen and (max-width: 768px) {
  .hero {
    padding: 32px 0;
  }

  .hero-title {
    font-size: 36px;
    margin-bottom: 20px;
  }

  .hero-title .typing-text {
    min-width: 150px;
    display: inline-block;
    margin-top: 8px;
  }

  .hero-subtitle {
    font-size: 18px;
    line-height: 28px;
    margin-bottom: 24px;
  }

  .hero-infos {
    flex-wrap: wrap;
    gap: 8px 12px;
    margin-bottom: 32px;
  }

  .hero-infos p {
    font-size: 14px;
  }

  .hero-buttons {
    flex-direction: column;
    gap: 12px;
    width: 100%;
  }

  .learn-button,
  .apply-button {
    width: 100%;
    padding: 20px 40px;
    font-size: 16px;
  }

  .hero-right .icon {
    left: 30%;
    height: 200px;
    width: 200px;
    top: -20px;
  }

  .hero-right .img {
    height: 300px;
  }
}

@media screen and (max-width: 480px) {
  .hero-title {
    font-size: 28px;
  }

  .hero-title .typing-text {
    min-width: 120px;
    font-size: 28px;
  }

  .hero-subtitle {
    font-size: 16px;
    line-height: 24px;
  }

  .hero-infos p {
    font-size: 13px;
  }

  .learn-button,
  .apply-button {
    padding: 20px 32px;
    font-size: 15px;
    border-radius: 24px;
  }

  .hero-right .icon {
    left: 30%;
    height: 180px;
    width: 180px;
  }

  .hero-right .img {
    height: 250px;
  }

  .container {
    gap: 32px;
  }
}
</style>
