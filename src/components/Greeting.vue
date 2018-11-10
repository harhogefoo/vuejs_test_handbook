<template lang="pug">
  div {{ greeting }}
</template>

<script>
export default {
  name: "Greeting",

  data() {
    return {
      greeting: "Vue and TDD"
    };
  }
};
</script>
