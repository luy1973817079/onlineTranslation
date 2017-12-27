<template>
  <div id="translateForm" class="row">
  <div class="col-md-6 col-md-offset-3" >
    <form class="well form-inline" v-on:submit="formSubmit" >
          <input type="text" placeholder="请输入要翻译的内容" class="form-control" v-model="translateText">
          <select class="form-control" v-model="language">
            <option value="en">English</option>
            <option value="ru">Russian</option>
            <option value="ko">Korean</option>
            <option value="ja">Japanese</option>
          </select>
          <input type="submit" class="btn btn-primary" value="翻译">
        </form>
  </div>
  </div>
</template>

<script>

export default {
  name: 'translateForm',
  data:function(){
    return{
      translateText:"",
      language:""
    }
  },
  methods:{
    formSubmit:function(ev){
      this.$emit("submitText",this.translateText,this.language)
      ev.preventDefault();
    }
  },
  created:function(){
    this.language = "en"
  }
}
</script>

<style>

</style>
