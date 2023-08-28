<template>
<div id="anaalan">
  <center>
  <div id="todolist">
    <div id="başlık">
      <h3>To do list</h3>
      <input type="text" name="yapılacaklar" id="yapılacaklarr" v-on:keyup.enter="ekle"  v-model="doing">
      <button type="button" @click="ekle">Ekle</button>
      <button type="button" @click="hepsinisil">Tümünü Sil</button>
    </div>
    <div id="yapılacaklar">
      <ul>
        <li :class="{düzeltme:index.state}" v-for="(todo,index) in todoList">{{todo}}

          <button  id="silme" type="button" @click="sil(index)">sil</button>
          <button  id="silme" type="button" @click="changestatus(index)">tamamlandı</button>
        </li>

      </ul>
    </div>

  </div>
  </center>
</div>

</template>

<script>
export default{
data() {
  return {
    todoList : [],
    doing:"",
    state: false,
  }
},

  methods:{
  ekle(){
    if(document.getElementById("yapılacaklarr").value == ""){
      alert("Lütfen Bir Değer Giriniz")
    }

   else{return this.todoList.push(this.doing),
       this.doing='';}

  },
    sil(index){
    return this.todoList.splice(index,1)

    },
    hepsinisil(){
    this.todoList=[]
    },
    changestatus(index){
      var indexno=[];
      indexno.push(index);
      for (index in indexno){
      index.state=!index.state}
    }



  }
}
</script>

<style>
#anaalan{
  width:100%;
}

#todolist{
  margin-top: 50px;
  background-color: cornflowerblue;
  width: 50%;
  border-radius: 10px;
}

#başlık{
  margin-bottom: 40px;
  padding:10px;
}

h3{
  padding-bottom:20px;
}

input{
  border-radius: 10px;
  background-color: cornsilk;

}

button{
  border-radius: 5px;
  background-color: cornsilk;
  color:blue;
}
#yapılacaklar{
  background-color: cornsilk;
  visibility:visible;

}
ul { list-style-type:none;
  width: 100%;
}

li{
  padding:10px;
  border: 2px solid cornflowerblue ;
  width:50%;
  padding:10px;
}

#silme {
  background-color: cornflowerblue;
  color: white;
  float: right;
  height: auto;
}


.düzeltme {
  text-decoration:line-through;
}


</style>

