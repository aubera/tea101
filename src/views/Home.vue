<template>
  <div class="home">
    <h1>Delicious</h1>
    <h1>Delights</h1>
    <button @click="$router.push('details')">
      <h2>Check 'em out!</h2>
    </button>
  </div>
</template>

<style scoped lang="sass">
.home
  margin: 200px auto
  width: 70vw

  h1
    font-size: 5rem
    margin: 0
    text-align: right

  button
    background-color: #E8C65A
    border: 1px solid #000
    float: right

    h2
      font-size: 1.5rem
      margin: 5% auto
</style>
