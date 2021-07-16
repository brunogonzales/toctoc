<template>
	<div>
		<nuxt-link to="/" class="font-bold">back to home</nuxt-link>
		<p>create a toctoc</p>
		<photobooth/>
		<form @submit.prevent="submitPost">
			<input v-model="title">
		</form>
	</div>
</template>
<script>
export default {
	data(){
		return {
			title:"",
		}
	},
	methods: {
		submitPost(){
			alert("post submitted!" + this.title)
		},
	},
}
</script>
