<template>
    <div class="inputBox shadow">
        <!-- v-model 디렉티브 : 폼에 입력한 값을 뷰 인스턴스의 데이터와 즉시 동기화합니다. -->
        <!-- 화면에 입력된 값을 저장하여 서버에 보내거나 watch와 같은 고급 속성을 이용하여 추가 로직을 수행할 수 있습니다. -->
        <input type="text" v-model="newTodoItem" placeholder="Type what you want to do" v-on:keyup.enter="addTodo">
        <span class="addContainer" v-on:click="addTodo">
            <i class="addBtn fa fa-plus" aria-hidden="true"></i>
        </span>
    </div>
</template>

<script>
export default {
    data() {
        return {
            newTodoItem: ''
        }
    },
    methods: {
        // 입력받은 텍스트를 로컬 스토리지에 저장하기
        // setItem()은 로컬스토리지에 데이터를 추가하는 API이다.
        // 형식은 키, 값 형태.
        // 여기서는 저장 기능 단순화를 위해 키, 값 모두 입력받은 텍스트로 지정하였다.
        addTodo() {
            // 인풋 박스의 입력 값이 있을 때만 저장
            if(this.newTodoItem !==""){
                // 인풋 박스에 입력된 텍스트의 앞뒤 공백 문자열 제거
                var value = this.newTodoItem && this.newTodoItem.trim();
                localStorage.setItem(value, value);
                // 인풋 박스의 입력 값을 초기화
                this.clearInput();
            }
        },
        clearInput() {
            this.newTodoItem = "";
        }
    }
}
</script>

<style scoped>
 input:focus{
     outline: none;
 }
 .inputBox {
     background: white;
     height: 50px;
     line-height: 50px;
     border-radius: 5px;
 }
 .inputBox input {
     border-style: none;
     font-size: 0.9rem;
 }
 .addContainer {
     float: right;
     background: linear-gradient(to right, #6478FB, #8763FB);
     /* display: inline-block; */
     width: 3rem;
     border-radius: 0 5px 5 px 0;
 }
 .addBtn {
     color: white;
     vertical-align: middle;
 }
</style>
