<template>
  <div id="app">
    <h1>在线翻译</h1>
    <h5>简单/易用/便捷</h5>
    <translate-form v-on:formSubmit="translateText"></translate-form>
    <translate-output :output="translateResult"></translate-output>
  </div>
</template>

<script>
import TranslateForm from "./components/TranslateForm"
import TranslateOutput from "./components/TranslateOutput"
export default {
  name: 'app',
  data: function() {
    return {
      translateResult:""
    }
  },
  components: {
    TranslateForm,
    TranslateOutput
  },
  methods: {
    translateText:function(text, language) {
      var key = "trnsl.1.1.20171026T081522Z.b82114432badd2af.6681744a2913b2467ad2f54fcc600cd3345ec5f3"
      var url = "https://translate.yandex.net/api/v1.5/tr.json/translate?key="+key+"&lang="+language+"&text=";
      this.$http.get(url + text).then((response) => {
        console.log(response.body.text[0])
        this.translateResult = response.body.text[0];
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
