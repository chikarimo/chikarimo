<script setup>
import {ref} from "vue";
import {statuses} from "../const/statuses";

const input = ref("");
const inputDate = ref("");

const isErrMsg = false;

const onSubmitForm = () => {

    //ローカルストレージからデータを取得
    const items = JSON.parse(localStorage.getItem("items")) || [];

    //保存するタスクのオブジェクト作成
    const newItem = {
        id: items.length,
        content: input.value,
        limit: inputDate.value,
        state: statuses.NOT_START,
        onEdit: false,
    };

    //配列にデータを保管
    items.push(newItem);
    //配列データをローカルストレージに保存
    localStorage.setItem("items",JSON.stringify(items));
}
</script>

<template>
    <header>
        <form v-on:submit.prevent.passive="onSubmitForm">
            <label>やること：<input type="text" v-model="input" required/></label><br />
            <label>期 &nbsp; &nbsp; 限：<input type="date" v-model="inputDate" required/></label>
            <input type="submit" value="登録!" id="sub" />
            <TodoListView />
        </form>
    </header>


</template>

<style scoped>
#sub{
    background-color:greenyellow;
}

</style>