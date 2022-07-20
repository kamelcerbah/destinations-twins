<template>
  <div class="container">
    <div class="row row-cols-2 justify-content-center">


      <div
        class="card text-start"
        style="width: 18rem"
        v-for="country in filteredCountries"
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
import { ref, toRef,computed  } from "@vue/reactivity";
import { Country, State, City }  from 'country-state-city';
import { stringSimilarity } from "string-similarity-js";
//add computed

export default {
  name: "SearchResult.component",
  props: {
    filteredCountries: {
      type: Array,
      required: false,
    },
  },
  setup(props) {

    const filteredCountries = toRef(props, "filteredCountries");
    console.log(filteredCountries);
    

    return {
      filteredCountries

    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style >
</style>
