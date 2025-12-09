<template>
  <TheHeader />

  <main>
    <section class="hero">
      <div class="container">
        <div class="hero-left">
          <h1 class="hero-title">Welcome to BMU Admission</h1>
          <p class="hero-subtitle">
            Your journey to a brighter future starts here. Explore our programs
            and apply today!
          </p>
          <div class="hero-infos">
            <p>Live & Online</p>
            <p>Language: EN</p>
            <p>Asia/Tashkent (UTC+5)</p>
            <p>PMI® ATP Courseware</p>
          </div>
          <button class="hero-learn-button">Learn More</button>
          <button class="hero-apply-button">Apply Now!</button>
        </div>
        <div class="hero-right">
          <img src="/img/hero-1.webp" alt="BMU Campus" />
        </div>
      </div>
    </section>
  </main>
</template>

<style scoped>
.hero {
  padding: 80px 0;
  height: calc(100vh - 90px);
  background-color: #f9f9f9;
}
.container {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.hero-left {
  max-width: 600px;
}
.hero-title {
  font-size: 48px;
  font-weight: bold;
  margin-bottom: 24px;
}
.hero-subtitle {
  font-size: 20px;
  margin-bottom: 32px;
}
.hero-infos {
  display: flex;
  gap: 24px;
  margin-bottom: 40px;
}
.hero-infos p {
  font-size: 16px;
  color: #666666;
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
</style>
