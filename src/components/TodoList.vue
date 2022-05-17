<template>
  <section>
      <!-- v-for로 뷰 데이터의 아이템 개수만큼 화면에 표시하기 -->
      <!-- index는 v-for 디렉티브에서 기본적으로 제공하는 변수 -->
      <!-- v-for 디렉티브로 반복한 요소는 모두 뷰에서 내부적으로 인덱스를 부여함 -->
      <li v-for="(todoItem, index) in propsdata" :key="todoItem" class="shadow">
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
    // 받는쪽에서 명시
    props: ['propsdata'],

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
