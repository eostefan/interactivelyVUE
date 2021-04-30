<template>

  <div id="app">
    <div id="nav">
      <div class="brand">
        <a href="/" class="brand-logo">
          People-App
        </a>
      </div>

      <router-link to="/">Home</router-link>
      <router-link to="/users">Users</router-link>
    </div>
    <router-view/>
  </div>

</template>
<script>

</script>
<style lang="scss">

/* ------------------
    STUFF THAT KEEPS THINGS DRY :))
------------------ */ 

:root {
  --font-def: 'Antonio';
  --font-main: 'Orelega One';
  --text-shadow: 1px 1px rgba(0,0,0,.3);

  --shadow-bottom: 0 8px 6px -6px rgba(0,0,0,.2);

  --red: #AB2346;
  --white: #E6E8E6;
  --black: #130303;

  --charcoal: #233D4D;
  --olive: #A1C181;
  --pine: #619b8a;

  --green: #1C5253;
  --gray: #403F4C;
  --pumpkin: #FE7F2D;
}

/* ------------------
    DEFAULT STYLES
------------------ */ 

*,
*::after,
*::before {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html {
  font-size: 62.5%; /* 10px === 1rem */
}

body {
  font-size: 1.6rem;
  background-color: var(--charcoal);
  font-family: var(--font-def);
}

h1,
h2,
h3 {
  margin: 0;
  font-family: var(--font-main);
}

p, 
small,
strong,
em {
  margin: 0;
}

a,
a:visited {
  text-decoration: none;
}

.btn {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 18rem;
  height: 4rem;
  border-radius: .5rem;
  margin-top: 1vw;
  box-shadow: var(--shadow-bottom);
  text-shadow: var(--text-shadow);
  color: var(--white);
  background-color: var(--pumpkin);
  transition: transform .25s ease;

  &:hover {
    transform: translateY(-.25rem) scale(1.01);
  }

  // created mqs like this, but also at the bottom of the style tag
  // both methods work fine for me personally
  // but I prefer this approach as it seems more organized
  @media screen and (max-width: 31.875em) {
    width: 15rem;
    height: 3.5rem;
    
  }
}

#nav {
  display: flex;
  align-items: center;
  justify-content: flex-end;
  background-color: var(--olive);
  border-bottom: 1px solid var(--gray);
  padding-right: 5vw;
  min-height: 5rem;
  width: 100%;
  position: fixed;
  z-index: 3;

  a {
    display: flex;
    align-items: center;
    justify-content: center;
    color: var(--pine);
    font-size: 2.2rem;
    padding-right: 2vw;
    transition: all .15s ease;



    &:hover {
      transform: translateY(-.25rem);
    }
  }

  .router-link-exact-active {
    color: var(--green) !important;
  }
}

.brand {
  color: var(--white);
  margin-right: auto;
  padding-left: 5vw;
  letter-spacing: .25rem;

  &-logo {
    font-family: var(--font-main);
  }
}

</style>
