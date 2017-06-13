<template lang="html">
    <li class="list-group-item" @click="selectNote">
        <h4>{{this.note.title}}</h4>
        <p>{{this.note.date}}</p>
        <!-- <button type="button" class="btn btn-danger">删除</button> -->
    </li>
</template>

<script>
export default {
    name:'Vitem',
    data(){
        return{

        }
    },
    props:{
        note:Object
    },
    methods:{
        // li点击事件
        selectNote(){
            this.$store.commit('selectNote',this.note)
        }
    }
}
</script>

<style scoped>
    li{
        cursor: pointer;
    }
    li:hover{
        background-color: rgb(228, 238, 246);
    }
    p{
        text-align: center;
    }
    button{
        margin-left: 70%;
    }

</style>
