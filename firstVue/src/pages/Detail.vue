<!-- Detail.vue -->
<template>
	<div class="detail">
		<detail-header></detail-header>
	</div>
</template>
<style scoped>
	.detail {
		padding: 0.24rem;
		font-size: 12px;
	}
	img {
		display: block;
		width: 80%;
		margin: 0 auto 0.2rem;
	}
	p {
		font-size: 14px;
		line-height: 0.5rem;
		text-align: justify;
		padding-bottom: 0.24rem;
	}
</style>
<script>
	import DetailHeader from '../components/DetailHeader'
	

	export default {
		
		components: {
			DetailHeader,
			
		}
	}
</script>