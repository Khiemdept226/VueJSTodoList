<template>
  <div class="app-container">
    <h1 class="app-header">VueJS TodoList</h1>

    <div class="add-task">
      <input
        type="text"
        placeholder="Add new task"
        class="task-input"
        v-model="tasks.name"
      />
      <input
        type="submit"
        class="submit-task"
        title="Add Task"
        v-on:click="newItem"
      />
    </div>
    <ul class="task-list">
      <li
        class="task-list-item"
        v-for="(task, index) in tasks"
        v-bind:key="index"
      >
        <label class="task-list-item-label">
          <input type="checkbox" />
          <span>{{ task.name }}</span>
        </label>
        <!-- <button class="delete-btn">Delete</button> -->
        <span class="delete-btn" title="Delete Task" v-on:click="delItem()"
          >Delelte{{ task.del }}</span
        >
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      tasks: [
        { name: "Today : học VueJS" },
        { name: "Tomorrow : học VueJS" },
        { name: "Daily : học VueJS" }
      ]
    };
  },
  methods: {
    newItem: function() {
      if (!this.tasks.name) {
        return;
      }
      this.tasks.push({
        name: this.tasks.name,
        del: ""
      });
      this.tasks.name = "";
    },
    delItem: function(task) {
      this.tasks.splice(this.tasks.indexOf(task), 1);
    }
  }
};
</script>

<style>
* {
  box-sizing: border-box;
}
body {
  width: 100%;
  height: 100vh;
  margin: 0;
  padding: 15px;
  display: flex;
  justify-content: center;
  align-items: center;
  font-family: sans-serif;
  overflow: hidden;
}
input {
  outline: none;
}
ul {
  list-style: none;
  padding: 0;
}
.app-container {
  min-width: 480px;
  width: 100%;
  max-height: 100%;
  background-color: aqua;
  padding: 25px;
  border-radius: 25px;
  color: #222;
}
.app-header {
  font-size: 25px;
  line-height: 15px;
  margin: 0 0 12px 0;
  color: #272727;
  text-align: center;
}
.submit-task {
  background-color: rgb(140, 165, 192);
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
.add-task {
  height: 40px;
  font-size: 14px;
  display: flex;
}
.task-input {
  width: 100%;
  padding: 0 5px;
  outline: none;
  border: none;
  border-bottom: 1px solid #272727;
  margin-right: 15px;
  color: #272727;
}
.task-list-item {
  background-color: #37dbe7;
  display: flex;
  align-items: center;
  padding: 8px;
  border-radius: 25px;
  margin-bottom: 12px;
}
.task-list-item input {
  width: 16px;
  height: 16px;
  border: 1px solid #272727;
  border-radius: 50%;
}
.task-list-item input:checked {
  background-size: 10px;
  border: 1px solid green;
}
.task-list-item input:checked + span {
  color: #272727;
  text-decoration: line-through #272727;
}
.task-list-item-label {
  display: flex;
  align-items: flex-start;
  color: #272727;
  margin-right: 8px;
  font-size: 14px;
  line-height: 24px;
  position: relative;
  transition: 0.2s;
  cursor: pointer;
}
.delete-btn {
  padding: 5px;
  margin-left: auto;
  margin-right: 5px;
  display: block;
  background-color: #286583;
  color: #37dbe7;
  border: none;
  border-radius: 15px;
  cursor: pointer;
}
</style>
