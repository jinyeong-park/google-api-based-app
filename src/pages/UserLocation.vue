<template>
  <section class ="ui two column centered grid">
    <div class="column">
      <form class="ui segment large form">
        <div class="ui message red"></div>
        <div class="ui segment">
          <div class="field">
            <div class="ui right icon input large">
              <input type="text" placeholder="Enter your address" />
              <i class="dot circle link icon" @click="locatorButtonPressed"></i>
            </div>
          </div>
          <button class="ui button"><i class="search icon"></i></button>

        </div>
      </form>
    </div>
  </section>
</template>

<script>
export default {
  methods: {
    locatorButtonPressed () {
      // check whether geolocation API is supported in user's browser
      if (navigator.geolocation) {
        navigator.geolocation.getCurrentPosition(
          position => {
            console.log(position.coords.latitute)
            console.log(position.coords.longitute)
          },
          error => {
            console.log(error.message)
          }
        )
      } else {
        console.log("Your browser does not support geolocation API")
      }
    }
  }
}
</script>

<style>
.ui.button,
.dot.circle.icon {
  background-color: #ff5a5f;
  color: white;
}
</style>