<template>
  <div class="hello">
    <div class="form-group row">
      <label for="example-text-input" class="col-2 col-form-label">TODO：</label>
      <div class="col-4">
        <input class="form-control" type="text" v-model="inputtodo">
      </div>
      <button class="btn btn-primary" @click="addTodo()">新增</button>
    </div>
    <div class="todoborder">
      <ul>
        <li v-for="(todo,index) in todos" :class="{iscomplate:todo.iscomplate}">{{todo.text}}<button class="btn btn-danger" @click="deleteTodo(index)">刪除</button><button class="btn btn-primary" @click="complateTodo(index)">已完成</button></li>
      </ul>
    </div>
    
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      inputtodo: '',
      todos: []
    }
  },
  methods: {
    complateTodo (index){
      this.todos[index].iscomplate = !this.todos[index].iscomplate
    },
    addTodo () {
      var obj = {
        text:this.inputtodo,
        iscomplate: false
      }
      this.todos.push(obj)
    },
    deleteTodo (index) {
      this.todos.splice(index,1)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.todoborder {
  width: 30%;
  margin-left: 15%;
}
.iscomplate {
  text-decoration: line-through;
}
</style>
