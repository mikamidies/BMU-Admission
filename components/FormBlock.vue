<template>
  <div class="wrapper">
    <div class="container">
      <div class="top section__top">
        <h2 class="title section__title">Contact Us!</h2>
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
</script>

<style scoped>
.wrapper {
  padding: 60px 0 120px 0;
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
}
</style>
