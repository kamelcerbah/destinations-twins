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

</style>
