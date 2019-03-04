<template>
  <div class="match-day">
    <button type="button" :class="['day-btn', {'active': day == 1}]"
      @click="changeDay(1)">فردا</button>
    <button type="button" :class="['day-btn', {'active': day == 0}]"
      @click="changeDay(0)">امروز</button>
    <button type="button" :class="['day-btn', {'active': day == -1}]"
      @click="changeDay(-1)">دیروز</button>
  </div>
</template>

<script>
export default {
  name: 'match-day',
  props: ['day'],
  methods: {
    changeDay(day) {
      this.$emit('onClick', day);
    },
  },
};
</script>

<style scoped lang="scss">
.match-day {
  margin-top: 20px;
  .day-btn {
    width: 110px;
    height: 35px;
    background-color: #2196F3;
    box-shadow: 0px 8px 15px rgba(0, 0, 0, 0.1);
    margin: 0;
    padding: 0;
    border: none;
    color: #E3F2FD;
    font-size: 1.1rem;
    transition: all 0.3s ease 0s;
    cursor: pointer;
  }
  .day-btn.active {
    background-color: #1565C0;
  }
  .day-btn:hover {
    box-shadow: 0px 15px 20px rgba(100, 181, 246, 0.4);
    transform: translateY(-7px);
  }
  .day-btn:first-child {
    border-top-left-radius: 5px;
    border-bottom-left-radius: 5px;
  }
  .day-btn:last-child {
    border-top-right-radius: 5px;
    border-bottom-right-radius: 5px;
  }
}
</style>
