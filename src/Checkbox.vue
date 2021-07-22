<template>
  <label class="checkbox">
    <input
      type="checkbox"
      :value="value"
      :checked="isChecked"
      @change="onChange"
    >{{ label }}
  </label>
</template>

<script>
import { defineComponent } from 'vue';

export default defineComponent({
  props: {
    modelValue: {
      type: Array,
      required: true,
    },
    value: {
      type: String,
      required: true,
    },
    label: {
      type: String,
      required: true,
    },
  },
  emits: [
    'update:modelValue',
  ],
  data() {
    return {
      key: 10,
    };
  },
  computed: {
    isChecked() {
      return this.modelValue.includes(this.value);
    },
  },
  methods: {
    onChange(event) {
      const updatedModel = [...this.modelValue];

      if (event.target.checked) {
        updatedModel.push(this.value);
      } else {
        updatedModel.splice(updatedModel.indexOf(this.value), 1);
      }
      this.$emit('update:modelValue', updatedModel);
    },
  },
});
</script>
