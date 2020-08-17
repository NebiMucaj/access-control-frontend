<template>
  <div class="container " >
  <div class="row">
  
  <div id="memberhistory" class="col-4">
 <MemberHistory v-bind:accessedMemberList="accessedMemberList.slice(1)"/>
  </div>
  <div id="member"  class="col-8">
  <member v-bind:member="memberElement" />
  </div>
  </div>
  
  </div>
  
</template>

<script>
import Member from './Member'
import MemberHistory from './MemberHistory'
export default {
  components:{
    Member,MemberHistory
  },
  name: 'AccessOverview',
  created:function(){
   var  currentDate= new Date();
    this.currentTimestamp= [currentDate.getFullYear(),currentDate.getMonth(), currentDate.getDate()].join('-')+' '+
              [currentDate.getHours(),
               currentDate.getMinutes(),
               currentDate.getSeconds()].join(':');

      fetch('http://localhost:5000/member/logs/'+this.currentTimestamp)
  .then(response => response.json())
  .then(data => this.accessedMemberList=data.log);
  },
  data:function() {
    return{
      accessedMemberList:[],
      currentTimestamp:''
    }
    
  },methods:{
    getlogs:function(){
      const self=this; 
   setInterval(function () {  fetch('http://localhost:5000/member/logs/'+self.currentTimestamp)
  .then(response => response.json())
  .then(data => self.accessedMemberList=data.log);},1000);
        

        }
    },
  mounted () {
  this.getlogs()
  
}
,computed:{
  memberElement:function(){
    if(this.accessedMemberList.length==0){
      return{
        LastName:"",
        name:"",
        sex:"",
        birthday:""
      }
    }
    else{
      return this.accessedMemberList[0]
    }
  }
}
 
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.card{
  
  padding: 0px;
  margin-left: 190px;
}
#member{
  padding: 0;
}
#memberhistory{
  padding: 0;
}
.container{
  border: 1px solid rgb(2, 117, 216);
  border-radius: 2px;
  height: 600px;
  
}

</style>
