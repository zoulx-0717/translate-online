<template>
	<div class="row" id="translateForm">
		<div class="col-md-6 col-md-offset-3">
		<form class="well form-inline" v-on:submit="formSubmit">
			<input v-model="textToTranslate" class="form-control" type="text" placeholder="请输入要翻译的内容">
			<select v-model="language" class="form-control" name="" id="">
				<option class="form-control" value="en">English</option>
				<option class="form-control" value="ru">Russian</option>
				<option class="form-control" value="ko">Korear</option>
				<option class="form-control" value="ja">Japan</option>
			</select>
			<input class="form-control btn btn-primary" type="submit" value="翻译">
		</form>
		</div>
	</div>
</template>

<script>
	export default{
		name:"TranslateIndex",
		data(){
			return{
				textToTranslate:"",
				language:""
			}
		},
		methods:{
			formSubmit(e){		
				this.$emit("formSubmit",this.textToTranslate,this.language);
				e.preventDefault();
			}
		},
		created(){
			this.language = "en";
		}
	}
</script>

<style scoped>
.form-control{
	border: none;
	outline: none;
	box-shadow: none;
	border-bottom: 1px solid #ced4da;
}
#translateForm{
	border: 1xp solid #ced4da;
	border-radius: 10px;
}

</style>
