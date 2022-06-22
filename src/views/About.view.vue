<template>
  <div class="about">
    <h1>{{text}}</h1>
    <!--

      <div class="card" style="width: 18rem;">
  <img src="..." class="card-img-top" alt="...">
  <div class="card-body">
    <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
  </div>
</div>
    -->
    <!--show the country in a bootstrap  card-->
    <div class="card" >
      <div class="card-body">
        <h5 class="card-title">{{country.name}}</h5>
        <p class="card-text">{{country.isoCode}}</p>
      </div>
    </div>

  </div>
</template>

<script>
import { Country, State, City }  from 'country-state-city';


export default ({
  setup() {
   
    console.log(Country.getAllCountries());
    let country = Country.getAllCountries()[0];
     let text = 'This is '+ country.name ;
    return {
      text,
      country

    }
  },
})
</script>
