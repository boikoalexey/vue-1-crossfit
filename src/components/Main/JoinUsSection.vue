<script setup lang="ts">
import posterImg from '../../assets/images/video-placeholder.jpg'
</script>

<template>
  <section class="join-us">
    <div class="join-us-video-wrapper">
      <video
        class="join-us-video"
        src=""
        width="960"
        height="600"
        :poster="posterImg"
      ></video>
      <button class="join-us-video-play-button" type="button">Play</button>
    </div>
    <div class="join-us-body container">
      <h2 class="join-us-title">Join us</h2>
      <form class="join-us-form">
        <header class="join-us-form-header">
          <h3
            class="join-us-form-title title-big backdrop-title centered"
            data-title="Go!"
          >
            Start Here
          </h3>
          <div class="join-us-form-subtitle">
            <p>Fill the form below to start your journey</p>
          </div>
        </header>
        <div class="join-us-form-body">
          <label class="visually-hidden" for="username">Name</label>
          <input
            name="username"
            class="join-us-form-input input"
            type="text"
            autocomplete="name"
            placeholder="Name"
            id="username"
          />
          <label class="visually-hidden" for="email">Email</label>
          <input
            name="email"
            class="join-us-form-input input"
            type="email"
            autocomplete="email"
            placeholder="Email"
            id="email"
          />
          <button class="join-us-form-button button transparent" type="submit">
            Subscribe
          </button>
        </div>
      </form>
    </div>
  </section>
</template>

<style scoped>
.join-us-video-wrapper {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 150px 30px;
  background: url('../../assets/images/join-us-bg.jpg') center/cover no-repeat
    var(--color-dark-alternate);
}

.join-us-video-play-button {
  position: absolute;
  top: 50%;
  left: 50%;
  translate: -50% -50%;
  display: inline-flex;
  justify-content: center;
  align-items: center;
  column-gap: 4px;
  width: 200px;
  aspect-ratio: 1;
  font-size: 14px;
  font-weight: 700;
  color: var(--color-light);
  text-transform: uppercase;
  background-color: transparent;
  border-radius: 50%;
  border: var(--border);
}

.join-us-video-play-button::after {
  content: '';
  width: 26px;
  aspect-ratio: 1;
  background: url('../../assets/icons/bold-arrow-top-right.svg') center/contain
    no-repeat;
  transition-duration: var(--transition-duration);
}

.join-us-video-play-button:hover {
  color: var(--color-dark);
  background-color: var(--color-light);
}

.join-us-video-play-button:hover::after {
  filter: invert(1);
}

.join-us-body {
  padding-bottom: 150px;
}

.join-us-title {
  position: relative;

  margin-top: -0.4em;
  font-size: clamp(64px, 9.37vw, 180px);
  line-height: 1;
  text-align: center;
}

.join-us-title::after {
  content: '';
  display: inline-block;
  aspect-ratio: 1;
  height: 0.7em;
  margin-left: 0.14em;
  background: url('../../assets/icons/bold-arrow-down-right.svg') center/contain
    no-repeat;
  scale: 1 -1;
}

.join-us-title:not(:last-child) {
  margin-bottom: 130px;
}

.join-us-form-header {
  display: flex;
  flex-direction: column;
  align-items: center;
  row-gap: 7px;
}

.join-us-form-header:not(:last-child) {
  margin-bottom: 52px;
}

.join-us-form-subtitle {
  font-size: 20px;
  line-height: 1.65;
  text-transform: uppercase;
  color: var(--color-light);
  text-align: center;
}

.join-us-form-body {
  display: flex;
  justify-content: center;
  column-gap: 20px;
}

.join-us-form-input {
  max-width: 400px;
}

@media (width <= 1024px) {
  .join-us-body {
    padding-bottom: 80px;
  }

  .join-us-title:not(:last-child) {
    margin-bottom: 80px;
  }
}

@media (width <= 767px) {
  .join-us-video-play-button {
    width: 140px;
  }


  .join-us-title:not(:last-child) {
    margin-bottom: 40px;
  }

  .join-us-form-subtitle {
    font-size: 16px;
  }

  .join-us-form-body {
    flex-direction: column;
    align-items: center;
    row-gap: 20px;
  }
}
</style>
