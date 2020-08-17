<template>
	<div>
		<home-header></home-header>
		<home-swiper :list="swiperList"></home-swiper>
		<home-icons :list="iconList"></home-icons>
		<home-recommend :list="recommendList"></home-recommend>
		<home-weekend :list="weekendList"></home-weekend>
	</div>
</template>

<script type="text/javascript">
import HomeHeader from './components/Header.vue'
import HomeSwiper from './components/Swiper.vue'
import HomeIcons from './components/Icons.vue'
import HomeRecommend from './components/Recommend.vue'
import HomeWeekend from './components/Weekend.vue'
import axios from 'axios'
import {mapState} from 'vuex'

export default {
  name: 'Home',
  components: {
    HomeHeader,
    HomeWeekend,
    HomeRecommend,
    HomeIcons,
    HomeSwiper
  },
  data : function() {
  	return {
      lastCity : '',
  		swiperList : [],
  		iconList : [],
  		recommendList : [],
  		weekendList : [],
  	}
  },
  computed : {
    ...mapState(['city'])
  },
  mounted : function () {
    this.lastCity = this.city
  	this.getHomeInfo();
  },
  activated () {
    if(this.lastCity !== this.city) {
      this.lastCity = this.city
      this.getHomeInfo()
    }
  },
  methods : {
  	getHomeInfo : function () {
  		axios.get('/api/index.json?city=' + this.city)
  			.then(this.getHomeInfoSucc)
  	},
  	getHomeInfoSucc : function (res) {
  		var res = res.data;
  		if(res.ret && res.data){
  			var data = res.data
  			this.swiperList = data.swiperList
  			this.iconList = data.iconList
  			this.recommendList = data.recommendList
  			this.weekendList = data.weekendList
  		}
  	}
  }
}
</script>

<style>

</style>
