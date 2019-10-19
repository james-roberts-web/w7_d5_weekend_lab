<template lang="html">
  <div class="">
    <ul>
      <h3>Launches:</h3>
      <launch-list-item v-for="(launch, index) in launches" :launch="launch" :key="index" ></launch-list-item>
    </ul>
  </div>
</template>

<script>

import LaunchListItem from '@/components/LaunchListItem.vue';

export default {
  name: 'launch-list',
  props: ['launches'],
  components: {
    'launch-list-item': LaunchListItem
  }
};
</script>

<style lang="css" scoped>
</style>
