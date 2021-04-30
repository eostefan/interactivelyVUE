<template>
  <div class="user">
    <div class="user-avatar">
      <span class="user-initials"> {{ formatAvatar }} {{ user.id }} </span>
    </div>
    <div class="user-details">
      <h2 class="user-name"> {{ user.name }} </h2>
      <p class="user-company"> {{ user.company.name }} </p>
      <a :href="'mailto:'" class="user-email">Email: {{user.email}} </a>
      <a :href="'tel:' + user.phone" class="user-phone">Mobile: {{user.phone}} </a>
      <p class="user-address"> {{ formatAddress }} </p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'User',
  props: ['user', 'formatAvatar', 'formatAddress'],
}
</script>

<style lang="scss">
  .user {
    display: flex;
    flex-direction: column;
    width: 100%;
    padding: 1rem;
    max-width: calc((100% / 2) - 1rem);
    min-height: 30rem;
    color: var(--white);
    border-radius: .5rem;
    background: linear-gradient(65deg, rgba(0,0,0, .75), rgba(0,0,0, .75)), url('../assets/cover2.jpeg');
    background-size: cover;
    background-position: 50% 20%;
    position: relative;
    cursor: pointer;
    border: 2px solid var(--olive);
    transition: all .25s ease;

    &-avatar {
      display: flex;
      align-items: center;
      justify-content: center;
      width: 5rem;
      height: 5rem;
      border-radius: 10rem;
      margin-right: 1rem;
      font-size: 1.8rem;
      color: var(--white);
      background-color: var(--olive);
      transition: all .5s ease-in;
    }

    &-details {
      display: flex;
      flex-direction: column;
      justify-content: center;
      transition: transform .5s ease-in;
      overflow: hidden;
      font-size: 1.4rem;
    }

    &-name {
      margin: .25rem 0;
    }

    &-email,
    &-phone,
    &-email:visited,
    &-phone:visited {
      color: var(--pumpkin);
      text-decoration: none;
    }

    /* -= 359 and down  */
    @media screen and (max-width: 22.4375em) {
      max-width: 100%;
      min-height: 20rem;
      margin: 0 1rem;
    }

    /* -= 767 and up  */
    @media screen and (min-width: 47.9375em) {
      padding: 1rem;
      max-width: calc((100% / 3) - 1rem);

      &-avatar {
        width: 10rem;
        height: 10rem;
      }
      &-name {
        font-size: 2.6rem;
      }
      &-details {
        font-size: 1.8rem;
      }
    }

    /* -= 1199 and up  */
    @media screen and (min-width: 75em) {
      overflow: hidden;
      max-width: calc((100% / 4) - 1rem);

      &-avatar {
        opacity: .8;
        transform: scale(4);
      }
      &-details {
        transform: translateY(15rem);
      }

      &:hover {
        border: 2px solid var(--pumpkin);

        .user-details {
          transform: translateY(5rem);
        }
        .user-avatar {
          opacity: 1;
          background-color: var(--pumpkin);
          transform: scale(1);
        }
      }
    }

    /* -= between 359px and 1199px  */
    @media screen and (min-width: 22.4375em) and (max-width: 47.9375em) {
      min-height: 25rem;
    }
  }
</style>