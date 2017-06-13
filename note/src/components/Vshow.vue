<template lang="html">
    <div class="panel panel-default">
    <div class="panel-body">
        <button type="button" class="btn btn-info" @click="saveNote">保存笔记</button>
        <hr/>
        <div class="marked">
                <div class="title">
                    <input id="titleValue" type="text" placeholder="请输入文章标题" v-model="noteTitle">
                </div>
                <div class="editor">
                    <textarea id="markdownValue" name="name" rows="8" cols="8" v-model="content"></textarea>
                </div>
                <div class="screen" v-html="domarked"></div>
                <div style="display:none">
                    {{text}}
                </div>
                <div style="display:none">
                    {{text2}}
                </div>
            </div>
    </div>
  </div>
</template>

<script>
import marked from 'marked'
export default {
  name: 'Vshow',
  data() {
    return {
      noteTitle:'',
      content:''
    }
  },
  methods: {
      saveNote(){
          var titleValue = document.getElementById('titleValue').value;
          var markdownValue =  document.getElementById('markdownValue').value;


          if(titleValue){
              //将note保存到全局的note里
              this.$store.commit('saveNote',{
                  title:titleValue,
                  markdown:markdownValue
              })
              alert("保存成功");
          }else{
              alert("请填写标题");
          }

      }
  },
  computed: {
    domarked() {
      return marked(this.content);
    },

    // 获取note里的title
    // noteTitle(){
    //     return this.$store.state.note.title
    // },

    text2(){
        this.noteTitle = this.$store.state.note.title
        return  this.$store.state.note.title;
    },


    // 获取note里面的markdown
    // content(){
    //     return this.$store.state.note.markdown
    // }

    text(){
        this.content = this.$store.state.note.markdown
        return  this.$store.state.note.markdown;
    }

  },
  components: {

  }
}
</script>

<style scoped>
.marked {
  width: 50vw;
  margin: 2px auto;
  overflow: hidden;
}

.title input {
  width: 100%;
  height: 50px;
  padding: 10px;
  outline: none;
  border: 1px solid #ccc;
  border-bottom: none;
  border-radius: 5px 5px 0 0;
}

input::-webkit-input-placeholder {
  color: rgba(94, 204, 226, 0.62);
  font-weight: 200;
}

.editor,
.screen {
  width: 50%;
  height: 300px;
  float: left;
  border: 1px solid #ccc;
  box-sizing: border-box;
}

.editor {
  border-right: none;
  border-radius: 0 0 0 5px;
}

.screen {
  padding: 10px;
  background-color: rgba(140, 214, 143, 0.1);
  border-radius: 0 0 5px 0;
  word-wrap: break-word;
}

textarea {
  padding: 10px;
  height: 100%;
  width: 100%;
  border: none;
  background-color: rgba(208, 214, 140, 0.1);
}

textarea:focus {
  outline: none;
}
</style>
