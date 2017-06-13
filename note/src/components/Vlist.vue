<template lang="html">
    <div class="panel panel-default">
    <div class="panel-body">
        <button type="button" class="btn btn-primary" @click="addNote">添加笔记</button>
        <hr/>
        <ul class="list-group">
            <Vitem v-for="(note,index) in getNotes" :key="index" :note="note"></Vitem>
        </ul>
    </div>
  </div>
</template>

<script>
import Vitem from './Vitem'
export default {
    name:'Vlist',
    data(){
        return{

        }
    },
    methods: {
        addNote() {

            var min = 1;
            var max = 1000000;
            var num = Math.random() * (max - min) + min;
            num = Math.round(num);

            if (this.$store.state.note.title) {
                //   需要触发一个mutatuons执行,必须使用commit方法
                this.$store.commit('addNote', {
                    id: num,
                    title: this.$store.state.note.title,
                    date: new Date().toLocaleString(),
                    markdown: this.$store.state.note.markdown
                })
                // console.log(this.$store.state.note);

            } else {
                alert("没有笔记可以添加");
            }


        }
    },
    computed:{
        getNotes(){
            return this.$store.state.notes;
        }
    },
    components:{
        Vitem
    }
}
</script>

<style lang="css">
    button{
        outline: none;
    }
</style>
