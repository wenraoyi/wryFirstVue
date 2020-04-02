<template>
  <modal name="as-modal">
    <div class="modalBody">
       <ul class="cont_ul">
				<user-list
          @func="getMsgFromSon"
					v-for="user in users" 
					:key="user.id"
					:name="user.name"
          :selected="user.selected"
          :users="users"
          >
				</user-list>
			</ul>
    </div>
   
    <div class="modalFoot">
       <div style="text-align: center;">
        {{selectedUser.name}}
      </div>
      <div @click="confirm" class="foot-btn"><button class="confirm-btn">confirm</button></div>
      <div @click="closeModal" class="foot-btn"><button class="close-btn">close</button></div>
    </div>
  </modal>
  
</template>

<script>
import userList from '../components/UserList';
export default {
  data () {
    return {
      users: [],
      selectedUser:{'name':'Not yet'},
    }
  },
  
  methods: {
    closeModal () {
        this.$emit("closeme");      
    },
    confirm(){
      this.closeModal();
    },
    getMsgFromSon(user){
      this.selectedUser = user;
      this.$emit('func2',this.selectedUser);
    }
  },
  created (){
    // 在main.js里导入并使用vue-resource之后，就可以通过this.$http来使用vue-resource了，这里我们用到了get方法
    this.$http.get('/api/userData').then((reponse) => {
      this.users = reponse.data.data.users;
      for(var i in this.users){
        this.users[i].selected = false;
      }
    })
  },
  components:{
    userList
  }
}
</script>
<style>
.modalBody{
  height: 70%
}
.modalFoot{
    height: 20%;
    margin: 0 auto;
    width: 200px;
}
.foot-btn{
  width: 48%;
  text-align: center;
  display: inline-block;
}
.confirm-btn{
    border-radius: 2px;
    padding: 6px;
    color: white;
    box-shadow: inset rgba(255,255,255,0.3) 1px 1px 0;
    background: rgb(255,183,0);
    background: -moz-linear-gradient(top, rgba(255,183,0,1) 0%, rgba(255,140,0,1) 100%);
    background: -webkit-gradient(linear, left top, left bottom, color-stop(0%,rgba(255,183,0,1)), color-stop(100%,rgba(255,140,0,1)));
    background: -webkit-linear-gradient(top, rgba(255,183,0,1) 0%,rgba(255,140,0,1) 100%);
    background: -o-linear-gradient(top, rgba(255,183,0,1) 0%,rgba(255,140,0,1) 100%);
    background: -ms-linear-gradient(top, rgba(255,183,0,1) 0%,rgba(255,140,0,1) 100%);
    background: linear-gradient(to bottom, rgba(255,183,0,1) 0%,rgba(255,140,0,1) 100%);
    filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#ffb700', endColorstr='#ff8c00',GradientType=0 );
    border: 1px solid #e59500;
}
.close-btn{
border-radius: 2px;
    padding: 6px;
    color: white;
    box-shadow: inset rgba(255,255,255,0.3) 1px 1px 0;
    background: rgb(163, 181, 196);
    background: -moz-linear-gradient(top, rgb(163, 181, 196) 0%, rgb(163, 181, 196) 100%);
    background: -webkit-gradient(linear, left top, left bottom, color-stop(0%,rgb(163, 181, 196)), color-stop(100%,rgba(255,140,0,1)));
    background: -webkit-linear-gradient(top, rgb(163, 181, 196) 0%,rgb(163, 181, 196) 100%);
    background: -o-linear-gradient(top, rgb(163, 181, 196) 0%,rgb(163, 181, 196) 100%);
    background: -ms-linear-gradient(top, rgb(163, 181, 196) 0%,rgb(163, 181, 196) 100%);
    background: linear-gradient(to bottom, rgb(163, 181, 196) 0%,rgb(163, 181, 196) 100%);
    filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#ffb700', endColorstr='#ff8c00',GradientType=0 );
    border: 1px solid rgb(163, 181, 196);
}
</style>