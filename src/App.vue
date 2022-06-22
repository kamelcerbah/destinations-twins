<template>
  <div class="container mt-5 mx-auto text-center">
    <nav>
      <ul class="nav justify-content-center">
        <li class="nav-item mx-2">
          <router-link class="btn btn-outline-success" to="/">Home</router-link>
        </li>
        <li class="nav-item mx-2">
          <router-link class="btn btn-outline-success" to="/about">About</router-link>
        </li>
      </ul>
    </nav>

    <router-view />
  </div>
</template>

<style>
/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
} */
</style>
