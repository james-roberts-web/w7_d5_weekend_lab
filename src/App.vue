<template lang="html">
  <div class="app-container">
    <div class="content-container">

      <header>
        <h1>Rocket Info</h1>
      </header>



      <div class="rocket-info">
        <rocket-list class="rocket-list" :rockets="rockets"></rocket-list>

        <rocket-detail class="rocket-detail" v:if="selectedRocket"
        :rocket="selectedRocket"></rocket-detail>

      </div>



      <div class="launch-info">

        <launch-list class="launch-list" :launches="launches"></launch-list>

        <launch-detail class="launch-detail" v:if="selectedLaunch"
        :launch="selectedLaunch"></launch-detail>
      </div>
    </div>
  </div>
</template>

<script>

import { eventBus } from '@/main.js';

import RocketList from '@/components/RocketList.vue';
import RocketListItem from '@/components/RocketListItem.vue';
import RocketDetail from '@/components/RocketDetail.vue';

import LaunchList from '@/components/LaunchList.vue';
import LaunchListItem from '@/components/LaunchListItem.vue';
import LaunchDetail from '@/components/LaunchDetail.vue';
import LaunchPatchImage from '@/components/LaunchPatchImage.vue';

export default {
  name: 'app',
  data() {
    return {
      rockets: [],
      launches:[],
      selectedRocket: "",
      selectedLaunch: ""
    };
  },

  components: {
    "rocket-list": RocketList,
    "rocket-detail": RocketDetail,
    "launch-list": LaunchList,
    "launch-detail": LaunchDetail,
    "launch-patch-image": LaunchPatchImage
  },

  mounted() {
    this.getRockets();
    this.getLaunches();
    eventBus.$on("rocket-selected", rocket => (this.selectedRocket = rocket));
    eventBus.$on("launch-selected", launch => (this.selectedLaunch = launch));
  },

  methods: {
    getRockets() {
      fetch('https://api.spacexdata.com/v3/rockets')
      .then(result => result.json())
      .then(data => this.rockets = data);
    },
    getLaunches() {
      fetch('https://api.spacexdata.com/v3/launches')
      .then(result => result.json())
      .then(launches => this.launches = launches)
    }
  }
}
</script>

<style lang="css" scoped>

.app-container {

  margin: 0 20%;
  font-family: Helvetica, Arial, sans-serif;
}
.content-container {
  display: contents;
  justify-content: center;
}

header {
  display: flex;
  justify-content: center;
}

.info {
  display:flex;
  justify-content: space-between;
}

.rocket-info, .launch-info {
  display: flex;
  justify-content: center;
}
.rocket-list, .launch-list {
  width:25%;
  border: 1px solid black;
  padding: 15px;
  margin: 5px;
}

.rocket-detail, .launch-detail {
  width:75%;
  border: 1px solid black;
  padding: 15px;
  margin: 5px;
}
</style>
