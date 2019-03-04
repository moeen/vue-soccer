<template>
  <div class="home" v-if="dataRecived">
    <match-day :day="dayNumber" @onClick="changeDay"></match-day>
    <div v-for="(league, index) in showingResult" :key="index">
      <h3 class="title">
        {{ league.info.title }}
      </h3>
      <match-result
        v-for="match in league.data"
        :key="match.match_id"
        :home-name="match.host_name"
        :home-logo="match.host_logo"
        :home-goals="match.host_goal"
        :guest-name="match.guest_name"
        :guest-logo="match.guest_logo"
        :guest-goals="match.guest_goal"
        :time="match.match_time_jalali">
      </match-result>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import matchResult from '@/components/matchResult.vue';
import matchDay from '@/components/matchDay.vue';

export default {
  name: 'home',
  components: {
    matchResult,
    matchDay,
  },
  data() {
    return {
      result: {},
      showingResult: {},
      dataRecived: false,
      dayNumber: 0,
    };
  },
  created() {
    axios.get('https://cors-anywhere.herokuapp.com/https://api.aparat.com/fa/v1/aparat/sport/footballmatchlive')
      .then((res) => {
        this.result = res.data.data;
        this.showingResult = res.data.data.attributes.data.today.data;
        this.dataRecived = true;
      });
  },
  methods: {
    changeDay(day) {
      this.dayNumber = day;
    },
  },
  watch: {
    dayNumber(day) {
      if (day === -1) {
        this.showingResult = this.result.attributes.data.yesterday.data;
      } else if (day === 0) {
        this.showingResult = this.result.attributes.data.today.data;
      } else if (day === 1) {
        this.showingResult = this.result.attributes.data.tomorrow.data;
      }
    },
  },
};
</script>

<style scoped lang="scss">
.home {
  text-align: center;
  .title {
    margin-top: 35px;
    margin-bottom: 10px;
  }
}
</style>
