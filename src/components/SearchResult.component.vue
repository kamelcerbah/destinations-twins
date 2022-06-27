<template>
  <div>
    <h1>{{title}}</h1>
   
  </div>
</template>

<script>
import { ref,toRef } from '@vue/reactivity';
export default {
  name: 'SearchResult.component',
  props: {
    searchInput: String
  },
  setup(props) {
   
    const title = toRef(props, 'searchInput');
    console.log(title.value);




    return {
      title
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style >
</style>
