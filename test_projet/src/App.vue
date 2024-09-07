<template>
  <div>
    <h1>Carte Leaflet</h1>
    <MapComponent />
  </div>
</template>

<script>
import MapComponent from './components/MapComponent.vue';

export default {
  name: 'App',
  components: {
    MapComponent
  }
};
</script>
