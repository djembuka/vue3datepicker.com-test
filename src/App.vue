<template>
  <div class="grid">
    <control-date-single
      :control="single"
      @input="inputSingle"
    ></control-date-single>
    <control-date-range
      :control="range"
      @input="inputRange"
    ></control-date-range>
  </div>
</template>

<script>
import ControlDateSingle from './components/ControlDateSingle.vue';
import ControlDateRange from './components/ControlDateRange.vue';

export default {
  name: 'App',
  data() {
    return {
      single: {
        property: 'date',
        type: 'single',
        id: 'id45',
        name: 'DATE',
        required: true,
        value: '28.02.2024',
        dependency: 'id6',
      },
      range: {
        property: 'date',
        type: 'range',
        id: 'id45',
        name: 'DATE',
        required: true,
        value: ['20.02.2024', '28.02.2024'],
        dependency: 'id6',
      },
    };
  },
  components: {
    ControlDateSingle,
    ControlDateRange,
  },
  methods: {
    inputSingle({ value }) {
      this.single.value = value;
    },
    inputRange({ value }) {
      this.range.value = value;
    },
  },
};
</script>

<style>
.grid {
  display: flex;
  justify-content: space-between;
}
</style>
