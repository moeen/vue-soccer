<template>
  <div class="match-result">
    <div class="home">
      <p class="name">
        {{ homeName }}
      </p>
      <img
        class="logo"
        :src="homeLogo"
        alt="home logo"
      />
      <span class="goals">
        {{ homeGoals }}
      </span>
    </div>
    <div class="guest">
      <span class="goals">
        {{ guestGoals }}
      </span>
      <img
        class="logo"
        :src="guestLogo"
        alt="guest logo"
      />
      <p class="name">
        {{ guestName }}
      </p>
    </div>
    <time class="time">{{ time }}</time>
  </div>
</template>

<script>
export default {
  name: 'match-result',
  props: [
    'homeName',
    'homeLogo',
    'homeGoals',
    'guestName',
    'guestLogo',
    'guestGoals',
    'time',
  ],
};
</script>

<style scoped lang="scss">
.match-result {
  position: relative;
  display: flex;
  flex-wrap: nowrap;
  margin: 15px auto;
  width: 50%;
  border-radius: 6px;
  background-color: #0d47a1;
  color: #e3f2fd;
  .home,
  .guest {
    width: 50%;
    justify-content: center;
    align-items: center;
    * {
      margin-left: 5px;
      margin-right: 5px;
      display: inline-block;
      vertical-align: middle;
    }
    .name {
      font-size: 1.1rem;
    }
    .goals {
      font-size: 1.3rem;
    }
    .logo {
      width: 40px;
      height: 40px;
    }
  }
  .home {
    text-align: right;
  }
  .guest {
    text-align: left;
  }
  .home:after {
    content: "-";
  }
  .time {
    position: absolute;
    right: 5px;
    top: 5px;
  }
}
@media (max-width: 920px) {
  .match-result {
    width: 98%;
    .home,
    .guest {
      .name {
        font-size: 1rem;
      }
      .goals {
        font-size: 1.1rem;
      }
      .logo {
        height: 30px;
        width: 30px;
      }
    }
  }
}
@media (max-width: 420px) {
  .match-result {
    width: 99%;
    .home,
    .guest {
      * {
        margin-left: 2px;
        margin-right: 2px;
      }
      .name {
        font-size: 0.7rem;
      }
      .goals {
        font-size: 0.85rem;
      }
      .logo {
        height: 22px;
        width: 22px;
      }
    }
  }
}
</style>
