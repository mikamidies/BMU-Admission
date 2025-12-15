<template>
  <footer class="wrapper">
    <div class="container">
      <div class="grid">
        <div class="col-1">
          <div class="logo">
            <img src="/img/white.svg" alt="UzAeroSpace" />
          </div>
          <div class="socials">
            <a href="#" class="soc">
              <Icon name="mdi:facebook" />
            </a>
            <a href="#" class="soc">
              <Icon name="mdi:instagram" />
            </a>
            <a href="#" class="soc">
              <Icon name="mdi:telegram" />
            </a>
            <a href="#" class="soc">
              <Icon name="mdi:linkedin" />
            </a>
          </div>
        </div>

        <div class="col-2">
          <ul>
            <h4 class="ul-title">Menu</h4>
            <li><NuxtLink to="/">Main</NuxtLink></li>
            <li><NuxtLink to="/">About Us</NuxtLink></li>
            <li><NuxtLink to="/">Articles and News</NuxtLink></li>
            <li><NuxtLink to="/">Vacancies</NuxtLink></li>
            <li><NuxtLink to="/">Contacts</NuxtLink></li>
          </ul>
        </div>

        <div class="col-3">
          <ul>
            <h4 class="ul-title">Directions</h4>
            <li><NuxtLink to="/">Management</NuxtLink></li>
            <li><NuxtLink to="/">Bachelors</NuxtLink></li>
            <li><NuxtLink to="/">Postgraduate</NuxtLink></li>
            <li><NuxtLink to="/">Undergraduate</NuxtLink></li>
          </ul>
        </div>

        <div class="col-4">
          <h4 class="ul-title no-margin">Contacts</h4>
          <div class="item">
            <div class="item-title">
              <Icon name="mdi:phone" />
              <span>Phone</span>
            </div>
            <a href="tel:+998901234567">+998 (90) 123-45-67</a>
            <a href="tel:+998901234568">+998 (90) 123-45-68</a>
          </div>

          <div class="item">
            <div class="item-title">
              <Icon name="mdi:map-marker" />
              <span>Address </span>
            </div>
            <p>Tashkent, Example St., 123</p>
          </div>

          <div class="item">
            <div class="item-title">
              <Icon name="mdi:email" />
              <span>Email</span>
            </div>
            <a href="mailto:info@uzaerospace.uz">info@bmuedu.uz</a>
          </div>
        </div>
      </div>
    </div>

    <div class="bottom">
      <div class="container">
        <p>© 2025 BMU</p>
        <p>All rights reserved</p>
      </div>
    </div>
  </footer>
</template>

<style scoped>
.wrapper {
  background-color: var(--blue);
  color: #fff;
  padding-top: 80px;
}

.container {
  margin: 0 auto;
  padding: 0 20px;
}

.grid {
  display: grid;
  grid-template-columns: 1.5fr 1fr 1fr 1.5fr;
  gap: 60px;
  padding-bottom: 60px;
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
}

.col-1 {
  display: flex;
  flex-direction: column;
  gap: 30px;
}

.logo img {
  height: 78px;
  width: auto;
}

.socials {
  display: flex;
  gap: 12px;
}

.soc {
  width: 50px;
  height: 50px;
  display: flex;
  align-items: center;
  justify-content: center;
  background: var(--lighten);
  border-radius: 12px;
  color: #fff;
  font-size: 20px;
  transition: background-color 0.3s ease, transform 0.2s ease;
  color: var(--blue);
}

.col-2 ul,
.col-3 ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.ul-title {
  font-size: 20px;
  font-weight: 500;
  margin-bottom: 24px;
  color: #fff;
}

.col-2 li,
.col-3 li {
  margin-bottom: 20px;
}

.col-2 a,
.col-3 a {
  color: rgba(255, 255, 255, 0.7);
  text-decoration: none;
  font-size: 16px;
  line-height: 24px;
  transition: color 0.3s ease;
}

.col-2 a:hover,
.col-3 a:hover {
  color: #fff;
}

.col-4 {
  display: flex;
  flex-direction: column;
  gap: 24px;
}

.item {
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.item-title {
  display: flex;
  align-items: center;
  gap: 8px;
  font-weight: 400;
  font-size: 15px;
  color: rgba(255, 255, 255, 0.7);
  margin-bottom: 4px;
}

.item-title :deep(svg) {
  width: 18px;
  height: 18px;
  color: var(--blue, #3b82f6);
}

.item a,
.item p {
  color: white;
  text-decoration: none;
  font-size: 14px;
  margin: 0;
  line-height: 1.6;
  transition: color 0.3s ease;
}

.item a:hover {
  color: #fff;
}

.bottom {
  padding: 30px 0;
  background-color: var(--blue);
}
.bottom .container {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.bottom p {
  text-align: center;
  color: rgba(255, 255, 255, 0.5);
  font-size: 14px;
  margin: 0;
}

.no-margin {
  margin-bottom: 0;
}

@media (max-width: 1024px) {
  .wrapper {
    padding-top: 60px;
  }

  .grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 40px;
    padding-bottom: 50px;
  }

  .col-1 {
    grid-column: 1 / -1;
    gap: 24px;
  }

  .logo img {
    width: 120px;
    height: 60px;
  }

  .socials {
    gap: 10px;
  }

  .soc {
    width: 44px;
    height: 44px;
    font-size: 18px;
    border-radius: 10px;
  }

  .ul-title {
    font-size: 18px;
    margin-bottom: 20px;
  }

  .col-2 li,
  .col-3 li {
    margin-bottom: 16px;
  }

  .col-2 a,
  .col-3 a {
    font-size: 15px;
  }

  .col-4 {
    gap: 20px;
  }

  .item {
    gap: 6px;
  }

  .item-title {
    font-size: 14px;
  }

  .item a,
  .item p {
    font-size: 13px;
  }

  .bottom {
    padding: 24px 0;
  }

  .bottom .container {
    flex-direction: column;
    gap: 8px;
  }

  .bottom p {
    font-size: 13px;
  }
}

@media (max-width: 968px) {
  .grid {
    grid-template-columns: repeat(2, 1fr);
    gap: 40px;
  }

  .col-1 {
    grid-column: 1 / -1;
  }
}

@media (max-width: 768px) {
  .wrapper {
    padding-top: 60px;
  }

  .grid {
    grid-template-columns: 1fr;
    gap: 40px;
    padding-bottom: 40px;
  }

  .col-1 {
    grid-column: auto;
  }
}
</style>
