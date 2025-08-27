<script setup lang="ts">
import img1 from '../../assets/images/motivation/1.jpg'
import img2 from '../../assets/images/motivation/2.jpg'

type CardTitle = {
  main: string
  sub: string
}

type Card = {
  id: number
  title: CardTitle
  dataTitle: string
  description: string
  img: string
  alt: string
}

const motivationCards = [
  {
    id: 1,
    title: {
      main: 'Be you, just stronger!',
      sub: 'power is in you',
    },
    dataTitle: 'Strong',
    description:
      'Unum solum justo ex ius. Pro cu probo laboramus eius insolens euripidis te eos, ut agam tota.',
    img: img1,
    alt: 'Man doing pull-ups on horizontal bar',
  },
  {
    id: 2,
    title: {
      main: 'Today is the best',
      sub: 'day to start!',
    },
    dataTitle: 'Start',
    description:
      'Sed abhorreant constituam consectetuer eu. At mei clita deserunt, his movet molestie nemore.',
    img: img2,
    alt: 'Man with dumbbell',
  },
] as const satisfies ReadonlyArray<Card>
</script>

<template>
  <section class="motivation">
    <h2 class="visually-hidden" aria-labelledby="motivation-title">
      Motivation
    </h2>

    <ul class="motivation-list">
      <li
        v-for="card in motivationCards"
        class="motivation-item"
        :key="card.id"
      >
        <div class="motivation-card container">
          <div class="motivation-card-body">
            <h3
              class="motivation-card-title title-medium backdrop-title"
              :data-title="card.dataTitle"
            >
              {{ card.title.main }} <br />
              {{ card.title.sub }}
            </h3>
            <div class="motivation-card-description">
              <p>{{ card.description }}</p>
            </div>
            <a class="motivation-card-button button transparent" href="/">
              View more
            </a>
          </div>
          <img
            class="motivation-card-image"
            :src="card.img"
            :alt="card.alt"
            width="518"
            height="760"
            loading="lazy"
          />
        </div>
      </li>
    </ul>
  </section>
</template>

<style scoped>
.motivation-item:nth-child(even) {
  background-color: var(--color-dark-alternate);
}

.motivation-item:nth-child(even) .motivation-card {
  flex-direction: row-reverse;
}

.motivation-card {
  display: flex;
  justify-content: start;
  align-items: center;
  column-gap: clamp(30px, 10.42vw, 200px);
}

.motivation-card-title:not(:last-child) {
  margin-bottom: 14px;
}

.motivation-card-description:not(:last-child) {
  max-width: 400px;
  margin-bottom: 37px;
  line-height: 1.75;
  letter-spacing: 0.8px;
}

.motivation-card-body {
  padding-left: 35px;
}

.motivation-card-image {
  margin-block: -60px;
}

.motivation-item:last-child .motivation-card-image {
  margin-block-end: 0;
}

@media (width <= 1919px) {
  .motivation-card-image {
    margin-block: -20px;
  }
}

@media (width <= 1024px) {
  .motivation-card {
    padding-block: 50px;
  }

  .motivation-card-image {
    width: 30%;
    margin-block: 0;
  }
}

@media (width <= 767px) {
  .motivation-card,
  .motivation-item:nth-child(even) .motivation-card {
    flex-direction: column-reverse;
  }

  .motivation-card {
    row-gap: 30px;
    padding-block: 30px;
  }

  .motivation-card-description:not(:last-child) {
    margin-bottom: 20px;
  }

  .motivation-card-image {
    width: 60%;
  }
}
</style>
