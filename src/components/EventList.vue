<template>
  <div class="class-times">
    <!--
    The _editable attribute makes the next
    DOM-element clickable so the sidebar can
    show the right component.
    -->
    <div v-editable="blok" class="class-times__inner">
      <h2>
        Upcoming Events
      </h2>
      <ul id="upcoming-events">
        <li v-for="event in this.upcomingEvents">
          {{ getEventDate(event.date) }}
          {{ event.venue }}
          {{ event.location }}
        </li>
      </ul>
      <h2>
        Past Events
      </h2>
      <ul id="upcoming-events">
        <li v-for="event in this.pastEvents">
          {{ getEventDate(event.date) }}
          {{ event.venue }}
          {{ event.location }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>

export default {
  props: ['blok'],
  data () {
    return {
      upcomingEvents: this.getUpcomingEvents(this.blok.events),
      pastEvents: this.getPastEvents(this.blok.events)
    }
  },
  methods: {
    getUpcomingEvents (events) {
      let upcomingEvents = events.filter(function (event) {
        let eventDate = new Date(event.date)
        let currentDate = new Date()
        return eventDate > currentDate
      })
      return upcomingEvents
    },
    getPastEvents (events) {
      let pastEvents = events.filter(function (event) {
        let eventDate = new Date(event.date)
        let currentDate = new Date()
        return eventDate < currentDate
      })
      return pastEvents
    },
    getEventDate (eventDate) {
      let dateTime = new Date(eventDate)
      let month = dateTime.getMonth() + 1
      let date = dateTime.getDate()
      let year = dateTime.getFullYear()
      return `${month}/${date}/${year}`
    },
    isUpcomingEvent (event) {
      let eventDate = new Date(event.date)
      let currentDate = new Date()
      return eventDate > currentDate
    }
  }
}
</script>

<style lang="scss" scoped>
h1, h2 {
  font-size: 2rem;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
