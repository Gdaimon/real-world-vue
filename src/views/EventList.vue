<template>
  <h1>Events for good</h1>
  <div class="events">
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<script>
// @ is an alias to /src
import EventCard from "@/components/EventCard.vue";
// import axios from "axios";
import EventService from "@/services/EventService.js";

export default {
  name: "EventList",
  components: {
    EventCard,
  },
  data() {
    return {
      events: null,
    };
  },
  async created() {
    // try {
    //   const response = await axios.get(
    //     "https://my-json-server.typicode.com/Code-Pop/Real-World_Vue-3/events"
    //   );
    //   // console.log(response);
    //   this.events = response.data;
    // } catch (error) {
    //   console.log(error);
    // }
    try {
      const response = await EventService.getEvents();
      // console.log(response);
      this.events = response.data;
    } catch (error) {
      console.log(error);
    }
  },
};
</script>
<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
