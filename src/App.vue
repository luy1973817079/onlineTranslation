<template>
  <div id="app">
    <h1>在线翻译</h1>
    <p class="text-muted">易用 / 简单 / 便捷</p>
    <translateForm v-on:submitText="text"></translateForm>
    <translateOut v-text="translatedText"></translateOut>
  </div>
</template>

<script>
import TranslateForm from './components/TranslateForm'
import TranslateOut from './components/TranslateOut'

export default {
  name: 'app',
  data(){
    return{
    translatedText:""
    }
  },
  components: {
    TranslateForm,
    TranslateOut
  },
  methods:{
    text:function(translateText,language){
     this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20171226T064131Z.e4b04d3055ff3e1e.f1455bf015d0d439bcc60287c79f4af23db9f73d&lang='+language+'&text='+translateText)
                .then((response)=>{
                  this.translatedText =response.body.text[0]
                })
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
