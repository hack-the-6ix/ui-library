<template>
  <div :class="$style.container">
    <div :class="[$style.cover, $style[`color--${color}`]]">
      <input
        v-bind="{ ...$attrs, ...formableProps }"
        v-on="$listeners"
        :class="$style.input"
        :checked="formValue"
        @input="handler"
        type="checkbox"
      />
      <div :class="$style.box">
        <Icon name="check" :class="$style.check" />
      </div>
    </div>
    <label :htmlFor="name" :class="$style.label" v-if="label || $slots.label">
      <slot name="label" v-if="$slots.label" />
      <span v-else>{{ label }}</span>
      <span v-if="required" :class="$style.label__asterisk"> *</span>
    </label>
  </div>
</template>

<script>
import formableMixin from '../utils/mixins/formableMixin';
import Icon from 'vue-awesome/components/Icon';
import 'vue-awesome/icons/check';
import Stack from '../Stack';

export default {
  name: 'Checkbox',
  components: {
    Stack,
    Icon,
  },
  mixins: [formableMixin],
  data() {
    return {
      dataValue: false,
    };
  },
  props: {
    label: String,
    color: {
      type: String,
      default: 'teal',
    },
  },
  methods: {
    handler(el) {
      this.formHandler({
        target: {
          value: el.target.checked,
        },
      });
    },
  },
};
</script>

<style src="./Checkbox.module.scss" lang="scss" module />
