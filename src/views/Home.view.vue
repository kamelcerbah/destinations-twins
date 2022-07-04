<template>
  <div class="container">
    <div class="row my-3">
      <h1 class="fw-light">Welcome</h1>
      <p class="h3 fw-light">
        Find countries with similar states "only this for now" and cities
      </p>
    </div>
    <form class="form-inline w-25 m-auto">
      <input
        v-model="searchInput"
        class="form-control"
        type="search"
        placeholder="Search"
        aria-label="Search"
      />
      <button
        class="btn btn-outline-success my-2"
        type="submit"
        @click="findSimilarStates"
      >
        Search
      </button>
    </form>
    <SearchResult v-if="searchClicked" :filteredCountries="filteredCountries" />
  </div>
</template>

<script>
// @ is an alias to /src
import SearchResult from "@/components/SearchResult.component.vue";
import { Country, State, City } from "country-state-city";
import { stringSimilarity } from "string-similarity-js";
import { ref } from "vue";
export default {
  name: "HomeView",
  components: {
    SearchResult,
  },
  setup() {
    let searchClicked = ref(false);
    const searchInput = ref("");
    var filteredCountries =[];

    const findSimilarStates = () => {
      //alert(searchInput.value);
      searchClicked.value = searchClicked.value ? false : true;

      let states = State.getAllStates();
      //filter the states that have similar state name to the search input
      if (searchInput.value.length > 2) {
        var filteredStates = states.filter(
          (state) => stringSimilarity(state.name, searchInput.value) > 0.4
        );
       // console.log(filteredStates);




        //get countries from filtered states
        //let countryOne = Country.getCountryByCode(filteredStates[2].countryCode);
        //console.log(countryOne);


        //get countries from filtered states
        
        for (let state of filteredStates) {
          let country = Country.getCountryByCode(state.countryCode);
          filteredCountries.push(country);
        }
        //console.log(filteredCountries);
      }
    };

    return {
      searchInput,
      searchClicked,
      filteredCountries,
      
      findSimilarStates
    };
  },
};
</script>
