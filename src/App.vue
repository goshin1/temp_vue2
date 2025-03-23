<template>
  <div id="app">
    <div>
      <h1>Vuex</h1>
      <p>Count : {{ count }}</p>
      <p>Double : {{ doubleCount }}</p>
      <button @click="increment">+</button>
    </div>
    <h1>ToDoList</h1>
    <input type="text" v-model="newTask" @keyup.enter="addTask" placeholder="새로운 할 일">
    <button @click="addTask">Add</button>
    <ul>
      <li v-for="(task, index) in tasks" :key="index">
        {{ task }}
        <button @click="removeTask(index)">삭제</button>
      </li>
    </ul>
  </div>
</template>

<script>
import { mapState, mapMutations, mapGetters } from 'vuex';

export default {
  name: 'App',
  data(){
    return {
      newTask : '',
      tasks : []
    }
  },
  computed : {
    ...mapState(['count']),
    ...mapGetters(['doubleCount'])
  },
  methods : {
    addTask(){
      if(this.newTask.trim()){
        this.tasks.push(this.newTask);
        this.newTask = "";
      }
    },
    removeTask(index){
      this.tasks.splice(index, 1);
    },
    ...mapMutations(['increment'])
  }
}
</script>

<style>

</style>
