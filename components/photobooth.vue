<template>
	<div class="flex flex-col space-y-4">
		<video autoplay ref="preview" id="preview" width='200' height="300"></video>
		<button class="bg-blue-200 px-4 py-3 rounded text-center" @click="snapshot()">take snapshot</button>
		<canvas class="hidden" id="canvas" ref='canvas' width="60" height="90"></canvas>
		<div ref="captureRoll" id="captureRoll" class="w0max-w-md overflow-x-scroll px-2 space-x-2 flex-nowrap flex">
			<img class='w-1/8' v-for="capture in captures" :src="capture" alt="captures">
		</div>
		<button v-if="captures.length" @click="clearCaptures">delete photo{{captures.length===1?'':'s'}} </button>
	</div>
</template>
<script>
export default {
	data(){
		return {
			preview: {},
			canvas: {},
			captures: [],
		}
	},
	methods:{
		snapshot(){
			this.canvas = this.$refs.canvas
			var context = this.canvas
				.getContext("2d")	
				.drawImage(this.preview,0,0,60,90)
			this.captures.push(canvas.toDataURL('image/png'))
			this.$nextTick(()=>{
				this.$refs.captureRoll.scroll(
					{left: this.$refs.captureRoll.scrollWidth, behaviour:"smooth"}
				)
			})
		},
		clearCaptures(){
			this.captures = []
		}
	},
	mounted(){
		this.preview = this.$refs.preview
		if (navigator.mediaDevices && navigator.mediaDevices.getUserMedia) {
			navigator
				.mediaDevices
				.getUserMedia({ video: true, audio: false })
				.then(stream => {
					preview.srcObject = stream;
					this.preview.play();
			});
		}
	}
}
</script>
