<template lang="html">
  <div class="description">
    <p>{{ tea }}</p>
  </div>
</template>

<script>
export default {
  name: "Description",
  props: {
    tea: String
  }
};
</script>

<style scoped lang="sass">
.description
  min-height: 550px
  width: 67%

  p
    text-align: justify
</style>
