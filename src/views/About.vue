<template>
  <div class="about">
    <h1>{{ test }}</h1>
    <button @click="_focus">test</button><br><br>
    <input-component ref="input1" v-next-input="'input2'" /><br><br>
    <input-component ref="input2" v-next-input="'select1'" /><br><br>
    <select-component ref="select1" />
  </div>
</template>

<script>
// import TC from '@/components/TC.vue';
import InputComponent from '@/components/InputComponent.vue';
import SelectComponent from '@/components/SelectComponent.vue';

export default {
  name: 'About',
  components: { InputComponent, SelectComponent },
  data() {
    return {
      test: '11',
      // next: null,
    };
  },
  computed: {
    input1() {
      return this.$refs.input1;
    },
    input2() {
      return this.$refs.input2;
    },
  },
  methods: {
    _focus() {
      this.$refs.ic.$el.focus();
    },
  },
  mounted() {},
  directives: {
    'next-input': {
      inserted(el, binding, vnode) {
        const $this = vnode.context;
        el.addEventListener('keyup', (e) => {
          if (e.keyCode === 13) {
            $this.$refs[binding.value].$el.focus();
          }
        });
      },
    },
    'next-click': {
      inserted(el, binding, vnode) {
        const $this = vnode.context;
        el.addEventListener('keyup', (e) => {
          if (e.keyCode === 13) {
            $this.$refs[binding.value].$el.click();
          }
        });
      },
    },
  },
};
</script>

<style lang="scss">
</style>
