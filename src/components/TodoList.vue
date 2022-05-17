<template>
  <section>
      <!-- v-for로 뷰 데이터의 아이템 개수만큼 화면에 표시하기 -->
      <!-- index는 v-for 디렉티브에서 기본적으로 제공하는 변수 -->
      <!-- v-for 디렉티브로 반복한 요소는 모두 뷰에서 내부적으로 인덱스를 부여함 -->
      <li v-for="(todoItem, index) in todoItems" :key="todoItem" class="shadow">
        <i class="checkBtn fas fa-check" aria-hidden="true"></i>
        {{ todoItem }}
        <span class="removeBtn" type="button" @click="removeTodo(todoItem, index)">
          <i class="far fa-trash-alt" aria-hidden="true"></i>
        </span>
      </li>
  </section>
</template>


<script>
export default {
    // localStorage 데이터를 뷰 데이터에 저장하기
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
        removeTodo(todoItem, index) {
            // 로컬스토리지에서 지우기
            localStorage.removeItem(todoItem);
            // index부터 1개 삭제
            this.todoItems.splice(index, 1);
        }
    }
}
</script>

<style>
    ul {
        list-style-type: none;
        padding-left: 0px;
        margin-top: 0;
        text-align: left;
    }

    li {
        display: flex;
        min-height: 50px;
        height: 50px;
        line-height: 50px;
        margin: 0.5rem 0;
        padding: 0 0.9rem;
        background: white;
        border-radius: 5px;
    }
    .checkBtn {
        line-height: 45px;
        color: #62acde;
        margin-right: 5px;
    }
    .removeBtn {
        margin-left: auto;
        color: #de4343;
    }
    .list-enter-active, .list-leave-active {
        transition: all 1s;
    }
    .list-enter, .list-leave-to {
        opacity: 0;
        transform: translateY(30px);
    }


</style>
