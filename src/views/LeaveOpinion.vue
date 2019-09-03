<template lang="html">
  <div class="feedback">
    <div class="img"></div>
    <div class="opinion">
      <h1>Leave your opinion</h1>
      <label for="name">NAME</label>
      <input
        type="text"
        name="name"
        v-model="userOpinion.name"
        placeholder="Type here..."
      />
      <label for="opinion">OPINION</label>
      <textarea
        type="text"
        name="opinion"
        v-model="userOpinion.opinion"
        rows="5"
        placeholder="Type here..."
      >
      </textarea>
      <button type="button" name="button" @click.prevent="submit">
        SUBMIT
      </button>
    </div>
  </div>
</template>

<script>
import { eventBus } from "../main";

export default {
  data() {
    return {
      userOpinion: {
        name: "",
        opinion: ""
      }
    };
  },
  methods: {
    submit() {
      eventBus.$emit("userOpinion", this.userOpinion);
      this.$router.push("detail");
    }
  }
};
</script>

<style scoped lang="sass">
.feedback
  align-items: center
  display: flex
  height: 100vh
  width: 100vw

  .img
    background-image: url('http://www.winemag.com/wp-content/uploads/2016/02/taiwantea.jpg')
    background-position: center
    background-repeat: no-repeat
    background-size: cover
    height: 100%
    width: 50%

  .opinion
    display: flex
    flex-direction: column
    margin: auto

    h1
      margin: 0

    textarea, input
      border-radius: 2px
      border: 1px solid #ccc
      padding: 5px
      font-size: 1rem
      min-width: calc(100% - 10px)
      max-width: calc(100% - 10px)

    input
      height: 30px

    textarea
      min-height: 100px
      max-height: 100px

    label, button
      font-size: .75rem
      font-weight: 900

    label
      align-self: flex-start
      margin-top: 10px

    button
      margin-top: 10px
      border: 3px solid #E8C65A
      border-radius: 30px
      background-color: transparent
      align-self: flex-end
      height: 50px
      color: #2E44A7
      width: 100px
</style>
