<template>
<div>
 <div class="container">
        <div class="intro">
            <form action="" @submit.prevent="SearchMethod">
                <input  type="search" placeholder="Write address . . ." id="address" v-model="formData.address">
                <button type="submit">Search</button>
            </form>

            <div id="weather" class="weahter">
                <h1 class="title">Weather info</h1>
                <span class="temp">Temp:<span class="temp_info">{{ info.temp }}</span></span>
                <span class="town">Town:<span class="town_info">Moscow</span></span>
                <span class="weather_info">Sunny</span>
                <img class="weather_info_photo" src="images/sun.png" alt="">
            </div>
        </div>
  </div>
</div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'SearchMethod',
  data () {
    return {
      info: {
        temp: '',
        weather: '',
        region: '',
        error: ''
      },
      formData: {
        address: ''
      }
    }
  },
  methods: {
    SearchMethod () {
      axios.get('http://localhost:8000/getweatherinfo/', {
        params: { address: this.formData.address }
      }).then(response => (this.info = response)).catch(error => console.log(error)).then(response => (console.log(response)))
    }
  }

}
</script>
