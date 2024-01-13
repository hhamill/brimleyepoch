<template>
  <div>
    <label for="startdate">Start Date:</label>
    <input type="date" id="startdate" v-model="startdate" @change="updateOutput" />
</div>
<div>
    <label for="enddate">End Date:</label>
    <input type="date" id="enddate" v-model="enddate" @change="updateOutput" />

    <div>
      <p>{{ output }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      startdate: '',
      enddate: '',
      output: ''
    };
  },
  methods: {
    updateOutput() {
      var startDateDate = new Date(this.startdate);
      var endDateDate = new Date(this.enddate);

      if (this.startdate == '' || this.enddate == '') { return; }

      let dayDelta = endDateDate.getTime() - startDateDate.getTime();
 
    // To calculate the no. of days between two dates
      let dayDiff = Math.round(dayDelta / (1000 * 3600 * 24));

      let brimley = dayDiff / 18530;
      this.output = `The span between ${startDateDate.toISOString().split('T')[0]} and ${endDateDate.toISOString().split('T')[0]} is ${brimley} Brimleys`;
    }
  }
};
</script>

<style scoped>
/* Your component-specific styles go here */
</style>