<template>
  <div>
    <div class="card add">
      <div class="cb-container">
        <button id="add-btn" v-on:click="addtodo">+</button>
      </div>
      <div class="txt-container">
        <label for="addt">افزودن </label>
        <input
          type="text"
          class="txt-input"
          placeholder="افزودن وظیفه جدید..."
          spellcheck="false"
          v-model="title"
          id="addt"
          dir="rtl"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: "",
    };
  },
  methods: {
    addtodo() {
      this.$emit("Addnewtodo", this.title);
      this.title = "";
    },
  },
};
</script> 