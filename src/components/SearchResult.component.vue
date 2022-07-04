<template>
  <div class="container">
    <div class="row row-cols-2 justify-content-center">
      <div
        class="card text-start"
        style="width: 18rem"
        v-for="country in countries"
        :key="country.id"
      >
        <!-- <img :src="`http://localhost/destination-twins-images/${country.name}.jpg`" class="card-img-top" alt="flag" /> -->
        <img
          :src="` https://flagcdn.com/256x192/${country.isoCode.toLowerCase()}.png `"
          width="256"
          height="192"
          class="card-img-top"
          :alt="country.name"
        />
        <div class="card-body">
          <p class="card-text">
            {{ country.name }} has a similar state name , learn more about them.
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { ref, toRef } from "@vue/reactivity";
import { Country, State, City }  from 'country-state-city';
import { stringSimilarity } from "string-similarity-js";

export default {
  name: "SearchResult.component",
  props: {
    searchInput: String,
  },
  setup(props) {
    //props
    const searchInput = toRef(props, "searchInput");

  
    

    //get all countries from the country-state-city library
    let countries = Country.getAllCountries();
    //filter the countries that have similar state name to the search input
    // let filteredCountries = countries.filter(
    //   (country) =>
    //     country.name.toLowerCase().includes(props.searchInput.toLowerCase())
    // );



    //get all states from the country-state-city library
    let states = State.getAllStates();
    //filter the states that have similar state name to the search input
     if(searchInput.value.length >2){
     var filteredStates = states.filter(
       (state) =>
          stringSimilarity(state.name, searchInput.value) > 0.4
     );
     //console.log(filteredStates);
     }

     //fileter contries that have similar state name to the search input
 
    

    return {
      searchInput,
      countries,
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style >
</style>
