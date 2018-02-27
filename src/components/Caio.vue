<template>
	<div class="body">
		<!-- <img class="imagem" src="../assets/caiio.jpg"> -->
		<section class="sec">
			<form class="order">
				<div>
					<label>Ordernar por:</label>
					<select v-model="configs.orderBy">
						<option value="nome">Nome</option>
       					 <option value="idade">Idade</option>
					</select>
				</div>
				<div>
					<label>Orderm:</label>
					<select class="cresdec" v-model="configs.order">
        			<option value="asc">Crescente</option>
        			<option value="desc">Decrescente</option>
      				</select>
				</div>
				<div>
					<label>Filtrar</label>
					<input type="text" placeholder="Filtrar por nome" v-model="configs.filter">
				</div>
			</form>
		</section>
		<ListaAluno :list="list"></ListaAluno>
	</div>
</template>
<script>
import _ from 'lodash'
import ListaAluno from './ListaAluno.vue' 
export default {
	name: 'Caio',
	data(){
    	return {
	    	configs:{
	    		orderBy: 'idade',
	      		order: 'desc',
	      		filter:''
	      	},
	    	alunos:[
		    	{
		    		nome:'caio',
		    		idade:'16',
		    		img:'https://www.designerd.com.br/wp-content/uploads/2016/10/textura-e-3d-nos-animais-de-maxim-shkret-4.jpg'
		    	},
		    	{
		    		nome:'rennan',
		    		idade:'30',
		    		img:'http://www.fubiz.net/wp-content/uploads/2014/04/Predators-Illustrations-by-Maxim-Shkret6.jpg'
		    	},
		    	{
		    		nome:'romulo',
		    		idade:'30',
		    		img:'https://blazepress.com/.image/t_share/MTI5MTk5NzcwMzM3MDc5MjY2/3d-rendered-animal-portraits-1jpg.jpg'
		    	},
		    	{
		    		nome:'karol',
		    		idade:'17',
		    		img:'http://www.edev.com.br/wp-content/uploads/2016/11/textura-e-3d-nos-animais-de-maxim-shkret-3.jpg'
		    	},
		    	{
			    	nome:'guilherme',
			    	idade:'17',
			    	img:'https://i.pinimg.com/236x/af/35/17/af35178d5020fb146ebe952e40c5010e--digital-portrait-digital-art.jpg'
		    	},
		    	{
		    		nome:'Ana luiza',
		    		idade:'21',
		    		img:'http://www.edev.com.br/wp-content/uploads/2016/11/textura-e-3d-nos-animais-de-maxim-shkret-2.jpg'
		    	},
		    	{
		    		nome:'Maria',
		    		idade:'48',
		    		img:'http://78.media.tumblr.com/4f22461dadbc31ca8deeaf1541e491c8/tumblr_ouyeneP8cO1srklmio1_1280.png'
		    	}
	    	]
	    }  
	},
	computed:{
	  	list() {
	  		const filter = this.configs.filter;
	    	const list = _.orderBy(this.alunos, this.configs.orderBy, this.configs.order); 

	    	if (_.isEmpty(filter)) {
	      		return list;
	    	}
	    	return _.filter(list, aluno => aluno.nome.indexOf(filter) >= 0);
	    }
	},
	components:{
		ListaAluno
	}
}
</script>
<style scoped>
	.body{
		width: 100%;
		background: lightblue url(https://http2.mlstatic.com/adesivo-textura-3d-branca-rolo-com-220x47cm-D_NQ_NP_920425-MLB25420485088_032017-F.jpg);
		background-size: 10%; 
		font-size: 1.4em;
		font-style: normal;
		font-family: sans-serif;
		text-align: left;
		line-height: 32.4px;
		letter-spacing: 0em;
		min-height: 100vh;
		display: flex;
	}
	.order{
		align-items: flex-end;
    	/*min-width: 100%; */
    	/*min-height: 100%;*/
		width: auto;
		height: auto;
		right: 0;
    	bottom: 0;
    	background-size: cover;
    	border: 10px solid transparent;
    	opacity: 0.8;
    	/*padding: 25px;*/
    	border-image: url(https://s-media-cache-ak0.pinimg.com/originals/e6/3e/64/e63e64daab219e0820a27cc9ef918524.jpg) 30 round;
	}
		.titulo{
		background-color: green;
	}
	ul{
		list-style:none;
	}
	#alunosVNW{
		background-color: yellow;
	}
	.sec{
		background: rgba(225,225,225,0.3);
		height: 100%;
	}
	.cresderc{
		background: url(https://cdn.pixabay.com/photo/2016/05/31/12/42/red-button-1426817_960_720.png);
	}
</style>