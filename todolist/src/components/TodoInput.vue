<script>
export default {
  name: "TodoInput",
  data() {
    return {
      newTodoItem: ''
    }
  },
  methods:{
    addTodo(){
      if (this.newTodoItem !== ""){
        let value = this.newTodoItem && this.newTodoItem.trim();
        console.log(this.newTodoItem);
        localStorage.setItem(this.newTodoItem, this.newTodoItem);
        this.$emit('addTodo', value);
        this.clearInput();
      }
    },
    clearInput(){
      this.newTodoItem = "";
    },

  }
}
</script>

<template>
  <div class="inputBox shadow">
    <input type="text" v-model="newTodoItem" placeholder="Type what you have to do" v-on:keyup.enter="addTodo">
    <span class="addContainer" v-on:click="addTodo">
      <i class="addBtn fa fa-plus" aria-hidden="true"></i>
    </span>
  </div>
</template>

<style scoped>
input:focus{
  outline:none;
}

.inputBox{
  background-color: white;
  height: 50px;
  line-height: 50px;
  border-radius : 5px;
}
.inputBox input{
  border-style: none;
  font-size: 0.9em;
}

.addContainer{
  float: right;
  background: linear-gradient(to right, #6478FB,#8763FB );
  display: inline-block;
  width: 3rem;
  border-radius: 0 5px 5px 0;
 }
.addBtn{
  color: white;
  vertical-align: middle;
}

</style>
