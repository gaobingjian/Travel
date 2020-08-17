<template>
  <div>
    <city-header></city-header>
    <city-search :cities="cities"></city-search>
    <city-list
     :cities="cities"
     :hot="hotCities"
     :letter="letter"
    >
    </city-list>
    <city-alphabet 
      :cities="cities" 
      @change="handleLeterChange"
    >
    </city-alphabet>
  </div>
</template>

<script type="text/javascript">
  import axios from 'axios'
  import CityHeader from './components/Header.vue'
  import CitySearch from './components/Search.vue'
  import CityList from './components/List.vue'
  import CityAlphabet from './components/Alphabet.vue'

  export default {
    name: 'City',
    components : {
      CityHeader,
      CityAlphabet,
      CityList,
      CitySearch
    },
    data () {
      return {
        cities : {},
        hotCities : [],
        letter : ''
      }
    },
    mounted () {
      this.getCityInfo();
    },
    methods : {
      getCityInfo () {
        axios.get('/api/city.json')
          .then(this.handleGetCityInfoSucc)
      },
      handleGetCityInfoSucc (res) {
        var res = res.data
        if(res.ret && res.data) {
          var data = res.data
          this.cities = data.cities
          this.hotCities = data.hotCities
        }
      },
      handleLeterChange (letter) {
        this.letter = letter
      }
    }
  }
</script>

<style>

</style>
