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
        <li v-for="event in this.blok.events">
          <div v-if="isUpcomingEvent(event)">
            {{ getEventDate(event.date) }}
            {{ event.venue }}
            {{ event.location }}
          </div>
        </li>
      </ul>
      <h2>
        Past Events
      </h2>
      <ul id="upcoming-events">
        <li v-for="event in this.blok.events">
          <div v-if="!isUpcomingEvent(event)">
            {{ getEventDate(event.date) }}
            {{ event.venue }}
            {{ event.location }}
          </div>
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
    }
  },
  methods: {
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
