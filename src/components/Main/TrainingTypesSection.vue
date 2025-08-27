<script setup lang="ts">
import img1 from '../../assets/images/training-types/1.svg'
import img2 from '../../assets/images/training-types/2.svg'
import img3 from '../../assets/images/training-types/3.svg'
import img4 from '../../assets/images/training-types/4.svg'
import img5 from '../../assets/images/training-types/5.svg'
import img6 from '../../assets/images/training-types/6.svg'

type TrainingTypes = {
  id: number
  url: string
  title: string
}

const trainingTypes = [
  { id: 1, url: img1, title: 'Maxpump' },
  { id: 2, url: img2, title: 'Aron gym' },
  { id: 3, url: img3, title: 'Fit & tone' },
  { id: 4, url: img4, title: 'Forza' },
  { id: 5, url: img5, title: 'Balance fitness' },
  { id: 6, url: img6, title: 'Body sculpt' },
] as const satisfies ReadonlyArray<TrainingTypes>
</script>

<template>
  <section class="training-types main-container">
    <h2 class="visually-hidden" aria-labelledby="training-types-title">
      Training types
    </h2>

    <ul class="training-types-list">
      <li
        v-for="type in trainingTypes"
        class="training-types-item"
        :key="type.id"
      >
        <img
          class="training-types-img"
          :src="type.url"
          alt=""
          width="150"
          height="140"
          loading="lazy"
        />
        <h3 class="training-types-title">
          {{ type.title }}
        </h3>
      </li>
    </ul>
  </section>
</template>

<style scoped>
.training-types {
  padding-top: 70px;
  padding-bottom: 120px;
}

.training-types-list {
  display: grid;
  grid-template-columns: repeat(6, 1fr);
  gap: 60px;
}

.training-types-item {
  --trainingTypesTtemBgIconSize: 80px;

  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
  row-gap: 32px;
  padding-top: var(--trainingTypesTtemBgIconSize);
  background: url('../../assets/icons/bold-arrow-down-left.svg') 100% 0 /
    var(--trainingTypesTtemBgIconSize) no-repeat;
}

.training-types-img {
  width: 150px;
  height: 140px;
}

.training-types-title {
  font-size: 16px;
  font-weight: 700;
  line-height: 1.75;
  letter-spacing: 0.8px;
}

@media (width <= 1280px) {
  .training-types-list {
    grid-template-columns: repeat(3, 1fr);
    gap: 30px;
  }
}

@media (width <= 767px) {
  .training-types-list {
    grid-template-columns: repeat(2, 1fr);
    gap: 10px;
  }

  .training-types-item {
    --trainingTypesTtemBgIconSize: 50px;

    row-gap: 12px;
  }

  .training-types-img {
    max-width: 120px;
  }
}

@media (width <= 480px) {
  .training-types-list {
    gap: 0;
  }

  .training-types-img {
    max-width: 100px;
  }
}
</style>
