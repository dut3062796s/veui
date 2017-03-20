<template>
  <button class="veui-button" v-bind="attrs" @click="$emit('click', $event)"><template v-if="!loading"><slot></slot></template><template v-else><slot name="loading">加载中…</slot></template></button>
</template>

<script>
export default {
  name: 'veui-button',
  props: {
    ui: String,
    disabled: Boolean,
    name: String,
    type: String,
    value: String,
    loading: Boolean
  },
  data () {
    let attrs = {
      ...this.$props
    }
    delete attrs.loading
    return { attrs }
  }
}
</script>

<style lang="less">
@import "../styles/theme-default/abstract.less";

.veui-button {
  padding: 0 20px;
  min-width: 94px;
  height: @veui-height-normal;
  border: 1px solid @veui-theme-color-primary;
  background-color: #fff;
  color: @veui-theme-color-primary;
  border-radius: 2px;

  &:hover,
  &:active {
    border-color: @veui-theme-color-hover;
    color: @veui-theme-color-hover;
    .veui-shadow();
  }

  &:active {
    background-color: @veui-theme-color-sup-4;
  }

  &:focus {
    outline: none;
  }

  &:disabled {
    &,
    &:focus,
    &:hover,
    &:active {
      border: none;
      background-color: @veui-gray-color-sup-3;
      color: @veui-text-color-weak;
      .veui-shadow(none);
    }
  }

  &[ui~="aux"] {
    border-color: @veui-gray-color-sup-1;
    color: @veui-text-color-normal;

    &:hover,
    &:active {
      border-color: @veui-gray-color-sup-1;
      color: @veui-text-color-strong;
      .veui-shadow();
    }

    &:active {
      background-color: @veui-gray-color-sup-3;
    }

    &:disabled {
      &,
      &:focus,
      &:hover,
      &:active {
        background-color: @veui-gray-color-sup-3;
        color: @veui-text-color-weak;
        .veui-shadow(none);
      }
    }
  }

  &[ui~="primary"] {
    border: none;
    background-color: @veui-theme-color-primary;
    color: #fff;
    .veui-shadow();

    &:hover,
    &:active {
      background-color: @veui-theme-color-hover;
      color: #fff;
      .veui-shadow(strong);
    }

    &:active {
      background-color: @veui-theme-color-active;
      .veui-shadow();
    }

    &:disabled {
      &,
      &:focus,
      &:hover,
      &:active {
        background-color: @veui-gray-color-sup-1;
        color: #fff;
        .veui-shadow(none);
      }
    }
  }

  &[ui~="large"] {
    min-width: 130px;
    height: @veui-height-large;
  }

  &[ui~="small"] {
    min-width: 80px;
    height: @veui-height-small;
  }

  &[ui~="round"] {
    border-radius: 50%;
    width: @veui-height-normal;
    min-width: auto;
    padding: 0;
    text-align: center;

    &[ui~="large"] {
      width: @veui-height-large;
    }

    &[ui~="small"] {
      width: @veui-height-small;
    }
  }
}
</style>