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
          :alt="country.name"
        />
        <div class="card-body">
          <p class="card-text">
            {{ country.name }} have similar state name , learn more about them.
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { ref, toRef } from "@vue/reactivity";
import { Country, State, City }  from 'country-state-city';
export default {
  name: "SearchResult.component",
  props: {
    searchInput: String,
  },
  setup(props) {
    let countries = Country.getAllCountries();
    console.log(countries[0].name);

    const title = toRef(props, "searchInput");
    console.log(title.value);

    return {
      title,
      countries,
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style >
</style>
