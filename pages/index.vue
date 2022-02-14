<template>
  <v-container>
    <event-editor v-model="event" />
    <v-btn
      fixed
      elevation="2"
      fab
      large
      bottom
      right
      color="primary"
      @click="submit"
    >
      Go!
    </v-btn>
  </v-container>
</template>

<script>
import EventEditor from '../components/EventEditor.vue'
export default {
  name: 'IndexPage',
  components: { EventEditor },
  data () {
    return {
      event: {
        title: '',
        description: '',
        date: []
      }
    }
  },
  head () {
    return {
      title: 'New Event'
    }
  },
  methods: {
    submit () {
      this.$store.dispatch('createEvent', {
        title: this.event.title.trim(),
        description: this.event.description.trim(),
        dates: this.event.dates
      })
        .then((id) => {
          this.$router.push(`/${id}`)
        })
    }
  }
}
</script>
