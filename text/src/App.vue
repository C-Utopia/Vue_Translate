<template>
  <div id="app" >
     <br>
   <h1>西翻译</h1>
   <h6 class="text-muted">{{en}} </h6>
   <h6 class="text-muted">{{ch}} </h6>
  
<TranslateForm v-on:formSubmit="translateText"></TranslateForm>

<TranslateOutput v-text="translatedText"></TranslateOutput>

<Music></Music>

  </div>
  
</template>

<script>
import TranslateForm from "./components/TranslateForm";
import TranslateOutput from "./components/TranslateOutput";
import Music from "./components/Music";
export default {
  name: "App",
  components: {
    TranslateForm,
    TranslateOutput,
    Music
  },
  data() {
    return {
      translatedText: "",
      en: "",
      ch:"",
     
    };
  },
  methods: {
    translateText: function(text, language) {
     
      this.$http
        .get(
          "https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20180210T084703Z.3ee3dea5db93dbe1.1271e89c0acaadfc5bf0af5dc26eead2de2f1bba&lang=" +
            language +
            "&text=" +
            text
        )
        .then(response => {
          this.translatedText = response.body.text[0];
          console.log(response);
        });
    },

  },
  created: function() {


// 加载mock数据
   this.$http.get('http://localhost:3000/sentence').then(function(res){

     let en=res.data.enArr,
         ch=res.data.chArr;
     
    let num=Math.floor(Math.random()*en.length)
    this.en=en[num];
    this.ch=ch[num];
   })



    

  }
};
</script>

<style>
body{
  overflow: hidden;
}
#app {
  text-align: center;
}

</style>
