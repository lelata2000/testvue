<template>
<div class="main">
  <h1>Список дел</h1>
  <h3>Добавьте в список новые значения</h3>
  <form @submit.prevent="add">
    <div class="class1">
      <input v-model="mytask" type="text" placeholder="введите текст"><button id="myid">Добавить</button>
    </div>
    
  </form>
  <div v-if="articles.length > 0" id="articles">
    <div class="post" v-for="el in articles" :key="el.id">
      <p>{{ el.text }}</p>
      <button @click="deletePost(el.id)">Удалить</button>            
    </div>
  </div>

</div>  
</template>

<script>
export default {
  data() {
    return {
    mytask:"",  
    articles:[
   
    ],
    };
  },
  computed: {
   
  },
  methods: {
    add(){
      if(this.mytask !== ""){
        //alert(this.mytask);
        this.articles.push(
          {
              id: Math.random() * 1000000000,     
              text:this.mytask.trim()
          })
          this.mytask="";
          console.log(this.articles);
      }      
    },
    deletePost(id){
      this.articles = this.articles.filter((el) => el.id !== id);
    }
  },
  
  
};
</script>

<style lang="css" scoped>
.main{
    width: 50%;
    height: 400px;
    margin: 50px auto;
}
h1, h3 {
  text-align: center;
  color:rgb(97, 93, 93);
}
h3 {
  padding: 10px;
}
.class1 {
  text-align: center;
  padding-top:10px;
  padding-bottom: 15px;
}
.class1 input{
  width: 40%;
  padding: .5em;
  border-radius: 10px;
  border: 1px solid gray;
  font-size: 14px;
}
.class1 input:hover
.class1 input:active {
  border: 1px solid darkgray;
}
.class1 button{
  padding: .5em;
  border-radius: 10px;
  cursor: pointer;
  margin-left: 5px;
  background-color: gray;
  color: white;
  font-size: 14px;
  border: 1px solid gray;
}
.class1 button:hover,
.post button:hover
{  
  background-color: rgb(85, 78, 78);
  border: 1px solid gray;
}
.post{
  display: flex;
  justify-content: center;
  font-size:14px; 
  margin-bottom: .3em;   
}
.post p{
  padding: .4em;
}
.post button{
  padding:.4em;
  background-color: rgb(143, 136, 136);
  color: white;
  border-radius: 10px;
  border: 1px solid gray;
  cursor: pointer;
}


</style>