<template>
  <div class="home">
    <div class="home-message">
      <h1 class="home-title">
        hello from <span class="home-accent">home</span>
      </h1>
      <p class="home-tag">From the people that brought you 'hello world'</p>

      <router-link to="/users" class="btn btn-xl">
        Check out the users
      </router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Home',
}
</script>

<style lang="scss">
  .home {
    display: flex;
    align-items: center;
    background-size: cover;
    padding-top: 10vw;
    background-position: bottom;
    background-image: linear-gradient(45deg, rgba(254, 129, 45, 0.418) 15%, rgba(0,0,0, .95) 100%), url('../assets/cover.jpg');
    min-height: 100vh;
    color: var(--white);

    &-message {
      display: flex;
      padding-left: 12vw;
      flex-direction: column;
    }

    &-tag {
      padding: .5rem 0;
      text-align: center;
      letter-spacing: .5rem;
      color: var(--charcoal);
      background-color: var(--olive);
    }

    &-title {
      font-size: 7rem;
      text-shadow: var(--text-shadow);
    }

    &-accent {
      position: relative;
      z-index: 1;
      padding: 0 1rem;

      &::before {
        content: ' ';
        width: 100%;
        height: 100%;
        position: absolute;
        background-color: var(--pumpkin);
        top: 0;
        left: 0;
        z-index: -1;
        transform: skew(-10deg);
      }
    }

    // desktop first for the hp
    // 700px and down
    @media screen and (max-width: 43.75em) {
      &-title {
        font-size: 5rem;
      }
      &-tag {
        font-size: 1.3rem;
        padding: .5rem;
        letter-spacing: .25rem;
      }
    }

    // 510px and down
    @media screen and (max-width: 31.875em) {
      &-message {
        padding-left: 5vw;
      }
    }

    // 436px and down
    @media screen and (max-width: 27.25em) {
      &-title {
        font-size: 3.5rem;
      }
      &-tag {
        font-size: 1.2rem;
        padding: .5rem;
        letter-spacing: .15rem;
      }
      &-message {
        padding-left: 5vw;
      }
    }
  }
</style>