<template>
  <div>
      <!-- access assets files -->
      <!-- img src="~/assets/logo.png" -->
      <!-- logo / -->
      <h1>Events</h1>
      <EventCard
        v-for="(event, index) in events"
        :key="index"
        :event="event"
        :data-index="index"
      />
  </div>
</template>

<script>
import Logo from '~/components/Logo.vue'
import EventCard from '~/components/EventCard.vue'

export default {
  components: {
    Logo
  },
  head() {
    return {
      title: 'Event Listing'
    }
  },
  // ES6 Destructuring syntax
  async asyncData({ $axios, error }) {
    try {
      const { data } = await $axios.get('http://localhost:3000/events')
        return {
          events: data
        }
    } catch(e){
      error({
        statusCode: 503,
        message: 'Unable to fetch events at this time. Please try again.'
      })
    }
  },
  components: {
    EventCard
  }
}
</script>

<style scoped>
</style>
