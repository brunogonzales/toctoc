<template>
	<div class="flex pt-4 justify-center space-x-4">
    <p @click='() => activeCategoryId = category.id ' v-for='category in categories' :key='category.id' :class='{active:activeCategoryId===category.id}'>
        {{category.name}}
    </p>
  </div>
</template>
<script>
export default {
	data(){
		return {
			activeCategoryId: 2,
      categories: [
        { name: 'Following', id: 1 },
        { name: 'For you', id: 2 }
      ]
		}
	}
}
	
</script>
<style>
.active {
  @apply font-bold
}

</style>

