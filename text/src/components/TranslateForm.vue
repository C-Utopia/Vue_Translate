<template>

<div id="translateForm" class="row">

    <div class=" col-md-6 col-md-offset-3" >
<form  v-on:submit="formSubmit" transForm class='well form-inline' >

    <input type="text" v-model="textToTranslate" class="form-control form-input" placeholder="请输入要翻译的内容..">

    <select  class="form-control" v-model="language">
        <option value="en" >English</option>
        <option value="zh" >中文</option>
        <option value="ko" >韩文</option>
        <option value="jv" >日文</option>
        
    
    </select>

    <input type="submit" value="翻译" class=" btn btn-info">
</form>

</div>
</div>
</template>
<script>
export default {
  name: "translateForm",
  data() {
    return {
      textToTranslate: "",
      language: ""
    };
  },
  methods: {
    formSubmit: function(e) {
      //   alert('c')
      console.log(this.language);
      console.log(this.textToTranslate);
      this.$emit("formSubmit", this.textToTranslate, this.language);
      e.preventDefault();
    }
  },

  created: function() {
    this.language = "en";
  }
};
</script>
<style>
#transForm{
    border: 1px #ccc solid;
}
.form-input{
    /* border: 0px;
     */
}
</style>
