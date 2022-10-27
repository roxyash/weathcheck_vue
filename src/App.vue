<template>
<div>
 <div class="container">
        <div class="intro">
            <form action="" @submit.prevent="SearchMethod">
                <input  type="search" placeholder="Write address . . ." id="address" v-model="formData.address">
                <button type="submit">Search</button>
            </form>

            <div class="weahter">
                <h1 class="title">Weather info</h1>
                <span class="temp">Temp:<span class="temp_info">32</span></span>
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
      formData: {
        address: ''
      }
    }
  },
  methods: {
    SearchMethod () {
      axios.get('http://localhost:8000/getweatherinfo/', {
        params: { address: this.formData.address }
        // headers: {
        //   accept: 'application/json'
        // }
      }).then(response => console.log(response))
    }
  }

}
</script>

<!-- name: 'SearchMethod',
data () {
  return {
    formData: {
      address: ''
    }
  }
},
methods: {
  SearchMethod () {
    axios.get('http://localhost:8000/getweatherinfo?address=%D0%9F%D1%80%D0%B5%D1%81%D0%BD%D0%B5%D0%BD%D1%81%D0%BA%D0%B0%D1%8F%20%D0%BD%D0%B0%D0%B1%D0%B5%D1%80%D0%B5%D0%B6%D0%BD%D0%B0%D1%8F').then(response => (this.info = response))
    // fetch('http://localhost:8000/getweatherinfo?address=%D0%9F%D1%80%D0%B5%D1%81%D0%BD%D0%B5%D0%BD%D1%81%D0%BA%D0%B0%D1%8F%20%D0%BD%D0%B0%D0%B1%D0%B5%D1%80%D0%B5%D0%B6%D0%BD%D0%B0%D1%8F',
    //   {
    //     method: 'GET',
    //     mode: 'cors',
    //     headers: {
    //       accept: 'application/json'
    //     }
    //   })
  }
} -->
