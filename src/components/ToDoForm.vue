<template>
  <form @submit.prevent="onSubmit">
    <label for="new-todo-input" class="label__lg">
      What needs to be done?
    </label>
    <input 
      type="text"
      id="new-todo-input"
      name="new-to-do"
      autocomplete="off"
      v-model.lazy.trim="userInput"
      class="input__lg"
      >
      <button type="submit" class="btn btn__primary btn__lg">
        Add
      </button>
  </form>
</template>

<script>
  export default {
    methods: {
      onSubmit() {
        if(this.userInput === "") {
          return;
        }
        this.$emit("todo-added", this.userInput);
        this.userInput = "";
      }
    },
    data() {
      return {
        userInput: ""
      }
    }
  }
</script>