<template>
  <section>
      <!-- transition-group태그는 목록에 애니메이션을 추가할 때 사용되는 태그 -->
      <transition-group name="list" tag="ul">
        <!-- v-for로 뷰 데이터의 아이템 개수만큼 화면에 표시하기 -->
        <!-- index는 v-for 디렉티브에서 기본적으로 제공하는 변수 -->
        <!-- v-for 디렉티브로 반복한 요소는 모두 뷰에서 내부적으로 인덱스를 부여함 -->
        <!-- :key는 v-bind:key를 간략하게 표현한 것 -->
        <li v-for="(todoItem, index) in propsdata" :key="todoItem" class="shadow">
          <i class="checkBtn fas fa-check" aria-hidden="true"></i>
          {{ todoItem }}
          <span class="removeBtn" type="button" @click="removeTodo(todoItem, index)">
            <i class="far fa-trash-alt" aria-hidden="true"></i>
          </span>
        </li>
      </transition-group>
  </section>
</template>


<script>
export default {
    // 받는쪽에서 명시
    props: ['propsdata'],

    methods: {
        removeTodo(todoItem, index) {
            this.$emit('removeTodo', todoItem, index);
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
