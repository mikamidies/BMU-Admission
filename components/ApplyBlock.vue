<script setup>
import { ref, computed, onMounted } from "vue";
const { $gsap, $ScrollTrigger } = useNuxtApp();

const selectedLevel = ref("ielts5"); // 'ielts5' or 'ielts6'
const fullPayment = ref(false);

const price = computed(() => {
  let base = selectedLevel.value === "ielts6" ? 32000000 : 40000000;
  if (fullPayment.value) {
    base *= 0.95; // 5% discount
  }
  return base.toLocaleString() + " UZS";
});

onMounted(() => {
  // Анимации для левой части
  $gsap.fromTo(
    ".left-title",
    {
      x: -50,
      opacity: 0,
    },
    {
      scrollTrigger: {
        trigger: ".apply-block",
        start: "top 90%",
        toggleActions: "restart none restart none",
      },
      x: 0,
      opacity: 1,
      duration: 1,
      ease: "power2.out",
    }
  );

  $gsap.fromTo(
    ".left-desc",
    {
      x: -30,
      opacity: 0,
    },
    {
      scrollTrigger: {
        trigger: ".apply-block",
        start: "top 80%",
        toggleActions: "restart none restart none",
      },
      x: 0,
      opacity: 1,
      duration: 1,
      delay: 0.2,
      ease: "power2.out",
    }
  );

  // Анимации для counter
  $gsap.fromTo(
    ".counter",
    {
      y: 50,
      opacity: 0,
      scale: 0.9,
    },
    {
      scrollTrigger: {
        trigger: ".counter",
        start: "top 85%",
        toggleActions: "restart none restart none",
      },
      y: 0,
      opacity: 1,
      scale: 1,
      duration: 1,
      ease: "back.out(1.7)",
    }
  );

  $gsap.fromTo(
    ".price",
    {
      y: 20,
      opacity: 0,
    },
    {
      scrollTrigger: {
        trigger: ".price",
        start: "top 90%",
        toggleActions: "restart none restart none",
      },
      y: 0,
      opacity: 1,
      duration: 0.8,
      delay: 0.3,
      ease: "power2.out",
    }
  );
});
</script>

<template>
  <div class="apply-block">
    <div class="container">
      <div class="left">
        <h4 class="left-title section-title">Pricing & Financial Aid</h4>
        <p class="left-desc">
          We are committed to making education accessible and affordable for all
          students. <br />
          Our tuition fees are competitive, and we offer a range of financial
          aid options
        </p>
        <div class="counter">
          <div class="item">
            <div class="option">
              <input
                id="five"
                type="checkbox"
                :checked="selectedLevel === 'ielts5'"
                @change="
                  selectedLevel = 'ielts5';
                  fullPayment = false;
                "
                class="item-title"
              />
              <label for="five"> I have IELTS 5.5 or I don't have any </label>
            </div>
            <div class="option">
              <input
                id="no-ielts"
                type="checkbox"
                :checked="fullPayment && selectedLevel === 'ielts5'"
                @change="
                  if (selectedLevel === 'ielts5') fullPayment = !fullPayment;
                "
                class="item-title"
              />
              <label for="no-ielts">
                I can pay full before the Autumn semester
              </label>
            </div>
          </div>
          <div class="item">
            <div class="option">
              <input
                id="six"
                type="checkbox"
                :checked="selectedLevel === 'ielts6'"
                @change="
                  selectedLevel = 'ielts6';
                  fullPayment = false;
                "
                class="item-title"
              />
              <label for="six"> I have IELTS 6.0 or higher </label>
            </div>
            <div class="option">
              <input
                id="no-ielts-six"
                type="checkbox"
                :checked="fullPayment && selectedLevel === 'ielts6'"
                @change="
                  if (selectedLevel === 'ielts6') fullPayment = !fullPayment;
                "
                class="item-title"
              />
              <label for="no-ielts-six">
                I can pay full before the Autumn semester
              </label>
            </div>
          </div>
          <h4 class="price">
            Total Price: <span>{{ price }}</span>
          </h4>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.apply-block {
  padding: 80px 0;
  overflow: hidden;
}
.container {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 40px;
}
.left {
  background: #0086ff;
  padding: 24px;
  border-radius: 24px;
}
.left-title {
  font-size: 32px;
  font-weight: 700;
  color: #ffffff;
  margin-bottom: 16px;
}
.left-desc {
  font-size: 14px;
  line-height: 20px;
  color: #f0f0f0;
  margin-bottom: 16px;
}
.counter {
  background: white;
  padding: 16px;
  border-radius: 12px;
}
.item {
  padding: 16px 0;
  border-bottom: 1px solid #ebebeb;
}
.item:last-child {
  border-bottom: none;
}
.item .option {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 12px;
}
.item input[type="checkbox"] {
  width: 20px;
  height: 20px;
  accent-color: var(--blue);
  cursor: pointer;
}
.item label {
  font-size: 16px;
  font-weight: 500;
  color: #333333;
  cursor: pointer;
  margin: 0;
}
.price {
  font-size: 24px;
  font-weight: 700;
  margin-top: 16px;
  padding: 8px 0;
}
.price span {
  color: var(--blue);
  font-size: 28px;
}

/* Responsive */
@media (max-width: 768px) {
  .container {
    grid-template-columns: 1fr;
    gap: 24px;
  }
  .left {
    padding: 20px;
  }
  .left-title {
    font-size: 28px;
  }
  .item label {
    font-size: 15px;
  }
  .price {
    font-size: 20px;
  }
  .price span {
    font-size: 24px;
  }
}
</style>
