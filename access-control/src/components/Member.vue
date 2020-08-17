<template>
  <div id="container">
 <div class="card card text-white bg-primary mb-3">
     <div class="card-header ">
         <div class="float-left"><h3>{{member.name}} {{member.lastName}}</h3>
         </div>
     </div>
     <div class="card-body mt-2">
         <div class="row justify-content-center">
         <div class="col-12">
             <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn%3AANd9GcRTP_ZGxx9idftw49_CVyWxvri-MFQf6Z-TTA&usqp=CAU" class="rounded mx-auto d-block mb-4" alt="...">
         </div>

            <div class="col-6  align-self-center" id="myTabContent">
                           
                                        <div class="row ">
                                            <div class="col-md-6">
                                                <label><b>Name</b></label>
                                            </div>
                                            <div class="col-md-6">
                                                <p>{{member.lastName}}</p>
                                            </div>
                                        </div>
                                        <div class="row">
                                            <div class="col-md-6">
                                                <label><b> First name</b></label>
                                            </div>
                                            <div class="col-md-6">
                                                <p>{{member.name}}</p>
                                            </div>
                                        </div>
                                        <div class="row">
                                            <div class="col-md-6">
                                                <label><b>Age</b></label>
                                            </div>
                                            <div class="col-md-6">
                                                <p>{{calcAge}}</p>
                                            </div>
                                        </div>
                                        <div class="row">
                                            <div class="col-md-6">
                                                <label><b>sex</b></label>
                                            </div>
                                            <div class="col-md-6">
                                                <p>{{member.sex}}</p>
                                            </div>
                                        </div>
                                    
                        
                        </div>
     </div>
     </div>
 </div>

  </div>
</template>

<script>
export default {
  name: 'Member',
  props: ['member'],
  computed:{
      calcAge:function(){
          if (this.member.birthday===""){
               return " ";

          } 
          else{ 
       var today = new Date();
       var birthday =new Date(this.member.birthday)
    var thisYear = 0;
    if (today.getMonth() < birthday.getMonth()) {
        thisYear = 1;
    } else if ((today.getMonth() == birthday.getMonth()) && today.getDate() < birthday.getDate()) {
        thisYear = 1;
    }
    var age = today.getFullYear() - birthday.getFullYear() - thisYear;
    return age;
      }
      }
  },
  
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

#container{
    padding: 0;
    font-size: 28px;
}
.card-header{
    height: 48px;

}
.card{
    height: 598px;
    border-radius: 0px;
    
}
</style>
