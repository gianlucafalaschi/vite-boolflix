<script>
import axios from 'axios';
import { store } from './store.js';
import AppFilter from './components/AppFilter.vue';

export default {
    components: {
      AppFilter,
    },
    data() {
      return {
        store,
      };
    },
    methods: {
    
    },
    mounted () {

    }
  }

</script>

<template>
  <AppFilter></AppFilter>
</template>

<style lang="scss">
@use'./style/generic';
</style>
