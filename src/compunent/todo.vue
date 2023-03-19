<template>
  <div>
    <li class="card" draggable="true">
      <div class="cb-container">
        <input
          type="checkbox"
          class="cb-input"
          :checked="todo.iscompilte ? true : false"
          @click="statuschang"
        />
        <span class="check"></span>
      </div>
      <del class="item" v-if="todo.iscompilte">{{ todo.title }}</del>
      <span v-else>{{ todo.title }}</span>

      <button class="clear" @click="deletetodo">
        <img src="src/assets/images/icon-cross.svg" alt="Clear it" />
      </button>
    </li>
  </div>
</template>

<script>
export default {
  props: {
    todo: Object,
  },
  methods: {
    deletetodo() {
      if (confirm("حذف شود؟")) {
        this.$emit("delete", this.todo.id);
      }
    },
    statuschang() {
      this.$emit("statuschang", this.todo.id, !this.todo.iscompilte);
    },
  },
};
</script>