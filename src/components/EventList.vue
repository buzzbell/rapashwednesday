<template>
  <div class="class-times">
    <!--
    The _editable attribute makes the next
    DOM-element clickable so the sidebar can
    show the right component.
    -->
    <div v-editable="blok" class="class-times__inner">
      <h2>
        <!--
        You can access every attribute you
        define in the schema in the blok variable
        -->
      </h2>
      <ul id="upcoming-events">
        <li v-for="event in this.blok.events">
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
    }
  },
  methods: {
    getEventDate (eventDate) {
      let dateTime = new Date(eventDate)
      let month = dateTime.getMonth()
      let date = dateTime.getDate()
      let year = dateTime.getYear()
      return `${month}/${date}/${year}`
    }
  }
}
</script>
