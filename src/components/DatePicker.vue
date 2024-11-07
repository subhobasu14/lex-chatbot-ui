<template>
  <div>
      <VueDatePicker :model-value="date" :enableTimePicker="false" @update:model-value="handleDate" :state="false" />
    
  </div>
</template>

<script>
import VueDatePicker from '@vuepic/vue-datepicker';
import '@vuepic/vue-datepicker/dist/main.css';

export default {
  name: 'date-picker',
  components: {
    VueDatePicker,

  },
  data() {
    return {
      date: new Date(),
    };
  },
  computed: {
  },
  methods: {
    handleDate(modelData) {
      console.log("modelData selected from function is ==========  ", modelData);
      this.date.value = modelData;
      console.log("Date selected from function is ==========  ", this.date.value);
      // do something else with the data
      const message = {
        type: 'human',
        text: modelData.toDateString()
      };
      this.$store.dispatch('postTextMessage', message)
      },
  },
};
</script>