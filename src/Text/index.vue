<template>
  <component
    :class="[
      transform && $style[`text--transform-${transform}`],
      color && $style[`text--color-${color}`],
      align && $style[`text--align-${align}`],
      $style[`text--type-${type}`],
      $style.text,
    ]"
    v-on="$listeners"
    v-bind="$attrs"
    :is="tag"
  >
    <slot />
  </component>
</template>

<script>
export default {
  name: 'TextComponent',
  props: {
    transform: String,
    color: String,
    align: String,
    type: String,
    as: String,
  },
  computed: {
    tag() {
      return this.as || this.$style[this.type] || 'span';
    },
  },
};
</script>

<style src="./Text.module.scss" lang="scss" module />
