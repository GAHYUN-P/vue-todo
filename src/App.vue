<template>
  <div id="app">
    <!-- 컴포넌트 태그 추가 -->
    <TodoHeader></TodoHeader>
    <!-- 할일 추가 버튼을 클릭했을 때 App 컴포넌트로 이벤트를 전달할 수 있게 v-on 디렉티브를 추가 -->
    <TodoInput v-on:addTodo="addTodo"></TodoInput>
    <!-- props 전달 -->
    <TodoList v-bind:propsdata="todoItems"></TodoList>
    <TodoFooter></TodoFooter>
  </div>
</template>

<script>
// 각 vue file import 해주기
import TodoHeader from './components/TodoHeader.vue'
import TodoFooter from './components/TodoFooter.vue'
import TodoList from './components/TodoList.vue'
import TodoInput from './components/TodoInput.vue'

// 컴포넌트 등록
export default {

    data() {
      return {
        todoItems: []
      }
    },

    // 뷰의 인스턴스가 생성되자마자 뷰 데이터에 접근할 수 있도록
    // created 라이프 사이클 훅에서 로컬스토리지의 데이터를 뷰 데이터로 옮김
    created() {
        if (localStorage.length > 0) {
            for(var i = 0; i < localStorage.length; i++) {
                this.todoItems.push(localStorage.key(i));
            }
        }
    },

    methods: {
      addTodo(todoItem) {
        localStorage.setItem(todoItem, todoItem);
			  this.todoItems.push(todoItem);
      }
    },

    components: {
      "TodoHeader": TodoHeader,
      "TodoInput": TodoInput,
      "TodoList": TodoList,
      "TodoFooter": TodoFooter,
    }
}
</script>

<style>
  body {
      text-align: center;
      background-color: #F6F6F8;
  }
  input {
      border-style: groove;
      width: 200px;
  }
  button {
      border-style: groove;
  }
  .shadow {
      box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03)
  }
</style>
