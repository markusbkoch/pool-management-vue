<template>
  <div>
    <div class="px-4 mb-4 overflow-hidden">
      <p class="mb-3">Venenatis urna cursus eget nunc scelerisque viverra.</p>
    </div>
    <div
      class="text-left mb-7 mx-6 overflow-hidden border border-bottom-0 rounded-1"
    >
      <a
        v-for="(right, i) in rights"
        :key="i"
        @click="switchRight(i)"
        class="border-bottom p-3 d-block text-normal"
      >
        <Icon
          name="check"
          class="check v-align-middle mr-2"
          :class="{ 'text-blue': rights[i] }"
          size="28"
        />
        <span :class="{ 'text-gray': rights[i] }">{{ makeTitle(i) }}</span>
      </a>
    </div>
  </div>
</template>

<script>
import capitalize from 'lodash/capitalize';
import startCase from 'lodash/startCase';

export default {
  props: ['value'],
  data() {
    return {
      rights: {}
    };
  },
  methods: {
    makeTitle(str) {
      return capitalize(startCase(str).toLowerCase());
    },
    switchRight(right) {
      this.rights[right] = !this.rights[right];
      this.$emit('input', this.rights);
    }
  },
  created() {
    this.rights = this.value;
  }
};
</script>
