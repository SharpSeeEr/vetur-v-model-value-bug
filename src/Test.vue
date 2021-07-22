<template>
  <div>
    <Checkbox
      v-for="color in colors"
      :key="color"
      v-model="selected"
      :value="color"
      :label="color"
    />
    {{ fo }}
  </div>
</template>

<script>
import * as _ from 'lodash'
import Checkbox from './Checkbox.vue';

export default {
  components: { Checkbox },
  props: ['foo', 'bar'],
  data() {
    return {
      colors: ['Red', 'Blue', 'Green'],
      selected: [];
    };
  },
}
</script>
