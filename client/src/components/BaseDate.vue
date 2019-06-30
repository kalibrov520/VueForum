<template>
  <span 
  :title="timestamp | diffFromNow"
  >
  {{timestamp | timeStampToDateTime}}
  </span>
</template>

<script>
import moment from 'moment'
export default {
  props: {
    timestamp: {
      required: true,
      type: Number
    }
  },

  filters: {
    timeStampToDateTime(date) {
      return moment.unix(date).format("MMMM Do YYYY, h:mm:ss a");
    },

    diffFromNow(date) {
      return moment.unix(date).fromNow();
    }
  }
};
</script>

