<template>
  <div>
    <h1>Push Notification Test</h1>
    <form>
      <textarea
        v-model="message"
        cols="45"
        rows="10"
        style="resize: none;"
      />
      <br/>
      <input
        :disabled="!isPermiitted"
        type="submit"
        value="Notify Me"
        @click.prevent="notify"
      />
    </form>
    <button
      v-if="!isPermiitted"
      @click="askPermission"
    >
      Enable notifications
    </button>
  </div>
</template>
<script>
export default {
  name: 'App',
  data () {
    return {
      message: '',
      isPermiitted: false
    }
  },
  computed: {
    img: () => require('@/assets/logo.png')
  },
  created() {
    this.isPermiitted = Notification.permission === 'granted'
  },
  methods: {
    askPermission () {
      Notification.requestPermission()
        .then(res => this.isPermiitted = res === 'granted')
        .catch(err => console.error(err))
    },
    notify () {
      return new Notification('Push Notification Test', {
        image: this.img,
        body: this.message
      })
    }
  }
}
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

input[type="submit"], button {
  width: 25%;
}
</style>
