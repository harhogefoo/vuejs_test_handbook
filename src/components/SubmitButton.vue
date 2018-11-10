<template lang="pug">
div
  span(v-if="isAdmin") 管理者権限を実行する
  span(v-else) 権限がありません
  button {{ msg }}
</template>

<script>
export default {
  name: 'Submitbutton',

  props: {
    msg: {
      type: String,
      required: true
    },
    isAdmin: {
      type: Boolean,
      default: false
    }
  }
}
</script>
