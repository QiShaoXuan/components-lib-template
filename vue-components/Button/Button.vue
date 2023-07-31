<script>
export default {
  props: {
    disabled: {
      type: Boolean,
      default: false,
    },
    type: {
      type: String,
      default: 'default',
      validator(value) {
        return ['dashed', 'text', 'primary', 'default'].indexOf(value) >= 0;
      },
    },
  },
  computed: {
    classes() {
      return {
        ['disabled']: this.disabled,
      };
    },
  },
  methods: {
    onClick() {
      console.log('kk');
      if (this.disabled) {
        console.log('kk');
        return;
      }
      this.$emit('click');
    },
  },
};
</script>

<template>
  <button class="button" :class="classes" @click="onClick" :disabled="disabled">
    <slot></slot>
  </button>
</template>

<style lang="scss">
.button {
  background-color: #fff;
  border: 1px solid #dcdfe6;
  border-radius: 4px;
  color: #606266;
  cursor: pointer;
  display: inline-block;
  font-size: 14px;
  font-weight: 400;
  height: 32px;
  line-height: 1.5;
  outline: 0;
  padding: 0 15px;
  text-align: center;
  white-space: nowrap;
  -moz-user-select: none;
  -webkit-user-select: none;
  -ms-user-select: none;
  user-select: none;

  &:hover {
    border-color: #c0c4cc;
    color: #409eff;
  }
}
</style>
