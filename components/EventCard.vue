<template>
  <nuxt-link :to="'/event/' + event.id">
    <div class="event-card">
      <span> @ {{ event.time }} on {{ parsedDate }} </span>
      <h4 class="title">
        {{ event.title }}
      </h4>
      <span>{{ event.attendees.length }} attending</span>
    </div>
  </nuxt-link>
</template>

<script>
export default {
  name: 'EventCard',
  props: {
    event: {
      type: Object,
      default: null,
    },
  },
  computed: {
    parsedDate() {
      const eventDate = new Date(this.event.date)
      return eventDate.toDateString()
    },
  },
}
</script>
<style scoped>
.event-card {
  padding: 20px;
  margin-bottom: 24px;
  transition: all 0.2s linear;
  cursor: pointer;
}
.event-card:hover {
  transform: scale(1.01);
  box-shadow: 0 3px 12px 0 rgba(0, 0, 0, 0.2), 0 1px 15px 0 rgba(0, 0, 0, 0.19);
}
.event-card > .title {
  margin: 0;
}
.event-link {
  color: black;
  text-decoration: none;
  font-weight: 100;
}
.title {
  color: black;
  font-family: 'Times New Roman', Times, serif;
  font-size: 2rem;
}
</style>
