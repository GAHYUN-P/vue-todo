<template>
  <div id="app">
    <!-- 컴포넌트 태그 추가 -->
    <TodoHeader></TodoHeader>
    <TodoInput></TodoInput>
    <TodoList></TodoList>
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
