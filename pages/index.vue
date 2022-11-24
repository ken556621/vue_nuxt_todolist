<template>
  <main>
    <div class="inputArea">
      <input 
        type="text" 
        v-model="newTask" 
        placeholder="Please add new item!" 
        @keypress.enter="addTask"
      />
      <button @click="addTask">
        Add Item
      </button>
    </div>
    <div class="todoList">
      <Task
        v-for="(task, i) in $store.state.tasks"
        :key="i"
        :task="task" 
      />
    </div>
  </main>
</template>

<script>
  export default {
    data() {
      return {
        newTask: ""
      }
    },
    methods: {
      addTask(){
        if (this.newTask) {
        this.$store.commit('ADD_TASK', this.newTask);
        this.newTask = "";
      }
      }
    }
  }
</script>