<template>
    <div class="page">
    <header><h1>Yewon todo1</h1></header>
    <main>
      <div class="todos">
        <div class="write">
          <input ref="writeArea" v-model="addItemText" type="text" @keyup.enter="addItem"/>
          <button class="btn add" @click="addItem">Add</button>
        </div>
        <ul  v-for="(item,i) in todos" class="list" :key="item.text">
          <li>
            <i  @click="checkItem(i)" :class="[item.state==='yet'? 'far':'fas','fa-check-square' ]"></i>
            <span>
              {{item.text}}
              <b>
                <a href="">Edit</a>
                <a href="">Del</a>
              </b>
            </span>
          </li>
        </ul>
      </div>
    </main>
    </div>
</template>

<script>
export default {
    data(){
        return{
          addItemText:'',
          todos:[
          {text: '공부하기', state: 'yet'},
          {text: '운동하기', state: 'done'},
          {text: '글쓰기', state: 'done'},],

          checkSquare: {
           'yet':'far'
          ,'done':'fas'
          }
      
        }
    },
    methods:{
      addItem(ev){
        if (ev.target==='') return;
        this.todos.push({text:this.addItemText,state:'yet'})
        this.addItemText='';
      },
      checkItem(i){
        if (this.todos[i].state==='yet') {
          this.todos[i].state='done';
        }else{
          this.todos[i].state='yet';
        }
  
      },

    },
    mounted(){
      this.$refs.writeArea.focus();
    }


}
</script>

<style>
i{
    font-size: 40px;
}

</style>