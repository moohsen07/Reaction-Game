<template>
  <p v-if="score <= 400">Whoooo ,You are very observant 😀</p>
  <p v-else-if="score <= 700">You are immediate 😉</p>
  <p v-else>Your are very slowely 😥</p>
  <p class="score">Reaction Score is : {{ score }}</p>
</template>

<script>
export default {
  props: ["score"],
};
</script>

<style>
p.score {
  color: crimson;
  font-size: 18px;
  font-weight: bold;
}
p {
  color: #307f73;
  font-size: 27px;
  font-weight: bold;
}
</style>