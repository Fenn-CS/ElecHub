<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <b-button href="/#/monitor">
      Get Started
    </b-button>
    <h2>Know more, MS IoTHub Hackaton</h2>
    <ul>
      <li>
        <a
        href="https://azurehacks.devpost.com/details/resources"
        target="_blank"
        >
        Azure IoT Serverless Hackathon
      </a>
    </li>
    <li>
      <a
      href="http://vuex.vuejs.org/"
      target="_blank"
      >
      Github
    </a>
  </li>

</ul>
</div>
</template>

<script>
export default {
  name: 'Welcome',
  data () {
    return {
      msg: 'Welcome to ElecHub, a remote monitoring/control solution'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}

</style>
