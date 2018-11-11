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
    async handleSubmitAsync() {
      try {
        await this.$http.get('/api/v1/register', { username: this.username })
      } catch(e) {
        throw Error('Something went wrong', e)
      }
    }
  }
}
</script>
