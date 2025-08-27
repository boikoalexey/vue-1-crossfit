<script setup lang="ts">
import { ref } from 'vue'

const headerMenuLinks = [
  { text: 'Home', link: '/' },
  { text: 'Pages', link: '/' },
  { text: 'Portfolio', link: '/' },
  { text: 'Blog', link: '/' },
  { text: 'Shop', link: '/' },
]

const isCurrentPage = ref<number>(0)
</script>

<template>
  <header class="header">
    <div class="header-container main-container">
      <a class="header-logo" href="/">
        <img
          class="header-logo-img"
          src="../assets/images/logo.png"
          alt="Kropp Logo"
          width="136"
          height="26"
          loading="lazy"
        />
      </a>

      <nav class="header-menu">
        <ul class="header-menu-list">
          <li
            v-for="(item, index) in headerMenuLinks"
            class="header-menu-item"
            :key="index"
          >
            <a
              class="header-menu-link"
              href="/"
              :class="{ 'is-current': isCurrentPage === index }"
            >
              {{ item.text }}
            </a>
          </li>
        </ul>
      </nav>

      <div class="header-actions">
        <button class="header-book-button button" type="button">Book now</button>
        <button class="header-burger-button" type="button" title="Open menu">
          <span class="visually-hidden">Open menu</span>
          <span class="header-burger-button-line"></span>
          <span class="header-burger-button-line"></span>
          <span class="header-burger-button-line"></span>
        </button>
      </div>
    </div>
  </header>
</template>

<style scoped>
.header {
  height: var(--header-height);
  padding-inline: 32px;
  background-color: var(--color-dark-alternate);
}

.header-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  column-gap: 20px;
}

.header-logo {
  flex-shrink: 0;
}

.header-menu-list {
  display: flex;
  flex-wrap: wrap;
  column-gap: 50px;
}

.header-menu-link {
  display: inline-flex;
  align-items: center;
  column-gap: 7px;
  height: var(--header-height);
  font-size: 12px;
  font-weight: 700;
  letter-spacing: 1.2px;
  text-decoration: none;
  text-transform: uppercase;
}

.header-menu-link.is-current::after {
  content: '';
  aspect-ratio: 1;
  width: 5px;
  background-color: currentColor;
  border-radius: 50%;
}

.header-actions {
  display: flex;
  align-items: center;
  column-gap: 40px;
}

.header-burger-button {
  display: inline-flex;
  flex-direction: column;
  justify-content: center;
  row-gap: 5px;
  aspect-ratio: 1;
  width: 40px;
  padding-left: 8px;
  color: var(--color-light);
  background-color: transparent;
  border: var(--border);
  border-radius: 50%;
}

.header-burger-button:hover {
  color: var(--color-light-gray);
  border-color: currentColor;
}

.header-burger-button-line {
  width: 6px;
  height: 1px;
  background-color: currentColor;
  box-shadow: 16px 0 0 currentColor;
}

@media (width <= 1024px) {
  .header-container {
    flex-wrap: wrap;
    row-gap: 10px;
    padding-inline: 15px;
    padding-top: 20px;
  }

  .header-menu {
    order: 1;
    flex-basis: 100%;
  }

  .header-menu-link {
    height: 50px;
  }
}

@media (width <= 767px) {
  .header {
    padding-top: 10px;
  }

  .header-menu-list {
    column-gap: 24px;
  }

  .header-menu-link {
    height: 32px;
  }

  .header-actions {
    column-gap: 15px;
  }
}
</style>
