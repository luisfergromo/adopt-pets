<template>
  <div>
    <!-- {{$route.params.species}} -->
    <h1>
      <b>{{animal.name}}</b>
      – ({{$route.params.species}})
    </h1>
    <p>
      <b>Age:</b>
      {{animal.age}} years old.
    </p>
    <p>
      <b>Breed:</b>
      {{animal.breed}}
    </p>
    <!-- {{$route.params.id}} -->
  </div>
</template>
<script>
import { mapState } from "vuex";
export default {
  data() {
    return {
      animal: {}
    };
  },
  computed: {
    ...mapState(["cats", "dogs"])
    // cats(){
    //   return this.$store.state.cats
    // }
  },
  mounted() {
    const animal = this[this.$route.params.species][this.$route.params.id];
    this.animal = animal;
  }
};
</script>
