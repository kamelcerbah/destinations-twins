<template>
  <div class="home ">
    <h1 class="h1 fw-light">This is a home page</h1>
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.component.vue'

export default {
  name: 'HomeView',
  components: {
    HelloWorld
  }
}
</script>
