<template lang="pug">
div
  form(@submit.prevent='handleSubmitAsync')
    input(v-model='username' data-username)
    input(type='submit')
  div(class='message' v-show='submitted') {{ username }}さん、お問い合わせ、ありがとうございます。
</template>

<script>
export default {
  name: 'FormSubmitter',

  data() {
    return {
      username: '',
      submitted: false
    }
  },

  methods: {
    handleSubmit() {
      this.submitted = true
    },
    handleSubmitAsync() {
      return this.$http.get('/api/v1/register', { username: this.username })
        .then(() => {
          // メッセージを表示するなど
          this.submitted = true
        })
        .catch(e => {
          // エラーをハンドル
          throw Error('Something went wrong', e)
        })

    }
  }
}
</script>
