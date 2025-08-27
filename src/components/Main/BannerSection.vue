<script setup lang="ts">
import { ref } from 'vue'

const isCurrentButton = ref<number>(3)
</script>

<template>
  <section class="banner">
    <h2 class="visually-hidden" aria-labelledby="banner-title">
      Upcoming events
    </h2>

    <div class="banner-body main-container">
      <div class="banner-info">
        New event <br />
        coming up /
        <time datetime="06-07">june 7</time> &nbsp; - &nbsp;
        <time datetime="06-13">13</time>
      </div>
      <h3 class="banner-title">Crossfit</h3>
    </div>
    <div class="banner-pagination">
      <ul class="banner-pagination-list">
        <li v-for="i in 3" class="banner-pagination-item" :key="i">
          <button
            class="banner-pagination-button"
            :class="{ 'is-current': isCurrentButton === i }"
            type="button"
          ></button>
        </li>
      </ul>
    </div>
  </section>
</template>

<style scoped>
.banner {
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  min-height: calc(100dvh - var(--header-height));
  padding: 36px 70px;
  color: var(--color-light);
  background-color: var(--color-dark-alternate);
}

.banner-body {
  text-transform: uppercase;
}

.banner-info {
  display: flex;
  align-items: end;
  font-size: clamp(12px, 1.56vw, 30px);
  font-weight: 700;
  line-height: 1.27;
}

.banner-info::before {
  content: '';
  aspect-ratio: 1;
  width: clamp(60px, 10.1vw, 194px);
  margin-right: 30px;
  background: url('../../assets/icons/bold-arrow-down-right.svg') center/contain
    no-repeat;
}

.banner-title {
  font-size: min(18.758vw, 360px);
  font-weight: 700;
  line-height: 1;
}

.banner-pagination-list {
  display: flex;
  justify-content: center;
}

.banner-pagination-item {
  display: flex;
}

.banner-pagination-button {
  display: inline-flex;
  justify-content: center;
  align-items: center;
  padding: 7px;
  background-color: transparent;
  border: none;
}

.banner-pagination-button::after {
  content: '';
  aspect-ratio: 1;
  width: 10px;
  border: var(--border);
  border-radius: 50%;
  transition-duration: var(--transition-duration);
}

.banner-pagination-button.is-current::after {
  background-color: var(--color-light);
}

.banner-pagination-button:not(.is-current):hover::after {
  border-color: var(--color-light-gray);
}

@media (width <= 1024px) {
  .banner {
    row-gap: 15px;
    padding-inline: 15px;
  }

  .banner-info::before {
    margin-right: 10px;
  }
}

@media (width <= 767px) {
  .banner-info {
    margin-bottom: 10px;
  }
}
</style>
