<template lang="html">
  <div class="">
    <h3>{{launch.flight_number}}</h3>
    <!-- <launch-patch-image :imageURL="launch.links.mission_patch_small"> </launch-patch-image> -->
    <h3>{{launch.mission_name}}</h3>
    <p>{{launch.details}}</p>
  </div>
</template>

<script>
import { eventBus } from '@/main.js';
import LaunchPatchImage from '@/components/LaunchPatchImage.vue';

export default {
  name: 'launch-detail',
  props: ['launch'],
  components: {
    "launch-patch-image": LaunchPatchImage
  }
}

</script>

<style lang="css" scoped>
</style>
