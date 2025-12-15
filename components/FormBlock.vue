<template>
  <div class="wrapper">
    <img src="/img/star.svg" alt="" class="star-1" />
    <img src="/img/star.svg" alt="" class="star-2" />
    <img src="/img/star.svg" alt="" class="star-3" />
    <img src="/img/star.svg" alt="" class="star-4" />
    <div class="container">
      <div class="top section__top">
        <h2 class="title">Contact Us!</h2>
      </div>

      <form @submit.prevent="handleSubmit">
        <input
          type="text"
          class="name"
          placeholder="Ваше имя"
          v-model="form.name"
          required
        />

        <div class="flexer">
          <input
            type="email"
            class="email"
            placeholder="Email"
            v-model="form.email"
            required
          />
          <input
            type="tel"
            class="number"
            placeholder="Номер телефона"
            v-model="form.number"
            required
          />
        </div>

        <textarea
          class="message"
          placeholder="Сообщение"
          v-model="form.message"
          rows="5"
        ></textarea>

        <button type="submit" class="submit">Отправить</button>
      </form>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";

const { $gsap, $ScrollTrigger } = useNuxtApp();

const form = ref({
  name: "",
  email: "",
  number: "",
  company: "",
  message: "",
});

const handleSubmit = () => {
  console.log("Form submitted:", form.value);
};

onMounted(() => {
  $gsap.fromTo(
    ".title",
    {
      y: 50,
      opacity: 0,
    },
    {
      y: 0,
      opacity: 1,
      duration: 1,
      ease: "power2.out",
      scrollTrigger: {
        trigger: ".wrapper",
        start: "top 80%",
        toggleActions: "play none none reverse",
      },
    }
  );

  $gsap.fromTo(
    "form",
    {
      y: 30,
      opacity: 0,
    },
    {
      y: 0,
      opacity: 1,
      duration: 1,
      delay: 0.3,
      ease: "power2.out",
      scrollTrigger: {
        trigger: ".wrapper",
        start: "top 80%",
        toggleActions: "play none none reverse",
      },
    }
  );

  $gsap.to(".star-1", {
    scrollTrigger: {
      trigger: ".wrapper",
      start: "top 80%",
      toggleActions: "play none none reverse",
    },
    rotation: 360,
    duration: 2,
    ease: "power2.out",
  });

  $gsap.to(".star-2", {
    scrollTrigger: {
      trigger: ".wrapper",
      start: "top 70%",
      toggleActions: "play none none reverse",
    },
    rotation: -360,
    duration: 2.5,
    ease: "power2.out",
  });

  $gsap.to(".star-3", {
    scrollTrigger: {
      trigger: ".wrapper",
      start: "top 60%",
      toggleActions: "play none none reverse",
    },
    rotation: 180,
    duration: 3,
    ease: "power2.out",
  });

  $gsap.to(".star-4", {
    scrollTrigger: {
      trigger: ".wrapper",
      start: "top 50%",
      toggleActions: "play none none reverse",
    },
    rotation: -180,
    duration: 2.5,
    ease: "power2.out",
  });
});
</script>

<style scoped>
.wrapper {
  padding: 60px 0 120px 0;
  position: relative;
}

.container {
  max-width: 800px;
  margin: 0 auto;
  padding: 0 20px;
}

.top {
  display: flex;
  align-items: center;
  flex-direction: column;
  gap: 16px;
  margin-bottom: 24px;
}

.title {
  font-size: 36px;
  font-weight: 700;
  margin: 0;
  text-align: center;
  color: var(--blue);
}

form {
  display: flex;
  flex-direction: column;
  gap: 16px;
}

input,
textarea {
  width: 100%;
  padding: 18px 24px;
  background: #ebebeb;
  border-radius: 24px;
  font-size: 16px;
  font-family: inherit;
  transition: border-color 0.3s ease, box-shadow 0.3s ease;
  padding: 24px 32px;
  font-size: 20px;
  line-height: 28px;
  outline: none;
  border: none;
}

input::placeholder,
textarea::placeholder {
  color: #62748e;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: var(--blue, #3b82f6);
  box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.1);
}

.flexer {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 16px;
}

textarea.message {
  resize: vertical;
  min-height: 120px;
}

.submit {
  padding: 24px 40px;
  background-color: var(--blue, #3b82f6);
  color: white;
  border: none;
  border-radius: 24px;
  font-size: 20px;
  line-height: 28px;
  font-weight: 600;
  cursor: pointer;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.submit:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 16px rgba(59, 130, 246, 0.3);
}

.submit:active {
  transform: translateY(0);
}

/* Star styles */
.star-1 {
  position: absolute;
  top: 20%;
  left: 10%;
  width: 32px;
  height: 32px;
  z-index: 0;
  transform: rotate(-10deg);
}
.star-2 {
  position: absolute;
  top: 40%;
  right: 10%;
  width: 24px;
  height: 24px;
  z-index: 0;
  transform: rotate(-10deg);
}
.star-3 {
  position: absolute;
  top: 60%;
  left: 15%;
  width: 40px;
  height: 40px;
  z-index: 0;
  transform: rotate(10deg);
}
.star-4 {
  position: absolute;
  bottom: 20%;
  right: 15%;
  width: 24px;
  height: 24px;
  z-index: 0;
  transform: rotate(10deg);
}

@media (max-width: 1024px) {
  .wrapper {
    padding: 40px 0 80px 0;
  }
  .top {
    margin-bottom: 16px;
  }
  .title {
    font-size: 28px;
  }
  form {
    gap: 24px;
  }
  .flexer {
    grid-template-columns: 1fr;
    gap: 24px;
  }
  input,
  textarea {
    padding: 24px 28px;
    font-size: 17px;
    line-height: 24px;
    border-radius: 20px;
  }
  textarea.message {
    min-height: 100px;
  }
  .submit {
    padding: 24px 32px;
    font-size: 17px;
    line-height: 24px;
    border-radius: 20px;
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
  .wrapper {
    padding: 60px 0;
  }
  .title {
    font-size: 24px;
  }
  form {
    padding: 30px 20px;
  }
  .flexer {
    grid-template-columns: 1fr;
    gap: 20px;
  }
  input,
  textarea {
    padding: 16px 20px;
    font-size: 15px;
  }
  .star-1,
  .star-2,
  .star-3,
  .star-4 {
    display: none;
  }
}
</style>
