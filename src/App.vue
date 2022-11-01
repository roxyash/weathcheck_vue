<template>
<div>
 <div class="container">
        <div class="intro">
            <form action="" @submit.prevent="SearchMethod">
                <input  type="search" placeholder="Write address . . ." id="address" v-model="formData.address">
                <button type="submit">Search</button>
            </form>

            <div id="weather" class="weahter" v-if="isVisible">
                <h1 class="title">Weather info</h1>
                <span class="temp">Temp:<span class="temp_info">{{ info.temp }}</span></span>
                <span class="town">Town:<span class="town_info">{{ info.region }}</span></span>
                <span class="weather_info">{{ info.weather }}</span>
                <img v-if="weather == 'Clear'" class="weather_info_photo" src="images/sun.png" alt="">
                <img v-if="weather == 'Clouds'" class="weather_info_photo" src="images/cloud.png" alt="">
                <img v-if="weather == 'Rain'" class="weather_info_photo" src="images/cloud_rain.png" alt="">
                <img v-if="weather == 'Snow'" class="weather_info_photo" src="images/snow.png" alt="">
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
      isVisible: false,
      weather: false,
      info: {
        temp: '',
        town: '',
        weather: ''
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
      }).then(response => {
        this.info = response.data
        this.isVisible = true
        this.weather = this.info.weather
      })
        .catch(error => console.log(error))
    }
  }

}

</script>
