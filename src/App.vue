<template>
  <div id="app">
    <div id="nav">
      <img alt="Nutrio logo" src="./assets/logo-final.png" />
      <div class="router">
        <router-link to="/">Home</router-link> |
        <router-link to="/about">About</router-link>
      </div>
    </div>
    <b-container>
      <router-view />
    </b-container>
  </div>
</template>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Quicksand:wght@300;400;500;600;700&display=swap");

#app {
  font-family: "Quicksand", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }

  img {
    max-width: 300px;
    width: 5%;
  }
}

.spacer {
  margin: 40px auto 40px;
}

.green-button {
  background-color: #aaca5b;
  padding: 16px 64px;
  border-radius: 7px;
  border: 1px solid #9c9797;
  color: white;
  font-weight: 800;
}

.green-button:focus {
  outline: none !important;
}

.green-button:hover {
  background-color: #839c43;
  cursor: pointer;
}
</style>
