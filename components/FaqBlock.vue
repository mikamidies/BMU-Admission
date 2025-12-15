<script setup>
import { ref, computed, onMounted, nextTick } from "vue";
const { $gsap, $ScrollTrigger } = useNuxtApp();

const activeIndex = ref(null);
const accordionRefs = ref([]);
const accordionHeights = ref([]);

const toggleAccordion = async (index) => {
  if (activeIndex.value === index) {
    activeIndex.value = null;
  } else {
    activeIndex.value = index;

    await nextTick();

    if (accordionRefs.value[index]) {
      accordionHeights.value[index] = accordionRefs.value[index].scrollHeight;
    }
  }
};

const content = ref([
  {
    title: "What is BMU?",
    description:
      "BMU is a prestigious institution dedicated to providing high-quality education and fostering academic excellence.",
  },
  {
    title: "What programs does BMU offer?",
    description:
      "BMU offers a wide range of undergraduate and postgraduate programs in various fields, including business, management, and information technology.",
  },
  {
    title: "What is the admission process for BMU?",
    description:
      "The admission process for BMU involves submitting an online application, providing necessary documents, and attending an interview.",
  },
  {
    title: "Does BMU offer scholarships?",
    description:
      "Yes, BMU offers various scholarships based on academic merit and financial need. Please visit our scholarships page for more information.",
  },
  {
    title: "What facilities are available on campus?",
    description:
      "BMU's campus is equipped with modern facilities, including libraries, computer labs, sports complexes, and student lounges.",
  },
]);

const contentLeft = content.value.slice(0, Math.ceil(content.value.length / 2));
const contentRight = content.value.slice(Math.ceil(content.value.length / 2));

onMounted(() => {
  // Анимация заголовка
  $gsap.fromTo(
    ".section__title",
    {
      y: 50,
      opacity: 0,
    },
    {
      scrollTrigger: {
        trigger: ".faq",
        start: "top 90%",
        toggleActions: "restart none restart none",
      },
      y: 0,
      opacity: 1,
      duration: 1,
      ease: "power2.out",
    }
  );

  // Анимация элементов аккордеона слева
  $gsap.fromTo(
    ".accordion-left .accordion-item",
    {
      x: -50,
      opacity: 0,
    },
    {
      scrollTrigger: {
        trigger: ".accordion-left",
        start: "top 85%",
        toggleActions: "restart none restart none",
      },
      x: 0,
      opacity: 1,
      duration: 0.8,
      stagger: 0.2,
      ease: "back.out(1.7)",
    }
  );

  // Анимация элементов аккордеона справа
  $gsap.fromTo(
    ".accordion-right .accordion-item",
    {
      x: 50,
      opacity: 0,
    },
    {
      scrollTrigger: {
        trigger: ".accordion-right",
        start: "top 85%",
        toggleActions: "restart none restart none",
      },
      x: 0,
      opacity: 1,
      duration: 0.8,
      stagger: 0.2,
      ease: "back.out(1.7)",
    }
  );
});
</script>

<template>
  <section class="faq">
    <div class="site-container">
      <h4 class="section__title">Frequently Asked Questions</h4>
      <div class="accordion">
        <div class="accordion-left">
          <div
            class="accordion-item"
            v-for="(item, index) in contentLeft"
            :key="'left-' + index"
          >
            <div
              class="accordion-header"
              @click="toggleAccordion(index)"
              :class="{ opened: activeIndex === index }"
            >
              <span class="accordion-title"> {{ item.title }} </span>
              <Icon
                name="lucide:chevron-down"
                alt="toggle-icon"
                :style="{
                  transform:
                    activeIndex === index ? 'rotate(180deg)' : 'rotate(0deg)',
                }"
              />
            </div>

            <div
              :ref="(el) => (accordionRefs[index] = el)"
              class="template-accordion-content"
              :style="{
                maxHeight:
                  activeIndex === index
                    ? accordionHeights[index] + 'px'
                    : '0px',
                opacity: activeIndex === index ? '1' : '0',
              }"
            >
              <p>
                {{ item.description }}
              </p>
            </div>
          </div>
        </div>
        <div class="accordion-right">
          <div
            class="accordion-item"
            v-for="(item, index) in contentRight"
            :key="'right-' + index"
          >
            <div
              class="accordion-header"
              @click="toggleAccordion(index + contentLeft.length)"
              :class="{ opened: activeIndex === index + contentLeft.length }"
            >
              <span class="accordion-title"> {{ item.title }} </span>
              <Icon
                name="lucide:chevron-down"
                alt="toggle-icon"
                :style="{
                  transform:
                    activeIndex === index + contentLeft.length
                      ? 'rotate(180deg)'
                      : 'rotate(0deg)',
                }"
              />
            </div>

            <div
              :ref="(el) => (accordionRefs[index + contentLeft.length] = el)"
              class="template-accordion-content"
              :style="{
                maxHeight:
                  activeIndex === index + contentLeft.length
                    ? accordionHeights[index + contentLeft.length] + 'px'
                    : '0px',
                opacity: activeIndex === index + contentLeft.length ? '1' : '0',
              }"
            >
              <p>
                {{ item.description }}
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.faq {
  padding: 80px 0;
  background-color: #f9f9f9;
  overflow: hidden;
}

.section__title {
  font-size: 36px;
  font-weight: 700;
  text-align: center;
  margin-bottom: 40px;
  color: var(--blue);
}

.accordion {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 40px;
  max-width: 1200px;
  margin: 0 auto;
}

.accordion-item {
  background: #ffffff;
  border-radius: 16px;
  overflow: hidden;
  margin-bottom: 16px;
}

.accordion-header {
  padding: 24px;
  cursor: pointer;
  display: flex;
  justify-content: space-between;
  align-items: center;
  transition: 0.4s;
}

.accordion-header.opened {
  background-color: var(--blue);
}

.accordion-header.opened .accordion-title,
.accordion-header.opened span {
  color: white;
}

.accordion-title {
  font-size: 18px;
  font-weight: 600;
  color: #333333;
}

.template-accordion-content {
  max-height: 0;
  overflow: hidden;
  transition: max-height 0.3s ease, opacity 0.3s ease;
  background-color: var(--blue);
}

.template-accordion-content p {
  padding: 0 24px 24px 24px;
  margin: 0;
  font-size: 16px;
  line-height: 24px;
  color: white;
}

/* Responsive */
@media (max-width: 768px) {
  .accordion {
    grid-template-columns: 1fr;
    gap: 20px;
  }

  .section__title {
    font-size: 28px;
    margin-bottom: 30px;
  }

  .accordion-header {
    padding: 20px;
  }

  .accordion-title {
    font-size: 16px;
  }

  .template-accordion-content p {
    padding: 0 20px 20px 20px;
    font-size: 15px;
  }
}
</style>
