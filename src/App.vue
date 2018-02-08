<template>
  <div class="text-center" id="app">
   <h1>Word Translator</h1>
   <span>Crafted by</span><a href="http://jinas.org">Jinas</a>
   <TranslateForm v-on:formSubmit="translateText"></TranslateForm>
   <TranslateOutput v-text="translatedText"></TranslateOutput>

  </div>
</template>

<script>

import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'
export default {
  name: 'app',
  components:{

    TranslateForm,
    TranslateOutput

  },
  data: function(){
    return {
      translatedText:''
    }

  },
  methods: {
    translateText:function(text, language){
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20180208T185842Z.9d30718e5342936c.c17f87b5e09ad374c9cc51fdafb62fe32b72fde3&lang='+language+'&text='+text)
      .then((response) => {
        this.translatedText = response.body.text[0];
      });

    }
  }
}
</script>

<style>
body {
  background:#fefefe;
  
}
</style>
