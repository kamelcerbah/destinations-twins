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
        @click="similarCountries"
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
    var filteredCountries = ref([]);

    /* FUNCTIONs */
    const getSimilarStates = () => {
      let filteredStates = [];

      //get all states of the world with country-state-city library
      let states = State.getAllStates();

      //filter the states that have similar state name to the search input
      //when search input is over 3 characters

      filteredStates = states.filter(
        (state) => stringSimilarity(state.name, searchInput.value) > 0.4
      );

      return filteredStates;
    };
    const similarCountries = async () => {
      // searchResult switching
      searchClicked.value = searchClicked.value ? false : true;

      let filteredStates = [];

      //get countries from filtered states

      filteredStates = await getSimilarStates();
      //console.log(filteredStates);
      filteredCountries.value = [];

      for (let state of filteredStates) {
        let country = Country.getCountryByCode(state.countryCode);
        filteredCountries.value.push(country);
      }
      
    };

    return {
      searchInput,
      searchClicked,
      filteredCountries,
      similarCountries,
    };
  },
};
</script>
