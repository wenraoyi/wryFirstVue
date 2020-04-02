<!-- List.vue -->
<template>
	<li class="sec_li">
		<div class="lp_li_imgWrap">
			<div class="col-sm-5" style="display:inline-block;padding-left: 0.5em;">
				{{ title }},{{assignUser.name}}</div>
			<!-- <router-link to="/detail" class="lp_li_a col-sm-5">
				<img src="../assets/img/lp_01.jpg" alt="">
			</router-link> -->
			<img src="../assets/img/lp_01.jpg" alt="" class="lp_li_a col-sm-5"
			@click="assignTask">
			
		</div>
		<as-modal v-show="showModal" v-on:closeme="closeme" @func2="sendSelectedUser"
		/>
	</li>
</template>

<style scoped>
	.sec_li {
		float: left;
		width: 100%;
		margin-bottom: 0.1rem;
		font-size: 23px;
	}
	
	.lp_li_imgWrap {
		background-color: white;
		height: 40px;
	}
	.lp_li_imgWrap > img {
		width: auto;
		height: 25px;
	}
	.lp_li_name {
		height: 0.5rem;
		line-height: 0.5rem;
		font-size: 16px;
		color: #333;
	}
	.lp_li_a{
		float:right;
		padding-right: 20px
	}
	
</style>

<script>
	import asModal from '../components/as-modal';
	
	export default {
		props: ['title'],
		data(){
			return {
				showModal:false,
				assignUser:{name:''}
			}
		},
		methods: {
			assignTask () {
				this.$modal.show('as-modal');
				this.showModal = !this.showModal;
			},
			closeme:function(){
				this.showModal = !this.showModal;
			},
			sendSelectedUser:function(data){
				this.assignUser = data;
			}
		},
		components:{
			asModal,
		}
	}
</script>