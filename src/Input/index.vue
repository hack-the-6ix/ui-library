<template>
  <LabelContainer v-bind="labelContainerProps">
    <input
      v-bind="{ ...$attrs, ...formableProps }"
      v-on="$listeners"
      :class="[$style.input, { [$style[`input--error`]]: formError }]"
      :placeholder="placeholder"
      :aria-invalid="!!formError"
      @input="formHandler"
      :value="formValue"
      :type="type"
    />
  </LabelContainer>
</template>

<script>
import LabelContainerMixin from '../LabelContainer/LabelContainerMixin';
import formableMixin from '../utils/mixins/formableMixin';
import LabelContainer from '../LabelContainer';

export default {
  name: 'Input',
  components: {
    LabelContainer,
  },
  props: {
    placeholder: String,
    type: String,
  },
  mixins: [LabelContainerMixin, formableMixin],
};
</script>

<style src="./Input.module.scss" lang="scss" module />
