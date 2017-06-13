<template lang="html">

<div class="container">
  <div class="row">
     <div class="col-lg-12">
         <div class="panel panel-default">
           <div class="panel-heading">
             <h3 class="panel-title">Title</h3>
           </div>
           <div class="panel-body div1">
             项目笔记
           </div>
           <ul>
               要点
               <li>安装环境</li>
               <li>单页面应用:利用路由来实现页面跳转</li>
               <li>scoped属于布尔属性，可限定css的作用范围</li>
               <li>组件的引用有三部:引入、注册、使用</li>
           </ul>
         </div>
     </div>
  </div>
</div>
</template>

<script>
export default {

}
</script>

<style lang="css" scoped>
    .div1{
        font-size: 20px;
    }
    ul{
        list-style: none;
        font-size: 22px;
    }
    li{
        font-size: 16px
    }
</style>
