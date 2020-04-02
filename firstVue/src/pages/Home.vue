<!-- Home.vue -->
<template>
	<div class="container">
		<home-header></home-header>
		<div class="content">
			<ul class="cont_ul">
				<list
					v-for="item in items" 
					:key="item.id"
					:title="item.title"
					:assignUser="item.assignUser">
				</list>
			</ul>
		</div>
	</div>
</template>
<style>
	.container {
		max-width: 640px;
		margin: 0 auto;
		overflow-x: hidden;
	}
	.cont_ul {
		padding-top: 0.05rem;
		
	}
	.cont_ul:after {
		content: "";
		display: block;
		width: 0;
		height: 0;
		clear: both;
	}
</style>
<script>
	// 导入要用到的子组件
	import HomeHeader from '../components/HomeHeader'
	import List from '../components/List'

	export default {
		data () {
			return {
				items: []
			}
		},
		// 在components字段中，包含导入的子组件
		components: {
			HomeHeader,
			List
		},
		created (){
			// 在main.js里导入并使用vue-resource之后，就可以通过this.$http来使用vue-resource了，这里我们用到了get方法
			this.$http.get('/api/appData').then((reponse) => {
				this.items = reponse.data.data.tasks;
				console.log('home')
			})
		}
	}
</script>