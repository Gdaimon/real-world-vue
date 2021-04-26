<template>
  <div v-if="event">
    <h1>{{ event.title }}</h1>
    <p>{{ event.time }} on {{ event.date }} @ {{ event.location }}</p>
    <p>{{ event.description }}</p>
  </div>
</template>

<script>
import EventService from "@/services/EventService.js";
export default {
  props: ["id"],
  data() {
    return {
      event: null,
    };
  },
  async created() {
    // fetch event (by id) and set local data
    try {
      const response = await EventService.getEvent(this.id);
      // console.log(response);
      this.event = response.data;
    } catch (error) {
      console.log(error);
    }
  },
};
</script>
