<template>
  <vl-map
    :load-tiles-while-animating="true"
    :load-tiles-while-interacting="true"
    style="height: 100%"
    ref="viewer"
    >
    <vl-view :center.sync="center" :zoom.sync="zoom" :rotation.sync="rotation"></vl-view>

    <vl-layer-tile>
      <vl-source-osm></vl-source-osm>
    </vl-layer-tile>
  </vl-map>
</template>

<style scoped>
</style>

<script>
import Vue from 'vue';
import VueLayers from 'vuelayers';

import 'vuelayers/lib/style.css';

Vue.use(VueLayers);

export default {
  data () {
    return {
      center: [0, 0],
      zoom: 3,
      rotation: 0
    };
  },
  mounted () {
    window.addEventListener('resize', this.updateSize);
  },
  beforeDestroy () {
    window.removeEventListener('resize', this.updateSize);
  },
  methods: {
    updateSize () {
      console.log('resize');
      this.$refs.viewer.updateSize();
    }
  }
};
</script>
