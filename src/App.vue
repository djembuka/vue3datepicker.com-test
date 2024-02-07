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
        label: 'Календарь',
        name: 'DATE',
        required: true,
        value: '28.02.2024',
        hint_external:
          'Подсказка для checkbox может быть неожиданно очень длинной.',
        dependency: 'id6',
      },
      range: {
        property: 'date',
        type: 'range',
        id: 'id45',
        label: 'Календарь',
        name: 'DATE',
        required: true,
        value: ['20.02.2024', '28.02.2024'],
        hint_external:
          'Подсказка для checkbox может быть неожиданно очень длинной.',
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

:root {
  --slr2-background: #fcfcfc;
  --slr2-buttons: #0a16aa;
  --slr2-color: #000;
  --slr2-light: #f7f9ff;
  --slr2-font-size-sm: 14px;
  --slr2-font-size: 16px;
  --slr2-gap-big: 30px;
  --slr2-gap: 24px;
  --slr2-gap-middle: 16px;
  --slr2-padding: 16px;
}
#app {
  font-family: 'Open Sans', sans-serif;
  width: 1000px;
  margin: 0 auto;
  padding: 50px;
}
#app a {
  text-decoration: none;
  color: cornflowerblue;
}
#app hr {
  margin: 20px;
  border: none;
}
</style>
