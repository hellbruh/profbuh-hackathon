<template>
  <div id="app">
    
    <div class="top">
      <img class="pic" src="../public/icon.svg" width="80" height="63">
      <div id="name">PROFBUH HACKATHON</div>
    </div>
    
    <div class="instruction">
        Введите ссылку и нажмите на кнопку, 
        чтобы получить результат
    </div>
    
    <div class="main">
    
      <div class="input-group mb-3" id="inp">
        <span class="input-group-text" id="basic-addon1">URL</span>
        <input type="text" v-model="link" class="form-control" placeholder="Введите ссылку" >
      </div>
      <div v-if="res==-1" id="valid">Поле не должно быть пустым</div>

      <div class="input-group mb-3" id="inp">
        <span class="input-group-text" id="basic-addon1">Количество символов  в статье</span>
        <input type="text" v-model="stlen" class="form-control" placeholder="По умолчанию ограничений нет" aria-label="Имя пользователя" >
      </div>

      <div class="input-group mb-3" id="inp">
        <span class="input-group-text" id="basic-addon1">Количество символов  в аннотации</span>
        <input type="text" v-model="stan" class="form-control" placeholder="По умолчанию 500 символов" >
      </div>

      <div class="input-group mb-3" id="inp">
        <span class="input-group-text" id="basic-addon1">Фрагмент видео (необязательно)</span>
        <input type="text" v-model="timing" class="form-control" placeholder="Введите в формате чч:мм:сс чч:мм:сс" aria-label="Имя пользователя" aria-describedby="basic-addon1">
      </div>
      <button type="button" @click="showResult()" class="btn btn-primary" id="b">Сгенерировать</button>
    </div>
    
    
    <result v-if="res==1" ></result>

  </div>
</template>

<script>
import Result from './components/Result.vue'
export default {
  name: 'App',
  components: {
    Result
  },
  data(){
    return{
      res:0,
      stlen:'',
      stan:'',
      timing:'',
      link:'',
    }
  },
  methods:{
    showResult(){
      if (this.link.length>0){
        this.res=1
        if (this.stlen.length>0){
          this.stlen=Number(this.stlen)
        }
        if (this.stan.length>0){
          this.stan=Number(this.stan)
        }
        else{
          this.stan = 500
        }
      }
      else{
        this.res=-1
      }
    }
  }
}
</script>

<style>
#app {
  margin:0%;
  width:100%;
  display:flex;
  align-items:center;
  flex-direction:column;
}
.top{
  width:100%;
  height:85px;
  background-color: rgb(68, 194, 253);
  font-family: 'Belanosima', sans-serif;
  color:white;
  font-size:28px;
  display:flex; 
  align-items:center;
}
#name{
  margin-left:20px;
  display:flex;
}
.pic{
  display:flex;
  margin-left:20px;
}
.main{
  display:flex;
  width:100%;
  align-items:center;
  margin-top:20px;
  flex-direction:column;
}
.instruction{
  display:flex;
  font-family:'Roboto',sans-serif;
  font-weight:100;
  font-size:28px;
  margin-top:100px;
  flex-wrap:wrap;
  width:40%;
  text-align:center;
}
#inp{
  width:40%;
  display:flex;
  flex-direction:row;
  margin-top:15px;
}
#basic-addon1{
  color:rgb(43, 43, 43);
  width:285px;
  display:flex;
  flex-wrap:wrap;
  text-align:center;
}

#valid{
  display:flex;
  color:rgb(194, 2, 2);
  font-size:12px;
  font-family:'Roboto',sans-serif;
  margin-top:-15px;
}
#b{
  background-color:rgb(60, 179, 235);
  border-color:rgb(60, 179, 235); 
}
#b:hover{
  background-color:rgb(4, 130, 189);
  border-color:rgb(4, 130, 189); 
}
</style>
