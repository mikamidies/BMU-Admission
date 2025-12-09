<script setup>
import { ref } from "vue";

const handleDropdown = ref(false);
const isMobileMenuOpen = ref(false);

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value;
};
</script>

<template>
  <header>
    <nav class="navbar">
      <div class="container">
        <div class="navbar-start">
          <a class="navbar-brand" href="/">
            <img src="/img/brand.svg" alt="BMU Admission Logo" />
          </a>
          <button
            @click="toggleMobileMenu"
            role="button"
            class="navbar-burger"
            :class="{ 'is-active': isMobileMenuOpen }"
            aria-label="menu"
            :aria-expanded="isMobileMenuOpen"
          >
            <span aria-hidden="true"></span>
            <span aria-hidden="true"></span>
            <span aria-hidden="true"></span>
          </button>
        </div>

        <div class="navbar-menu" :class="{ 'is-active': isMobileMenuOpen }">
          <div class="navbar-end">
            <button class="navbar-link">Home</button>
            <button class="navbar-link">About</button>
            <button class="navbar-link">Programs</button>
            <button class="navbar-link">Contact</button>
          </div>

          <div class="navbar-languages">
            <button
              @click="handleDropdown = !handleDropdown"
              class="navbar-lang active"
            >
              English
              <img src="/img/en.png" alt="" />
            </button>
            <div :class="{ show: handleDropdown }" class="navbar-dropdown">
              <button class="navbar-lang">
                Русский
                <img src="/img/ru.png" alt="" />
              </button>
              <button class="navbar-lang">
                O'zbekcha
                <img src="/img/uz.png" alt="" />
              </button>
            </div>
          </div>

          <div class="navbar-button">
            <button class="apply-button">
              <p>Apply Now!</p>
              <img class="gif" src="/img/animation.gif" alt="" />
            </button>
          </div>
        </div>
      </div>
    </nav>
  </header>
</template>

<style scoped>
header {
  background-color: #ffffff;
  border: 1px solid #ebebeb;
  position: sticky;
  top: 0;
  z-index: 10;
}
.container {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.navbar-brand {
  display: flex;
}
.navbar-brand img {
  width: 200px;
  height: auto;
  object-fit: contain;
}
.navbar-menu {
  display: flex;
  align-items: center;
  gap: 64px;
}
.navbar-end {
  display: flex;
  align-items: center;
}
.navbar-link {
  background: none;
  border: none;
  font-size: 16px;
  cursor: pointer;
  font-size: 18px;
  line-height: 24px;
  position: relative;
  padding: 32px 24px;
  font-weight: 500;
}
.navbar-link::after {
  content: "";
  position: absolute;
  bottom: 0px;
  left: 0;
  width: 0;
  height: 4px;
  background-color: var(--blue);
  transition: width 0.3s ease;
}
.navbar-link:hover::after {
  width: 100%;
}
.navbar-languages {
  position: relative;
}
.navbar-lang {
  background: none;
  border: none;
  font-size: 18px;
  line-height: 24px;
  cursor: pointer;
  display: flex;
  align-items: center;
  gap: 8px;
  font-weight: 500;
  color: var(--blue);
}
.navbar-lang img {
  width: 24px;
  height: 24px;
  object-fit: cover;
  border: 1px solid #ebebeb;
  border-radius: 50%;
}
.navbar-dropdown {
  position: absolute;
  top: 40px;
  left: 0;
  background-color: #ffffff;
  border: 1px solid #ebebeb;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  border-radius: 16px;
  opacity: 0;
  visibility: hidden;
  transform: translateY(-100px);
  transition: all 0.3s ease;
}
.navbar-dropdown.show {
  opacity: 1;
  visibility: visible;
  transform: translateY(0);
}
.navbar-dropdown .navbar-lang {
  display: flex;
  width: 100%;
  justify-content: space-between;
  align-items: center;
  padding: 12px 20px;
  font-weight: 400;
  color: black;
}
.navbar-dropdown .navbar-lang:first-child {
  border-bottom: 1px solid #ebebeb;
}
.navbar-button .apply-button {
  background-color: var(--blue);
  color: #ffffff;
  border: none;
  border-radius: 16px;
  padding: 20px 48px;
  font-size: 18px;
  cursor: pointer;
  font-weight: 500;
  position: relative;
  white-space: nowrap;
  overflow: hidden;
}
.navbar-button .apply-button p {
  position: relative;
  z-index: 2;
  transform: translateY(2px);
}
.navbar-button .apply-button .gif {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0%;
  right: 0%;
  object-fit: cover;
  z-index: 1;
  opacity: 0.5;
  pointer-events: none;
}

/* Burger Menu Styles */
.navbar-start {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;
}

.navbar-burger {
  display: none;
  flex-direction: column;
  justify-content: space-around;
  width: 32px;
  height: 28px;
  background: transparent;
  border: none;
  cursor: pointer;
  padding: 0;
  z-index: 20;
}

.navbar-burger span {
  width: 100%;
  height: 3px;
  background-color: var(--blue);
  border-radius: 10px;
  transition: all 0.3s ease;
  transform-origin: center;
}

.navbar-burger.is-active span:nth-child(1) {
  transform: translateY(9px) rotate(45deg);
}

.navbar-burger.is-active span:nth-child(2) {
  opacity: 0;
  transform: translateX(-20px);
}

.navbar-burger.is-active span:nth-child(3) {
  transform: translateY(-9px) rotate(-45deg);
}

/* Responsive Styles */
@media screen and (max-width: 1024px) {
  .navbar {
    padding: 24px 0;
  }
  .navbar-burger {
    display: flex;
  }

  .navbar-menu {
    position: fixed;
    top: 90px;
    left: 0;
    right: 0;
    background-color: #ffffff;
    flex-direction: column;
    gap: 0;
    padding: 24px 0;
    border-top: 1px solid #ebebeb;
    transform: translateX(-100%);
    opacity: 0;
    visibility: hidden;
    transition: all 0.3s ease;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
    max-height: calc(100vh - 90px);
    overflow-y: auto;
  }

  .navbar-menu.is-active {
    transform: translateX(0);
    opacity: 1;
    visibility: visible;
  }

  .navbar-end {
    flex-direction: column;
    width: 100%;
    align-items: stretch;
  }

  .navbar-link {
    padding: 16px 24px;
    text-align: left;
    border-bottom: 1px solid #f5f5f5;
  }

  .navbar-link::after {
    display: none;
  }

  .navbar-languages {
    width: 100%;
    padding: 16px 24px;
    border-bottom: 1px solid #f5f5f5;
  }

  .navbar-dropdown {
    position: static;
    box-shadow: none;
    border: none;
    border-radius: 0;
    margin-top: 12px;
    transform: none;
  }

  .navbar-dropdown.show {
    transform: none;
  }

  .navbar-button {
    padding: 16px 24px;
    width: 100%;
  }

  .navbar-button .apply-button {
    width: 100%;
  }
}

@media screen and (max-width: 768px) {
  .navbar-brand img {
    width: 150px;
  }

  .container {
    padding: 0 12px;
  }
}
</style>
