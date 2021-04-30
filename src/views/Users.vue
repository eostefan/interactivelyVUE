<template>
  <div class="users">
    <div class="users-filter">
      <form class="form" @submit.prevent="">
        <input v-model="searchQuery" type="text" name="search" id="search" placeholder="Search by name: Leanne" class="form-input" autocomplete="off">
        <select name="form-select" id="form-select" class="form-select" v-model="filterQuery">
          <option selected>Select sorting type</option>
          <option value="desc">Sort descending</option>
          <option value="asc">Sort ascending</option>
        </select>
      </form>
    </div>
    <div class="users-wrap">
      <User
        v-for="(user, idx) in searchFilter" 
        :key="user.id" 
        :user="user" 
        :format-address="formatAddress(idx)" 
        :format-avatar="formatAvatarName(idx)">
      </User>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import User from '@/components/User.vue';

export default {
  name: 'Users',
  components: {
    User
  },
  mounted: function() {
    axios.get('https://jsonplaceholder.typicode.com/users').then((response) => {
      this.users = response.data;
    });
  },
  data() {
    return {
      users: [],
      searchQuery: null,
      filterQuery: 'Select sorting type'
    }
  },
  methods: {
    formatAddress(idx) {
      let self = this;
      return `${self.users[idx].address.city }, 
              ${self.users[idx].address.city}, 
              ${self.users[idx].address.zipcode}`;
    },
    formatAvatarName(idx) {
      let self = this;
      const nameArr = self.users[idx].name.split(' ');
      return nameArr.reduce((result, word) => result += word.slice(0,1), '');
    }
  },
  computed: {
    searchFilter() {
      let users = [...this.users];
      if(this.searchQuery) {
        return this.users.filter(user => user.name.toLowerCase().includes(this.searchQuery.toLowerCase()));
      }
      else if (this.filterQuery === 'desc') {
        users.sort((a, b) => b.id - a.id);
        return users;
      }
      else if (this.filterQuery === 'asc') {
        users.sort((a, b) => a.name - b.name);
        return users;
      }
      else {
        return users;
      }
    },
  }
}
</script>

<style lang="scss">
  .users {
    margin: 0 auto;
    padding: 10rem 0;
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
    background-image: linear-gradient(45deg, rgba(254, 129, 45, 0.418) 15%, rgba(0,0,0, .95) 100%), url('../assets/cover.jpg');
    min-height: 100vh;
    // min-height: 100vh;
    // background-image: linear-gradient(45deg, #489FB5, #16697A);

    &-wrap {
      display: flex;
      align-items: flex-start;
      justify-content: flex-start;
      flex-wrap: wrap;
      gap: 1rem;
      padding: 0 .5rem;
      max-width: 140rem;
      width: 100%;
      margin: 0 auto;

      /* -= 767 and up  */
      @media screen and (max-width: 47.9375em) {
        grid-gap: 0;
        justify-content: space-evenly;
        grid-row-gap: 1rem;
      }
    }

    &-filter {
      display: flex;
      flex-direction: row;
      justify-content: center;

      width: 100%;
      max-width: 90rem;
      margin: 0 auto 4rem;
    }
  }

  .form {
    display: flex;
    justify-content: center;
    width: 100%;
    margin: 0 1rem;
  }

  .form-input {
    width: 100%;
    max-width: 48rem;
    height: 3rem;
    padding: 0 0 0 1rem;
    box-shadow: var(--shadow-bottom);
    border: 1px solid transparent;

    &:focus {
      outline: none;
      border: 1px solid var(--pumpkin);
    }
  }

  .form-select {
    width: 100%;
    max-width: 14rem;
    margin-left: 1rem;
    cursor: pointer;
    color: var(--white);
    background: var(--pumpkin);
  }

  .form-select option {
    padding: 1rem 0;
  }

  .form-select {
    border: 0;
  }
</style>
