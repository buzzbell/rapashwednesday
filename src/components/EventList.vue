<template>
  <div class="event-list">
    <a name="shows"></a>
    <!--
    The _editable attribute makes the next
    DOM-element clickable so the sidebar can
    show the right component.
    -->
    <div v-editable="blok" class="class-times__inner">
      <h3>Upcoming Shows</h3>
      <table class="table left-align" width="100%" id="upcoming-events">
        <span v-if="this.upcomingEvents.length > 0">
          <tr>
            <th>Date</th>
            <th>Venue</th>
            <th>Location</th>
          </tr>
          <tr v-for="event in this.upcomingEvents" >
            <td class="table-cell">{{ getEventDate(event.date) }}</td>
            <td class="table-cell">{{ event.venue }}</td>
            <td>{{ event.location }}</td>
          </tr>
        </span>
        <span class="no-upcoming-shows" v-else>
          No upcoming shows currently.
        </span>


      </table>
      <h3>Past Shows</h3>
      <table class="table left-align" width="100%" id="past-events">
        <tr>
          <th>Date</th>
          <th>Venue</th>
          <th>Location</th>
        </tr>
        <tr v-for="event in this.pastEvents">
          <td class="table-cell">{{ getEventDate(event.date) }}</td>
          <td class="table-cell">{{ event.venue }}</td>
          <td>{{ event.location }}</td>
        </tr>
      </table>
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
        let eventDate = new Date(event.date.replace(/\s/, 'T'))
        let currentDate = new Date()
        return eventDate > currentDate
      })
      return upcomingEvents
    },
    getPastEvents (events) {
      let pastEvents = events.filter(function (event) {
        let eventDate = new Date(event.date.replace(/\s/, 'T'))
        let currentDate = new Date()
        return eventDate < currentDate
      })
      return pastEvents
    },
    getEventDate (eventDate) {
      let dateTime = new Date(eventDate.replace(/\s/, 'T'))
      let month = dateTime.getMonth() + 1
      let date = dateTime.getDate()
      let year = dateTime.getFullYear()
      return `${month}/${date}/${year}`
    },
    isUpcomingEvent (event) {
      let eventDate = new Date(event.date.replace(/\s/, 'T'))
      let currentDate = new Date()
      return eventDate > currentDate
    }
  }
}
</script>

<style lang="scss" scoped>
h3 {
  color: #2c3e50;
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

table {
  border-collapse: collapse;
  border: 1px solid #BC4975;
  th {
    padding: 8px;
  }
  tr:nth-child(odd) {
    background-color: #f2f2f2;
  }
  tr:first-child {
    background-color: #BC4975;
    color: white;
  }
  td {
    padding: 8px;
  }
}
</style>
