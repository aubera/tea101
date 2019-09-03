<template lang="html">
  <div class="side">
    <button
      v-for="(tea, index) in teas"
      type="button"
      :key="index"
      v-bind:class="{ active: index === selectedId }"
      @click.prevent="selected(index)"
    >
      <h2>What is {{ tea.name }}?</h2>
    </button>
  </div>
</template>

<script>
import { eventBus } from "../main";

export default {
  name: "SideNav",
  props: {
    teas: Array
  },
  data() {
    return {
      selectedId: 0
    };
  },
  methods: {
    selected(index) {
      this.selectedId = index;
      eventBus.$emit("selectedTeaIndex", this.selectedId);
    }
  }
};
</script>

<style scoped lang="sass">
.side
  width: 30%

  button
    background-color: #E8C65A
    border: 1px solid #000
    border-radius: 3px
    margin-top: 10px
    width: 250px

    h2
      font-size: 1.5rem
      margin: 5% auto

  .active
    background-color: blue
    color: #fff
</style>
