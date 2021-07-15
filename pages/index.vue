<template>
	<div class="flex flex-col"> 
		<categories></categories>
		<main class="flex-grow">
			video
		</main>
		<nav class="absolute bottom-0 left-0 flex justify-between self-end">
			<nuxt-link class="block px-4 py-2" v-for="link in links" :to="link.path">{{link.name}}</nuxt-link>
		</nav>
	</div>
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
