<script setup></script>

<template>
  <div class="advantages-block">
    <div class="container">
      <h4 class="adv-title">Why choose BMU?</h4>
      <div class="adv-grid">
        <div class="adv-left">
          <div class="adv-button">
            <div class="button-top">
              <p class="button-name">Double Degree</p>
              <div class="button-arrow">
                <Icon name="lucide:arrow-right" size="16" />
              </div>
            </div>
            <div class="button-bottom">
              <Icon name="lucide:graduation-cap" size="32" />
              <p class="button-desc">
                Earn degrees from both BMU and the University of Reading,
                enhancing your global career prospects
              </p>
            </div>
          </div>
          <div class="adv-button">
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
                learning and extracurricular activities
              </p>
            </div>
          </div>
          <div class="adv-button">
            <div class="button-top">
              <p class="button-name">International Faculty</p>
              <div class="button-arrow">
                <Icon name="lucide:arrow-right" size="16" />
              </div>
            </div>
            <div class="button-bottom">
              <Icon name="lucide:user" size="32" />
              <p class="button-desc">
                Learn from experienced international faculty members who bring
                global perspectives to the classroom
              </p>
            </div>
          </div>
          <div class="adv-button">
            <div class="button-top">
              <p class="button-name">Student Life</p>
              <div class="button-arrow">
                <Icon name="lucide:arrow-right" size="16" />
              </div>
            </div>
            <div class="button-bottom">
              <Icon name="lucide:user-star" size="32" />
              <p class="button-desc">
                Join a vibrant student community with diverse clubs, events, and
                activities
              </p>
            </div>
          </div>
          <div class="adv-button">
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
          <div class="adv-button">
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
                achieve your professional goals
              </p>
            </div>
          </div>
        </div>
        <div class="adv-right"></div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.advantages-block {
  padding: 80px 0;
  background-color: #f9f9f9;
}
.adv-title {
  font-size: 36px;
  font-weight: 700;
  margin-bottom: 40px;
  color: var(--blue);
}
.adv-grid {
  display: grid;
  grid-template-columns: 7fr 3fr;
  gap: 40px;
}
.adv-left {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 4px;
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
}
.button-desc {
  font-size: 16px;
  line-height: 24px;
  color: #666666;
  margin-top: 8px;
  max-width: 100%;
  text-align: right;
}
.button-bottom {
  display: flex;
  align-items: center;
  justify-content: flex-end;
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
}
.button-arrow span {
  color: #ffffff;
}
</style>
