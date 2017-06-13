<template>
<div id="app">
  <nav class="navbar navbar-default">
    <div class="container-fluid">
      <div class="navbar-header">
        <a class="navbar-brand" href="#">
        <img alt="Brand" src="./assets/logo.png" width="32">
      </a>
      </div>
      <ul class="nav navbar-nav">
        <li>
          <router-link to="/">主页</router-link>
        </li>
        <li>
          <router-link to="/note">笔记</router-link>
        </li>
      </ul>
    </div>
  </nav>
  <!-- 过渡效果  切换两个页面，主页和笔记页面 -->
  <transition name="fade">
    <router-view></router-view>
  </transition>
</div>
</template>

<script>
import 'bootstrap/dist/css/bootstrap.min.css'
import axios from 'axios'
export default {
  name: 'app',
  data(){
      return{

      }
  },
  methods:{

  },
  mounted() {

        axios.get('http://127.0.0.1:7428/api/comments')
            .then(function(response) {
                console.log(response.data);
                this.$store.state.notes = response.data;
            }.bind(this))
            .catch(function(error) {
                console.log(error);
            });
    }

}
</script>

<style scoped>
.fade-enter-active {
  transition: all .3s .3s ease;
}

.fade-enter {
  transform: translateY(-30px);
  opacity: 0;
}

.fade-leave-active {
  transition: all .3s ease;
  transform: translateY(30px);
  opacity: 0;
}
</style>
