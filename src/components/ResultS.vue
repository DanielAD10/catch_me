<template>
  <p>Result is {{score}}ms.</p>
  <div v-if="score<250">
      <p>You're too fast!!</p>
  </div>
  <div v-else-if="score>250 && score<500">
      <p>You're normal.....</p>
  </div>
  <div v-else>
      <p>You're too slow!! Try Again</p>
  </div>
</template>

<script>
export default {
    props:['score']
}
</script>

<style>

</style>