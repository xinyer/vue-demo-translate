<template>
  <div id="translateForm">
    <form v-on:submit="formSubmit">
      <input type="text" placeholder="input text to translate" v-model="textToTranslate">
      <select v-model="language">
        <option value="en">English</option>
        <option value="th">Thai</option>
        <option value="fr">French</option>
        <option value="ko">Korean</option>
      </select>
      <input type="submit" value="go">
    </form>
  </div>
</template>

<script>

export default {
  name: 'translateForm',
  data: function() {
    return {
      textToTranslate: "",
      language: ""
    }
  },
  methods: {
    formSubmit:function(event) {
      this.$emit("formSubmit", this.textToTranslate, this.language)
      event.preventDefault()
    }
  },
  created: function() {
    this.language = "en"
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
