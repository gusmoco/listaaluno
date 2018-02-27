<template>
<section class="conteudo">
  <h1 class="titulo">Alunos</h1>
  <ul class="borderimg">
      <li v-for="aluno in list">
        {{ aluno.nome }}
        <br>
        {{ aluno.idade }} anos
        <br>
        <img class="imgprofile" v-bind:src="aluno.img">
        <hr>
      </li>
  </ul>
</section>
</template>
<script>
  export default{
    name:'ListaAluno',
    props:{
      list:{
        type: Array,
        required: true
      }
    },
    data(){
      return{

      }
    }
  }

</script>
<style>
  .conteudo{
  min-width: 80%; 
  min-height: 80%;
  }
  .borderimg{ 
  border: 10px solid transparent;
  opacity: 0.8;
  /*padding: 25px;*/
  border-image: url(https://s-media-cache-ak0.pinimg.com/originals/e6/3e/64/e63e64daab219e0820a27cc9ef918524.jpg) 30 round;
  background: rgba(225,225,225,0.4);
  height: 80%;
  width: 70%;
  display: flex;
  align-items:  flex-start;
  flex-flow: row wrap;
  }
  .imgprofile{
  height: 200px;
  /*width: 200px;*/
  /*border-radius:50%;*/

  }
</style>