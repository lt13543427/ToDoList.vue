<script setup>
import TheWelcome from '../components/TheWelcome.vue'
</script>
<template>
    <div class="todolist-body w-full h-screen bg-blue-100">
      <div class="nav w-full h-[80px] bg-orange-200"></div>
      <div class="add w-full h-[80px] flex justify-center items-center gap-2" >
        <input type="text" id="" class="add-text w-2/4 h-3/4 " />
        <button class="add-Todo w-[100px] h-[50px] bg-emerald-500" type="button">新增</button>
      </div>
      <div>
        <div class="search-btn gap-5 w-full h-[80px] flex items-center border-b-4">
          <div class="all w-[100px] h-full border-2 flex items-center justify-center" type="button" data-search="all">全部</div>
          <div class="is-todo w-[100px] h-full border-2 flex items-center justify-center" type="button" data-search="isTodo">已執行</div>
          <div class="not-todo w-[100px] h-full border-2 flex items-center justify-center" type="button" data-search="notTodo">未執行</div>
        </div>
      </div>
      <table class="todo w-full h-[80px]">
        <thead class="w-full h-full flex">
          <tr class="w-full h-full flex justify-between items-center">
            <th class="lg:w-[200px] xl:w-[400px] h-full">執行</th>
            <th class="lg:w-[200px] xl:w-[400px] h-full">事項</th>
            <th class="lg:w-[200px] xl:w-[400px] h-full">功能</th>
          </tr>
        </thead>
        <tbody class="data-show"></tbody>
      </table>
      <button class="sava-local" type="button">儲存進Local</button>
    </div>
</template>
