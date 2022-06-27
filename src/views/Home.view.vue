<template>
  <div class="container">
    <div class="row my-3">
      <h1 class="fw-light">Welcome</h1>
      <p class="h3 fw-light">Find countries with similar states "only this for now" and cities</p>
    </div>
    <form class="form-inline w-25 m-auto ">
      <input
        v-model="searchInput"
        class="form-control "
        type="search"
        placeholder="Search"
        aria-label="Search"
      />
      <button class="btn btn-outline-success my-2" type="submit" @click="findSimilarStates">Search</button>
    </form>
    <SearchResult v-if="searchClicked" :searchInput="searchInput" />
    
  </div>
</template>

<script>
// @ is an alias to /src
import SearchResult from "@/components/SearchResult.component.vue";
import { ref } from 'vue';
export default {
  name: "HomeView",
  components: {
    SearchResult,
  },
  setup(){
    let searchClicked = ref(false);
    const searchInput = ref('');
    const findSimilarStates = () => {
      //alert(searchInput.value);
      searchClicked.value =  searchClicked.value ? false : true;

    };
  
    
    return {
      searchInput,
      searchClicked,
      findSimilarStates,
    }
  }
};
</script>
