<!-- UserList.vue -->
<template>
	<li class="sec_li" @click="selectUser">
		<div class="lp_li_imgWrap userCls" :class="{'selectedCls': selected}">
			<div class="col-sm-5 " style="display:inline-block;">{{ name }}</div>			
		</div>
	</li>
</template>

<style scoped>
	.sec_li {
		float: left;
		width: 30%;
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
	.userCls{
        display: inline-block;
        background-color: yellow;
        padding: 10px;
        border-radius: 100px;
        width: 150px;
        margin: 0 auto;
        text-align: center;
        cursor: pointer;
    }
    .userCls:hover{
        background-color: rgb(230, 230, 167);
    }
    .selectedCls{
        background-color: rgb(214, 214, 158);
    }
</style>

<script>
	export default {
        props: ['name','selected','users'],
        data () {
            return {
                users2:this.users
            }
        },
		methods: {
			selectUser () {
                for(var i in this.users){
                    this.users[i].selected = false;
                    if(this.users[i].name == this.name){
                        this.users[i].selected = true;
                         this.$emit('func',this.users[i]);
                    }
                }
                  
			}
		},
        
		components:{
			
        },
       
	}
</script>