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
        <div class="dir-item"></div>
        <div class="dir-item"></div>
      </div>
    </div>
  </div>
</template>

<script setup></script>

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
  grid-template-columns: repeat(4, 1fr);
  gap: 30px;
}
.dir-item.big__item {
  background-color: var(--blue);
  padding: 32px;
  border-radius: 16px;
  -webkit-box-shadow: 0px 0px 54px -25px var(--blue);
  -moz-box-shadow: 0px 0px 54px -25px var(--blue);
  box-shadow: 0px 0px 54px -25px var(--blue);
  grid-column: 1/3;
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
</style>
