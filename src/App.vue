<template>
  <div id="main-app" class="container">
    <h4>{{ title }}</h4>
    <font-awesome-icon icon="plus" />Add Appointment
    <div v-for="(item, i) in appointments" v-bind:key="i">
      <h4>{{item.petName}} </h4>
      <p>{{item.aptNotes}} </p>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: 'MainApp',
  data: function () {
    return {
      title: "Appointment List",
      appointments: []
    };
  },
  mounted() {
    axios
      .get("./data/appointments.json")
      .then(response => (this.appointments = response.data))
  }
};
</script>
