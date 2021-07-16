<template>
		<nav class="absolute bottom-0 left-0 w-full flex justify-between self-end">
			<nuxt-link :key="link.name" class="relative block px-4 py-2" v-for="link in links" :to="link.path">{{link.name}}</nuxt-link>
		</nav>
</template>
<script>
export default {
	data(){
		return {
			links: [
				{ name: 'Home', path:"/" },
				{ name: 'Discover', path:"/discover" },
				{ name: 'Create', path: "/create" },
				{ name: 'Inbox', path: "/inbox" },
				{ name: 'Me', path: "/me" },
			]
		}
	},
}

</script>
<style>
.nuxt-link-exact-active::before {
	content: "";
	display: block;
	height: 10px;
	width: 10px;
	background: red;
	border-radius: 4px;
	position: absolute;
	top: 5px;
	left: 2px;
}
</style>
