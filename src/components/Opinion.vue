<template>
  <div class="opinion">
    <div class="img-container">
      <div class="img"></div>
      <h3>{{ user.name }}</h3>
    </div>
    <div class="text">
      <p>{{ user.opinion }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "Opinion",
  props: {
    user: Object
  }
};
</script>

<style scoped lang="sass">
.opinion
  margin-top: -3%
  display: flex
  align-items: center
  justify-content: space-between

  .img-container
    display: flex
    flex-direction: column
    align-items: center
    width: 30%

    .img
      background-image: url("https://s-media-cache-ak0.pinimg.com/564x/75/d3/12/75d3127d64388683f9723f301547009c.jpg")
      background-position: center
      background-repeat: no-repeat
      background-size: cover
      border-radius: 50%
      border: 1px solid #000
      height: 250px
      width: 250px

  .text
    background-color: #E3E6ED
    border-radius: 5px
    text-align: justify
    padding: 1% 3%
    width: 61%
</style>
