<template>
    <div class="page">
    <header><h1>Yewon todo1</h1></header>
    <main>
      <div class="todos">
        <div class="write">
          <input  v-model="content" type="text"/>
          <button class="btn add" @click="addClick">Add</button>
        </div>
        <ul v-for="item in todos" class="list" :key="item.text">
          <li>
            <i  :class="[checkSquare[item.state],'fa-check-square' ]"></i>
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
          content:"",
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
      addClick(){
        console.log(this.content)
        this.todos.push({text:this.content,state:'yet'})
      },
      select(ev){
        console.log(ev.target)
        ev.target.classList.remove('far fa-check-square');
        console.log(ev.target)
        ev.target.classList.add('fas fa-check-square');
      }
    }

}
</script>

<style>
i{
    font-size: 40px;
}

</style>