<template>
  <div id="app">
    <img src="./assets/translate.jpg" width="400" height="200">
		<div id="titleContent">
			<h1>在线翻译</h1>
			<h5 class="text-muted">极简至上</h5>
		</div>
    <TranslateIndex v-on:formSubmit="TranslateText"></TranslateIndex>
		<TranslateResult v-bind:translateResult="translateResult"></TranslateResult>
		<Copyright></Copyright>
  </div>
</template>

<script>
import TranslateIndex from './components/TranslateIndex.vue'
import TranslateResult from './components/TranslateResult.vue'
import Copyright from './components/Copyright.vue'
export default {
  name: 'App',
	data(){
		return{
			translateResult:""
		}
	},
	components:{
		TranslateIndex,
		TranslateResult,
		Copyright
	},
	methods:{
		TranslateText(text,language){
			this.$http.get('http://dict.youdao.com/suggest?q=text&num=1&doctype=json)
			.then((response) =>{
				this.translateResult = response.data.entries[0].explain;
			})
		}
	}
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
img{
	border-radius: 10px;
}
#titleContent{
	padding: 20px;
}
</style>
