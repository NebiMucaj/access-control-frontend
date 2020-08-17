<template>
  <div >
<ul class="list-group list-group-flush">
    
  <li class="list-group-item list-group-item-primary">last accessed member</li>
  
  <li v-for="(item,index) in accessedMemberList" :key="index"  class="list-group-item list-group-item-action"><p> <b>{{item.name}} {{item.lastName}}</b> </p> <p><small class="float-right">{{new Date(item.timestamp).toLocaleTimeString()}}</small></p></li>
 
</ul>
  
  </div>
</template>

<script>
export default {
  name: 'MemberHistory',
  props: {
      accessedMemberList:Array
    
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
li{
    border-bottom:  rgb(2, 117, 216) 0.5px solid;
}
p{
    margin:0;
    text-align: left;
}
small{
    color: grey;
}
ul{
    height: 595px;
    overflow-y: scroll;
  scroll-behavior: smooth;
}

</style>
