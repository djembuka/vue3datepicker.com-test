<template>
  <VueDatePicker
    v-model="date"
    @range-start="onRangeStart"
    @range-end="onRangeEnd"
    locale="ru"
    range
    multi-calendars
    ref="controlDateRange"
    :format="'dd.MM.yyyy'"
  ></VueDatePicker>
</template>

<script>
import VueDatePicker from '@vuepic/vue-datepicker';
import '@vuepic/vue-datepicker/dist/main.css';

export default {
  components: { VueDatePicker },
  data() {
    return {
      start: '',
    };
  },
  props: ['control'],
  emits: ['input'],
  computed: {
    date: {
      get() {
        let date = [];
        if (
          typeof this.control.value === 'object' &&
          this.control.value.length
        ) {
          this.control.value.forEach((d) => {
            if (typeof d === 'string') {
              const valueArray = d.split('.');
              if (valueArray.length && valueArray.length === 3) {
                date.push(`${valueArray[1]}/${valueArray[0]}/${valueArray[2]}`);
              }
            }
          });
        }

        return date;
      },
      set(value) {
        this.$emit('input', { value });
      },
    },
  },
  methods: {
    onRangeStart(start) {
      this.start = start;
    },
    onRangeEnd(end) {
      this.date = [this.formatDate(this.start), this.formatDate(end)];
      this.$refs.controlDateRange.closeMenu();
    },
    formatDate(date) {
      const d = new Date(date);
      let day = String(d.getDate());
      let month = String(d.getMonth() + 1);

      day = day.length === 1 ? `0${day}` : day;
      month = month.length === 1 ? `0${month}` : month;

      return `${day}.${month}.${d.getFullYear()}`;
    },
  },
};
</script>
