<template>
  <div>
      <ComTest v-bind:card="card"/>
  </div>
</template>

<script>
import ComTest from "../components/ComTest"
export default {
    components:{
        ComTest
    }
}
</script>

<style>

</style>