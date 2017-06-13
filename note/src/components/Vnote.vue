<template lang="html">
    <div class="container">
      <div class="row">
         <div class="col-lg-12">
             <div class="panel panel-default">
               <div class="panel-heading">
                 <h3 class="panel-title">Title</h3>
               </div>
               <div class="panel-body">
                 <div class="row">
                     <div class="col-lg-3">
                         <Vlist></Vlist>
                     </div>
                     <div class="col-lg-9">
                         <Vshow></Vshow>
                     </div>
                 </div>
               </div>

             </div>
         </div>
      </div>
    </div>
</template>

<script>
import Vlist from './Vlist'
import Vshow from './Vshow'

export default {

    name:'Vnote',
    data(){
        return{

        }
    },
    components:{
        Vlist,
        Vshow
    }

}
</script>

<style lang="css">
</style>
