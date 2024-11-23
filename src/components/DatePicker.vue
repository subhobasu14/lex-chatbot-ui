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
      console.log("Date selected from function is ==========  ", modelData);
      if (modelData)  {
        const message = {
        type: 'human',
        text: modelData?.toDateString()
      };
      this.$store.dispatch('postTextMessage', message)
      }
      
    },
  },
};
</script>