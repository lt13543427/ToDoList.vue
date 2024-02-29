<script>

export default {
  data() {
    return {
      Text: '',
      todoText: [],
      check : null,
    };
  },

  methods: {
    getText(e) {
      this.Text = e.target.value;
      console.log(this.Text);
    },

    pushText() {
      let myId = 0;
      if (this.todoText.length !== 0) {
        myId = this.todoText[this.todoText.length - 1].id;
      }
      if (this.Text !== "") {
        const newText = {
          id: myId + 1,
          edit: false,
          msg: this.Text,
        };
          this.todoText.push(newText);
          console.log(this.todoText);
      }
    },

    deleteText(index){
      this.todoText.splice(index,1);
    },

    editText(id) {
      this.todoText.map((item) => {
        if (item.id === id) {
          const content = prompt('請修改文字');
            if (content !== null && content !== "") {
            item.msg = content;
            }
        }
      });
    },
    filterText(){
      if(this.check === null){
        return this.todoText
        }else{
          return this.todoText.filter(item =>item.edit == this.check)
        }
    },
  },
};



</script>
<template>
    <div class="todolist-body w-full h-screen bg-gray-200">
      <div class="nav w-full h-[60px]  bg-teal-500"></div>
      <div class="add w-full h-[80px] flex justify-center items-center gap-2" >
        <input type="text" id="" class="add-text w-2/4 h-3/4 " @change="getText"/>
        <button class="add-Todo w-[100px] h-[50px] bg-teal-500 border-4" type="button" @click="pushText()">新增</button>
      </div>
      <div>
        <div class="search-btn gap-5 w-full h-[80px] flex items-center border-b-4">
          <div class="all w-[100px] h-[60px] border-2 flex items-center justify-center text-white  bg-teal-500 rounded-lg" type="button" data-search="all" @click="check = null" :class="{'active':check == null}">全部</div>
          <div class="is-todo w-[100px] h-[60px] border-2 flex items-center justify-center text-white  bg-teal-500 rounded-lg" type="button" data-search="isTodo" @click="check = true" :class="{'active':check == true}">已執行</div>
          <div class="not-todo w-[100px] h-[60px] border-2 flex items-center justify-center text-white  bg-teal-500 rounded-lg" type="button" data-search="notTodo"  @click="check= false" :class="{'active':check == false}">未執行</div>
        </div>
      </div>
      <div class="title-div w-full h-[60px] bg-teal-500 flex justify-between items-center">
          <div class="div w-[400px] flex justify-center items-center">狀態</div>
          <div class="div w-[400px] flex justify-center items-center">訊息</div>
          <div class="div w-[400px] flex justify-center items-center">功能</div>
        </div>
      <table class="todo w-full h-[60px]">
        <thead class="w-full h-full flex flex-col">
          <tr class="w-full h-full flex  justify-between items-center bg-teal-500" v-for="(item , index) in filterText()" :key="item.id">
            <th class="lg:w-[200px] xl:w-[400px] h-full flex justify-center items-center">
              <input type="checkbox" v-model="item.edit">
            </th>
            <th class="lg:w-[200px] xl:w-[400px] h-full flex justify-center items-center">
              <td>{{ item.msg }}</td>
            </th>
            <th class="lg:w-[200px] xl:w-[400px] h-full flex justify-center items-center">
              <button @click="editText(item.id)">編輯</button>
              <button @click="deleteText(index)">刪除</button>
            </th>
          </tr>
        </thead>
        <tbody class="data-show"></tbody>
      </table>
      <button class="sava-local w-[100px] h-[50px]  bg-teal-400 text-white rounded-md" type="button">儲存進Local</button>
    </div>
</template>

<style scoped>
.active {
  @apply bg-white text-black;
}
</style>
