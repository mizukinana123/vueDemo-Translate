<template>
  <div id="translateForm" class='row'>
    <div class="col-md-6 col-md-offset-3">
      <form v-on:submit='formSubmit' class='well form-inline' id='transForm'>
        <input type="text" placeholder="输入需要翻译的内容" v-model='textToTranslate' class='form-control'>
        <select v-model='language' class='form-control'>
          <option value="en">English</option>
          <option value="ru">Russian</option>
          <option value="ko">Korean</option>
          <option value="ja">Janpenese</option>
        </select>
        <input type="submit" value='翻译' class='btn btn-primary'>
      </form>
    </div>

  </div>
</template>

<script>
  export default {
    name: 'translateForm',
    data() {
      return {
        textToTranslate: '',
        language: ''
      }
    },
    methods: {
      formSubmit: function (e) {
        this.$emit('formSubmit', this.textToTranslate, this.language);
        e.preventDefault();

      }
    },
    created: function () {
      this.language = 'en';
    }
  }

</script>


<style scoped>
  #transForm {
    border: 1px solid #ccc;
    border-radius: 10px;
  }

</style>
