<template>
  <div id="app">
    <h1>在线翻译</h1>
    <h5 class='text-muted'>简单/易用/便捷</h5>
    <translateForm v-on:formSubmit='translateText'></translateForm>
    <translateOutput v-text='translatedText'></translateOutput>
  </div>
</template>

<script>
  import translateForm from './components/TranslateForm.vue'
  import translateOutput from './components/TranslateOutput.vue'

  export default {
    name: 'app',
    data() {
      return {
        translatedText: ''
      }
    },
    components: {
      translateForm,
      translateOutput
    },
    methods: {
      translateText: function (text, language) {
        // alert(text);
        this.$http.get(
          'https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20171025T033857Z.17a90185f745fa7b.8a32244bb82b594f2b184d51d38181d24c65faf1&lang=' +
          language + '&text=' +
          text).then((response) => {
          console.log(response.body.text[0])
          this.translatedText = response.body.text[0];
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
