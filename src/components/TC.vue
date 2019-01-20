<template>
  <div class="tc">
    <p>test component</p>
    <input ref="tInput" @keyup="tKeyup" /><br><br>
    <input ref="nInput" @keyup="nKeyup" />
  </div>
</template>

<script>
export default {
  name: 'TC',
  data() {
    return {
      test: 1,
    };
  },
  methods: {
    tKeyup(e) {
      if (e.keyCode === 13) {
        this.$refs.nInput.focus();
      }
    },
    nKeyup(e) {
      if (e.keyCode === 13) {
        this.$refs.nInput.blur();
      }
    },
  },
  directives: {},
  mounted() {
    this.$refs.tInput.focus();
  },
};
</script>

<style>

</style>
