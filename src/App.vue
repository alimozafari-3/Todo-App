<template>
  <div id="app">
    <header class="card">
      <h1>لیست وظایف</h1>
    </header>
    <addtodo-app @Addnewtodo="newtodo"></addtodo-app>
    <main>
      <ul class="todos">
        <todo-app
          v-for="item in gettodo"
          :key="item"
          :todo="item"
          @delete="deletetodo"
          @statuschang="statuschek"
        ></todo-app>
      </ul>

      <div class="card stat">
        <p class="corner">
          <span id="items-left">{{ activetodo }}</span> مورد باقی مانده
        </p>
        <div class="filter">
          <button id="all" :class="{ on: active === 'all' }" @click="changtab('all')">
            همه
          </button>
          <button
            id="active"
            :class="{ on: active === 'active' }"
            @click="changtab('active')"
          >
            فعال
          </button>
          <button
            id="completed"
            :class="{ on: active === 'completed' }"
            @click="changtab('completed')"
          >
            تکمیل
          </button>
        </div>
        <div class="corner">
          <button id="clear-completed" @click="totaldelete">حذف تکمیل شده ها</button>
        </div>
      </div>
    </main>
    <footer>
      <p>
        برای مرتب کردن وظایف میتوانید وظیفه موردنظر را بکشید و رها کنید - Drag And Drop
      </p>
    </footer>
  </div>
</template>

<script>
import addtodo from "./compunent/addtodo.vue";
import todo from "./compunent/todo.vue";

export default {
  components: {
    "addtodo-app": addtodo,
    "todo-app": todo,
  },
  data() {
    return {
      todos: [],
      active: "all",
    };
  },
  computed: {
    activetodo() {
      return this.todos.filter((f) => f.iscompilte === false).length;
    },
    gettodo() {
      switch (this.active) {
        case "all":
          return this.todos;
        case "active":
          return this.todos.filter((f) => f.iscompilte == false);
        case "completed":
          return this.todos.filter((f) => f.iscompilte == true);
      }
    },
  },
  methods: {
    newtodo(title) {
      const todo = {
        id: Math.random().toString(16).slice(2),
        title: title,
        iscompilte: false,
      };
      this.todos.push(todo);
    },
   
  },
};
</script>
